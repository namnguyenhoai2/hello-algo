# Cùng nhau đóng góp

Do năng lực có hạn, cuốn sách này khó tránh khỏi một số thiếu sót và lỗi. Chúng tôi rất cảm kích sự thông cảm của bạn và biết ơn sự giúp đỡ của bạn trong việc sửa chữa chúng. Nếu phát hiện lỗi chính tả, liên kết hỏng, nội dung bị thiếu, cách diễn đạt mơ hồ, phần giải thích chưa rõ ràng hoặc vấn đề về cấu trúc, hãy giúp chúng tôi sửa chữa để mang đến cho độc giả những tài nguyên học tập chất lượng hơn.

GitHub ID của tất cả [người đóng góp](https://github.com/krahets/hello-algo/graphs/contributors) sẽ được hiển thị trên trang chủ của repository của cuốn sách, phiên bản web và phiên bản PDF để ghi nhận những đóng góp desinterested của họ cho cộng đồng mã nguồn mở.

!!! success "Sức hấp dẫn của mã nguồn mở"

    Khoảng thời gian giữa hai lần in của một cuốn sách giấy thường khá dài, khiến việc cập nhật nội dung rất bất tiện.

    Với cuốn sách mã nguồn mở này, thời gian cập nhật nội dung đã được rút ngắn xuống chỉ còn vài ngày, thậm chí vài giờ.

### Điều chỉnh nội dung nhỏ

Như minh họa trong hình bên dưới, ở góc trên bên phải của mỗi trang có một "edit icon". Bạn có thể sửa đổi văn bản hoặc code bằng cách thực hiện các bước sau.

1. Nhấp vào "edit icon". Nếu gặp lời nhắc yêu cầu bạn "Fork this repository", hãy chấp thuận thao tác này.
2. Sửa đổi nội dung của tệp Markdown nguồn, kiểm tra tính chính xác của nội dung và cố gắng duy trì định dạng nhất quán.
3. Điền mô tả về các thay đổi ở cuối trang, sau đó nhấp vào nút "Propose file change". Sau khi trang mới tải xong, nhấp vào nút "Create pull request" để gửi pull request của bạn.

![Nút chỉnh sửa trang](contribution.assets/edit_markdown.png)

Không thể sửa đổi hình ảnh trực tiếp. Vui lòng mô tả vấn đề bằng cách tạo một [Issue](https://github.com/krahets/hello-algo/issues) mới hoặc để lại bình luận. Chúng tôi sẽ nhanh chóng vẽ lại và thay thế hình ảnh.

### Tạo nội dung

Nếu bạn quan tâm đến việc đóng góp cho dự án mã nguồn mở này, bao gồm dịch code sang các ngôn ngữ lập trình khác hoặc mở rộng nội dung bài viết, bạn cần thực hiện theo quy trình Pull Request dưới đây.

1. Đăng nhập vào GitHub và Fork [code repository](https://github.com/krahets/hello-algo) của cuốn sách vào tài khoản cá nhân của bạn.
2. Truy cập trang repository đã fork của bạn và sử dụng lệnh `git clone` để clone repository về máy cục bộ.
3. Tạo nội dung cục bộ và tiến hành kiểm thử toàn diện để xác minh tính chính xác của code.
4. Commit các thay đổi cục bộ và push chúng lên remote repository.
5. Làm mới trang web của repository và nhấp vào nút "Create pull request" để gửi pull request của bạn.

### Triển khai Docker

Từ thư mục gốc của `hello-algo`, chạy lệnh Docker sau để truy cập dự án tại `http://localhost:8000`:

```shell
docker-compose up -d
```

Sử dụng lệnh sau để xóa deployment:

```shell
docker-compose down
```