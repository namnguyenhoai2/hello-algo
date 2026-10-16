# Tóm tắt

### Đánh giá chính

- Đồ thị gồm các đỉnh và cạnh, đồng thời có thể được biểu diễn dưới dạng một tập hợp các đỉnh và một tập hợp các cạnh.
- So với các mối quan hệ tuyến tính được mô hình hóa bằng linked list và các mối quan hệ chia để trị được mô hình hóa bằng cây, các mối quan hệ mạng được mô hình hóa bằng đồ thị linh hoạt hơn nhiều, do đó cũng phức tạp hơn.
- Trong đồ thị có hướng, các cạnh có hướng; trong đồ thị liên thông, mọi đỉnh đều có thể đi tới từ bất kỳ đỉnh nào khác; và trong đồ thị có trọng số, mỗi cạnh mang một trọng số.
- Ma trận kề sử dụng ma trận để biểu diễn đồ thị, trong đó mỗi hàng (cột) biểu diễn một đỉnh, còn các phần tử ma trận biểu diễn các cạnh; dùng $1$ hoặc $0$ để cho biết hai đỉnh có cạnh nối hay không. Ma trận kề có hiệu suất rất cao đối với các thao tác thêm, xóa, tra cứu và sửa đổi, nhưng tiêu tốn nhiều không gian.
- Danh sách kề sử dụng nhiều linked list để biểu diễn một đồ thị: linked list thứ $i$ tương ứng với đỉnh $i$ và lưu trữ tất cả các đỉnh kề với nó. So với ma trận kề, danh sách kề sử dụng ít không gian hơn, nhưng việc tra cứu cạnh kém hiệu quả hơn vì phải duyệt linked list.
- Khi các linked list trong danh sách kề trở nên quá dài, có thể chuyển chúng thành red-black tree hoặc hash table, từ đó cải thiện hiệu suất tra cứu.
- Xét từ góc độ thuật toán, ma trận kề thể hiện việc “đánh đổi không gian lấy thời gian”, còn danh sách kề thể hiện việc “đánh đổi thời gian lấy không gian”.
- Đồ thị có thể được dùng để mô hình hóa nhiều hệ thống trong thế giới thực, chẳng hạn như mạng xã hội và các tuyến tàu điện ngầm.
- Cây là một trường hợp đặc biệt của đồ thị, còn việc duyệt cây là một trường hợp đặc biệt của việc duyệt đồ thị.
- Breadth-first search trong đồ thị khám phá từ gần đến xa, mở rộng theo từng lớp và thường được triển khai bằng queue.
- Depth-first search trong đồ thị đi theo một đường đi sâu nhất có thể và quay lui khi không thể đi xa hơn, thường được triển khai bằng recursion.

### Hỏi & Đáp

**Q**: Một path được định nghĩa là một chuỗi các đỉnh hay một chuỗi các cạnh?

Các định nghĩa trong những phiên bản Wikipedia bằng các ngôn ngữ khác nhau không thống nhất: phiên bản tiếng Anh nêu rằng “a path is a sequence of edges”, trong khi phiên bản tiếng Trung nêu rằng “a path is a sequence of vertices”. Dưới đây là nguyên văn tiếng Anh: In graph theory, a path in a graph is a finite or infinite sequence of edges which joins a sequence of vertices.

Trong tài liệu này, path được xem là một chuỗi các cạnh, không phải một chuỗi các đỉnh. Nguyên nhân là có thể có nhiều cạnh nối cùng hai đỉnh; khi đó, mỗi cạnh tương ứng với một path.

**Q**: Trong một đồ thị không liên thông, có tồn tại các đỉnh không thể đi tới không?

Trong một đồ thị không liên thông, nếu bắt đầu từ một đỉnh, sẽ có ít nhất một đỉnh khác không thể đi tới. Để duyệt một đồ thị không liên thông, bạn cần nhiều điểm bắt đầu để bao phủ tất cả các thành phần liên thông.

**Q**: Trong một danh sách kề, các đỉnh kề với một đỉnh nhất định có bắt buộc phải được sắp xếp theo thứ tự nào không?

Chúng có thể xuất hiện theo bất kỳ thứ tự nào. Tuy nhiên, trong thực tế, chúng có thể cần được sắp xếp theo các quy tắc cụ thể, chẳng hạn như thứ tự các đỉnh được thêm vào hoặc thứ tự của các giá trị đỉnh, nhằm hỗ trợ việc nhanh chóng tìm một đỉnh có giá trị cực trị nào đó.