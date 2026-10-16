# Đánh giá hiệu quả của thuật toán

Trong thiết kế thuật toán, chúng ta lần lượt theo đuổi hai cấp độ mục tiêu sau:

1. **Tìm lời giải cho bài toán**: Thuật toán phải luôn tìm được lời giải chính xác trong phạm vi đầu vào được chỉ định.
2. **Tìm kiếm lời giải tối ưu**: Một bài toán có thể có nhiều lời giải, và chúng ta mong muốn tìm được thuật toán hiệu quả nhất có thể.

Nói cách khác, với tiền đề là có thể giải quyết bài toán, hiệu quả của thuật toán đã trở thành tiêu chí đánh giá hàng đầu để đo lường chất lượng của thuật toán. Hiệu quả bao gồm hai phương diện sau:

- **Hiệu quả về thời gian**: Khoảng thời gian thuật toán chạy.
- **Hiệu quả về không gian**: Dung lượng bộ nhớ mà thuật toán sử dụng.

Tóm lại, **mục tiêu của chúng ta là thiết kế các cấu trúc dữ liệu và thuật toán "vừa nhanh vừa tiết kiệm bộ nhớ"**. Việc đánh giá hiệu quả thuật toán một cách chính xác là rất quan trọng, vì chỉ có như vậy chúng ta mới có thể so sánh các thuật toán khác nhau và định hướng cho quá trình thiết kế, tối ưu hóa thuật toán.

Các phương pháp đánh giá hiệu quả chủ yếu được chia thành hai loại: kiểm thử thực tế và ước tính lý thuyết.

## Kiểm thử thực tế

Giả sử hiện tại chúng ta có thuật toán `A` và thuật toán `B`, cả hai đều có thể giải quyết cùng một bài toán, và chúng ta cần so sánh hiệu quả của chúng. Phương pháp trực tiếp nhất là chạy chúng trên máy tính rồi đo thời gian chạy và mức sử dụng bộ nhớ. Cách đánh giá này có thể phản ánh hành vi trong thực tế, nhưng cũng có những hạn chế đáng kể.

Một mặt, **rất khó loại bỏ các yếu tố gây nhiễu khỏi môi trường kiểm thử**. Cấu hình phần cứng ảnh hưởng đến hiệu năng của thuật toán. Ví dụ, nếu một thuật toán có mức độ song song hóa cao, nó sẽ phù hợp hơn khi chạy trên CPU đa lõi; nếu một thuật toán thực hiện các thao tác sử dụng nhiều bộ nhớ, nó sẽ hưởng lợi nhiều hơn từ bộ nhớ hiệu năng cao. Nói cách khác, kết quả kiểm thử của một thuật toán trên các máy khác nhau có thể không nhất quán. Điều này có nghĩa là chúng ta cần kiểm thử trên nhiều máy khác nhau và tính hiệu quả trung bình, nhưng cách làm này không thực tế.

Mặt khác, **thực hiện kiểm thử đầy đủ tiêu tốn rất nhiều tài nguyên**. Khi khối lượng dữ liệu đầu vào thay đổi, thuật toán sẽ thể hiện hiệu quả khác nhau. Ví dụ, khi khối lượng dữ liệu đầu vào nhỏ, thời gian chạy của thuật toán `A` ngắn hơn thuật toán `B`; nhưng khi khối lượng dữ liệu đầu vào lớn, kết quả kiểm thử có thể hoàn toàn ngược lại. Vì vậy, để có được kết luận thuyết phục, chúng ta cần kiểm thử dữ liệu đầu vào ở nhiều quy mô khác nhau, điều này đòi hỏi một lượng lớn tài nguyên tính toán.

## Ước tính lý thuyết

Vì kiểm thử thực tế có những hạn chế đáng kể, chúng ta có thể cân nhắc đánh giá hiệu quả thuật toán thông qua tính toán lý thuyết. Phương pháp ước tính này được gọi là <u>phân tích độ phức tạp tiệm cận</u>, hoặc gọi tắt là <u>phân tích độ phức tạp</u>.

Phân tích độ phức tạp có thể phản ánh mối quan hệ giữa tài nguyên thời gian, không gian cần thiết để thuật toán thực thi và quy mô dữ liệu đầu vào. **Nó mô tả xu hướng tăng của thời gian và không gian cần thiết cho việc thực thi thuật toán khi quy mô dữ liệu đầu vào tăng lên**. Định nghĩa này hơi khó hiểu, vì vậy chúng ta có thể chia nhỏ thành ba điểm chính để tìm hiểu:

- “Tài nguyên thời gian và không gian” lần lượt tương ứng với <u>độ phức tạp thời gian</u> và <u>độ phức tạp không gian</u>.
- “Khi quy mô dữ liệu đầu vào tăng lên” có nghĩa là độ phức tạp phản ánh mối quan hệ giữa hiệu quả chạy của thuật toán và quy mô dữ liệu đầu vào.
- “Xu hướng tăng của thời gian và không gian” cho thấy phân tích độ phức tạp không tập trung vào các giá trị cụ thể của thời gian chạy hoặc dung lượng không gian đã sử dụng, mà tập trung vào việc thời gian hoặc không gian tăng “nhanh” đến mức nào.

**Phân tích độ phức tạp khắc phục những hạn chế của phương pháp kiểm thử thực tế**, thể hiện ở các khía cạnh sau:

- Không cần thực sự chạy mã, nhờ đó thân thiện hơn với môi trường và tiết kiệm năng lượng hơn.
- Không phụ thuộc vào môi trường kiểm thử, và kết quả phân tích có thể áp dụng cho mọi nền tảng chạy.
- Có thể phản ánh hiệu quả của thuật toán ở các quy mô dữ liệu khác nhau, đặc biệt là hiệu năng của thuật toán khi khối lượng dữ liệu lớn.

!!! tip

    Nếu bạn vẫn còn bối rối về khái niệm độ phức tạp, đừng lo—we sẽ giới thiệu chi tiết về khái niệm này trong các chương tiếp theo.

Phân tích độ phức tạp cung cấp cho chúng ta một “thước đo” để đánh giá hiệu quả thuật toán, cho phép chúng ta đo lường tài nguyên thời gian và không gian cần thiết để thực thi một thuật toán nhất định, đồng thời so sánh hiệu quả giữa các thuật toán khác nhau.

Độ phức tạp là một khái niệm toán học có thể khiến người mới học cảm thấy trừu tượng và khó hiểu. Từ góc độ này, phân tích độ phức tạp có thể không phải là chủ đề phù hợp nhất để giới thiệu trước tiên. Tuy nhiên, khi thảo luận về đặc điểm của một cấu trúc dữ liệu hoặc thuật toán nhất định, rất khó tránh khỏi việc phân tích tốc độ chạy và mức sử dụng không gian của nó.

Tóm lại, trước khi tìm hiểu sâu về cấu trúc dữ liệu và thuật toán, bạn nên **trước hết xây dựng hiểu biết ban đầu về phân tích độ phức tạp để có thể phân tích độ phức tạp của các thuật toán đơn giản**.