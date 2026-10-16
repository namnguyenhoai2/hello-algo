# Sắp xếp cơ số

Phần trước đã giới thiệu counting sort, phù hợp khi số lượng phần tử $n$ lớn nhưng phạm vi giá trị $m$ nhỏ. Giả sử chúng ta cần sắp xếp $n = 10^6$ mã số sinh viên, mỗi mã là một số có 8 chữ số. Khi đó, phạm vi giá trị $m = 10^8$ rất lớn. Việc sử dụng counting sort sẽ đòi hỏi một lượng bộ nhớ lớn, trong khi radix sort tránh được vấn đề này.

<u>Sắp xếp cơ số</u> dựa trên cùng một ý tưởng cốt lõi với counting sort: cũng sắp xếp bằng cách đếm số lần xuất hiện. Dựa trên đó, radix sort tận dụng mối quan hệ về vị trí giữa các chữ số và sắp xếp từng chữ số một để thu được kết quả cuối cùng.

## Quy trình thuật toán

Lấy dữ liệu mã số sinh viên làm ví dụ, giả sử chữ số thấp nhất là chữ số thứ $1$ và chữ số cao nhất là chữ số thứ $8$. Quy trình của radix sort được minh họa trong hình dưới đây.

1. Khởi tạo chữ số $k = 1$.
2. Thực hiện "counting sort" trên chữ số thứ $k$ của các mã số sinh viên. Sau khi hoàn tất, dữ liệu sẽ được sắp xếp từ nhỏ đến lớn theo chữ số thứ $k$.
3. Tăng $k$ lên $1$, sau đó quay lại bước `2.` và tiếp tục lặp cho đến khi tất cả các chữ số được sắp xếp; khi đó, quá trình kết thúc.

![Quy trình thuật toán sắp xếp cơ số](radix_sort.assets/radix_sort_overview.png)

Tiếp theo, hãy xem xét đoạn mã. Với một số $x$ trong hệ cơ số $d$, chữ số thứ $k$ $x_k$ của nó có thể được tính bằng công thức sau:

$$
x_k = \lfloor\frac{x}{d^{k-1}}\rfloor \bmod d
$$

Trong đó, $\lfloor a \rfloor$ biểu thị việc làm tròn số thực $a$ xuống, còn $\bmod \: d$ biểu thị phép lấy phần dư theo modulo $d$. Đối với dữ liệu mã số sinh viên, $d = 10$ và $k \in [1, 8]$.

Ngoài ra, chúng ta cần sửa đổi một chút mã counting sort để nó sắp xếp dựa trên chữ số thứ $k$ của số:

```src
[file]{radix_sort}-[class]{}-[func]{radix_sort}
```

!!! question "Tại sao bắt đầu sắp xếp từ chữ số thấp nhất?"

    Trong các lượt sắp xếp liên tiếp, lượt sau sẽ ghi đè lên kết quả của lượt trước. Ví dụ, nếu lượt đầu tiên cho kết quả $a < b$ nhưng lượt thứ hai cho kết quả $a > b$, thì kết quả của lượt thứ hai sẽ được ưu tiên. Vì các chữ số ở hàng cao hơn có độ ưu tiên cao hơn các chữ số ở hàng thấp hơn, chúng ta nên sắp xếp các chữ số thấp hơn trước, sau đó mới sắp xếp các chữ số cao hơn.

## Đặc điểm của thuật toán

So với counting sort, radix sort phù hợp với các phạm vi giá trị lớn hơn, **nhưng chỉ khi dữ liệu có thể được biểu diễn bằng một số chữ số cố định và số chữ số đó không quá lớn**. Ví dụ, số thực dấu phẩy động không phù hợp với radix sort vì số chữ số $k$ có thể quá lớn, có khả năng dẫn đến độ phức tạp thời gian $O(nk) \gg O(n^2)$.

- **Độ phức tạp thời gian $O(nk)$, sắp xếp không thích nghi**: Gọi số lượng phần tử là $n$, biểu diễn các giá trị trong hệ cơ số $d$, và gọi số chữ số tối đa là $k$. Counting sort trên một chữ số mất thời gian $O(n + d)$, vì vậy việc sắp xếp cả $k$ chữ số mất thời gian $O((n + d)k)$. Trong thực tế, $d$ và $k$ thường tương đối nhỏ, nên độ phức tạp thời gian tổng thể tiến gần đến $O(n)$.
- **Độ phức tạp không gian $O(n + d)$, sắp xếp không tại chỗ**: Giống như counting sort, radix sort yêu cầu các mảng phụ `res` và `counter` có độ dài lần lượt là $n$ và $d$.
- **Sắp xếp ổn định**: Khi counting sort ổn định, radix sort cũng ổn định; khi counting sort không ổn định, radix sort không thể đảm bảo kết quả sắp xếp chính xác.