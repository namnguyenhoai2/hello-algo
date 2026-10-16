# Thuật toán là gì

## Định nghĩa thuật toán

<u>thuật toán</u> là một tập hợp các chỉ dẫn hoặc bước thao tác dùng để giải quyết một vấn đề cụ thể trong một khoảng thời gian hữu hạn. Thuật toán có các đặc điểm sau.

- Vấn đề được xác định rõ ràng, với định nghĩa rõ về đầu vào và đầu ra.
- Có tính khả thi và có thể hoàn thành trong số bước, thời gian và dung lượng bộ nhớ hữu hạn.
- Mỗi bước có ý nghĩa xác định; với cùng đầu vào và điều kiện vận hành, đầu ra luôn giống nhau.

## Định nghĩa cấu trúc dữ liệu

<u>cấu trúc dữ liệu</u> là cách tổ chức và lưu trữ dữ liệu, bao gồm bản thân dữ liệu, mối quan hệ giữa các phần tử dữ liệu và các phương thức dùng để thao tác với chúng. Cấu trúc dữ liệu có các mục tiêu thiết kế sau.

- Chiếm càng ít không gian càng tốt để tiết kiệm bộ nhớ máy tính.
- Các thao tác trên dữ liệu phải nhanh nhất có thể, bao gồm truy cập, thêm, xóa, cập nhật dữ liệu, v.v.
- Cung cấp cách biểu diễn dữ liệu cô đọng và thông tin logic để các thuật toán có thể chạy hiệu quả.

**Thiết kế cấu trúc dữ liệu là một quá trình đầy sự đánh đổi**. Nếu muốn cải thiện một khía cạnh, chúng ta thường phải thỏa hiệp ở một khía cạnh khác. Dưới đây là hai ví dụ.

- So với mảng, danh sách liên kết thuận tiện hơn cho các thao tác thêm và xóa dữ liệu nhưng phải đánh đổi tốc độ truy cập dữ liệu.
- So với danh sách liên kết, đồ thị cung cấp thông tin logic phong phú hơn nhưng yêu cầu dung lượng bộ nhớ lớn hơn.

## Mối quan hệ giữa cấu trúc dữ liệu và thuật toán

Như hình dưới đây minh họa, cấu trúc dữ liệu và thuật toán có mối liên hệ rất chặt chẽ và gắn kết với nhau, cụ thể thể hiện ở ba khía cạnh sau.

- Cấu trúc dữ liệu là nền tảng của thuật toán. Cấu trúc dữ liệu cung cấp cho thuật toán cách lưu trữ dữ liệu có cấu trúc và các phương thức thao tác trên dữ liệu.
- Thuật toán thổi sức sống vào cấu trúc dữ liệu. Bản thân cấu trúc dữ liệu chỉ lưu trữ thông tin dữ liệu; khi kết hợp với thuật toán, chúng có thể giải quyết các vấn đề cụ thể.
- Thuật toán thường có thể được triển khai dựa trên các cấu trúc dữ liệu khác nhau, nhưng hiệu suất thực thi có thể khác biệt rất lớn. Việc lựa chọn cấu trúc dữ liệu phù hợp là yếu tố then chốt.

![Mối quan hệ giữa cấu trúc dữ liệu và thuật toán](what_is_dsa.assets/relationship_between_data_structure_and_algorithm.png)

Cấu trúc dữ liệu và thuật toán giống như việc lắp ráp các khối xây dựng, như hình dưới đây minh họa. Một bộ khối xây dựng không chỉ bao gồm nhiều bộ phận mà còn đi kèm hướng dẫn lắp ráp chi tiết. Bằng cách làm theo hướng dẫn từng bước, chúng ta có thể lắp ráp thành một mô hình khối xây dựng tinh xảo.

![Lắp ráp các khối xây dựng](what_is_dsa.assets/assembling_blocks.png)

Mối tương ứng chi tiết giữa hai khái niệm được thể hiện trong bảng dưới đây.

<p align="center"> Bảng <id> &nbsp; So sánh cấu trúc dữ liệu và thuật toán với việc lắp ráp các khối xây dựng </p>

| Cấu trúc dữ liệu và thuật toán | Lắp ráp các khối xây dựng                                        |
| ------------------------------ | ------------------------------------------------------------------ |
| Dữ liệu đầu vào                | Các khối xây dựng chưa được lắp ráp                                |
| Cấu trúc dữ liệu               | Cách tổ chức các khối xây dựng, bao gồm hình dạng, kích thước, phương thức kết nối, v.v. |
| Thuật toán                     | Một loạt bước thao tác để lắp ráp các khối thành hình dạng mục tiêu |
| Dữ liệu đầu ra                 | Mô hình khối xây dựng                                               |

Cần lưu ý rằng cấu trúc dữ liệu và thuật toán độc lập với ngôn ngữ lập trình. Đó là lý do cuốn sách này có thể cung cấp các bản triển khai bằng nhiều ngôn ngữ lập trình.

!!! tip "Cách viết tắt thông dụng"

    Trong các cuộc thảo luận thực tế, chúng ta thường viết tắt "cấu trúc dữ liệu và thuật toán" thành "thuật toán". Ví dụ, các bài toán thuật toán LeetCode nổi tiếng thực tế kiểm tra kiến thức về cả cấu trúc dữ liệu và thuật toán.