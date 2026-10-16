# Tóm tắt

### Ôn tập chính

- Bubble sort thực hiện việc sắp xếp bằng cách hoán đổi các phần tử liền kề. Bằng cách thêm một flag để cho phép trả về sớm, chúng ta có thể tối ưu độ phức tạp thời gian trong trường hợp tốt nhất của bubble sort xuống còn $O(n)$.
- Trong mỗi lượt, insertion sort chèn một phần tử từ phần chưa sắp xếp vào đúng vị trí trong phần đã sắp xếp. Mặc dù insertion sort có độ phức tạp thời gian là $O(n^2)$, nó vẫn rất phổ biến trong các tác vụ sắp xếp nhỏ vì mỗi thao tác tương đối nhẹ.
- Quick sort dựa trên sentinel partitioning. Trong sentinel partitioning, việc liên tục chọn pivot tệ nhất có thể khiến độ phức tạp thời gian giảm xuống $O(n^2)$. Chọn pivot dựa trên median hoặc pivot ngẫu nhiên có thể làm giảm xác suất xảy ra tình trạng này. Bằng cách đệ quy trên mảng con ngắn hơn trước, chúng ta có thể giảm hiệu quả độ sâu đệ quy và tối ưu độ phức tạp không gian xuống $O(\log n)$.
- Merge sort bao gồm hai giai đoạn: chia và trộn, thường thể hiện chiến lược chia để trị. Trong merge sort, việc sắp xếp một mảng yêu cầu tạo các mảng phụ, với độ phức tạp không gian là $O(n)$; tuy nhiên, độ phức tạp không gian khi sắp xếp một linked list có thể được tối ưu xuống $O(1)$.
- Bucket sort gồm ba bước: phân phối dữ liệu vào các bucket, sắp xếp trong từng bucket và hợp nhất kết quả. Thuật toán này cũng thể hiện chiến lược chia để trị và phù hợp với khối lượng dữ liệu rất lớn. Điểm mấu chốt của bucket sort là phân phối dữ liệu đồng đều.
- Counting sort là một trường hợp đặc biệt của bucket sort, thực hiện sắp xếp bằng cách đếm số lần xuất hiện của dữ liệu. Counting sort phù hợp với những tình huống có khối lượng dữ liệu lớn nhưng phạm vi dữ liệu giới hạn, đồng thời yêu cầu dữ liệu có thể được chuyển đổi thành các số nguyên dương.
- Radix sort thực hiện sắp xếp dữ liệu bằng cách sắp xếp lần lượt từng chữ số, yêu cầu dữ liệu có thể được biểu diễn dưới dạng các số có số chữ số cố định.
- Nhìn chung, chúng ta mong muốn tìm được một sorting algorithm hiệu quả, stable, in-place và adaptive. Tuy nhiên, cũng như các cấu trúc dữ liệu và thuật toán khác, không có sorting algorithm nào có thể đồng thời đáp ứng tất cả các tiêu chí này. Trong thực tế, chúng ta cần lựa chọn sorting algorithm phù hợp dựa trên đặc điểm của dữ liệu.
- Hình dưới đây so sánh các sorting algorithm phổ biến về hiệu quả, tính stable, tính in-place và khả năng adaptive.

![So sánh các sorting algorithm](summary.assets/sorting_algorithms_comparison.png)

### Hỏi & Đáp

**Q**: Trong những tình huống nào tính stable của sorting algorithm là cần thiết?

Trong thực tế, chúng ta có thể sắp xếp dựa trên một thuộc tính nhất định của các đối tượng. Ví dụ, học sinh có hai thuộc tính: tên và chiều cao. Chúng ta muốn triển khai việc sắp xếp nhiều cấp: trước tiên sắp xếp theo tên để có được `(A, 180) (B, 185) (C, 170) (D, 170)`; sau đó sắp xếp theo chiều cao. Vì sorting algorithm không stable, chúng ta có thể nhận được `(D, 170) (C, 170) (A, 180) (B, 185)`.

Có thể thấy học sinh D và C đã đổi vị trí, phá vỡ thứ tự theo tên, đây không phải là điều chúng ta mong muốn.

**Q**: Có thể hoán đổi thứ tự “tìm kiếm từ phải sang trái” và “tìm kiếm từ trái sang phải” trong sentinel partitioning không?

Không. Khi sử dụng phần tử ngoài cùng bên trái làm pivot, trước tiên chúng ta phải “tìm kiếm từ phải sang trái”, sau đó “tìm kiếm từ trái sang phải”. Kết luận này hơi phản trực giác; hãy cùng phân tích lý do.

Bước cuối cùng của sentinel partitioning `partition()` là hoán đổi `nums[left]` và `nums[i]`. Sau khi hoàn tất việc hoán đổi, tất cả các phần tử ở bên trái pivot đều `<=` pivot, **điều này yêu cầu `nums[left] >= nums[i]` phải được đảm bảo trước lần hoán đổi cuối cùng**. Giả sử trước tiên chúng ta “tìm kiếm từ trái sang phải”, khi đó nếu không tìm thấy phần tử nào lớn hơn pivot, **chúng ta sẽ thoát khỏi vòng lặp khi `i == j`, lúc đó có thể `nums[j] == nums[i] > nums[left]`**. Nói cách khác, thao tác hoán đổi cuối cùng sẽ đưa một phần tử lớn hơn pivot sang đầu ngoài cùng bên trái của mảng, khiến sentinel partitioning thất bại.

Ví dụ, với mảng `[0, 0, 0, 0, 1]`, nếu trước tiên chúng ta “tìm kiếm từ trái sang phải”, mảng sau sentinel partitioning sẽ là `[1, 0, 0, 0, 0]`, kết quả này không chính xác.

Tương tự, nếu chọn `nums[right]` làm pivot, thứ tự sẽ đảo ngược: trước tiên chúng ta phải “tìm kiếm từ trái sang phải”.

**Q**: Về việc tối ưu độ sâu đệ quy trong quick sort, tại sao chọn mảng ngắn hơn có thể đảm bảo độ sâu đệ quy không vượt quá $\log n$?

Độ sâu đệ quy là số lần gọi đệ quy chưa trả về. Mỗi lượt sentinel partitioning chia mảng ban đầu thành hai mảng con. Sau khi tối ưu, mảng con được chọn để tiếp tục đệ quy có độ dài nhiều nhất bằng một nửa mảng ban đầu. Trong trường hợp xấu nhất, nếu độ dài luôn bằng một nửa, độ sâu đệ quy cuối cùng sẽ là $\log n$.

Khi xem xét quick sort ban đầu, chúng ta có thể liên tục đệ quy trên mảng dài hơn. Trong trường hợp xấu nhất, các độ dài sẽ là $n$, $n - 1$, $\dots$, $2$, $1$, với độ sâu đệ quy là $n$. Việc tối ưu độ sâu đệ quy có thể tránh được tình huống này.

**Q**: Khi tất cả các phần tử trong mảng đều bằng nhau, độ phức tạp thời gian của quick sort có phải là $O(n^2)$ không? Nên xử lý trường hợp suy biến này như thế nào?

Đúng. Trong trường hợp này, thông qua sentinel partitioning, mảng có thể được chia thành ba phần: nhỏ hơn, bằng và lớn hơn pivot. Sau đó, chúng ta chỉ đệ quy trên phần nhỏ hơn và phần lớn hơn. Với cách tiếp cận này, một mảng có tất cả phần tử bằng nhau có thể được sắp xếp chỉ trong một lượt sentinel partitioning.

**Q**: Tại sao độ phức tạp thời gian trong trường hợp xấu nhất của bucket sort là $O(n^2)$?

Trong trường hợp xấu nhất, tất cả các phần tử được phân phối vào cùng một bucket. Nếu sử dụng một algorithm $O(n^2)$ để sắp xếp các phần tử này, độ phức tạp thời gian sẽ là $O(n^2)$.