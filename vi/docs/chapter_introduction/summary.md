# Tóm tắt

### Những điểm chính cần ôn lại

- Algorithms hiện diện khắp nơi trong đời sống hằng ngày và không phải là một lĩnh vực kiến thức xa vời, khó hiểu. Trên thực tế, chúng ta đã vô thức học được nhiều algorithms và sử dụng chúng để giải quyết những vấn đề lớn nhỏ trong cuộc sống.
- Nguyên tắc tra từ điển nhất quán với thuật toán tìm kiếm nhị phân (binary search). Binary search thể hiện một tư tưởng thuật toán quan trọng là chia để trị (divide and conquer).
- Quy trình sắp xếp các lá bài rất giống với thuật toán sắp xếp chèn (insertion sort). Insertion sort phù hợp để sắp xếp các tập dữ liệu nhỏ.
- Các bước thối tiền về bản chất là một greedy algorithm, trong đó lựa chọn tốt nhất được đưa ra ở mỗi bước dựa trên tình huống hiện tại.
- Algorithm là một tập hợp các chỉ dẫn hoặc bước thao tác giúp giải quyết một vấn đề cụ thể trong một khoảng thời gian hữu hạn, còn data structure là cách tổ chức và lưu trữ dữ liệu trong máy tính.
- Data structures và algorithms có mối liên hệ chặt chẽ. Data structures là nền tảng của algorithms, còn algorithms làm cho data structures phát huy tác dụng.
- Chúng ta có thể ví data structures và algorithms với việc lắp ráp các khối xây dựng. Các khối đại diện cho dữ liệu, cách chúng được định hình và kết nối đại diện cho data structure, còn các bước dùng để lắp ráp chúng tương ứng với algorithm.

### Hỏi & Đáp

**Hỏi**: Là một programmer, tôi chưa bao giờ sử dụng algorithms để giải quyết vấn đề trong công việc hằng ngày. Các algorithms phổ biến đã được các ngôn ngữ lập trình đóng gói sẵn và có thể sử dụng trực tiếp. Điều này có nghĩa là những vấn đề trong công việc của chúng ta vẫn chưa đạt đến mức cần đến algorithms sao?

Nếu so sánh các kỹ năng cụ thể trong công việc với “chiêu thức” trong võ thuật, thì các môn học nền tảng có lẽ giống “nội công” hơn.

Tôi cho rằng ý nghĩa của việc học algorithms (và các môn học nền tảng khác) không nằm ở việc bạn sẽ phải tự triển khai chúng từ đầu trong công việc, mà ở chỗ những kiến thức bạn thu được giúp bạn đưa ra các phán đoán chuyên môn đúng đắn khi giải quyết vấn đề, qua đó nâng cao chất lượng tổng thể của công việc. Dưới đây là một ví dụ đơn giản. Mọi ngôn ngữ lập trình đều có một hàm sắp xếp tích hợp sẵn:

- Nếu chưa học data structures và algorithms, chúng ta có thể chỉ đơn giản đưa mọi dữ liệu nhận được vào hàm sắp xếp này. Hàm chạy trơn tru với hiệu năng tốt, và dường như không có vấn đề gì.
- Nhưng nếu đã học algorithms, chúng ta sẽ biết rằng độ phức tạp thời gian của hàm sắp xếp tích hợp sẵn là $O(n \log n)$. Tuy nhiên, nếu dữ liệu nhận được gồm các số nguyên có số chữ số cố định (chẳng hạn như mã số sinh viên), chúng ta có thể sử dụng “radix sort” hiệu quả hơn, giảm độ phức tạp thời gian xuống còn $O(nk)$, trong đó $k$ là số chữ số. Khi khối lượng dữ liệu rất lớn, thời gian chạy tiết kiệm được có thể tạo ra giá trị đáng kể (giảm chi phí, cải thiện trải nghiệm, v.v.).

Trong engineering, nhiều vấn đề rất khó được giải quyết một cách tối ưu, còn nhiều vấn đề khác chỉ được giải quyết ở mức “đủ tốt”. Độ khó của một vấn đề phụ thuộc một mặt vào bản chất của chính vấn đề đó, mặt khác vào kiến thức của người xem xét nó. Kiến thức của một người càng đầy đủ và kinh nghiệm càng phong phú, thì phân tích của họ càng sâu sắc, đồng thời vấn đề càng có thể được giải quyết một cách hiệu quả và tinh tế.

**Hỏi**: Giờ đây, khi chúng ta để các AI agent viết gần như toàn bộ code, liệu chúng ta vẫn cần học algorithms không?

Xin trích lời Mu Li: “An agent is an amplifier of ability—it multiplies your ability by 10, rather than adding 10 to it.”

Vì AI khuếch đại năng lực của chúng ta, nên những năng lực được nhân lên cũng rất quan trọng. Tôi cho rằng có hai năng lực đặc biệt đáng phát triển. Thứ nhất là giao tiếp, đặc biệt là khả năng làm việc với AI: làm rõ mục tiêu, cung cấp ngữ cảnh cần thiết và kịp thời điều chỉnh hướng đi. Việc giải thích một vấn đề cho AI cũng giúp chúng ta tự suy nghĩ thấu đáo hơn. Thứ hai là kiến thức nền tảng. AI có thể bổ sung các chi tiết, nhưng chúng ta cần tự mình hiểu các khái niệm cơ bản để đặt đúng câu hỏi, đánh giá câu trả lời có chính xác hay không và biến kết quả đầu ra của AI thành những kết quả hữu ích.

Một điểm đặc biệt của AI là, không giống các công cụ trước đây, nó không có những ranh giới chức năng được xác định rõ ràng. AI hơi giống nước, mang những hình dạng khác nhau trong tay những người khác nhau. Năng lực của một người càng lớn và gu thẩm mỹ càng tốt, hiệu ứng khuếch đại của AI càng rõ rệt.