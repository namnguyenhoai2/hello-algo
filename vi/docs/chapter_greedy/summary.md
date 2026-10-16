# Tóm tắt

### Nội dung chính

- Các thuật toán tham lam thường được sử dụng để giải các bài toán tối ưu hóa. Nguyên tắc của chúng là đưa ra các quyết định tối ưu cục bộ ở mỗi giai đoạn, với hy vọng đạt được lời giải tối ưu toàn cục.
- Các thuật toán tham lam lần lượt đưa ra hết lựa chọn tham lam này đến lựa chọn tham lam khác, biến bài toán thành một bài toán con nhỏ hơn ở mỗi vòng lặp, cho đến khi bài toán được giải quyết.
- Các thuật toán tham lam không chỉ dễ triển khai mà còn có hiệu quả giải quyết bài toán cao. So với quy hoạch động, các thuật toán tham lam thường có độ phức tạp thời gian thấp hơn.
- Trong bài toán đổi tiền, với một số tổ hợp mệnh giá tiền nhất định, thuật toán tham lam có thể đảm bảo tìm được lời giải tối ưu; tuy nhiên, với các tổ hợp mệnh giá tiền khác, thuật toán tham lam có thể tìm ra những lời giải rất kém.
- Các bài toán phù hợp để giải bằng thuật toán tham lam có hai tính chất chính: tính chất lựa chọn tham lam và cấu trúc con tối ưu. Tính chất lựa chọn tham lam thể hiện tính hiệu quả của chiến lược tham lam.
- Với một số bài toán phức tạp, việc chứng minh tính chất lựa chọn tham lam không đơn giản. Ngược lại, việc bác bỏ tính chất này tương đối dễ hơn, chẳng hạn như trong bài toán đổi tiền.
- Việc giải các bài toán tham lam chủ yếu gồm ba bước: phân tích bài toán, xác định chiến lược tham lam và chứng minh tính đúng đắn. Trong đó, xác định chiến lược tham lam là bước cốt lõi, còn chứng minh tính đúng đắn thường là khó khăn chính.
- Bài toán ba lô phân số, dựa trên bài toán ba lô 0-1, cho phép chọn một phần của các vật phẩm, vì vậy có thể được giải bằng thuật toán tham lam. Tính đúng đắn của chiến lược tham lam có thể được chứng minh bằng phương pháp phản chứng.
- Bài toán dung tích lớn nhất có thể được giải bằng cách liệt kê exhaustive với độ phức tạp thời gian $O(n^2)$. Bằng cách thiết kế một chiến lược tham lam để di chuyển phía ngắn hơn vào trong ở mỗi vòng lặp, độ phức tạp thời gian có thể được tối ưu xuống còn $O(n)$.
- Trong bài toán cắt để đạt tích lớn nhất, ta lần lượt suy ra hai chiến lược tham lam: các số nguyên $\geq 4$ đều nên tiếp tục được chia tách, và thừa số chia tối ưu là $3$. Mã nguồn bao gồm các phép lũy thừa, còn độ phức tạp thời gian phụ thuộc vào phương thức triển khai phép lũy thừa, thường là $O(1)$ hoặc $O(\log n)$.