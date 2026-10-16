# Tóm tắt

### Nội dung chính

- Thuật toán quay lui về bản chất là một phương pháp tìm kiếm toàn diện. Thuật toán tìm các nghiệm thỏa mãn những điều kiện đã chỉ định bằng cách duyệt theo chiều sâu trên không gian nghiệm. Trong quá trình tìm kiếm, khi tìm thấy một nghiệm thỏa mãn các điều kiện, thuật toán sẽ ghi nhận nghiệm đó. Quá trình tìm kiếm kết thúc sau khi tìm được tất cả nghiệm hoặc khi hoàn tất việc duyệt.
- Quá trình tìm kiếm của thuật toán quay lui gồm hai phần: thử và quay lui. Thuật toán thử các lựa chọn khác nhau thông qua tìm kiếm theo chiều sâu. Khi gặp tình huống vi phạm các ràng buộc, thuật toán hoàn tác lựa chọn trước đó, trở về trạng thái trước đó và tiếp tục khám phá các lựa chọn khác. Thử và quay lui là hai thao tác theo các hướng ngược nhau.
- Các bài toán quay lui thường có nhiều ràng buộc, có thể được tận dụng để triển khai thao tác cắt tỉa. Cắt tỉa có thể sớm kết thúc những nhánh tìm kiếm không cần thiết, nhờ đó cải thiện đáng kể hiệu suất tìm kiếm.
- Thuật toán quay lui chủ yếu được sử dụng để giải các bài toán tìm kiếm và bài toán thỏa mãn ràng buộc. Mặc dù có thể giải các bài toán tối ưu tổ hợp bằng quay lui, thường vẫn có những lời giải hiệu quả hơn hoặc có hiệu năng tốt hơn.
- Bài toán hoán vị nhằm tìm tất cả các hoán vị có thể có của các phần tử trong một tập hợp cho trước. Ta sử dụng một mảng để ghi nhận liệu mỗi phần tử đã được chọn hay chưa, từ đó cắt tỉa các nhánh tìm kiếm cố chọn lặp lại cùng một phần tử, bảo đảm mỗi phần tử được chọn đúng một lần.
- Trong bài toán hoán vị, nếu tập hợp chứa các phần tử trùng nhau, kết quả cuối cùng sẽ chứa các hoán vị trùng lặp. Ta cần áp đặt một ràng buộc để các phần tử bằng nhau chỉ được chọn một lần trong mỗi lượt, thường được thực hiện bằng một hash set.
- Bài toán tổng tập con nhằm tìm tất cả các tập con của một tập hợp cho trước có tổng bằng một giá trị đích. Vì tập hợp không có thứ tự nhưng quá trình tìm kiếm tạo ra kết quả theo mọi thứ tự, các tập con trùng lặp sẽ được sinh ra. Ta sắp xếp dữ liệu trước khi quay lui và sử dụng một biến để chỉ ra điểm bắt đầu của quá trình duyệt trong mỗi lượt, qua đó cắt tỉa các nhánh tìm kiếm tạo ra các tập con trùng lặp.
- Trong bài toán tổng tập con, các phần tử bằng nhau trong mảng sẽ tạo ra các tập con trùng lặp. Ta tận dụng điều kiện tiên quyết rằng mảng đã được sắp xếp bằng cách kiểm tra xem các phần tử kề nhau có bằng nhau hay không để thực hiện cắt tỉa, bảo đảm các phần tử bằng nhau chỉ được chọn một lần trong mỗi lượt.
- Bài toán $n$ quân hậu nhằm tìm cách đặt $n$ quân hậu trên bàn cờ $n \times n$ sao cho không có hai quân hậu nào có thể ăn nhau. Các ràng buộc của bài toán này bao gồm ràng buộc hàng, ràng buộc cột và ràng buộc đường chéo chính, đường chéo phụ. Để thỏa mãn ràng buộc hàng, ta áp dụng chiến lược đặt quân theo từng hàng, bảo đảm mỗi hàng có đúng một quân hậu.
- Cách xử lý ràng buộc cột và ràng buộc đường chéo là tương tự nhau. Đối với ràng buộc cột, ta sử dụng một mảng để ghi nhận mỗi cột đã có quân hậu hay chưa, qua đó xác định một ô được chọn có hợp lệ hay không. Đối với ràng buộc đường chéo, ta sử dụng hai mảng để lần lượt ghi nhận mỗi đường chéo chính hoặc đường chéo phụ đã có quân hậu hay chưa. Thách thức nằm ở việc tìm ra quy luật chỉ số hàng-cột đặc trưng cho các ô nằm trên cùng một đường chéo chính hoặc đường chéo phụ.

### Hỏi & Đáp

**Q**: Làm thế nào để hiểu mối quan hệ giữa quay lui và đệ quy?

Nhìn chung, quay lui là một chiến lược thuật toán, còn đệ quy phù hợp hơn khi được xem như một công cụ.

- Quay lui thường được triển khai bằng đệ quy. Tuy nhiên, quay lui chỉ là một ứng dụng của đệ quy, cụ thể là việc sử dụng đệ quy trong các bài toán tìm kiếm.
- Cấu trúc của đệ quy phản ánh một mô hình giải quyết vấn đề dựa trên việc phân rã một bài toán thành các bài toán con. Đệ quy thường được sử dụng trong chia để trị, quay lui và quy hoạch động (đệ quy có ghi nhớ).