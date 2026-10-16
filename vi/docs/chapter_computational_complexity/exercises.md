# Bài tập

## Ôn tập khái niệm

### Độ phức tạp về thời gian và không gian của phép lặp và đệ quy

Hai hàm dưới đây đều tính $1 + 2 + \dots + n$ (giả sử $n \ge 1$). Đặt `n` thành 4, trả lời các câu hỏi theo đúng thứ tự thực thi của chương trình, sau đó so sánh hiệu quả của hai cách tiếp cận.

```src
[file]{complexity_exercises}-[class]{}-[func]{sum_iter}
```

<!-- numbered-subquestions -->

1. Khi hàm lặp chạy với `n = 4`, giá trị của biến tích lũy `res` sau mỗi lần lặp là gì?
2. Khi hàm đệ quy chạy với `n = 4`, đối số `n` lần lượt nhận những giá trị nào? Khi các lời gọi trả về từ mức sâu nhất, kết quả được tính như thế nào?
3. Độ phức tạp về thời gian và không gian của hai cách tiếp cận là gì? Hãy giải thích dựa trên quy trình thực thi trong Câu hỏi 1 và 2.

??? success "Đáp án"

    1. Biến vòng lặp `i` nhận các giá trị `1, 2, 3, 4`. Sau mỗi lần lặp, `res` lần lượt trở thành
        `1, 3, 6, 10`, vì vậy hàm lặp trả về 10.

    2. Đối số `n` nhận các giá trị `4 → 3 → 2 → 1`.
        Lời gọi sâu nhất trả về 1. Sau đó, các lời gọi còn lại lần lượt nhận được `2 + 1 = 3`, `3 + 3 = 6` và `4 + 6 = 10`.
        Tại thời điểm sâu nhất, cả bốn lời gọi hàm vẫn chưa hoàn tất.

    3. Cả hai hàm đều thực hiện số lần lặp hoặc số lời gọi tỉ lệ với $n$, nên cả hai đều có độ phức tạp thời gian là $O(n)$.
        Độ phức tạp không gian của chúng khác nhau. Phiên bản lặp chỉ sử dụng một số lượng biến không đổi, nên có độ phức tạp không gian là $O(1)$.
        Trong phiên bản đệ quy, các lời gọi trước đó phải chờ kết quả trước khi trả về, nên call stack chứa tối đa $n$ lời gọi cùng lúc.
        Độ phức tạp không gian của phiên bản này là $O(n)$.

        Khi phân tích độ phức tạp không gian, hãy nhớ tính cả không gian được sử dụng bởi các lời gọi đệ quy cũng như các biến được khai báo trong mã.

### Độ phức tạp thời gian của ba đoạn mã

Mỗi đoạn mã sau nhận một số nguyên dương $n$ làm đầu vào. Hãy sắp xếp chúng từ độ phức tạp thời gian thấp nhất đến cao nhất và nêu độ phức tạp của từng đoạn.

```src
[file]{complexity_exercises}-[class]{}-[func]{linear_loop}
```

??? success "Đáp án"

    Thứ tự từ thấp nhất đến cao nhất là Đoạn mã 3 với $O(\log n)$, Đoạn mã 1 với $O(n)$ và Đoạn mã 2 với $O(n^2)$.
    Đoạn mã 3 chia đôi $n$ trong mỗi lần lặp, nên chạy khoảng $\log_2 n$ lần.
    Vòng lặp trong Đoạn mã 1 chạy đúng $n$ lần. Vòng lặp lồng nhau trong Đoạn mã 2 chạy
    lần lượt $n,n-1,\dots,1$ lần, tổng cộng là $n(n+1)/2$, nên có độ phức tạp thời gian bậc hai.

### Cách đảo nào sử dụng ít không gian hơn?

Có hai cách để đảo tất cả các phần tử trong mảng `nums`:

<!-- numbered-subquestions -->

1. Tạo một mảng mới `res` có cùng độ dài, sao chép các phần tử vào đó theo thứ tự ngược lại rồi trả về mảng này.
2. Di chuyển hai chỉ số `i` và `j` vào phía trong từ đầu và cuối mảng, hoán đổi `nums[i]` và `nums[j]` ở mỗi bước.

    Độ phức tạp không gian của mỗi cách tiếp cận là gì? Cách nào là thao tác "tại chỗ"?

??? success "Đáp án"

    1. Cách tiếp cận này cần một mảng phụ có cùng độ dài với đầu vào, nên có độ phức tạp không gian là $O(n)$.

    2. Cách tiếp cận này chỉ sử dụng hai biến chỉ số,
        nên có độ phức tạp không gian là $O(1)$. Đây là thao tác tại chỗ.

        Lưu ý rằng việc đảo tại chỗ sẽ thay đổi mảng đầu vào,
        vì vậy chỉ nên sử dụng khi được phép sửa đổi đầu vào. Nếu phải giữ nguyên mảng ban đầu, chi phí sao chép của cách tiếp cận thứ nhất là không thể tránh khỏi.

## Bài tập lập trình

### Số Fibonacci

Dãy Fibonacci được định nghĩa bởi $F(0)=0$, $F(1)=1$ và với $n\ge2$,
$F(n)=F(n-1)+F(n-2)$.

Cho một số nguyên không âm `n`, hãy sử dụng vòng lặp để tính và trả về $F(n)$. Không sử dụng đệ quy.

??? tip "Gợi ý"

    1. Xử lý riêng các trường hợp n bằng 0 hoặc 1
    2. Chỉ cần hai số hạng trước đó để tính số hạng tiếp theo; không cần lưu toàn bộ dãy
    3. Khi cập nhật hai biến, hãy cẩn thận không ghi đè lên một giá trị cũ trước khi sử dụng nó

[LeetCode](https://leetcode.com/problems/fibonacci-number/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }