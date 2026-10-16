---
comments: true

icon: material/rocket-launch-outline
---

# Lời nói đầu

Vài năm trước, tôi đã chia sẻ lời giải cho bài toán "Sword for Offer" trên LeetCode và nhận được sự động viên, ủng hộ từ nhiều độc giả. Trong quá trình trao đổi với độc giả, câu hỏi tôi thường gặp nhất là "làm thế nào để bắt đầu học thuật toán". Dần dần, tôi trở nên đặc biệt hứng thú với câu hỏi này.

Bắt tay ngay vào việc giải bài có vẻ là cách tiếp cận phổ biến nhất—đơn giản, trực tiếp và hiệu quả. Tuy nhiên, giải bài giống như chơi Dò mìn: những người có khả năng tự học tốt có thể lần lượt gỡ mìn thành công, trong khi những người có nền tảng chưa vững có thể bị xây xát và chật vật, từng bước nản lòng rút lui. Đọc sách giáo khoa cũng là một cách làm phổ biến, nhưng đối với người tìm việc, luận văn tốt nghiệp, việc nộp hồ sơ và quá trình chuẩn bị cho các bài kiểm tra viết cũng như phỏng vấn đã tiêu tốn phần lớn năng lượng, khiến việc nghiền ngẫm những cuốn sách dày trở thành một thử thách gian nan.

Nếu bạn đang gặp phải những khó khăn tương tự, thật may mắn là cuốn sách này đã "tìm thấy" bạn. Cuốn sách này là câu trả lời của tôi cho câu hỏi đó—dù có thể chưa phải là giải pháp tối ưu, ít nhất đây cũng là một nỗ lực tích cực. Mặc dù chỉ riêng cuốn sách này sẽ không trực tiếp mang lại cho bạn một lời mời làm việc, nó sẽ dẫn bạn khám phá "cảnh quan" của cấu trúc dữ liệu và thuật toán, giúp bạn hiểu hình dạng, kích thước và sự phân bố của các loại "bãi mìn" khác nhau, đồng thời giúp bạn nắm vững nhiều "phương pháp gỡ mìn". Với những kỹ năng này, tôi tin rằng bạn có thể tự tin hơn khi giải quyết bài toán và đọc tài liệu kỹ thuật, từng bước xây dựng một hệ thống kiến thức hoàn chỉnh.

Tôi hoàn toàn đồng tình với lời của Giáo sư Feynman: "Kiến thức không miễn phí. Bạn phải dành sự chú ý." Theo nghĩa này, cuốn sách này không hoàn toàn "miễn phí". Để không phụ lòng sự "chú ý" quý giá mà bạn dành cho cuốn sách, tôi sẽ nỗ lực hết sức và dành sự "chú ý" lớn nhất của mình để hoàn thành tác phẩm này.

Tôi nhận thức sâu sắc về những giới hạn trong kiến thức và kinh nghiệm của mình. Mặc dù nội dung cuốn sách đã được trau chuốt trong một khoảng thời gian, chắc chắn vẫn còn nhiều sai sót, và tôi chân thành hoan nghênh những lời phê bình, góp ý sửa chữa từ các thầy cô và bạn đọc.

![Xin chào, Thuật toán!](../assets/covers/chapter_hello_algo.jpg){ class="cover-image" }

<div style="text-align: center;">
    <h2 style="margin-top: 0.8em; margin-bottom: 0.8em;">Xin chào, Thuật toán!</h2>
</div>

Sự ra đời của máy tính đã mang đến những thay đổi to lớn cho thế giới. Với khả năng tính toán tốc độ cao và khả năng lập trình tuyệt vời, máy tính đã trở thành phương tiện lý tưởng để thực thi thuật toán và xử lý dữ liệu. Dù là đồ họa chân thực trong trò chơi điện tử, khả năng ra quyết định thông minh trong lái xe tự động, những ván cờ vây xuất sắc của AlphaGo hay các cuộc tương tác tự nhiên với ChatGPT, tất cả những ứng dụng này đều là những minh chứng nổi bật cho cách thuật toán hoạt động trên máy tính.

Trên thực tế, trước khi máy tính ra đời, thuật toán và cấu trúc dữ liệu đã tồn tại ở mọi nơi trên thế giới. Những thuật toán ban đầu tương đối đơn giản, chẳng hạn như các phương pháp đếm cổ xưa và quy trình chế tạo công cụ. Cùng với sự tiến bộ của nền văn minh, thuật toán dần trở nên tinh vi và phức tạp hơn. Từ kỹ nghệ khéo léo của những nghệ nhân bậc thầy, đến các sản phẩm công nghiệp giải phóng sức sản xuất, rồi những quy luật khoa học chi phối sự vận hành của vũ trụ, đằng sau hầu hết mọi sự vật bình thường hay đáng kinh ngạc đều ẩn chứa tư duy thuật toán đầy tài tình.

Tương tự, cấu trúc dữ liệu cũng hiện diện ở khắp nơi: từ các mạng xã hội quy mô lớn đến những hệ thống tàu điện ngầm nhỏ bé, nhiều hệ thống có thể được mô hình hóa thành "đồ thị"; từ một quốc gia đến một gia đình, những hình thức tổ chức cơ bản của xã hội đều thể hiện đặc điểm của "cây"; quần áo mùa đông giống như một "ngăn xếp", trong đó món đồ được mặc vào đầu tiên sẽ được cởi ra cuối cùng; một ống cầu lông giống như một "hàng đợi", với các vật được đưa vào từ một đầu và lấy ra từ đầu kia; từ điển giống như một "bảng băm", cho phép nhanh chóng tra cứu các mục tiêu cần tìm.

Cuốn sách này nhằm giúp độc giả hiểu các khái niệm cốt lõi của thuật toán và cấu trúc dữ liệu thông qua những hình minh họa động rõ ràng, dễ tiếp cận cùng các ví dụ mã có thể chạy được, đồng thời triển khai chúng bằng code. Trên nền tảng đó, cuốn sách nỗ lực cho thấy những biểu hiện sinh động của thuật toán trong thế giới phức tạp và làm nổi bật vẻ đẹp của thuật toán. Hy vọng cuốn sách này có thể giúp ích cho bạn!