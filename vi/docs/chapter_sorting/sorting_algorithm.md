# Thuật toán sắp xếp

Một <u>thuật toán sắp xếp</u> sắp xếp một tập dữ liệu theo một thứ tự cụ thể. Thuật toán sắp xếp có rất nhiều ứng dụng vì dữ liệu đã được sắp xếp thường có thể được tìm kiếm, phân tích và xử lý hiệu quả hơn.

Như trong hình bên dưới, dữ liệu được sắp xếp có thể là số nguyên, số dấu phẩy động, ký tự, chuỗi, v.v. Quy tắc sắp xếp có thể được định nghĩa tùy theo nhu cầu, chẳng hạn như thứ tự số, thứ tự ASCII hoặc một quy tắc tùy chỉnh.

![Ví dụ về kiểu dữ liệu và tiêu chí](sorting_algorithm.assets/sorting_examples.png)

## Các khía cạnh đánh giá

**Hiệu quả thực thi**: Chúng ta mong muốn độ phức tạp thời gian của các thuật toán sắp xếp thấp nhất có thể, với tổng số thao tác nhỏ hơn (giảm hệ số hằng trong độ phức tạp thời gian). Đối với khối lượng dữ liệu lớn, hiệu quả thực thi đặc biệt quan trọng.

**Tính tại chỗ**: Như tên gọi cho thấy, <u>sắp xếp tại chỗ</u> thực hiện việc sắp xếp trực tiếp trên mảng ban đầu mà không cần các mảng phụ bổ sung, từ đó tiết kiệm bộ nhớ. Thông thường, sắp xếp tại chỗ bao gồm ít thao tác di chuyển dữ liệu hơn và chạy nhanh hơn.

**Tính ổn định**: <u>Sắp xếp ổn định</u> đảm bảo rằng thứ tự tương đối của các phần tử bằng nhau trong mảng không thay đổi sau khi hoàn tất sắp xếp.

Sắp xếp ổn định là điều kiện cần cho các tình huống sắp xếp đa cấp. Giả sử chúng ta có một bảng lưu thông tin sinh viên, trong đó cột 1 và cột 2 lần lượt là tên và tuổi. Trong trường hợp này, <u>sắp xếp không ổn định</u> có thể khiến tính có thứ tự của dữ liệu đầu vào bị mất:

```shell
# Dữ liệu đầu vào được sắp xếp theo tên
# (tên, tuổi)
  ('A', 19)
  ('B', 18)
  ('C', 21)
  ('D', 19)
  ('E', 23)

# Giả sử chúng ta sử dụng một thuật toán sắp xếp không ổn định để sắp xếp danh sách theo tuổi.
# Trong kết quả, vị trí tương đối của ('D', 19) và ('A', 19) thay đổi,
# vì vậy tính chất dữ liệu đầu vào được sắp xếp theo tên bị mất.
  ('B', 18)
  ('D', 19)
  ('A', 19)
  ('C', 21)
  ('E', 23)
```


**Tính thích nghi**: <u>Sắp xếp thích nghi</u> có thể tận dụng thông tin về thứ tự hiện có trong dữ liệu đầu vào để giảm lượng tính toán, từ đó đạt hiệu quả thời gian tốt hơn. Độ phức tạp thời gian trong trường hợp tốt nhất của các thuật toán sắp xếp thích nghi thường tốt hơn độ phức tạp thời gian trung bình.

**Dựa trên so sánh hoặc không dựa trên so sánh**: <u>Sắp xếp dựa trên so sánh</u> dựa vào các toán tử so sánh ($<$, $=$, $>$) để xác định thứ tự tương đối của các phần tử, qua đó sắp xếp toàn bộ mảng. Độ phức tạp thời gian trong trường hợp xấu nhất của nó có cận dưới là $\Omega(n \log n)$. <u>Sắp xếp không dựa trên so sánh</u> không sử dụng các toán tử so sánh và có thể đạt độ phức tạp thời gian $O(n)$, nhưng tính linh hoạt của nó tương đối hạn chế.

## Thuật toán sắp xếp lý tưởng

**Nhanh, tại chỗ, ổn định, thích nghi và có phạm vi áp dụng rộng**. Rõ ràng, cho đến nay chưa có thuật toán sắp xếp nào được phát hiện có thể kết hợp tất cả các đặc điểm này. Vì vậy, khi lựa chọn một thuật toán sắp xếp, cần đưa ra quyết định dựa trên các đặc điểm cụ thể của dữ liệu và yêu cầu của bài toán.

Tiếp theo, chúng ta sẽ xem xét nhiều thuật toán sắp xếp khác nhau và phân tích ưu điểm, nhược điểm của chúng dựa trên các khía cạnh đánh giá ở trên.