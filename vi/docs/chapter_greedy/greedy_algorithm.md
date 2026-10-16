# Thuật toán tham lam

<u>Thuật toán tham lam</u> là một cách tiếp cận phổ biến để giải các bài toán tối ưu. Ý tưởng cơ bản của nó là chọn phương án có vẻ tốt nhất ở mỗi giai đoạn ra quyết định, tức là đưa ra các quyết định tối ưu cục bộ một cách tham lam với hy vọng đạt được lời giải tối ưu toàn cục. Thuật toán tham lam đơn giản, hiệu quả và được sử dụng rộng rãi trong nhiều bài toán thực tế.

Thuật toán tham lam và quy hoạch động đều thường được sử dụng để giải các bài toán tối ưu. Chúng có một số điểm tương đồng, chẳng hạn như đều dựa vào tính chất cấu trúc con tối ưu, nhưng cách hoạt động của chúng khác nhau.

- Quy hoạch động xem xét tất cả các quyết định trước đó khi đưa ra quyết định hiện tại, đồng thời sử dụng lời giải của các bài toán con trước đó để xây dựng lời giải cho bài toán con hiện tại.
- Thuật toán tham lam không xem xét các quyết định trước đó mà thay vào đó đưa ra các lựa chọn tham lam theo hướng tiến tới, liên tục giảm kích thước bài toán cho đến khi bài toán được giải.

Trước tiên, chúng ta sẽ tìm hiểu cách hoạt động của thuật toán tham lam thông qua bài toán ví dụ “đổi tiền”. Bài toán này đã được giới thiệu trong chương “Bài toán ba lô đầy đủ”, vì vậy có lẽ bạn đã quen thuộc với nó.

!!! question

    Cho $n$ loại tiền xu, trong đó mệnh giá của loại thứ $i$ là $coins[i - 1]$, một số tiền mục tiêu $amt$ và số lượng không giới hạn của mỗi loại tiền xu. Cần ít nhất bao nhiêu đồng xu để tạo thành số tiền mục tiêu? Nếu không thể tạo thành số tiền mục tiêu, hãy trả về $-1$.

Chiến lược tham lam cho bài toán này được minh họa trong hình dưới đây. Với một số tiền mục tiêu, **chúng ta tham lam chọn đồng xu không vượt quá số tiền đó và gần với nó nhất**, lặp lại bước này cho đến khi tạo thành số tiền mục tiêu.

![Chiến lược tham lam cho bài toán đổi tiền](greedy_algorithm.assets/coin_change_greedy_strategy.png)

Mã triển khai như sau:

```src
[file]{coin_change_greedy}-[class]{}-[func]{coin_change_greedy}
```

Có thể bạn sẽ phải thốt lên: “Thật gọn gàng!” Thuật toán tham lam giải bài toán đổi tiền chỉ với khoảng mười dòng mã.

## Ưu điểm và hạn chế của thuật toán tham lam

**Thuật toán tham lam không chỉ dễ áp dụng, dễ triển khai mà thường còn rất hiệu quả**. Trong đoạn mã trên, nếu mệnh giá đồng xu nhỏ nhất là $\min(coins)$, vòng lặp chọn tham lam chạy nhiều nhất $amt / \min(coins)$ lần, cho độ phức tạp thời gian là $O(amt / \min(coins))$. Con số này thấp hơn một bậc độ lớn so với độ phức tạp thời gian của lời giải quy hoạch động, là $O(n \times amt)$.

Tuy nhiên, **với một số tập mệnh giá tiền xu, thuật toán tham lam không thể tìm được lời giải tối ưu**. Hình dưới đây minh họa hai ví dụ.

- **Ví dụ tích cực $coins = [1, 5, 10, 20, 50, 100]$**: Với tập tiền xu này, thuật toán tham lam có thể tìm được lời giải tối ưu cho mọi $amt$.
- **Phản ví dụ $coins = [1, 20, 50]$**: Giả sử $amt = 60$. Thuật toán tham lam chỉ có thể tìm được tổ hợp $50 + 1 \times 10$, sử dụng tổng cộng $11$ đồng xu, trong khi quy hoạch động có thể tìm được lời giải tối ưu $20 + 20 + 20$, chỉ sử dụng $3$ đồng xu.
- **Phản ví dụ $coins = [1, 49, 50]$**: Giả sử $amt = 98$. Thuật toán tham lam chỉ có thể tìm được tổ hợp $50 + 1 \times 48$, sử dụng tổng cộng $49$ đồng xu, trong khi quy hoạch động có thể tìm được lời giải tối ưu $49 + 49$, chỉ sử dụng $2$ đồng xu.

![Các ví dụ trong đó thuật toán tham lam không thể tìm được lời giải tối ưu](greedy_algorithm.assets/coin_change_greedy_vs_dp.png)

Nói cách khác, đối với bài toán đổi tiền, thuật toán tham lam không thể đảm bảo lời giải tối ưu toàn cục và thậm chí có thể cho ra kết quả rất kém. Bài toán này phù hợp hơn với quy hoạch động.

Nhìn chung, thuật toán tham lam có thể áp dụng trong hai trường hợp sau.

1. **Có thể đảm bảo lời giải tối ưu**: Trong trường hợp này, thuật toán tham lam thường là lựa chọn tốt nhất vì nó có xu hướng hiệu quả hơn backtracking và quy hoạch động.
2. **Có thể tìm được lời giải gần tối ưu**: Thuật toán tham lam cũng hữu ích trong trường hợp này. Với nhiều bài toán phức tạp, việc tìm lời giải tối ưu toàn cục là rất khó, vì vậy tìm được một lời giải không tối ưu nhưng hiệu quả cũng đã là một kết quả rất tốt.

## Đặc điểm của thuật toán tham lam

Vậy câu hỏi đặt ra là: Những bài toán nào phù hợp để giải bằng thuật toán tham lam? Hay nói cách khác, trong những điều kiện nào thuật toán tham lam có thể đảm bảo tìm được lời giải tối ưu?

So với quy hoạch động, điều kiện sử dụng thuật toán tham lam khắt khe hơn, chủ yếu tập trung vào hai tính chất của bài toán.

- **Tính chất lựa chọn tham lam**: Chỉ khi các lựa chọn tối ưu cục bộ luôn có thể dẫn đến một lời giải tối ưu toàn cục thì thuật toán tham lam mới có thể đảm bảo tìm được lời giải tối ưu.
- **Cấu trúc con tối ưu**: Lời giải tối ưu của bài toán ban đầu chứa các lời giải tối ưu của các bài toán con.

Cấu trúc con tối ưu đã được giới thiệu trong chương “Quy hoạch động”, vì vậy chúng ta sẽ không trình bày chi tiết thêm ở đây. Đáng chú ý là cấu trúc con tối ưu của một số bài toán không hiển nhiên, nhưng chúng vẫn có thể được giải bằng thuật toán tham lam.

Chúng ta chủ yếu tìm hiểu các phương pháp xác định tính chất lựa chọn tham lam. Mặc dù mô tả của tính chất này có vẻ tương đối đơn giản, **trên thực tế, việc chứng minh tính chất lựa chọn tham lam đối với nhiều bài toán không hề dễ dàng**.

Ví dụ, trong bài toán đổi tiền, mặc dù chúng ta có thể dễ dàng đưa ra các phản ví dụ để bác bỏ tính chất lựa chọn tham lam, nhưng việc chứng minh tính chất này đúng lại khó hơn nhiều. Nếu được hỏi, **một tập tiền xu cần thỏa mãn những điều kiện nào để có thể giải bằng thuật toán tham lam**? Chúng ta thường chỉ có thể dựa vào trực giác hoặc các ví dụ để đưa ra một câu trả lời mơ hồ, và rất khó cung cấp một chứng minh toán học chặt chẽ.

!!! quote

    Có một bài báo trình bày một thuật toán $O(n^3)$ để xác định liệu một tập tiền xu có thể được giải tối ưu bằng thuật toán tham lam với mọi số tiền hay không.

    Pearson, D. A polynomial-time algorithm for the change-making problem[J]. Operations Research Letters, 2005, 33(3): 231-234.

## Các bước giải bài toán bằng thuật toán tham lam

Quy trình chung để giải các bài toán tham lam có thể được chia thành ba bước sau.

1. **Phân tích bài toán**: Sắp xếp và tìm hiểu các đặc điểm của bài toán, bao gồm định nghĩa trạng thái, mục tiêu tối ưu và các ràng buộc. Bước này cũng xuất hiện trong backtracking và quy hoạch động.
2. **Xác định chiến lược tham lam**: Quyết định cách đưa ra lựa chọn tham lam ở mỗi bước. Chiến lược này cần giảm dần kích thước bài toán và cuối cùng giải quyết toàn bộ bài toán.
3. **Chứng minh tính đúng đắn**: Thông thường cần chứng minh rằng bài toán có cả tính chất lựa chọn tham lam và cấu trúc con tối ưu. Bước này có thể yêu cầu các công cụ toán học như quy nạp hoặc chứng minh phản chứng.

Xác định chiến lược tham lam là bước cốt lõi khi giải các bài toán dạng này, nhưng trên thực tế việc này có thể không dễ dàng, chủ yếu vì những lý do sau.

- **Chiến lược tham lam thay đổi rất nhiều tùy theo từng bài toán**. Với nhiều bài toán, chiến lược tham lam khá trực quan và có thể được suy ra thông qua suy luận sơ bộ và thử nghiệm. Tuy nhiên, với một số bài toán phức tạp, chiến lược tham lam có thể ẩn sâu, đòi hỏi nhiều kinh nghiệm giải quyết vấn đề và năng lực thuật toán.
- **Một số chiến lược tham lam rất dễ đánh lừa**. Chúng ta có thể tự tin thiết kế một chiến lược tham lam, viết mã lời giải và gửi bài, rồi phát hiện một số trường hợp kiểm thử bị thất bại. Nguyên nhân là chiến lược tham lam được thiết kế chỉ “đúng một phần”, như trong bài toán đổi tiền đã thảo luận ở trên.

Để đảm bảo tính đúng đắn, chúng ta nên đưa ra một chứng minh toán học chặt chẽ cho chiến lược tham lam, **thường sử dụng chứng minh phản chứng hoặc quy nạp toán học**.

Tuy nhiên, việc chứng minh tính đúng đắn cũng có thể khó khăn. Nếu không có định hướng rõ ràng, chúng ta thường phải gỡ lỗi dựa trên các trường hợp kiểm thử, từng bước sửa đổi và xác thực chiến lược tham lam.

## Các bài toán điển hình được giải bằng thuật toán tham lam

Thuật toán tham lam thường được áp dụng cho các bài toán tối ưu thỏa mãn tính chất lựa chọn tham lam và cấu trúc con tối ưu. Dưới đây là một số bài toán thuật toán tham lam điển hình.

- **Bài toán đổi tiền**: Với một số tổ hợp tiền xu nhất định, thuật toán tham lam luôn có thể tìm được lời giải tối ưu.
- **Bài toán lập lịch khoảng thời gian**: Giả sử bạn có một số tác vụ, mỗi tác vụ diễn ra trong một khoảng thời gian, và mục tiêu của bạn là hoàn thành nhiều tác vụ nhất có thể. Nếu luôn chọn tác vụ kết thúc sớm nhất, thuật toán tham lam có thể tìm được lời giải tối ưu.
- **Bài toán ba lô phân số**: Cho một tập các vật phẩm và sức chứa, mục tiêu của bạn là chọn một tập vật phẩm sao cho tổng trọng lượng không vượt quá sức chứa và tổng giá trị đạt lớn nhất. Nếu luôn chọn vật phẩm có tỷ lệ giá trị trên trọng lượng cao nhất (value / weight), thuật toán tham lam có thể tìm được lời giải tối ưu trong một số trường hợp.
- **Bài toán giao dịch cổ phiếu**: Cho một tập giá cổ phiếu trong quá khứ, bạn có thể thực hiện nhiều giao dịch, nhưng nếu đang nắm giữ cổ phiếu thì không thể mua thêm trước khi bán, và mục tiêu là thu được lợi nhuận lớn nhất.
- **Mã hóa Huffman**: Mã hóa Huffman là một thuật toán tham lam được sử dụng để nén dữ liệu không mất mát. Bằng cách xây dựng cây Huffman và luôn gộp hai node có tần suất thấp nhất, cây Huffman thu được sẽ có độ dài đường đi có trọng số nhỏ nhất (độ dài mã hóa).
- **Thuật toán Dijkstra**: Với các đồ thị có trọng số cạnh không âm, đây là một thuật toán tham lam để giải bài toán tìm đường đi ngắn nhất từ một đỉnh nguồn đã cho đến tất cả các đỉnh khác.