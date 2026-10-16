# Các thuật toán tìm kiếm được xem xét lại

<u>Các thuật toán tìm kiếm</u> được sử dụng để tìm một hoặc một nhóm phần tử đáp ứng các điều kiện cụ thể trong các cấu trúc dữ liệu (chẳng hạn như mảng, danh sách liên kết, cây hoặc đồ thị).

Dựa trên cách triển khai, các thuật toán tìm kiếm có thể được chia thành hai loại sau:

- **Xác định vị trí các phần tử mục tiêu bằng cách duyệt qua cấu trúc dữ liệu**, chẳng hạn như duyệt mảng, danh sách liên kết, cây và đồ thị.
- **Tìm kiếm phần tử hiệu quả bằng cách tận dụng cách dữ liệu được tổ chức hoặc thông tin có sẵn về dữ liệu**, chẳng hạn như tìm kiếm nhị phân, tìm kiếm dựa trên hash và tìm kiếm trên cây tìm kiếm nhị phân.

Vì các chủ đề này đã được giới thiệu trong những chương trước, các thuật toán tìm kiếm hẳn đã khá quen thuộc với chúng ta. Trong phần này, chúng ta sẽ xem xét lại chúng từ một góc nhìn có hệ thống hơn.

## Tìm kiếm vét cạn

Tìm kiếm vét cạn xác định vị trí các phần tử mục tiêu bằng cách duyệt qua từng phần tử của cấu trúc dữ liệu.

- "Tìm kiếm tuyến tính" áp dụng cho các cấu trúc dữ liệu tuyến tính như mảng và danh sách liên kết. Phương pháp này bắt đầu từ một đầu của cấu trúc dữ liệu và truy cập lần lượt từng phần tử cho đến khi tìm thấy phần tử mục tiêu hoặc đi đến đầu còn lại mà không tìm thấy phần tử đó.
- "Tìm kiếm theo chiều rộng" và "tìm kiếm theo chiều sâu" là hai chiến lược duyệt dành cho đồ thị và cây. Tìm kiếm theo chiều rộng bắt đầu từ node ban đầu và tìm kiếm theo từng lớp, thăm các node từ gần đến xa. Tìm kiếm theo chiều sâu bắt đầu từ node ban đầu, đi theo một đường dẫn đến cuối, sau đó quay lui và thử các đường dẫn khác cho đến khi toàn bộ cấu trúc dữ liệu được duyệt.

Ưu điểm của tìm kiếm vét cạn là đơn giản và có tính tổng quát cao, **không yêu cầu tiền xử lý dữ liệu hoặc cấu trúc dữ liệu bổ sung**.

Tuy nhiên, **độ phức tạp thời gian của các thuật toán này là $O(n)$**, trong đó $n$ là số lượng phần tử, vì vậy hiệu năng kém khi xử lý lượng dữ liệu lớn.

## Tìm kiếm thích ứng

Tìm kiếm thích ứng tận dụng các thuộc tính của chính dữ liệu (chẳng hạn như thứ tự đã sắp xếp) để tối ưu hóa quá trình tìm kiếm và xác định vị trí các phần tử mục tiêu hiệu quả hơn.

- "Tìm kiếm nhị phân" sử dụng tính có thứ tự của dữ liệu để thực hiện tìm kiếm hiệu quả, chỉ áp dụng cho mảng.
- "Tìm kiếm dựa trên hash" sử dụng hash table để lưu trữ dữ liệu có thể tìm kiếm dưới dạng các cặp key-value, qua đó cho phép truy vấn hiệu quả.
- "Tìm kiếm trên cây" hoạt động trên các cấu trúc cây cụ thể (chẳng hạn như cây tìm kiếm nhị phân), nhanh chóng loại bỏ các node bằng cách so sánh giá trị của chúng để xác định phần tử mục tiêu.

Ưu điểm của các thuật toán này là hiệu suất cao, **với độ phức tạp thời gian đạt $O(\log n)$ hoặc thậm chí $O(1)$**.

Tuy nhiên, **việc sử dụng các thuật toán này thường yêu cầu tiền xử lý dữ liệu**. Ví dụ, tìm kiếm nhị phân yêu cầu sắp xếp mảng trước, trong khi tìm kiếm dựa trên hash và tìm kiếm trên cây đều yêu cầu các cấu trúc dữ liệu bổ sung; việc duy trì các cấu trúc dữ liệu này cũng cần thêm thời gian và không gian.

!!! tip

    Các thuật toán tìm kiếm thích ứng thường được gọi là các thuật toán lookup, **chủ yếu được sử dụng để nhanh chóng truy xuất các phần tử mục tiêu trong những cấu trúc dữ liệu cụ thể**.

## Lựa chọn phương pháp tìm kiếm

Với một tập dữ liệu có kích thước $n$, chúng ta có thể sử dụng tìm kiếm tuyến tính, tìm kiếm nhị phân, tìm kiếm trên cây, tìm kiếm dựa trên hash và các phương pháp khác để tìm kiếm phần tử mục tiêu. Nguyên lý hoạt động của từng phương pháp được thể hiện trong hình dưới đây.

![Nhiều chiến lược tìm kiếm](searching_algorithm_revisited.assets/searching_algorithms.png)

Hiệu suất và đặc điểm của các phương pháp này được tóm tắt trong bảng dưới đây.

<p align="center"> Bảng <id> &nbsp; So sánh hiệu suất của các thuật toán tìm kiếm </p>

|                    | Tìm kiếm tuyến tính | Tìm kiếm nhị phân         | Tìm kiếm trên cây          | Tìm kiếm dựa trên hash     |
| ------------------ | ------------------- | ------------------------- | -------------------------- | -------------------------- |
| Tìm kiếm phần tử   | $O(n)$              | $O(\log n)$               | $O(\log n)$                | $O(1)$                     |
| Chèn phần tử       | $O(1)$              | $O(n)$                    | $O(\log n)$                | $O(1)$                     |
| Xóa phần tử        | $O(n)$              | $O(n)$                    | $O(\log n)$                | $O(1)$                     |
| Không gian bổ sung | $O(1)$              | $O(1)$                    | $O(n)$                     | $O(n)$                     |
| Tiền xử lý dữ liệu | /                   | Sắp xếp $O(n \log n)$     | Xây dựng cây $O(n \log n)$ | Xây dựng hash table $O(n)$ |
| Dữ liệu có thứ tự  | Không có thứ tự     | Có thứ tự                 | Có thứ tự                  | Không có thứ tự            |

Việc lựa chọn thuật toán tìm kiếm cũng phụ thuộc vào khối lượng dữ liệu, yêu cầu về hiệu suất tìm kiếm, tần suất truy vấn và cập nhật dữ liệu, v.v.

**Tìm kiếm tuyến tính**

- Có tính tổng quát cao và không yêu cầu các thao tác tiền xử lý dữ liệu. Nếu chúng ta chỉ cần truy vấn dữ liệu một lần, thời gian tiền xử lý cần thiết cho ba phương pháp còn lại có thể lâu hơn chính quá trình tìm kiếm tuyến tính.
- Phù hợp với khối lượng dữ liệu nhỏ, khi độ phức tạp thời gian ít ảnh hưởng đến hiệu suất.
- Phù hợp với các kịch bản có tần suất cập nhật dữ liệu cao, vì phương pháp này không yêu cầu duy trì dữ liệu bổ sung.

**Tìm kiếm nhị phân**

- Phù hợp với các tập dữ liệu lớn, có hiệu suất ổn định và độ phức tạp thời gian trong trường hợp xấu nhất là $O(\log n)$.
- Khối lượng dữ liệu không thể quá lớn, vì việc lưu trữ mảng yêu cầu không gian bộ nhớ liên tục.
- Không phù hợp với các kịch bản có thao tác chèn và xóa dữ liệu thường xuyên, vì việc duy trì một mảng đã sắp xếp có chi phí cao.

**Tìm kiếm dựa trên hash**

- Phù hợp với các kịch bản có yêu cầu cao về hiệu suất truy vấn, với độ phức tạp thời gian trung bình là $O(1)$.
- Không phù hợp với các kịch bản yêu cầu dữ liệu có thứ tự hoặc tìm kiếm theo phạm vi, vì hash table không thể duy trì dữ liệu theo thứ tự đã sắp xếp.
- Phụ thuộc nhiều vào các hàm hash và chiến lược xử lý xung đột hash, với rủi ro suy giảm hiệu suất đáng kể.
- Không phù hợp với khối lượng dữ liệu quá lớn, vì hash table yêu cầu thêm không gian để giảm thiểu xung đột và nhờ đó cung cấp hiệu suất truy vấn tốt.

**Tìm kiếm trên cây**

- Phù hợp với các tập dữ liệu khổng lồ, vì các node của cây được lưu trữ không liên tục trong bộ nhớ.
- Phù hợp với các kịch bản yêu cầu duy trì dữ liệu có thứ tự hoặc thực hiện tìm kiếm theo phạm vi.
- Khi liên tục chèn và xóa node, cây tìm kiếm nhị phân có thể bị lệch, khiến độ phức tạp thời gian suy giảm xuống $O(n)$.
- Nếu sử dụng cây AVL hoặc cây đỏ-đen, mọi thao tác có thể luôn thực hiện trong thời gian $O(\log n)$, mặc dù việc duy trì cân bằng cây sẽ làm phát sinh thêm chi phí.