# Tóm tắt

### Nội dung chính

- Cây nhị phân là một cấu trúc dữ liệu phi tuyến thể hiện tư duy chia để trị bằng cách phân tách thành hai phần. Mỗi node của cây nhị phân chứa một giá trị và hai con trỏ, trỏ đến node con bên trái và bên phải.
- Đối với một node nhất định trong cây nhị phân, cây được tạo bởi node con bên trái (bên phải) của node đó và tất cả các node bên dưới được gọi là cây con bên trái (cây con bên phải) của node đó.
- Các thuật ngữ liên quan đến cây nhị phân bao gồm node gốc, node lá, level, degree, edge, height và depth.
- Các thao tác khởi tạo, chèn node và xóa node trong cây nhị phân tương tự như trong linked list.
- Các loại cây nhị phân phổ biến bao gồm cây nhị phân hoàn hảo, cây nhị phân đầy đủ, cây nhị phân strict và cây nhị phân cân bằng. Cây nhị phân hoàn hảo là dạng lý tưởng, trong khi linked list đại diện cho trường hợp suy biến tệ nhất.
- Có thể biểu diễn cây nhị phân bằng array bằng cách sắp xếp các giá trị node và các vị trí trống theo thứ tự duyệt level-order, đồng thời triển khai các con trỏ dựa trên mối quan hệ ánh xạ chỉ mục giữa node cha và node con.
- Duyệt level-order của cây nhị phân là một phương pháp breadth-first search, tiến hành lần lượt theo từng level và thường được triển khai bằng queue.
- Duyệt preorder, inorder và postorder đều thuộc depth-first search, tiến hành đi sâu nhất có thể trước khi quay lui và thường sử dụng đệ quy.
- Binary search tree là một cấu trúc dữ liệu hiệu quả để tìm kiếm phần tử, với các thao tác tìm kiếm, chèn và xóa đều có time complexity là $O(\log n)$. Khi binary search tree suy biến thành linked list, mọi time complexity đều giảm xuống còn $O(n)$.
- Cây AVL, còn được gọi là balanced binary search tree, đảm bảo cây luôn cân bằng sau các thao tác chèn và xóa node liên tiếp thông qua các thao tác rotation.
- Các thao tác rotation trong cây AVL bao gồm right rotation, left rotation, right rotation tiếp đó là left rotation, và left rotation tiếp đó là right rotation. Sau khi chèn hoặc xóa node, cây AVL thực hiện rotation từ dưới lên trên để khôi phục trạng thái cân bằng.

### Hỏi & Đáp

**Q**: Với một cây nhị phân chỉ có một node, height của cây và depth của node gốc có phải đều là $0$ không?

Đúng, vì height và depth thường được định nghĩa là số lượng edge trên đường đi.

**Q**: Việc chèn và xóa trong cây nhị phân thường được thực hiện bằng một tập hợp các thao tác. “Một tập hợp các thao tác” ở đây có nghĩa là gì? Điều đó có hàm ý giải phóng tài nguyên của các node con không?

Lấy binary search tree làm ví dụ, thao tác xóa một node cần được xử lý theo ba trường hợp khác nhau, mỗi trường hợp đều yêu cầu thực hiện nhiều bước thao tác trên node.

**Q**: Tại sao việc duyệt DFS của cây nhị phân có ba thứ tự là preorder, inorder và postorder, và chúng được sử dụng để làm gì?

Tương tự như việc duyệt array theo chiều thuận và chiều ngược, preorder, inorder và postorder là ba phương pháp duyệt cây nhị phân, cho phép chúng ta thu được kết quả duyệt theo một thứ tự cụ thể. Ví dụ, trong binary search tree, vì các node thỏa mãn mối quan hệ `left child node value < root node value < right child node value`, chúng ta chỉ cần duyệt cây theo thứ tự ưu tiên “left $\rightarrow$ root $\rightarrow$ right” để thu được một dãy node có thứ tự.

**Q**: Trong thao tác right rotation xử lý mối quan hệ giữa các node mất cân bằng `node`, `child` và `grand_child`, chẳng phải mối liên kết giữa `node` và node cha của nó sẽ bị mất sau right rotation sao?

Chúng ta cần nhìn nhận vấn đề này từ góc độ đệ quy. Thao tác right rotation `right_rotate(root)` nhận vào node gốc của cây con và cuối cùng trả về node gốc của cây con sau khi rotation với `return child`. Mối liên kết giữa node gốc của cây con và node cha của nó được hoàn tất sau khi hàm trả về, nên không thuộc phạm vi duy trì của thao tác right rotation.

**Q**: Trong C++, các hàm được chia thành các phần `private` và `public`. Cần cân nhắc những gì về điều này? Tại sao hàm `height()` và hàm `updateHeight()` lần lượt được đặt trong `public` và `private`?

Điều này chủ yếu phụ thuộc vào phạm vi sử dụng của phương thức. Nếu một phương thức chỉ được sử dụng bên trong class, thì nó được thiết kế dưới dạng `private`. Ví dụ, việc người dùng gọi riêng `updateHeight()` là không có ý nghĩa, vì đây chỉ là một bước trong thao tác chèn hoặc xóa. Tuy nhiên, `height()` được dùng để truy cập height của node, tương tự như `vector.size()`, nên nó được đặt là `public` để thuận tiện sử dụng.

**Q**: Làm thế nào để xây dựng một binary search tree từ một tập dữ liệu đầu vào? Việc lựa chọn node gốc có quan trọng không?

Có, phương pháp xây dựng cây được cung cấp trong phương thức `build_tree()` của code binary search tree. Về việc lựa chọn node gốc, chúng ta thường sắp xếp dữ liệu đầu vào, sau đó chọn phần tử ở giữa làm node gốc và đệ quy xây dựng các cây con bên trái và bên phải. Cách tiếp cận này tối đa hóa độ cân bằng của cây.

**Q**: Trong Java, có phải lúc nào cũng phải sử dụng phương thức `equals()` để so sánh string không?

Trong Java, đối với các kiểu dữ liệu nguyên thủy, `==` được sử dụng để so sánh xem giá trị của hai biến có bằng nhau hay không. Đối với các kiểu tham chiếu, nguyên lý hoạt động của hai ký hiệu này khác nhau.

- `==`: Dùng để so sánh xem hai biến có trỏ đến cùng một object hay không, tức là vị trí của chúng trong memory có giống nhau hay không.
- `equals()`: Dùng để so sánh xem giá trị của hai object có bằng nhau hay không.

Do đó, nếu muốn so sánh giá trị, chúng ta nên sử dụng `equals()`. Tuy nhiên, các string được khởi tạo thông qua `String a = "hi"; String b = "hi";` được lưu trong string constant pool và trỏ đến cùng một object, nên `a == b` cũng có thể được sử dụng để so sánh nội dung của hai string.

**Q**: Trước khi đạt đến level cuối, số node trong queue có phải là $2^h$ trong quá trình breadth-first traversal không?

Đúng, ví dụ, một cây nhị phân đầy đủ có height $h = 2$ có tổng cộng $n = 7$ node, khi đó level cuối có $4 = 2^h = (n + 1) / 2$ node.