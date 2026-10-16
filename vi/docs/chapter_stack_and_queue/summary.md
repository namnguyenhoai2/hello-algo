# Tóm tắt

### Nội dung chính

- Stack là một cấu trúc dữ liệu tuân theo nguyên tắc LIFO và có thể được triển khai bằng mảng hoặc danh sách liên kết.
- Về hiệu quả thời gian, triển khai stack bằng mảng có hiệu quả trung bình cao hơn, nhưng trong quá trình mở rộng, độ phức tạp thời gian của một thao tác push đơn lẻ sẽ giảm xuống còn $O(n)$. Ngược lại, triển khai stack bằng danh sách liên kết mang lại hiệu năng ổn định hơn.
- Về hiệu quả không gian, triển khai stack bằng mảng có thể dẫn đến một mức độ lãng phí không gian nhất định. Tuy nhiên, cần lưu ý rằng không gian bộ nhớ mà các node của danh sách liên kết chiếm dụng lớn hơn không gian của các phần tử mảng.
- Queue là một cấu trúc dữ liệu tuân theo nguyên tắc FIFO và cũng có thể được triển khai bằng mảng hoặc danh sách liên kết. Các kết luận về so sánh hiệu quả thời gian và hiệu quả không gian của queue tương tự như đối với stack đã đề cập ở trên.
- Deque là một queue linh hoạt hơn, cho phép thêm và xóa phần tử ở cả hai đầu.

### Hỏi & Đáp

**Q**: Chức năng tiến và lùi của trình duyệt có được triển khai bằng danh sách liên kết kép không?

Hành vi tiến và lùi của trình duyệt về cơ bản là một ứng dụng của “stack”. Khi người dùng truy cập một trang mới, trang đó được thêm vào đỉnh stack; khi người dùng nhấp vào nút quay lại, trang đó được lấy ra khỏi đỉnh stack. Deque có thể hỗ trợ thuận tiện một số thao tác bổ sung, như đã đề cập trong phần “Deque”.

**Q**: Sau khi lấy một node ra khỏi stack, chúng ta có cần giải phóng bộ nhớ của node đó không?

Nếu node đã lấy ra vẫn sẽ được cần đến sau này thì không cần giải phóng bộ nhớ. Nếu node đó không được sử dụng nữa, các ngôn ngữ như Java và Python có cơ chế thu gom rác tự động, nên không cần tự giải phóng bộ nhớ; trong C và C++, cần tự giải phóng bộ nhớ.

**Q**: Deque có vẻ giống như hai stack được ghép lại với nhau. Mục đích của nó là gì?

Deque giống như sự kết hợp giữa stack và queue, hoặc hai stack được ghép lại với nhau. Nó kết hợp logic của cả hai, nhờ đó có thể hỗ trợ mọi ứng dụng của stack và queue, đồng thời mang lại sự linh hoạt cao hơn.

**Q**: Undo và redo được triển khai cụ thể như thế nào?

Sử dụng hai stack: stack `A` cho undo và stack `B` cho redo.

1. Mỗi khi người dùng thực hiện một thao tác, hãy push thao tác đó vào stack `A` và xóa stack `B`.
2. Khi người dùng thực hiện “undo”, hãy pop thao tác gần nhất khỏi stack `A` rồi push thao tác đó vào stack `B`.
3. Khi người dùng thực hiện “redo”, hãy pop thao tác gần nhất khỏi stack `B` rồi push thao tác đó vào stack `A`.