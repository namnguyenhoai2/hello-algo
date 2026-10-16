# Tóm tắt

### Những điểm chính

- Heap là một cây nhị phân hoàn chỉnh. Tùy theo tính chất mà nó thỏa mãn, heap có thể được phân loại thành max heap hoặc min heap. Phần tử ở trên cùng của max heap (min heap) là phần tử lớn nhất (nhỏ nhất).
- Hàng đợi ưu tiên là một hàng đợi trong đó các phần tử được lấy ra theo độ ưu tiên, và thường được triển khai bằng heap.
- Các thao tác phổ biến trên heap và độ phức tạp thời gian tương ứng bao gồm: chèn một phần tử $O(\log n)$, xóa phần tử trên cùng $O(\log n)$ và truy cập phần tử trên cùng $O(1)$.
- Cây nhị phân hoàn chỉnh rất phù hợp để biểu diễn bằng mảng, vì vậy chúng ta thường dùng mảng để lưu trữ heap.
- Các thao tác heapify được sử dụng để duy trì tính chất heap và được áp dụng trong cả thao tác chèn lẫn xóa phần tử.
- Có thể tối ưu hóa việc xây dựng heap từ $n$ phần tử đầu vào xuống còn $O(n)$, đạt hiệu quả rất cao.
- Top-k là một bài toán thuật toán kinh điển có thể được giải hiệu quả bằng heap, với độ phức tạp thời gian là $O(n \log k)$.

### Hỏi & Đáp

**Q**: Thuật ngữ "heap" trong cấu trúc dữ liệu có cùng nghĩa với "heap" trong quản lý bộ nhớ không?

Đây không phải là cùng một khái niệm; chúng chỉ tình cờ có cùng tên. Trong các hệ thống máy tính, heap là một phần của cơ chế cấp phát bộ nhớ động, và các chương trình có thể sử dụng nó để lưu trữ dữ liệu trong thời gian chạy. Một chương trình có thể yêu cầu một lượng bộ nhớ heap nhất định để lưu trữ các cấu trúc phức tạp như object và array. Khi dữ liệu không còn cần thiết, chương trình phải giải phóng vùng nhớ đó để tránh rò rỉ bộ nhớ. So với bộ nhớ stack, bộ nhớ heap đòi hỏi việc quản lý và sử dụng cẩn thận hơn; nếu xử lý không đúng cách, có thể dẫn đến các vấn đề như rò rỉ bộ nhớ và con trỏ treo.