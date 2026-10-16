# Bài tập

## Ôn tập khái niệm

### Biểu diễn cùng một đồ thị theo hai cách

Một đồ thị vô hướng có bốn đỉnh, `A, B, C, D`, và các cạnh
`A-B, A-C, B-C, C-D`.

<!-- numbered-subquestions -->

1. Viết danh sách kề của đồ thị.
2. Điền ma trận kề bằng cách chỉ sử dụng các số 0 và 1.
3. Để xác định `A` và `D` có được nối trực tiếp hay không, biểu diễn đồ thị nào chỉ yêu cầu kiểm tra một phần tử đã lưu?
4. Nếu một đồ thị có nhiều đỉnh nhưng ít cạnh, biểu diễn nào thường sử dụng ít không gian hơn?

??? success "Đáp án"

    1. Danh sách kề là:

        ```text
        A: B, C
        B: A, C
        C: A, B, D
        D: C
        ```

    2. Ma trận kề là:

        | | A | B | C | D |
        | --- | --- | --- | --- | --- |
        | A | 0 | 1 | 1 | 0 |
        | B | 1 | 0 | 1 | 0 |
        | C | 1 | 1 | 0 | 1 |
        | D | 0 | 0 | 1 | 0 |

    3. Trong ma trận kề, bạn có thể kiểm tra trực tiếp hàng `A`, cột `D`, vì vậy ma trận kề rất phù hợp để xác định liệu hai đỉnh bất kỳ có được nối trực tiếp hay không.

    4. Khi một đồ thị có nhiều đỉnh nhưng ít cạnh, danh sách kề chỉ ghi lại những cạnh thực sự tồn tại. Vì vậy, nó thường sử dụng ít không gian hơn ma trận kề, vốn dành sẵn một vị trí cho mọi cặp đỉnh.

### Thứ tự duyệt theo chiều rộng và chiều sâu

Một đồ thị vô hướng có các đỉnh `A, B, C, D, E` và các cạnh
`A-B, A-C, B-D, C-D, D-E`.

Bắt đầu từ A. Khi có nhiều đỉnh kề chưa được duyệt, hãy chọn chúng theo thứ tự bảng chữ cái:

<!-- numbered-subquestions -->

1. Viết thứ tự duyệt theo chiều rộng (BFS).
2. Viết thứ tự duyệt theo chiều sâu đệ quy (DFS).
3. Tại sao cả hai phép duyệt đều phải ghi lại những đỉnh đã được duyệt?

??? success "Đáp án"

    1. Thứ tự duyệt BFS là `A, B, C, D, E`. Trước tiên, nó duyệt B và C, là các đỉnh cách A một cạnh,
        sau đó duyệt D và E, là các đỉnh ở xa hơn.

    2. Thứ tự duyệt DFS là `A, B, D, C, E`. Nó liên tục đi vào một đỉnh kề chưa được duyệt,
        trước tiên đi theo `A → B → D → C`. Khi C không còn đỉnh kề mới nào, nó quay lại D rồi duyệt E.

    3. Đồ thị chứa một chu trình, chẳng hạn như `A-B-D-C-A`. Nếu không ghi lại các đỉnh đã được duyệt,
        phép duyệt có thể liên tục duyệt lại các đỉnh quanh chu trình và không thể kết thúc bình thường.

### Một BFS có thể duyệt toàn bộ đồ thị không?

Một đồ thị vô hướng có các đỉnh `A, B, C, D, E, F` và chỉ có các cạnh
`A-B, B-C, D-E`.

<!-- numbered-subquestions -->

1. Một BFS bắt đầu từ A có thể duyệt những đỉnh nào?
2. Dựa trên Câu hỏi 1, BFS này đã duyệt mọi đỉnh trong đồ thị chưa? Tại sao?
3. Giả sử bạn quét tất cả các đỉnh theo thứ tự bảng chữ cái và bắt đầu một BFS mới mỗi khi gặp một đỉnh chưa được duyệt.
    Đỉnh bắt đầu của mỗi BFS là gì? Đồ thị được chia thành bao nhiêu phần không liên thông với nhau (thành phần liên thông)?

??? success "Đáp án"

    1. Bắt đầu từ A, phép duyệt chỉ có thể duyệt `A, B, C`.

    2. Phép duyệt chưa duyệt mọi đỉnh. `D, E` tạo thành một phần liên thông khác, còn F là một đỉnh cô lập.
        Không có đỉnh nào trong số đó có đường đi đến A, nên chúng không thể được tiếp cận từ A.

    3. Ba phép duyệt BFS bắt đầu tại `A, D, F`, và lần lượt duyệt
        `{A, B, C}`, `{D, E}`, và `{F}`. Vì vậy, đồ thị có 3 thành phần liên thông.

## Bài tập lập trình

### Xác định liệu có tồn tại đường đi trong đồ thị vô hướng hay không

Bạn được cho một đồ thị vô hướng có $n$ đỉnh được đánh số từ $0$ đến $n-1$. Mỗi phần tử `[u, v]` trong mảng `edges` biểu diễn một cạnh vô hướng giữa các đỉnh `u` và `v`.

Bạn cũng được cho một đỉnh bắt đầu `source` và một đỉnh đích `destination`. Trước tiên, hãy xây dựng danh sách kề từ `edges`, sau đó sử dụng BFS hoặc DFS
để xác định liệu có đường đi từ `source` đến `destination` hay không. Trả về `true` nếu có đường đi và `false` nếu không.
Đồ thị có thể chứa các chu trình và có thể không liên thông.

??? tip "Gợi ý"

    1. Thêm mọi cạnh vô hướng theo cả hai hướng
    2. Đồ thị có thể chứa các chu trình, vì vậy bạn phải ghi lại những đỉnh đã được duyệt
    3. Bắt đầu từ source, trả về true nếu gặp destination; nếu phép duyệt kết thúc mà không đến được đỉnh đó, hãy trả về false

[LeetCode](https://leetcode.com/problems/find-if-path-exists-in-graph/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }