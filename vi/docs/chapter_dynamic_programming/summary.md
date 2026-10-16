# Tóm tắt

### Các điểm chính

- Quy hoạch động phân rã bài toán và tránh việc tính toán trùng lặp bằng cách lưu trữ lời giải của các bài toán con, qua đó cải thiện đáng kể hiệu suất tính toán.
- Nếu không xét đến giới hạn thời gian, mọi bài toán quy hoạch động đều có thể được giải bằng backtracking (tìm kiếm vét cạn), nhưng cây đệ quy chứa rất nhiều bài toán con chồng lặp, dẫn đến hiệu suất cực kỳ thấp. Bằng cách sử dụng một danh sách memo, ta có thể lưu trữ lời giải của tất cả các bài toán con đã tính, bảo đảm rằng mỗi bài toán con chồng lặp chỉ được tính một lần.
- Memoization là lời giải đệ quy từ trên xuống, còn quy hoạch động tương ứng là lời giải lặp từ dưới lên, tương tự như “điền vào một bảng”. Vì trạng thái hiện tại chỉ phụ thuộc vào một số trạng thái cục bộ, ta có thể loại bỏ một chiều của bảng $dp$ để giảm độ phức tạp không gian.
- Phân rã bài toán con là một phương pháp thiết kế thuật toán tổng quát, với các đặc điểm khác nhau trong chia để trị, quy hoạch động và backtracking.
- Bài toán quy hoạch động có ba đặc điểm chính: các bài toán con chồng lặp, cấu trúc tối ưu và không có hậu quả về sau.
- Nếu lời giải tối ưu của bài toán ban đầu có thể được xây dựng từ các lời giải tối ưu của các bài toán con, thì bài toán đó có cấu trúc tối ưu.
- Không có hậu quả về sau nghĩa là với một trạng thái nhất định, sự phát triển của nó trong tương lai chỉ liên quan đến trạng thái đó và không liên quan đến tất cả các trạng thái trước đây. Nhiều bài toán tối ưu tổ hợp không thỏa mãn tính chất này và không thể được giải hiệu quả bằng quy hoạch động.

**Bài toán ba lô**

- Bài toán ba lô là một trong những bài toán quy hoạch động điển hình nhất, với các biến thể như ba lô 0-1, ba lô không giới hạn và ba lô nhiều lựa chọn.
- Định nghĩa trạng thái của bài toán ba lô 0-1 là giá trị lớn nhất có thể đạt được khi sử dụng $i$ vật phẩm đầu tiên với sức chứa ba lô là $c$. Dựa trên hai lựa chọn: không cho một vật phẩm vào ba lô hoặc cho vật phẩm đó vào, ta có thể xác định cấu trúc tối ưu và xây dựng công thức chuyển trạng thái. Khi tối ưu không gian, vì mỗi trạng thái phụ thuộc vào trạng thái ngay phía trên và trạng thái ở phía trên bên trái, danh sách cần được duyệt theo thứ tự ngược để tránh ghi đè lên trạng thái phía trên bên trái.
- Bài toán ba lô không giới hạn không giới hạn số lượng lựa chọn của mỗi loại vật phẩm, vì vậy chuyển trạng thái khi chọn đưa một vật phẩm vào sẽ khác với bài toán ba lô 0-1. Vì trạng thái phụ thuộc vào trạng thái ngay phía trên và ngay bên trái, khi tối ưu không gian cần duyệt theo thứ tự xuôi.
- Bài toán đổi tiền là một biến thể của bài toán ba lô không giới hạn. Bài toán này chuyển từ việc tìm giá trị “lớn nhất” sang tìm số lượng đồng xu “nhỏ nhất”, vì vậy cần đổi $\max()$ trong công thức chuyển trạng thái thành $\min()$. Bài toán cũng chuyển từ việc tìm tổng “không vượt quá” sức chứa ba lô sang tìm cách tạo thành “chính xác” số tiền mục tiêu, vì vậy sử dụng $amt + 1$ để biểu thị lời giải không hợp lệ, tức là “không thể tạo thành số tiền mục tiêu”.
- Bài toán đổi tiền II chuyển từ việc tìm “số lượng đồng xu nhỏ nhất” sang tìm “số cách kết hợp các đồng xu”, vì vậy công thức chuyển trạng thái tương ứng được thay đổi từ $\min()$ thành phép toán tổng.

**Bài toán khoảng cách chỉnh sửa**

- Khoảng cách chỉnh sửa (Levenshtein distance) được dùng để đo độ tương đồng giữa hai chuỗi, được định nghĩa là số bước chỉnh sửa nhỏ nhất để biến đổi một chuỗi thành chuỗi kia, với các phép chỉnh sửa gồm chèn, xóa và thay thế.
- Định nghĩa trạng thái của bài toán khoảng cách chỉnh sửa là số bước chỉnh sửa nhỏ nhất cần thiết để biến đổi $i$ ký tự đầu tiên của $s$ thành $j$ ký tự đầu tiên của $t$. Khi $s[i-1] \ne t[j-1]$, có ba lựa chọn: chèn, xóa và thay thế, mỗi lựa chọn tương ứng với một bài toán con còn lại. Từ đó, ta có thể xác định cấu trúc tối ưu và xây dựng công thức chuyển trạng thái. Khi $s[i-1] = t[j-1]$, không cần chỉnh sửa ký tự hiện tại.
- Trong bài toán khoảng cách chỉnh sửa, trạng thái phụ thuộc vào trạng thái ngay phía trên, ngay bên trái và phía trên bên trái, vì vậy sau khi tối ưu không gian, cả duyệt xuôi lẫn duyệt ngược đều không thể thực hiện chuyển trạng thái chính xác. Do đó, ta sử dụng một biến để tạm thời lưu trạng thái phía trên bên trái, từ đó chuyển thành tình huống tương đương với bài toán ba lô không giới hạn và cho phép duyệt xuôi sau khi tối ưu không gian.