# Thuật toán chia để trị

<u>Chia để trị</u> là một chiến lược thuật toán rất quan trọng và phổ biến. Chia để trị thường được triển khai dựa trên đệ quy, gồm hai bước: “chia” và “trị”.

1. **Chia (giai đoạn phân hoạch)**: Chia đệ quy bài toán ban đầu thành hai hoặc nhiều bài toán con cho đến khi đạt đến bài toán con nhỏ nhất.
2. **Trị (giai đoạn hợp nhất)**: Bắt đầu từ các bài toán con nhỏ nhất đã biết lời giải, hợp nhất lời giải của các bài toán con từ dưới lên để xây dựng lời giải cho bài toán ban đầu.

Như trong hình dưới đây, “merge sort” là một trong những ứng dụng điển hình của chiến lược chia để trị.

1. **Chia**: Chia đệ quy mảng ban đầu (bài toán ban đầu) thành hai mảng con (bài toán con) cho đến khi mảng con chỉ còn một phần tử (bài toán con nhỏ nhất).
2. **Trị**: Hợp nhất các mảng con đã sắp xếp (lời giải của các bài toán con) từ dưới lên để thu được mảng ban đầu đã sắp xếp (lời giải cho bài toán ban đầu).

![Chiến lược chia để trị của merge sort](divide_and_conquer.assets/divide_and_conquer_merge_sort.png)

## Cách xác định bài toán chia để trị

Thông thường, có thể xác định một bài toán có phù hợp để giải bằng chia để trị hay không dựa trên các tiêu chí sau:

1. **Bài toán có thể phân rã**: Bài toán ban đầu có thể được chia thành các bài toán con nhỏ hơn và tương tự nhau, đồng thời có thể tiếp tục chia đệ quy theo cùng một cách.
2. **Các bài toán con độc lập**: Các bài toán con không chồng lấn, độc lập với nhau và có thể được giải độc lập.
3. **Có thể hợp nhất lời giải của các bài toán con**: Lời giải của bài toán ban đầu được tạo ra bằng cách hợp nhất lời giải của các bài toán con.

Rõ ràng, merge sort đáp ứng cả ba tiêu chí này.

1. **Bài toán có thể phân rã**: Chia đệ quy mảng (bài toán ban đầu) thành hai mảng con (bài toán con).
2. **Các bài toán con độc lập**: Mỗi mảng con có thể được sắp xếp độc lập (các bài toán con có thể được giải độc lập).
3. **Có thể hợp nhất lời giải của các bài toán con**: Hai mảng con đã sắp xếp (lời giải của các bài toán con) có thể được hợp nhất thành một mảng đã sắp xếp (lời giải của bài toán ban đầu).

## Cải thiện hiệu suất thông qua chia để trị

**Chia để trị không chỉ có thể giải quyết hiệu quả các bài toán thuật toán mà thường còn có thể cải thiện hiệu suất của thuật toán**. Trong các thuật toán sắp xếp, quick sort, merge sort và heap sort nhanh hơn selection sort, bubble sort và insertion sort vì chúng áp dụng chiến lược chia để trị.

Điều này đặt ra câu hỏi: **Tại sao chia để trị có thể cải thiện hiệu suất của thuật toán và logic nền tảng là gì**? Nói cách khác, tại sao việc chia một bài toán lớn thành nhiều bài toán con, giải các bài toán con rồi hợp nhất lời giải của chúng lại hiệu quả hơn so với việc trực tiếp giải bài toán ban đầu? Có thể thảo luận câu hỏi này từ hai khía cạnh: số phép toán và tính toán song song.

### Tối ưu hóa số phép toán

Lấy “bubble sort” làm ví dụ, việc xử lý một mảng có độ dài $n$ cần thời gian $O(n^2)$. Giả sử ta chia mảng tại vị trí chính giữa thành hai mảng con, như trong hình dưới đây. Việc chia cần thời gian $O(n)$, việc sắp xếp mỗi mảng con cần thời gian $O((n / 2)^2)$, còn việc hợp nhất hai mảng con cần thời gian $O(n)$, do đó độ phức tạp thời gian tổng thể là:

$$
O(n + (\frac{n}{2})^2 \times 2 + n) = O(\frac{n^2}{2} + 2n)
$$

![Bubble sort trước và sau khi chia mảng](divide_and_conquer.assets/divide_and_conquer_bubble_sort.png)

Tiếp theo, ta tính bất đẳng thức sau, trong đó vế trái và vế phải lần lượt biểu thị tổng số phép toán trước và sau khi chia:

$$
\begin{aligned}
n^2 & > \frac{n^2}{2} + 2n \newline
n^2 - \frac{n^2}{2} - 2n & > 0 \newline
n(n - 4) & > 0
\end{aligned}
$$

**Điều này có nghĩa là khi $n > 4$, số phép toán sau khi chia sẽ ít hơn và hiệu suất sắp xếp sẽ cao hơn**. Lưu ý rằng độ phức tạp thời gian sau khi chia vẫn là bậc hai $O(n^2)$, nhưng hệ số không đổi trong độ phức tạp đã nhỏ hơn.

Tiến thêm một bước, **điều gì xảy ra nếu ta liên tục chia các mảng con từ vị trí chính giữa thành hai mảng con** cho đến khi các mảng con chỉ còn một phần tử? Cách tiếp cận này thực chất là “merge sort”, với độ phức tạp thời gian là $O(n \log n)$.

Tiếp tục suy nghĩ, **điều gì xảy ra nếu ta đặt nhiều điểm chia** và chia đều mảng ban đầu thành $k$ mảng con? Trường hợp này rất giống với “bucket sort”, vốn đặc biệt phù hợp để sắp xếp lượng dữ liệu khổng lồ, với độ phức tạp thời gian lý thuyết là $O(n + k)$.

### Tối ưu hóa tính toán song song

Ta biết rằng các bài toán con được tạo ra bởi chia để trị độc lập với nhau, **vì vậy chúng thường có thể được giải song song**. Điều này có nghĩa là chia để trị không chỉ có thể giảm độ phức tạp thời gian của thuật toán mà **còn phù hợp với việc tối ưu hóa song song bởi hệ điều hành**.

Tối ưu hóa song song đặc biệt hiệu quả trong môi trường đa lõi hoặc đa bộ xử lý, vì hệ thống có thể đồng thời xử lý nhiều bài toán con, tận dụng tốt hơn các tài nguyên tính toán và giảm đáng kể thời gian chạy tổng thể.

Ví dụ, trong “bucket sort” được minh họa ở hình dưới đây, ta phân phối đều lượng dữ liệu khổng lồ vào các bucket khác nhau, rồi phân phối các tác vụ sắp xếp của tất cả bucket cho các đơn vị tính toán khác nhau. Sau khi hoàn tất, các kết quả được hợp nhất.

![Tính toán song song trong bucket sort](divide_and_conquer.assets/divide_and_conquer_parallel_computing.png)

## Các ứng dụng phổ biến của chia để trị

Một mặt, chia để trị có thể được sử dụng để giải quyết nhiều bài toán thuật toán kinh điển.

- **Tìm cặp điểm gần nhất**: Thuật toán này trước tiên chia tập hợp điểm thành hai phần, sau đó tìm riêng cặp điểm gần nhất trong mỗi phần, cuối cùng tìm cặp điểm gần nhất trải qua cả hai phần.
- **Phép nhân số nguyên lớn**: Ví dụ, thuật toán Karatsuba phân rã phép nhân các số nguyên lớn thành một số phép nhân và phép cộng các số nguyên nhỏ hơn.
- **Phép nhân ma trận**: Ví dụ, thuật toán Strassen phân rã phép nhân các ma trận lớn thành nhiều phép nhân và phép cộng các ma trận nhỏ.
- **Bài toán Tháp Hà Nội**: Bài toán Tháp Hà Nội có thể được giải bằng đệ quy, đây là một ứng dụng điển hình của chiến lược chia để trị.
- **Giải bài toán cặp nghịch thế**: Trong một dãy, nếu một số đứng trước lớn hơn một số đứng sau thì hai số này tạo thành một cặp nghịch thế. Có thể giải bài toán cặp nghịch thế bằng phương pháp chia để trị với sự hỗ trợ của merge sort.

Mặt khác, chia để trị được áp dụng rộng rãi trong việc thiết kế thuật toán và cấu trúc dữ liệu.

- **Tìm kiếm nhị phân**: Tìm kiếm nhị phân chia một mảng đã sắp xếp thành hai phần tại chỉ số chính giữa, sau đó quyết định loại bỏ nửa nào dựa trên kết quả so sánh giữa giá trị mục tiêu và giá trị của phần tử ở giữa, rồi thực hiện cùng bước tìm kiếm nhị phân trên khoảng còn lại.
- **Merge sort**: Đã được giới thiệu ở đầu phần này, không cần trình bày thêm.
- **Quick sort**: Quick sort chọn một giá trị pivot, sau đó chia mảng thành hai mảng con, một mảng gồm các phần tử nhỏ hơn pivot và mảng còn lại gồm các phần tử lớn hơn pivot, rồi thực hiện cùng thao tác chia trên hai phần này cho đến khi các mảng con chỉ còn một phần tử.
- **Bucket sort**: Ý tưởng cơ bản của bucket sort là phân tán dữ liệu vào nhiều bucket, sau đó sắp xếp các phần tử trong từng bucket và cuối cùng lần lượt lấy các phần tử từ mỗi bucket để thu được một mảng đã sắp xếp.
- **Cây**: Ví dụ như binary search tree, cây AVL, cây đỏ-đen, B-tree, B+ tree, v.v. Các thao tác tìm kiếm, chèn và xóa của chúng đều có thể được xem là những ứng dụng của chiến lược chia để trị.
- **Heap**: Heap là một cây nhị phân hoàn chỉnh đặc biệt, và các thao tác khác nhau của nó, chẳng hạn như chèn, xóa và heapify, thực chất đều hàm chứa ý tưởng chia để trị.
- **Bảng băm**: Mặc dù bảng băm không trực tiếp áp dụng chia để trị, một số phương pháp xử lý xung đột băm lại gián tiếp áp dụng chiến lược chia để trị. Ví dụ, các linked list dài trong phương pháp chaining có thể được chuyển thành cây đỏ-đen để cải thiện hiệu suất tra cứu.

Có thể thấy rằng **chia để trị là một ý tưởng thuật toán “âm thầm hiện diện khắp nơi”**, được lồng ghép trong nhiều thuật toán và cấu trúc dữ liệu khác nhau.