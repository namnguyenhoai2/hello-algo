# Chiến lược tìm kiếm chia để trị

Chúng ta đã biết rằng các thuật toán tìm kiếm được chia thành hai loại chính.

- **Tìm kiếm vét cạn**: Được thực hiện bằng cách duyệt qua cấu trúc dữ liệu, với độ phức tạp thời gian là $O(n)$.
- **Tìm kiếm thích ứng**: Tận dụng cách tổ chức dữ liệu cụ thể hoặc thông tin có sẵn, với độ phức tạp thời gian đạt $O(\log n)$ hoặc thậm chí $O(1)$.

Trên thực tế, **các thuật toán tìm kiếm có độ phức tạp thời gian $O(\log n)$ thường được triển khai dựa trên chiến lược chia để trị**, chẳng hạn như tìm kiếm nhị phân và cây.

- Mỗi bước của tìm kiếm nhị phân chia bài toán (tìm một phần tử đích trong mảng) thành một bài toán nhỏ hơn (tìm phần tử đích trong một nửa mảng), tiếp tục cho đến khi mảng rỗng hoặc tìm thấy phần tử đích.
- Cây là đại diện tiêu biểu cho tư tưởng chia để trị. Trong các cấu trúc dữ liệu như cây tìm kiếm nhị phân, cây AVL và heap, độ phức tạp thời gian của nhiều thao tác là $O(\log n)$.

Chiến lược chia để trị của tìm kiếm nhị phân như sau.

- **Bài toán có thể được phân rã**: Tìm kiếm nhị phân đệ quy phân rã bài toán ban đầu (tìm kiếm trong một mảng) thành các bài toán con (tìm kiếm trong một nửa mảng), bằng cách so sánh phần tử ở giữa với phần tử đích.
- **Các bài toán con độc lập với nhau**: Trong tìm kiếm nhị phân, mỗi vòng chỉ xử lý một bài toán con và không bị ảnh hưởng bởi các bài toán con khác.
- **Không cần hợp nhất lời giải của các bài toán con**: Tìm kiếm nhị phân nhằm tìm một phần tử cụ thể, vì vậy không cần hợp nhất lời giải của các bài toán con. Khi một bài toán con được giải quyết, bài toán ban đầu cũng được giải quyết.

Chia để trị có thể cải thiện hiệu quả tìm kiếm vì tìm kiếm vét cạn chỉ có thể loại bỏ một lựa chọn trong mỗi vòng, **trong khi tìm kiếm chia để trị có thể loại bỏ một nửa số lựa chọn trong mỗi vòng**.

### Triển khai tìm kiếm nhị phân dựa trên chia để trị

Trong các phần trước, tìm kiếm nhị phân được triển khai dựa trên phép lặp. Bây giờ, chúng ta triển khai nó dựa trên chia để trị (đệ quy).

!!! question

    Cho một mảng đã được sắp xếp `nums` có độ dài $n$, trong đó tất cả các phần tử đều là duy nhất, hãy tìm `target`.

Từ góc nhìn chia để trị, chúng ta ký hiệu bài toán con tương ứng với khoảng tìm kiếm $[i, j]$ là $f(i, j)$.

Bắt đầu từ bài toán ban đầu $f(0, n-1)$, thực hiện tìm kiếm nhị phân theo các bước sau.

1. Tính điểm giữa $m$ của khoảng tìm kiếm $[i, j]$ và dùng nó để loại bỏ một nửa khoảng tìm kiếm.
2. Đệ quy giải quyết bài toán con đã được giảm một nửa về kích thước, có thể là $f(i, m-1)$ hoặc $f(m+1, j)$.
3. Lặp lại bước `1.` và `2.` cho đến khi tìm thấy `target`, hoặc trả về khi khoảng tìm kiếm rỗng.

Hình dưới đây minh họa quá trình chia để trị của tìm kiếm nhị phân phần tử $6$ trong một mảng.

![Quá trình chia để trị của tìm kiếm nhị phân](binary_search_recur.assets/binary_search_recur.png)

Trong mã triển khai, chúng ta khai báo một hàm đệ quy `dfs()` để giải quyết bài toán $f(i, j)$:

```src
[file]{binary_search_recur}-[class]{}-[func]{binary_search}
```
