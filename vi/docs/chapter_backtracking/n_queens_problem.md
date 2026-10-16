# Bài toán N quân hậu

!!! question

    Theo luật cờ vua, quân hậu có thể tấn công bất kỳ quân cờ nào nằm trên cùng hàng, cùng cột hoặc cùng đường chéo. Cho $n$ quân hậu và một bàn cờ $n \times n$, hãy tìm cách sắp xếp sao cho không có hai quân hậu nào có thể tấn công lẫn nhau.

Như hình dưới đây, khi $n = 4$, có thể tìm được hai nghiệm. Xét từ góc độ của thuật toán quay lui, một bàn cờ $n \times n$ có $n^2$ ô, cung cấp tất cả các lựa chọn `choices`. Trong quá trình lần lượt đặt các quân hậu, trạng thái bàn cờ liên tục thay đổi, và bàn cờ tại mỗi thời điểm biểu diễn trạng thái `state`.

![Lời giải bài toán 4 quân hậu](n_queens_problem.assets/solution_4_queens.png)

Hình dưới đây minh họa ba ràng buộc của bài toán này: **nhiều quân hậu không thể nằm trên cùng một hàng, cùng một cột hoặc cùng một đường chéo**. Cần lưu ý rằng các đường chéo được chia thành hai loại: đường chéo chính `\` và đường chéo phụ `/`.

![Các ràng buộc của bài toán n quân hậu](n_queens_problem.assets/n_queens_constraints.png)

### Chiến lược đặt quân theo từng hàng

Vì cả số quân hậu và số hàng trên bàn cờ đều là $n$, ta có thể dễ dàng suy ra một kết luận: **mỗi hàng trên bàn cờ cho phép đặt một và chỉ một quân hậu**.

Điều này có nghĩa là ta có thể áp dụng chiến lược đặt quân theo từng hàng: bắt đầu từ hàng đầu tiên, đặt một quân hậu trên mỗi hàng cho đến khi hoàn tất hàng cuối cùng.

Hình dưới đây minh họa quá trình đặt quân theo từng hàng cho bài toán 4 quân hậu. Do giới hạn về không gian, hình chỉ mở rộng một nhánh tìm kiếm của hàng đầu tiên; tất cả các phương án vi phạm ràng buộc về cột hoặc đường chéo đều bị cắt tỉa.

![Chiến lược đặt quân theo từng hàng](n_queens_problem.assets/n_queens_placing.png)

Về bản chất, **chiến lược đặt quân theo từng hàng có tác dụng cắt tỉa**, vì nó loại bỏ tất cả các nhánh tìm kiếm trong đó nhiều quân hậu xuất hiện trên cùng một hàng.

### Cắt tỉa theo cột và đường chéo

Để thỏa mãn ràng buộc về cột, ta có thể sử dụng một mảng boolean `cols` có độ dài $n$ để ghi lại việc mỗi cột đã có quân hậu hay chưa. Trước mỗi quyết định đặt quân, ta sử dụng `cols` để cắt tỉa các cột đã có quân hậu, đồng thời cập nhật động trạng thái của `cols` trong quá trình quay lui.

!!! tip

    Xin lưu ý rằng gốc của ma trận nằm ở góc trên bên trái, trong đó chỉ số hàng tăng dần từ trên xuống dưới, còn chỉ số cột tăng dần từ trái sang phải.

Vậy ta xử lý các ràng buộc về đường chéo như thế nào? Xét một ô trên bàn cờ có chỉ số hàng và cột là $(row, col)$. Nếu chọn một đường chéo chính cụ thể trong ma trận, ta nhận thấy rằng mọi ô trên đường chéo đó đều có cùng hiệu giữa chỉ số hàng và chỉ số cột, **nghĩa là $row - col$ có cùng một giá trị không đổi đối với mọi ô trên đường chéo chính**.

Nói cách khác, nếu hai ô thỏa mãn $row_1 - col_1 = row_2 - col_2$, chúng chắc chắn nằm trên cùng một đường chéo chính. Dựa trên quy luật này, ta có thể sử dụng mảng `diags1` như trong hình dưới đây để ghi lại việc mỗi đường chéo chính có quân hậu hay chưa.

Tương tự, **đối với mọi ô trên một đường chéo phụ, tổng $row + col$ có cùng một giá trị không đổi**. Ta cũng có thể sử dụng mảng `diags2` để xử lý các ràng buộc về đường chéo phụ.

![Xử lý các ràng buộc về cột và đường chéo](n_queens_problem.assets/n_queens_cols_diagonals.png)

### Cài đặt bằng code

Xin lưu ý rằng trong một ma trận vuông $n \times n$, miền giá trị của $row - col$ là $[-n + 1, n - 1]$, còn miền giá trị của $row + col$ là $[0, 2n - 2]$. Do đó, số lượng đường chéo chính và đường chéo phụ đều là $2n - 1$, nghĩa là độ dài của cả hai mảng `diags1` và `diags2` đều là $2n - 1$.

```src
[file]{n_queens}-[class]{}-[func]{n_queens}
```

Đặt $n$ quân hậu theo từng hàng, xét đến ràng buộc về cột, từ hàng đầu tiên đến hàng cuối cùng có lần lượt $n$, $n-1$, $\dots$, $2$, $1$ lựa chọn, nên cần thời gian $O(n!)$. Khi ghi nhận một nghiệm, cần sao chép ma trận `state` và thêm nó vào `res`, trong đó thao tác sao chép cần thời gian $O(n^2)$. Vì vậy, **độ phức tạp thời gian tổng thể là $O(n! \cdot n^2)$**. Trên thực tế, việc cắt tỉa dựa trên các ràng buộc về đường chéo cũng có thể làm giảm đáng kể không gian tìm kiếm, nên hiệu suất tìm kiếm thường tốt hơn độ phức tạp thời gian nêu trên.

Mảng `state` sử dụng không gian $O(n^2)$, còn các mảng `cols`, `diags1` và `diags2` mỗi mảng sử dụng không gian $O(n)$. Độ sâu đệ quy tối đa là $n$, sử dụng không gian $O(n)$ cho các stack frame. Vì vậy, **độ phức tạp không gian là $O(n^2)$**.