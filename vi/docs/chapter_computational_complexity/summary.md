# Tóm tắt

### Đánh giá chính

**Đánh giá hiệu quả thuật toán**

- Hiệu quả về thời gian và hiệu quả về không gian là hai chỉ số đánh giá chính để đo lường hiệu năng của thuật toán.
- Chúng ta có thể đánh giá hiệu quả thuật toán thông qua việc kiểm thử thực tế, nhưng rất khó loại bỏ ảnh hưởng của môi trường kiểm thử, đồng thời phương pháp này tiêu tốn đáng kể tài nguyên tính toán.
- Phân tích độ phức tạp có thể khắc phục những hạn chế của việc kiểm thử thực tế. Kết quả phân tích có thể áp dụng trên nhiều nền tảng chạy khác nhau và cho thấy hiệu quả của thuật toán ở các quy mô dữ liệu khác nhau.

**Độ phức tạp thời gian**

- Độ phức tạp thời gian được dùng để đo xu hướng thay đổi của thời gian chạy thuật toán khi khối lượng dữ liệu tăng lên. Nó có thể đánh giá hiệu quả thuật toán một cách hiệu quả, nhưng có thể kém hữu ích trong một số tình huống, chẳng hạn khi khối lượng dữ liệu đầu vào nhỏ hoặc khi các độ phức tạp thời gian giống nhau, khiến không thể so sánh chính xác hiệu quả của các thuật toán.
- Độ phức tạp thời gian trong trường hợp xấu nhất được biểu diễn bằng ký hiệu Big $O$, tương ứng với cận trên tiệm cận của một hàm, phản ánh mức độ tăng của số phép toán $T(n)$ khi $n$ tiến đến dương vô cùng.
- Việc suy ra độ phức tạp thời gian gồm hai bước: trước tiên đếm số phép toán, sau đó xác định cận trên tiệm cận.
- Các độ phức tạp thời gian phổ biến, được sắp xếp từ thấp đến cao, gồm $O(1)$, $O(\log n)$, $O(n)$, $O(n \log n)$, $O(n^2)$, $O(2^n)$ và $O(n!)$.
- Độ phức tạp thời gian của một số thuật toán không cố định mà phụ thuộc vào sự phân bố của dữ liệu đầu vào. Độ phức tạp thời gian được chia thành độ phức tạp thời gian trong trường hợp xấu nhất, trường hợp tốt nhất và trường hợp trung bình. Độ phức tạp thời gian trong trường hợp tốt nhất hiếm khi được sử dụng vì dữ liệu đầu vào thường phải thỏa mãn các điều kiện nghiêm ngặt mới đạt được trường hợp tốt nhất.
- Độ phức tạp thời gian trung bình phản ánh hiệu quả thời gian chạy của thuật toán khi dữ liệu đầu vào là ngẫu nhiên và gần với hiệu năng của thuật toán trong các ứng dụng thực tế nhất. Việc tính độ phức tạp thời gian trung bình đòi hỏi phải phân tích phân bố dữ liệu đầu vào và kỳ vọng toán học tương ứng.

**Độ phức tạp không gian**

- Độ phức tạp không gian có mục đích tương tự độ phức tạp thời gian, được dùng để đo xu hướng thay đổi của mức sử dụng bộ nhớ của thuật toán khi khối lượng dữ liệu tăng lên.
- Không gian bộ nhớ liên quan đến quá trình thực thi thuật toán có thể được chia thành không gian đầu vào, không gian tạm thời và không gian đầu ra. Thông thường, không gian đầu vào không được tính vào độ phức tạp không gian. Không gian tạm thời có thể được chia thành dữ liệu tạm thời, không gian stack frame và không gian lệnh; trong đó, không gian stack frame thường chỉ ảnh hưởng đến độ phức tạp không gian trong các hàm đệ quy.
- Thông thường, chúng ta chỉ quan tâm đến độ phức tạp không gian trong trường hợp xấu nhất, tức là độ phức tạp không gian của thuật toán với dữ liệu đầu vào và thời gian chạy đều ở trường hợp xấu nhất.
- Các độ phức tạp không gian phổ biến, được sắp xếp từ thấp đến cao, gồm $O(1)$, $O(\log n)$, $O(n)$, $O(n^2)$ và $O(2^n)$.

### Hỏi & Đáp

**Q**: Độ phức tạp không gian của đệ quy đuôi có phải là $O(1)$ không?

Về mặt lý thuyết, độ phức tạp không gian của các hàm đệ quy đuôi có thể được tối ưu xuống $O(1)$. Tuy nhiên, hầu hết các ngôn ngữ lập trình (chẳng hạn như Java, Python, C++, Go, C#, v.v.) không hỗ trợ tự động tối ưu hóa đệ quy đuôi, nên độ phức tạp không gian thường được xem là $O(n)$.

**Q**: Sự khác biệt giữa các thuật ngữ hàm và phương thức là gì?

Một <u>hàm</u> có thể được thực thi độc lập, với tất cả tham số được truyền một cách tường minh. Một <u>phương thức</u> được liên kết với một đối tượng, được liên kết ngầm với đối tượng gọi nó và có thể thao tác trên dữ liệu được chứa trong các thể hiện của lớp.

Các ví dụ sau sử dụng một số ngôn ngữ lập trình phổ biến để minh họa.

- C là một ngôn ngữ lập trình thủ tục không có các khái niệm hướng đối tượng, vì vậy nó chỉ có các hàm. Tuy nhiên, chúng ta có thể mô phỏng lập trình hướng đối tượng bằng cách tạo các cấu trúc (struct), và các hàm liên kết với cấu trúc tương đương với các phương thức trong những ngôn ngữ lập trình khác.
- Java và C# là các ngôn ngữ lập trình hướng đối tượng, trong đó các khối mã (phương thức) thường là một phần của một lớp. Các phương thức tĩnh hoạt động như các hàm vì chúng được liên kết với lớp và không thể truy cập các biến thể hiện cụ thể.
- C++ và Python hỗ trợ cả lập trình thủ tục (hàm) lẫn lập trình hướng đối tượng (phương thức).

**Q**: Biểu đồ về “các loại độ phức tạp không gian phổ biến” có phản ánh kích thước tuyệt đối của không gian bị chiếm dụng không?

Không, biểu đồ thể hiện độ phức tạp không gian, phản ánh xu hướng tăng trưởng thay vì kích thước tuyệt đối của không gian bị chiếm dụng.

Giả sử $n = 8$, bạn có thể nhận thấy giá trị của mỗi đường cong không tương ứng với các hàm. Điều này là do mỗi đường cong chứa một hằng số, được dùng để nén phạm vi giá trị vào một khoảng trực quan dễ quan sát.

Trong thực tế, vì chúng ta thường không biết chi phí “hạng tử hằng” của mỗi phương pháp, nên thường không thể chỉ dựa vào độ phức tạp để chọn giải pháp tối ưu cho các trường hợp như $n = 8$. Nhưng với $n = 8^5$, lựa chọn trở nên rõ ràng, vì xu hướng tăng trưởng đã chi phối.

**Q**: Có những trường hợp nào thuật toán được thiết kế để đánh đổi thời gian (hoặc không gian) dựa trên các trường hợp sử dụng thực tế không?

Trong các ứng dụng thực tế, phần lớn các trường hợp chọn đánh đổi không gian để lấy thời gian. Ví dụ, với các index cơ sở dữ liệu, chúng ta thường chọn xây dựng cây B+ hoặc hash index, sử dụng một lượng lớn không gian bộ nhớ để đổi lấy các truy vấn hiệu quả với độ phức tạp $O(\log n)$ hoặc thậm chí $O(1)$.

Trong những tình huống tài nguyên không gian khan hiếm, thời gian có thể được đánh đổi để tiết kiệm không gian. Ví dụ, trong phát triển hệ thống nhúng, bộ nhớ thiết bị rất quý giá, nên các kỹ sư có thể không sử dụng hash table mà chọn tìm kiếm tuần tự trên mảng để tiết kiệm bộ nhớ, đổi lại tốc độ tìm kiếm chậm hơn.