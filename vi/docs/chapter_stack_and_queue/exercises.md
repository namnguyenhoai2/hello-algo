# Bài tập

## Ôn tập khái niệm

### Phần tử nào rời khỏi Stack hoặc Queue trước?

Chuẩn bị một stack rỗng `S` và một queue rỗng `Q`. Thực hiện cùng một chuỗi thao tác trên mỗi cấu trúc:

Bước 1: Thêm `A`.  
Bước 2: Thêm `B`.  
Bước 3: Xóa và ghi lại một phần tử.  
Bước 4: Thêm `C`.  
Bước 5: Tiếp tục xóa và ghi lại các phần tử cho đến khi container rỗng.

Viết thứ tự các phần tử được xóa khỏi `S` và `Q`. Giải thích sự khác biệt bằng các khái niệm "last-in-first-out" hoặc "first-in-first-out".

??? success "Đáp án"

    Thứ tự xóa của stack `S` là `B, C, A`. Sau khi thêm các phần tử `A, B`, phần tử được thêm gần nhất, `B`, được pop trước. Sau khi thêm `C`,
    `C, A` được pop theo thứ tự đó. Đây là "last-in-first-out."

    Thứ tự xóa của queue `Q` là `A, B, C`. Sau khi thêm các phần tử `A, B`, phần tử được thêm sớm nhất, `A`, được xóa trước.
    Sau khi thêm `C`, `B, C` được xóa theo thứ tự đó. Đây là "first-in-first-out."

### Điều gì xảy ra khi rear vượt qua cuối mảng?

Một queue được triển khai bằng một mảng vòng có độ dài 5, với các chỉ số là `0–4`.
Hiện tại, `front = 3` và `size = 2`; `A, B` được lưu lần lượt tại các chỉ số 3 và 4.

<!-- numbered-subquestions -->

1. Khi `C` được enqueue, `C` nên được lưu tại chỉ số nào? `size` sẽ có giá trị gì sau thao tác enqueue?
2. Tiếp theo, thực hiện dequeue một lần. Phần tử nào bị xóa? Giá trị mới của `front` và `size` là gì?
3. Thứ tự logic từ front đến rear hiện tại là gì? Dequeue có cần di chuyển các phần tử khác trong mảng không? Tại sao?

??? success "Đáp án"

    1. Vị trí của phần tử mới là
        `(front + size) % 5 = (3 + 2) % 5 = 0`,
        nên `C` được lưu tại chỉ số 0. Sau thao tác enqueue, `size = 3`.

    2. Dequeue xóa phần tử front hiện tại, `A`. Chỉ số front mới là
        `(3 + 1) % 5 = 4`, vì vậy `front = 4` và `size = 2`.

    3. Thứ tự logic của các phần tử hợp lệ là `B, C`, với `B` ở chỉ số 4 và `C` ở chỉ số 0.
        Dequeue chỉ cần thay đổi `front` và `size`. Mảng vòng sử dụng phép toán lấy phần dư để đưa chỉ số quay lại đầu mảng,
        vì vậy không cần dịch chuyển tất cả các phần tử khác về phía trước.

### Các thao tác ở cả hai đầu của Deque

Ở đây, `push_first` thêm một phần tử ở front, `push_last` thêm một phần tử ở rear,
`pop_first` xóa một phần tử ở front, còn `pop_last` xóa một phần tử ở rear.

Thực hiện các thao tác sau trên một deque rỗng `deq`:

1. `push_last(A)`
2. `push_last(B)`
3. `push_first(C)`
4. `pop_last()`
5. `push_last(D)`
6. `pop_first()`

<!-- numbered-subquestions -->

1. Hai thao tác pop trả về những phần tử nào?
2. Sau khi hoàn tất tất cả các thao tác, những phần tử nào còn lại theo thứ tự từ front đến rear?
3. Xem xét sáu thao tác trên. Một queue chỉ cho phép chèn ở rear và xóa ở front có thể thực hiện tất cả các thao tác này không? Nếu không, hãy xác định các thao tác mà nó không thể thực hiện. Sau đó cho biết deque có thể thực hiện chúng hay không và giải thích lý do.

??? success "Đáp án"

    Sau ba bước đầu tiên, deque theo thứ tự từ front đến rear là `[C, A, B]`.

    <!-- numbered-subquestions -->

    1. `pop_last()` xóa `B`. Sau khi thêm `D`, deque là `[C, A, D]`,
        và `pop_first()` sau đó xóa `C`.

    2. `[A, D]` còn lại.

    3. Một queue chỉ cho phép chèn ở rear và xóa ở front không thể thực hiện tất cả các thao tác.
        Bước 3, `push_first(C)`, yêu cầu chèn ở front, còn Bước 4, `pop_last()`, yêu cầu xóa ở rear. Cả hai thao tác đều nằm ngoài các thao tác mà queue đó hỗ trợ.
        Deque cho phép chèn và xóa ở cả hai đầu, nên có thể thực hiện cả sáu thao tác.

## Bài tập lập trình

### Kiểm tra chuỗi dấu ngoặc

Cho một chuỗi `s` chỉ chứa ba loại dấu ngoặc `()`, `[]` và `{}`, hãy sử dụng stack để xác định xem chuỗi có hợp lệ hay không.

Một chuỗi hợp lệ phải thỏa mãn cả hai điều kiện: mọi dấu ngoặc đóng đều khớp với loại dấu ngoặc mở chưa được ghép gần nhất,
và không còn dấu ngoặc mở nào chưa được ghép sau khi duyệt. Trả về một giá trị Boolean cho kết quả.

??? tip "Gợi ý"

    1. Bạn có thể tạo một mapping từ mỗi dấu ngoặc đóng đến dấu ngoặc mở tương ứng
    2. Khi gặp một dấu ngoặc đóng, trước tiên hãy kiểm tra xem stack có rỗng không, sau đó kiểm tra xem phần tử trên cùng có khớp không
    3. Stack cũng phải rỗng sau khi duyệt

[LeetCode](https://leetcode.com/problems/valid-parentheses/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }