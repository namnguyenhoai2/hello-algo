# Đồ thị

Một <u>đồ thị</u> là một cấu trúc dữ liệu phi tuyến bao gồm các <u>đỉnh</u> và <u>cạnh</u>. Về mặt trừu tượng, ta có thể biểu diễn một đồ thị $G$ dưới dạng một tập hợp các đỉnh $V$ và một tập hợp các cạnh $E$. Ví dụ sau đây minh họa một đồ thị gồm 5 đỉnh và 7 cạnh.

$$
\begin{aligned}
V & = \{ 1, 2, 3, 4, 5 \} \newline
E & = \{ (1,2), (1,3), (1,5), (2,3), (2,4), (2,5), (4,5) \} \newline
G & = \{ V, E \} \newline
\end{aligned}
$$

Nếu xem các đỉnh là các nút và các cạnh là các tham chiếu (con trỏ) kết nối chúng, ta có thể coi đồ thị là một phần mở rộng của cấu trúc dữ liệu danh sách liên kết. Như hình dưới đây cho thấy, **so với các mối quan hệ tuyến tính (danh sách liên kết) và các mối quan hệ chia để trị (cây), các mối quan hệ mạng (đồ thị) có mức độ tự do cao hơn và do đó phức tạp hơn**.

![Mối quan hệ giữa danh sách liên kết, cây và đồ thị](graph.assets/linkedlist_tree_graph.png)

## Các loại và thuật ngữ đồ thị phổ biến

Dựa trên việc các cạnh có hướng hay không, đồ thị có thể được chia thành <u>đồ thị vô hướng</u> và <u>đồ thị có hướng</u>, như minh họa trong hình dưới đây.

- Trong đồ thị vô hướng, các cạnh biểu thị kết nối "hai chiều" giữa hai đỉnh, chẳng hạn như mối quan hệ bạn bè trên WeChat hoặc QQ.
- Trong đồ thị có hướng, các cạnh có hướng, nghĩa là các cạnh $A \rightarrow B$ và $A \leftarrow B$ độc lập với nhau, chẳng hạn như mối quan hệ theo dõi và người theo dõi trên Weibo hoặc TikTok.

![Đồ thị có hướng và vô hướng](graph.assets/directed_graph.png)

Dựa trên việc tất cả các đỉnh có được kết nối hay không, đồ thị có thể được chia thành <u>đồ thị liên thông</u> và <u>đồ thị không liên thông</u>, như minh họa trong hình dưới đây.

- Với đồ thị liên thông, bắt đầu từ bất kỳ đỉnh nào, ta đều có thể đi đến tất cả các đỉnh khác.
- Với đồ thị không liên thông, bắt đầu từ một đỉnh nhất định, tồn tại ít nhất một đỉnh không thể đi đến được.

![Đồ thị liên thông và không liên thông](graph.assets/connected_graph.png)

Ta cũng có thể thêm một biến "trọng số" vào các cạnh, tạo thành <u>đồ thị có trọng số</u> như minh họa trong hình dưới đây. Ví dụ, trong các trò chơi di động như "Honor of Kings", hệ thống tính toán "mức độ thân thiết" giữa những người chơi dựa trên thời gian họ đã chơi cùng nhau, và các mạng lưới thân thiết như vậy có thể được biểu diễn bằng đồ thị có trọng số.

![Đồ thị có trọng số và không trọng số](graph.assets/weighted_graph.png)

Cấu trúc dữ liệu đồ thị bao gồm các thuật ngữ thường dùng sau đây.

- <u>Tính kề</u>: Khi hai đỉnh được nối với nhau bằng một cạnh, hai đỉnh này được gọi là "kề nhau". Trong hình trên, các đỉnh kề với đỉnh 1 là các đỉnh 2, 3 và 5.
- <u>Đường đi</u>: Dãy các cạnh từ đỉnh A đến đỉnh B được gọi là "đường đi" từ A đến B. Trong hình trên, dãy cạnh 1-5-2-4 là một đường đi từ đỉnh 1 đến đỉnh 4.
- <u>Bậc</u>: Số lượng cạnh mà một đỉnh có. Đối với đồ thị có hướng, <u>bậc vào</u> cho biết có bao nhiêu cạnh hướng đến đỉnh đó, còn <u>bậc ra</u> cho biết có bao nhiêu cạnh đi ra từ đỉnh đó.

## Biểu diễn đồ thị

Các cách biểu diễn đồ thị phổ biến bao gồm "ma trận kề" và "danh sách kề". Phần sau sử dụng đồ thị vô hướng làm ví dụ.

### Ma trận kề

Cho một đồ thị có $n$ đỉnh, một <u>ma trận kề</u> sử dụng một ma trận $n \times n$ để biểu diễn đồ thị, trong đó mỗi hàng (cột) biểu diễn một đỉnh, còn các phần tử của ma trận biểu diễn các cạnh, sử dụng $1$ hoặc $0$ để cho biết giữa hai đỉnh có tồn tại cạnh hay không.

Như minh họa trong hình dưới đây, gọi ma trận kề là $M$ và danh sách đỉnh là $V$. Khi đó, phần tử ma trận $M[i, j] = 1$ cho biết tồn tại một cạnh giữa đỉnh $V[i]$ và đỉnh $V[j]$, trong khi $M[i, j] = 0$ cho biết không có cạnh giữa hai đỉnh này.

![Biểu diễn đồ thị bằng ma trận kề](graph.assets/adjacency_matrix.png)

Ma trận kề có các thuộc tính sau.

- Trong đồ thị đơn, các đỉnh không thể nối với chính chúng, vì vậy các phần tử trên đường chéo chính của ma trận kề không có ý nghĩa.
- Với đồ thị vô hướng, các cạnh theo cả hai hướng là tương đương, vì vậy ma trận kề đối xứng qua đường chéo chính.
- Thay các phần tử $1$ và $0$ trong ma trận kề bằng các trọng số cho phép ma trận biểu diễn đồ thị có trọng số.

Khi sử dụng ma trận kề để biểu diễn đồ thị, ta có thể truy cập trực tiếp các phần tử của ma trận để lấy các cạnh, nhờ đó các thao tác thêm, xóa, tra cứu và sửa đổi đều có hiệu suất rất cao, với độ phức tạp thời gian là $O(1)$. Tuy nhiên, độ phức tạp không gian của ma trận là $O(n^2)$, tiêu tốn đáng kể bộ nhớ.

### Danh sách kề

Một <u>danh sách kề</u> sử dụng $n$ danh sách liên kết để biểu diễn một đồ thị, trong đó các nút của danh sách liên kết biểu diễn các đỉnh. Danh sách liên kết thứ $i$ tương ứng với đỉnh $i$ và lưu trữ tất cả các đỉnh kề với đỉnh đó (các đỉnh được nối với đỉnh đó). Hình dưới đây minh họa một đồ thị được lưu trữ bằng danh sách kề.

![Biểu diễn đồ thị bằng danh sách kề](graph.assets/adjacency_list.png)

Danh sách kề chỉ lưu trữ các cạnh thực sự tồn tại, và tổng số cạnh thường nhỏ hơn nhiều so với $n^2$, nên tiết kiệm không gian hơn. Tuy nhiên, để tìm một cạnh trong danh sách kề, ta cần duyệt qua danh sách liên kết, vì vậy hiệu quả thời gian thấp hơn so với ma trận kề.

Như hình trên cho thấy, **cấu trúc của danh sách kề rất giống với phương pháp separate chaining trong hash table, vì vậy ta có thể sử dụng các phương pháp tương tự để cải thiện hiệu suất**. Ví dụ, khi một danh sách liên kết trở nên dài, ta có thể chuyển nó thành cây AVL hoặc cây đỏ-đen, cải thiện độ phức tạp thời gian từ $O(n)$ lên $O(\log n)$; hoặc cũng có thể chuyển nó thành hash table, giảm độ phức tạp thời gian xuống $O(1)$.

## Các ứng dụng phổ biến của đồ thị

Như minh họa trong bảng dưới đây, nhiều hệ thống trong thế giới thực có thể được mô hình hóa bằng đồ thị, và các bài toán tương ứng có thể được quy về các bài toán tính toán trên đồ thị.

<p align="center"> Bảng <id> &nbsp; Các đồ thị phổ biến trong đời thực </p>

|                | Các đỉnh        | Các cạnh                                  | Bài toán tính toán trên đồ thị     |
| -------------- | --------------- | -------------------------------------- | ----------------------------- |
| Mạng xã hội | Người dùng           | Mối quan hệ bạn bè                   | Đề xuất bạn bè tiềm năng |
| Tuyến tàu điện ngầm   | Nhà ga        | Kết nối giữa các nhà ga          | Đề xuất tuyến đường ngắn nhất |
| Hệ Mặt Trời   | Các thiên thể | Lực hấp dẫn giữa các thiên thể | Tính toán quỹ đạo hành tinh   |