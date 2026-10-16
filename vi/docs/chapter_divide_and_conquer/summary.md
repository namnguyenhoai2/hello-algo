# Tóm tắt

### Nội dung chính

- Chia để trị là một chiến lược thiết kế thuật toán phổ biến, gồm hai giai đoạn: chia (partition) và trị (merge), thường được triển khai bằng đệ quy.
- Các tiêu chí để xác định một bài toán có phải là bài toán chia để trị hay không bao gồm: bài toán có thể được phân rã hay không, các bài toán con có độc lập hay không và các bài toán con có thể được hợp nhất hay không.
- Merge sort là một ứng dụng điển hình của chiến lược chia để trị. Thuật toán này đệ quy chia một mảng thành hai mảng con có cùng độ dài cho đến khi mỗi mảng chỉ còn một phần tử, sau đó hợp nhất chúng theo từng tầng để hoàn tất việc sắp xếp.
- Việc áp dụng chiến lược chia để trị thường có thể cải thiện hiệu quả của thuật toán. Một mặt, nó làm giảm số lượng phép toán; mặt khác, nó giúp hệ thống dễ dàng thực hiện tối ưu hóa song song hơn.
- Chia để trị có thể giải quyết nhiều bài toán thuật toán và cũng được sử dụng rộng rãi trong cấu trúc dữ liệu và thiết kế thuật toán, nên nó xuất hiện ở khắp nơi.
- So với tìm kiếm vét cạn, tìm kiếm thích ứng hiệu quả hơn. Các thuật toán tìm kiếm có độ phức tạp thời gian $O(\log n)$ thường được triển khai dựa trên chiến lược chia để trị.
- Tìm kiếm nhị phân là một ứng dụng điển hình khác của chia để trị. Thuật toán này không bao gồm bước hợp nhất các lời giải của các bài toán con. Chúng ta có thể triển khai tìm kiếm nhị phân bằng phương pháp chia để trị đệ quy.
- Trong bài toán xây dựng cây nhị phân, việc xây dựng cây (bài toán ban đầu) có thể được chia thành việc xây dựng cây con trái và cây con phải (các bài toán con), bằng cách chia các khoảng chỉ mục của phép duyệt theo thứ tự trước và phép duyệt trung thứ tự.
- Trong bài toán Tháp Hà Nội, một bài toán có kích thước $n$ có thể được chia thành hai bài toán con có kích thước $n-1$ và một bài toán con có kích thước $1$. Sau khi lần lượt giải quyết ba bài toán con này, bài toán ban đầu sẽ được giải quyết.