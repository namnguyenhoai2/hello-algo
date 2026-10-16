# Bài tập

## Ôn tập khái niệm

### Khi nào nên sử dụng Quy hoạch động?

Một sinh viên nói: “Bất cứ khi nào có thể viết một recurrence, ta nên sử dụng quy hoạch động.”
Với mỗi bài toán dưới đây, hãy quyết định quy hoạch động, quay lui hay vòng lặp hoặc công thức toán học không dùng bảng `dp` là phù hợp hơn. Nêu một lý do chính.

<!-- numbered-subquestions -->

1. Sử dụng các mệnh giá tiền `[1, 3, 4]`, hãy tạo ra số tiền 6 bằng số lượng đồng xu ít nhất. Mỗi mệnh giá có thể được sử dụng nhiều lần.
2. Xuất tất cả các hoán vị của `[1, 2, 3]`.
3. Tính $1 + 2 + \dots + n$.

    Với bài toán mà bạn cho là phù hợp với quy hoạch động, hãy nêu thêm `dp[i]` biểu diễn điều gì.

??? success "Đáp án"

    1. Quy hoạch động là phù hợp. Gọi `dp[i]` là số lượng đồng xu tối thiểu cần để tạo ra số tiền `i`.
        Với mỗi đồng xu `c` không vượt quá `i`, `dp[i-c] + 1` là một đáp án ứng viên,
        và chọn giá trị nhỏ nhất trong các ứng viên này. Các lựa chọn khác nhau nhiều lần gặp lại cùng một số tiền, và một lời giải tối ưu cho số tiền lớn hơn có thể được xây dựng từ các lời giải tối ưu cho những số tiền nhỏ hơn.
        Đáp án cho số tiền 6 là 2, sử dụng `3 + 3`.

    2. Quay lui là phù hợp. Bài toán yêu cầu tạo từng hoán vị trong tổng số 6 hoán vị. Quay lui có thể lần lượt đưa ra một lựa chọn, tiếp tục tìm kiếm,
        hoàn tác lựa chọn đó rồi thử một nhánh khác. Dù sử dụng phương pháp nào, việc thực sự xuất ra mọi hoán vị vẫn yêu cầu liệt kê tất cả chúng.

    3. Một vòng lặp hoặc công thức cấp số cộng là đủ. Mặc dù có thể viết recurrence `S(i) = S(i-1) + i`, việc tính `S(i)` chỉ phụ thuộc vào một giá trị nhỏ hơn, `S(i-1)`.
        Mỗi tổng từng phần chỉ cần được tính một lần, nên không có bài toán con nào bị lặp lại và không cần bảng `dp`. “Có thể viết recurrence” không có nghĩa là “cần dùng quy hoạch động.”

### Tính một ô trong bảng Knapsack

Xét bài toán knapsack 0-1: trọng số các vật phẩm `wgt = [1, 2, 3]`, giá trị `val = [5, 11, 15]`, và sức chứa knapsack là 4.
`dp[i][c]` là giá trị lớn nhất có thể đạt được khi chỉ sử dụng $i$ vật phẩm đầu tiên với giới hạn sức chứa knapsack là $c$;
knapsack không nhất thiết phải được lấp đầy chính xác.

Chỉ tính trạng thái `dp[3][4]`. Cho trước `dp[2][4] = 16` và `dp[2][1] = 5`:

<!-- numbered-subquestions -->

1. Nếu không chọn vật phẩm thứ ba, giá trị ứng viên là bao nhiêu?
2. Nếu chọn vật phẩm thứ ba, còn lại bao nhiêu sức chứa và giá trị ứng viên là bao nhiêu?
3. `dp[3][4]` nên có giá trị bao nhiêu? Giá trị này tương ứng với việc chọn những vật phẩm nào?

??? success "Đáp án"

    1. Nếu không chọn vật phẩm thứ ba, giữ lại kết quả từ hai vật phẩm đầu tiên. Giá trị ứng viên là `dp[2][4] = 16`.

    2. Vật phẩm thứ ba có trọng lượng 3, nên sau khi đặt vào knapsack, sức chứa còn lại là $4-3=1$. Giá trị ứng viên là
        `dp[2][1] + 15 = 5 + 15 = 20`.

    3. So sánh 16 và 20 cho `dp[3][4] = 20`. Điều này tương ứng với việc chọn vật phẩm thứ nhất và thứ ba,
        có tổng trọng lượng là $1+3=4$ và tổng giá trị là $5+15=20$.

        Việc tính trạng thái này minh họa một phép so sánh “chọn hoặc không chọn” trong bài toán knapsack 0-1.

### Nên cập nhật sức chứa knapsack theo thứ tự nào?

Một bài toán knapsack 0-1 chỉ có một vật phẩm, với trọng lượng 2 và giá trị 5, còn knapsack có sức chứa 4.
Vật phẩm có thể được chọn nhiều nhất một lần. Mảng một chiều ban đầu là `dp = [0, 0, 0, 0, 0]`.

Một sinh viên xử lý vật phẩm bằng cách cập nhật các sức chứa từ 2 đến 4:

- Sau khi cập nhật `dp[2]`, giá trị của nó là 5.
- Sau khi cập nhật `dp[3]`, giá trị của nó cũng là 5.
- Khi cập nhật `dp[4]`, sinh viên sử dụng `dp[2]` vừa thu được, tạo ra `dp[4] = 10`.

<!-- numbered-subquestions -->

1. `dp[4] = 10` có đúng không? Tại sao đúng hoặc tại sao không?
2. Vì mỗi vật phẩm có thể được chọn nhiều nhất một lần, `dp[4]` nên có giá trị bao nhiêu?
3. Khi xử lý từng vật phẩm, nên cập nhật các sức chứa từ lớn đến nhỏ hay từ nhỏ đến lớn? Cách này tránh được vấn đề gì?

??? success "Đáp án"

    1. Kết quả không đúng. Giá trị 10 tương đương với việc đặt vật phẩm có giá trị 5 vào knapsack hai lần,
        vi phạm điều kiện mỗi vật phẩm chỉ có thể được chọn nhiều nhất một lần.

    2. Knapsack chỉ có thể chứa nhiều nhất một vật phẩm này, nên giá trị đúng của `dp[4]` là 5.

    3. Các sức chứa nên được cập nhật từ lớn đến nhỏ, theo thứ tự 4, 3, 2.
        Khi đó, lúc tính `dp[c]`, giá trị đọc từ `dp[c-2]` vẫn là giá trị trước khi vật phẩm hiện tại được xử lý,
        ngăn không cho vật phẩm hiện tại được sử dụng lại trong cùng một lượt.

## Bài tập lập trình

### Số cách leo cầu thang

Một cầu thang có `n` bậc. Mỗi bước đi có thể leo 1 hoặc 2 bậc, và bạn phải đặt chân chính xác lên bậc `n`.
Hãy tính số cách khác nhau để đi đến đỉnh. Giả sử `n >= 1`; các cách chỉ được phân biệt bởi chuỗi các bước đi 1 bậc và 2 bậc.
Sử dụng mảng quy hoạch động một chiều. Hiện tại, không sử dụng tối ưu hóa bộ nhớ chỉ giữ lại hai trạng thái.

??? tip "Gợi ý"

    1. Bước đi cuối cùng đến bậc i chỉ có thể bao phủ 1 hoặc 2 bậc
    2. Do đó, dp[i] = dp[i-1] + dp[i-2]
    3. Trước tiên xử lý các trường hợp n là 1 hoặc 2, sau đó điền bảng bắt đầu từ bậc 3

[LeetCode](https://leetcode.com/problems/climbing-stairs/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }

### Knapsack 0-1

Cho hai mảng có cùng độ dài `wgt` và `val`. Vật phẩm `i` có trọng lượng nguyên dương `wgt[i]` và giá trị nguyên không âm `val[i]`.
Sức chứa knapsack `cap` là một số nguyên không âm. Mỗi vật phẩm có thể được chọn nhiều nhất một lần. Hãy tìm tổng giá trị lớn nhất có thể đặt vào knapsack
mà không vượt quá `cap`. Sử dụng quy hoạch động một chiều.

??? tip "Gợi ý"

    1. Khởi tạo một mảng dp có độ dài cap + 1, trong đó dp[c] là giá trị lớn nhất với giới hạn sức chứa là c
    2. Khi xử lý vật phẩm i, hãy so sánh dp[c], tức là không chọn vật phẩm đó, với dp[c-wgt[i]] + val[i], tức là có chọn vật phẩm đó
    3. Cập nhật các sức chứa từ lớn đến nhỏ để tránh chọn lặp lại vật phẩm hiện tại trong cùng một lượt