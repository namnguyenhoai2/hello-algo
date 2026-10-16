# Bài tập

## Ôn tập khái niệm

### Những bài toán nào phù hợp với chia để trị?

Một sinh viên muốn giải mỗi bài toán dưới đây bằng cách “chia nó thành hai nửa, giải riêng từng nửa, rồi kết hợp các kết quả”.
Hãy phân loại mỗi bài toán là “phù hợp với chia để trị”, “có thể dùng chia để trị, nhưng sẽ không làm giảm tổng khối lượng công việc”, hoặc “không thể giải độc lập hai nửa”, và giải thích lý do.

<!-- numbered-subquestions -->

1. Sắp xếp một mảng chưa được sắp xếp.
2. Tìm giá trị lớn nhất trong một mảng.
3. Thực thi theo thứ tự một chuỗi gồm `push(x)` và `pop()` thao tác trên stack, rồi xuất phần tử được trả về bởi mỗi `pop()`.

??? success "Đáp án"

    1. Phù hợp: chia mảng thành hai nửa, sắp xếp độc lập từng nửa, rồi trộn chúng trong thời gian $O(n)$. Đây chính là merge sort.
    2. Có thể dùng chia để trị, nhưng không làm giảm tổng khối lượng công việc. Hai nửa vẫn cần kiểm tra tổng cộng đủ $n$ phần tử,
        nên độ phức tạp thời gian vẫn là $O(n)$, giống như khi quét trực tiếp.
    3. Không thể giải độc lập hai nửa. Nội dung của stack khi bắt đầu nửa thứ hai phụ thuộc vào kết quả thực thi nửa thứ nhất,
        vì vậy không thể hoàn tất hai nửa nếu chưa biết kết quả của nhau.

### Cách lũy thừa bằng bình phương làm giảm số phép tính

Hàm đệ quy dưới đây sử dụng chia để trị để tính $x^n$:

```src
[file]{fast_power}-[class]{}-[func]{fast_pow}
```

Đặt `x = 3` và `n = 5`, rồi dùng hàm này để tính kết quả:

<!-- numbered-subquestions -->

1. Khi các lời gọi đệ quy tiếp tục diễn ra, đối số `n` lần lượt nhận những giá trị nào?
2. Bắt đầu từ lời gọi sâu nhất, mỗi cấp trả về giá trị nào?
3. Tại sao nên lưu kết quả đệ quy vào `half` thay vì gọi cùng một bài toán con một lần ở mỗi phía của phép nhân?

??? success "Đáp án"

    1. Đối số nhận các giá trị `5 → 2 → 1 → 0`. Số mũ được chia đôi ở mỗi bước cho đến khi đạt đến trường hợp cơ sở.

    2. Khi `n = 0`, hàm trả về 1. Khi `n = 1`, hàm trả về $1×1×3=3$.
        Khi `n = 2`, hàm trả về $3×3=9$. Khi `n = 5`, hàm trả về $9×9×3=243$.

    3. Nếu cùng một bài toán con được gọi một lần ở mỗi phía của phép nhân, hai lời gọi đệ quy sẽ thực hiện chính xác cùng một phép tính.
        Lưu kết quả vào `half` nghĩa là mỗi cấp chỉ thực hiện một lời gọi đệ quy, nên độ sâu đệ quy xấp xỉ $\log n$.
        Việc thực hiện hai lời gọi sẽ gây ra rất nhiều phép tính lặp lại.

### Chia các chuỗi duyệt thành cây con trái và cây con phải

Một cây nhị phân không có các node trùng lặp. Các phép duyệt preorder và inorder của cây là:

- Preorder: `[A, B, D, E, C]`
- Inorder: `[D, B, E, A, C]`

Chỉ chia các chuỗi đúng một lần, tại root. Bạn không cần tiếp tục đệ quy hoặc vẽ toàn bộ cây:

<!-- numbered-subquestions -->

1. Node nào là root?
2. Những chuỗi con nào của phép duyệt inorder tương ứng với cây con trái và cây con phải?
3. Những chuỗi con nào của phép duyệt preorder tương ứng với cây con trái và cây con phải? Các node con trực tiếp của root là những node nào?

??? success "Đáp án"

    1. Node đầu tiên trong phép duyệt preorder là root, nên root là `A`.

    2. `A` chia phép duyệt inorder thành hai phần: `[D, B, E]` cho cây con trái và `[C]` cho cây con phải.

    3. Cây con trái chứa 3 node, nên 3 phần tử preorder đứng sau root `A` thuộc về cây con trái,
        tạo thành `[B, D, E]`. Các phần tử còn lại `[C]` thuộc về cây con phải.
        Vì vậy, node con trái của root là `B`, còn node con phải là `C`.

## Bài tập lập trình

### Lũy thừa bằng bình phương

Cho một số thực `x` và một số nguyên `n`, hãy tính $x^n$ mà không gọi hàm power tích hợp sẵn của ngôn ngữ.
Sử dụng chia để trị đệ quy: chia đôi số mũ ở mỗi bước và dùng lại kết quả của bài toán con đã được tính.
Bài tập này định nghĩa $x^0=1$, kể cả khi `x = 0`. Khi `n < 0`, `x != 0` được đảm bảo, và đáp án có thể được biến đổi thành $(1/x)^{-n}$.

??? tip "Gợi ý"

    1. Khi n bằng 0, đáp án là 1
    2. Sau khi tính x lũy thừa n // 2, hãy lưu kết quả vào half thay vì thực hiện lời gọi đệ quy lần thứ hai
    3. Khi n < 0, trước tiên đổi x thành 1 / x, rồi đổi n thành -n; trong C++ hoặc Java, trước tiên hãy chuyển n thành số nguyên 64-bit để tránh tràn số khi đổi dấu số nguyên 32-bit nhỏ nhất

[LeetCode](https://leetcode.com/problems/powx-n/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }