# Tóm tắt

### Nội dung chính

- Với một `key` đầu vào, bảng băm có thể truy xuất `value` tương ứng trong thời gian $O(1)$, đạt hiệu quả rất cao.
- Các thao tác phổ biến trên bảng băm bao gồm truy vấn, thêm các cặp key-value, xóa các cặp key-value và duyệt bảng băm.
- Hàm băm ánh xạ một `key` tới một chỉ mục mảng, cho phép truy cập bucket tương ứng và lấy `value`.
- Hai key khác nhau có thể tạo ra cùng một chỉ mục mảng sau khi băm, dẫn đến kết quả truy vấn không chính xác. Hiện tượng này được gọi là xung đột băm.
- Dung lượng của bảng băm càng lớn thì xác suất xảy ra xung đột băm càng thấp. Vì vậy, việc mở rộng bảng băm có thể giảm xung đột băm. Tương tự như mở rộng mảng, mở rộng bảng băm cũng tốn kém.
- Hệ số tải, được xác định bằng số phần tử chia cho số bucket, phản ánh mức độ nghiêm trọng của xung đột băm và thường được dùng làm điều kiện để kích hoạt việc mở rộng bảng băm.
- Separate chaining xử lý xung đột băm bằng cách lưu trữ tất cả các phần tử xung đột trong cùng một linked list. Tuy nhiên, các linked list quá dài có thể làm giảm hiệu quả truy vấn; vấn đề này có thể được cải thiện bằng cách tiếp tục chuyển các linked list thành red-black tree.
- Open addressing xử lý xung đột băm thông qua việc probing nhiều lần. Linear probing sử dụng một bước nhảy cố định nhưng không thể xóa phần tử và dễ dẫn đến hiện tượng tập cụm. Double hashing sử dụng nhiều hàm băm để probing, giúp giảm hiện tượng tập cụm so với linear probing nhưng làm tăng chi phí tính toán.
- Các ngôn ngữ lập trình khác nhau sử dụng những cách triển khai bảng băm khác nhau. Ví dụ, `HashMap` của Java sử dụng separate chaining, trong khi `dict` của Python sử dụng open addressing.
- Trong bảng băm, chúng ta mong muốn các thuật toán băm có tính xác định, hiệu quả cao và khả năng phân phối đồng đều. Trong mật mã học, các thuật toán băm còn cần có khả năng chống xung đột và hiệu ứng avalanche.
- Các thuật toán băm thường sử dụng những số nguyên tố lớn làm modulo để tối đa hóa sự phân phối đồng đều của các giá trị băm và giảm xung đột băm.
- Các thuật toán băm phổ biến bao gồm MD5, SHA-1, SHA-2 và SHA-3. MD5 thường được dùng để kiểm tra tính toàn vẹn của tệp, trong khi SHA-2 thường được dùng trong các ứng dụng và giao thức bảo mật.
- Các ngôn ngữ lập trình thường cung cấp sẵn các thuật toán băm cho các kiểu dữ liệu để tính chỉ mục bucket trong bảng băm. Nhìn chung, chỉ các đối tượng bất biến mới có thể được băm.

### Hỏi & Đáp

**Q**: Khi nào độ phức tạp thời gian của bảng băm giảm xuống $O(n)$?

Độ phức tạp thời gian của bảng băm có thể giảm xuống $O(n)$ khi xảy ra xung đột băm nghiêm trọng. Khi hàm băm được thiết kế tốt, dung lượng được thiết lập phù hợp và các xung đột được phân phối đồng đều, độ phức tạp thời gian là $O(1)$. Thông thường, chúng ta xem độ phức tạp thời gian là $O(1)$ khi sử dụng các bảng băm tích hợp sẵn trong ngôn ngữ lập trình.

**Q**: Tại sao không sử dụng hàm băm $f(x) = x$? Cách này sẽ loại bỏ xung đột.

Với hàm băm $f(x) = x$, mỗi phần tử tương ứng với một chỉ mục bucket duy nhất, tương đương với một mảng. Tuy nhiên, không gian đầu vào thường lớn hơn nhiều so với không gian đầu ra (độ dài mảng), vì vậy bước cuối của hàm băm thường là lấy modulo theo độ dài mảng. Nói cách khác, mục tiêu của bảng băm là ánh xạ một không gian trạng thái lớn hơn vào một không gian nhỏ hơn, đồng thời cung cấp hiệu quả truy vấn $O(1)$.

**Q**: Tại sao bảng băm có thể hiệu quả hơn mảng, linked list hoặc binary tree, mặc dù bảng băm được triển khai bằng những cấu trúc này?

Thứ nhất, bảng băm có hiệu quả thời gian cao hơn nhưng hiệu quả không gian thấp hơn. Một phần đáng kể bộ nhớ trong bảng băm vẫn không được sử dụng.

Thứ hai, bảng băm chỉ hiệu quả hơn về thời gian trong những trường hợp sử dụng cụ thể. Nếu một chức năng có thể được triển khai với cùng độ phức tạp thời gian bằng mảng hoặc linked list, thì cách đó thường nhanh hơn sử dụng bảng băm. Nguyên nhân là việc tính toán hàm băm tạo ra chi phí bổ sung, khiến hệ số hằng trong độ phức tạp thời gian lớn hơn.

Cuối cùng, độ phức tạp thời gian của bảng băm có thể suy giảm. Ví dụ, trong separate chaining, chúng ta thực hiện các thao tác tìm kiếm trên linked list hoặc red-black tree, và vẫn có nguy cơ suy giảm xuống thời gian $O(n)$.

**Q**: Double hashing cũng có nhược điểm là không thể xóa trực tiếp phần tử phải không? Các ô được đánh dấu là đã xóa có thể được tái sử dụng không?

Double hashing là một dạng của open addressing, và mọi phương pháp open addressing đều có nhược điểm là không thể xóa trực tiếp phần tử; chúng yêu cầu đánh dấu phần tử là đã xóa. Các ô được đánh dấu có thể được tái sử dụng. Khi chèn phần tử mới vào bảng băm, nếu hàm băm trỏ đến một vị trí được đánh dấu là đã xóa, phần tử mới có thể sử dụng vị trí đó. Điều này duy trì chuỗi probing của bảng băm, đồng thời bảo đảm sử dụng không gian hiệu quả.

**Q**: Tại sao xảy ra xung đột băm trong quá trình tìm kiếm bằng linear probing?

Trong quá trình tìm kiếm, hàm băm trỏ đến bucket và cặp key-value tương ứng. Nếu `key` không khớp, điều đó cho thấy đã xảy ra xung đột băm. Vì vậy, linear probing sẽ tìm kiếm xuống dưới theo bước nhảy được xác định trước cho đến khi tìm thấy cặp key-value chính xác hoặc việc tìm kiếm thất bại.

**Q**: Tại sao việc mở rộng bảng băm có thể giảm xung đột băm?

Bước cuối của hàm băm thường là lấy modulo theo độ dài mảng $n$ để giữ đầu ra trong phạm vi chỉ mục mảng. Khi mở rộng, độ dài mảng $n$ thay đổi và các chỉ mục tương ứng với các key cũng có thể thay đổi. Những key trước đây được ánh xạ tới cùng một bucket có thể được phân phối vào nhiều bucket sau khi mở rộng, từ đó giảm xung đột băm.

**Q**: Nếu mục tiêu là truy cập hiệu quả, tại sao không sử dụng trực tiếp một mảng?

Khi các giá trị `key` là các số nguyên liên tiếp trong một phạm vi nhỏ, mảng quả thực là lựa chọn đơn giản và hiệu quả. Nhưng khi `key` có kiểu khác, chẳng hạn như chuỗi, chúng ta cần một hàm băm để ánh xạ `key` tới một chỉ mục mảng, sau đó lưu trữ phần tử trong một mảng bucket. Cấu trúc đó chính là bảng băm.