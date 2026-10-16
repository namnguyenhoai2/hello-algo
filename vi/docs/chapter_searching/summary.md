# Tóm tắt

### Đánh giá chính

- Tìm kiếm nhị phân dựa trên dữ liệu có thứ tự và tìm kiếm bằng cách liên tục chia đôi khoảng tìm kiếm. Phương pháp này yêu cầu dữ liệu đầu vào đã được sắp xếp và chỉ áp dụng cho mảng hoặc các cấu trúc dữ liệu dựa trên mảng.
- Tìm kiếm vét cạn định vị dữ liệu bằng cách duyệt qua cấu trúc dữ liệu. Tìm kiếm tuyến tính áp dụng cho mảng và danh sách liên kết, trong khi tìm kiếm theo chiều rộng và tìm kiếm theo chiều sâu áp dụng cho đồ thị và cây. Các thuật toán này có phạm vi áp dụng rộng và không yêu cầu tiền xử lý dữ liệu, nhưng có độ phức tạp thời gian tương đối cao là $O(n)$.
- Tìm kiếm dựa trên hash, tìm kiếm trên cây và tìm kiếm nhị phân là các phương pháp tìm kiếm hiệu quả, có thể nhanh chóng định vị các phần tử mục tiêu trong những cấu trúc dữ liệu cụ thể. Các thuật toán này có hiệu suất cao, với độ phức tạp thời gian đạt $O(\log n)$ hoặc thậm chí $O(1)$, nhưng thường yêu cầu các cấu trúc dữ liệu bổ sung.
- Trong thực tế, chúng ta cần phân tích các yếu tố như quy mô dữ liệu, yêu cầu về hiệu suất tìm kiếm, cũng như tần suất truy vấn và cập nhật dữ liệu để lựa chọn phương pháp tìm kiếm phù hợp.
- Tìm kiếm tuyến tính phù hợp với các tập dữ liệu nhỏ hoặc dữ liệu được cập nhật thường xuyên; tìm kiếm nhị phân phù hợp với các tập dữ liệu lớn đã được sắp xếp; tìm kiếm dựa trên hash phù hợp khi yêu cầu hiệu suất truy vấn cao và không cần truy vấn theo phạm vi; tìm kiếm trên cây phù hợp với các tập dữ liệu động lớn cần duy trì thứ tự và hỗ trợ truy vấn theo phạm vi.
- Thay thế tìm kiếm tuyến tính bằng tìm kiếm dựa trên hash là một chiến lược thường được sử dụng để tối ưu hóa runtime, giảm độ phức tạp thời gian từ $O(n)$ xuống $O(1)$.