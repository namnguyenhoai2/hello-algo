# Bài tập

## Ôn tập khái niệm

### Thuật toán hoán vị này có bỏ sót kết quả không?

Một thuật toán backtracking cố gắng tạo ra tất cả các hoán vị bằng cách sử dụng `1, 2, 3` theo thứ tự đó. Mỗi khi chọn một số `x`, thuật toán sẽ:

1. Thêm `x` vào đường đi hiện tại.
2. Đánh dấu `x` là "đã dùng".
3. Đệ quy điền vào vị trí tiếp theo.

Khi lời gọi đệ quy trả về, sinh viên chỉ xóa `x` khỏi cuối đường đi rồi thử số tiếp theo.

<!-- numbered-subquestions -->

1. Thuật toán tạo ra hoán vị nào đầu tiên? Nó có thể vẫn tạo ra đủ 6 hoán vị không?
2. Trước khi quay về cấp trước đó, chỉ xóa số cuối cùng khỏi đường đi có đủ không? Nếu không, còn phải làm gì? Hãy giải thích tại sao.

??? success "Đáp án"

    1. Đầu tiên, thuật toán tạo ra `[1, 2, 3]`, nhưng không thể tạo ra tất cả các hoán vị. Mặc dù đường đi ngắn lại khi các lời gọi trả về,
        các dấu đánh dấu 1, 2 và 3 vẫn đều là "đã dùng", khiến các nhánh sau không còn số nào khả dụng.

    2. Như vậy là chưa đủ. Sau khi xóa `x` khỏi cuối đường đi, thuật toán cũng phải đánh dấu `x` là "chưa dùng" một lần nữa.
        Đường đi hiện tại và các dấu đánh dấu đã dùng cùng mô tả trạng thái tìm kiếm. Một lựa chọn thay đổi cả hai, vì vậy backtracking phải khôi phục cả hai
        trước khi một nhánh khác có thể chọn lại `x`.

### Thứ tự chọn các số có quan trọng không?

Bạn được cho mảng đã sắp xếp `[2, 3, 5]` và giá trị đích là 5. Mỗi số có thể được chọn nhiều lần.
Thuật toán yêu cầu các số trên mỗi đường tìm kiếm chỉ xuất hiện theo thứ tự không giảm.

<!-- numbered-subquestions -->

1. Có thể tìm thấy những tổ hợp phân biệt nào?
2. Tại sao không cần tìm cùng một nhóm số theo các thứ tự khác nhau? Việc giới hạn theo thứ tự không giảm mang lại tác dụng gì?
3. Giả sử đường đi hiện tại là `[3]`, lượng còn lại là 2 và ứng viên tiếp theo là 3. Tại sao thuật toán có thể dừng kiểm tra tất cả các ứng viên phía sau ở cấp này?

??? success "Đáp án"

    1. Các tổ hợp phân biệt là `[2, 3]` và `[5]`.

    2. Bài tập này xem `[2, 3]` và `[3, 2]` là cùng một tổ hợp; thứ tự chọn các số không tạo ra một đáp án khác.
        Yêu cầu các số trong một đường đi xuất hiện theo thứ tự không giảm cho phép quá trình tìm kiếm bỏ qua các cách sắp xếp trùng lặp như `[3, 2]`.

    3. Lượng còn lại là 2, trong khi ứng viên 3 đã lớn hơn 2. Vì mảng đã được sắp xếp,
        tất cả các ứng viên phía sau còn lớn hơn nữa và không thể được thêm vào tổ hợp hiện tại, nên thuật toán có thể dừng kiểm tra cấp này ngay lập tức.

### Quân hậu tiếp theo có thể được đặt ở đâu?

Đặt các quân hậu theo từng hàng trên bàn cờ `4 × 4`, với cả chỉ số hàng và cột đều bắt đầu từ 0.
Các quân hậu đã được đặt tại `(0, 1)` và `(1, 3)`. Quân hậu tiếp theo phải được đặt ở hàng 2.

<!-- numbered-subquestions -->

1. Những cột nào bị loại vì đã có quân hậu?
2. Trong các cột còn lại, những vị trí nào bị loại vì nằm trên cùng đường chéo với một quân hậu hiện có?
3. Những vị trí nào ở hàng 2 vẫn còn có thể thử?

??? success "Đáp án"

    1. Các cột 1 và 3 đã có quân hậu, vì vậy các vị trí `(2, 1)` và `(2, 3)` bị loại.

    2. Trong các vị trí còn lại, `(2, 2)` nằm trên cùng đường chéo với `(1, 3)`, nên cũng bị loại.
        Vị trí `(2, 0)` không cùng cột hay đường chéo với bất kỳ quân hậu nào trong hai quân hậu hiện có.

    3. Vị trí duy nhất có thể thử ở hàng 2 là `(2, 0)`.

        Bước này chỉ cho thấy vị trí hiện tại là hợp lệ. Nếu sau đó không thể hoàn tất bàn cờ, thuật toán vẫn phải backtrack và thử một lựa chọn trước đó.

## Bài tập lập trình

### Hoán vị của các phần tử phân biệt

Mảng số nguyên `nums` chứa ít nhất một phần tử và tất cả các phần tử đều khác nhau.
Hãy liệt kê mọi thứ tự có thể tạo thành bằng cách sử dụng mỗi phần tử đúng một lần, rồi trả về từng thứ tự dưới dạng một mảng.
Các hoán vị có thể xuất hiện theo bất kỳ thứ tự nào trong kết quả.
Hãy sử dụng backtracking, với một mảng Boolean ghi lại liệu phần tử tại mỗi vị trí đã được chọn cho hoán vị hiện tại hay chưa.

??? tip "Gợi ý"

    1. Độ sâu đệ quy cho biết vị trí nào của hoán vị hiện đang được điền
    2. Ở mỗi cấp, chỉ thử các phần tử chưa được sử dụng
    3. Khi độ dài của đường đi bằng độ dài của `nums`, hãy thêm một bản sao của đường đi vào đáp án

[LeetCode](https://leetcode.com/problems/permutations/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }