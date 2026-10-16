# Bộ nhớ truy cập ngẫu nhiên và Cache *

Trong hai phần đầu của chương này, chúng ta đã tìm hiểu về mảng và danh sách liên kết, hai cấu trúc dữ liệu cơ bản và quan trọng, lần lượt biểu diễn hai cách bố trí vật lý: “lưu trữ liền kề” và “lưu trữ phân tán”.

Trên thực tế, **cấu trúc vật lý phần lớn quyết định mức độ hiệu quả mà chương trình sử dụng bộ nhớ và cache**, từ đó ảnh hưởng đến hiệu năng tổng thể của các chương trình thuật toán.

## Thiết bị lưu trữ của máy tính

Máy tính bao gồm ba loại thiết bị lưu trữ: <u>ổ cứng</u>, <u>bộ nhớ truy cập ngẫu nhiên (RAM)</u>, và <u>bộ nhớ cache</u>. Bảng sau đây cho thấy vai trò và đặc điểm hiệu năng khác nhau của chúng trong một hệ thống máy tính.

<p align="center"> Bảng <id> &nbsp; Thiết bị lưu trữ của máy tính </p>

|                | Ổ cứng                                                       | RAM                                              | Cache                                                          |
| -------------- | ------------------------------------------------------------- | ------------------------------------------------ | -------------------------------------------------------------- |
| Mục đích       | Lưu trữ dữ liệu dài hạn, bao gồm hệ điều hành, chương trình và tệp | Lưu trữ tạm thời các chương trình đang chạy và dữ liệu đang được xử lý | Lưu trữ dữ liệu và chỉ thị được truy cập thường xuyên để giảm số lần CPU truy cập bộ nhớ |
| Tính biến động | Dữ liệu không bị mất sau khi tắt nguồn                         | Dữ liệu bị mất sau khi tắt nguồn                  | Dữ liệu bị mất sau khi tắt nguồn                                |
| Dung lượng     | Lớn, ở mức terabyte (TB)                                      | Nhỏ, ở mức gigabyte (GB)                         | Rất nhỏ, ở mức megabyte (MB)                                  |
| Tốc độ         | Chậm, hàng trăm đến hàng nghìn MB/s                           | Nhanh, hàng chục GB/s                            | Rất nhanh, hàng chục đến hàng trăm GB/s                        |
| Chi phí (CNY/GB) | Rẻ, từ vài phần mười nhân dân tệ đến vài nhân dân tệ mỗi GB | Đắt, từ hàng chục đến hàng trăm nhân dân tệ mỗi GB | Rất đắt, trên thực tế được tích hợp trong package CPU         |

Chúng ta có thể hình dung hệ thống lưu trữ của máy tính như một kim tự tháp, như minh họa bên dưới. Các thiết bị lưu trữ càng gần đỉnh thì càng nhanh, có dung lượng càng nhỏ và càng đắt. Thiết kế nhiều tầng này là có chủ đích, là kết quả của sự cân nhắc kỹ lưỡng từ các nhà khoa học máy tính và kỹ sư.

- **Ổ cứng không thể dễ dàng được thay thế bằng RAM**. Thứ nhất, dữ liệu trong bộ nhớ bị mất sau khi tắt nguồn, nên không phù hợp để lưu trữ dữ liệu dài hạn. Thứ hai, bộ nhớ đắt hơn ổ cứng hàng chục lần, khiến việc phổ biến nó trên thị trường tiêu dùng trở nên khó khăn.
- **Cache không thể đồng thời đạt được dung lượng lớn và tốc độ cao**. Khi dung lượng của cache L1, L2 và L3 tăng lên, kích thước vật lý của chúng cũng lớn hơn, đồng thời khoảng cách vật lý giữa chúng và lõi CPU tăng lên, dẫn đến thời gian truyền dữ liệu lâu hơn và độ trễ truy cập phần tử cao hơn. Với công nghệ hiện nay, cấu trúc cache nhiều tầng thể hiện điểm cân bằng tốt nhất giữa dung lượng, tốc độ và chi phí.

![Hệ thống lưu trữ của máy tính](ram_and_cache.assets/storage_pyramid.png)

!!! tip

    Hệ thống phân cấp lưu trữ của máy tính thể hiện sự cân bằng tinh tế giữa tốc độ, dung lượng và chi phí. Trên thực tế, những đánh đổi như vậy phổ biến trong mọi lĩnh vực công nghiệp, đòi hỏi chúng ta phải tìm ra điểm cân bằng tối ưu giữa các ưu thế và ràng buộc khác nhau.

Tóm lại, **ổ cứng được dùng để lưu trữ dài hạn lượng lớn dữ liệu, RAM được dùng để tạm thời lưu trữ dữ liệu đang được xử lý trong quá trình thực thi chương trình, còn cache được dùng để lưu trữ dữ liệu và chỉ thị được truy cập thường xuyên**, từ đó nâng cao hiệu quả thực thi chương trình. Ba thành phần này phối hợp với nhau để duy trì hoạt động hiệu quả của hệ thống máy tính.

Như minh họa trong sơ đồ bên dưới, trong quá trình thực thi chương trình, dữ liệu được đọc từ ổ cứng vào RAM để CPU tính toán. Cache có thể được xem là một phần của CPU. **Bằng cách tải dữ liệu một cách thông minh từ RAM**, cache cung cấp cho CPU khả năng truy cập dữ liệu tốc độ cao, cải thiện đáng kể hiệu quả thực thi chương trình và giảm sự phụ thuộc vào RAM chậm hơn.

![Luồng dữ liệu giữa ổ cứng, RAM và Cache](ram_and_cache.assets/computer_storage_devices.png)

## Hiệu quả sử dụng bộ nhớ của các cấu trúc dữ liệu

Xét về mức độ sử dụng không gian bộ nhớ, mảng và danh sách liên kết đều có ưu điểm và hạn chế riêng.

Một mặt, **bộ nhớ có giới hạn và cùng một vùng bộ nhớ không thể được nhiều chương trình chia sẻ**, vì vậy chúng ta mong muốn các cấu trúc dữ liệu sử dụng không gian hiệu quả nhất có thể. Các phần tử mảng được xếp liền kề và không cần thêm không gian để lưu trữ các tham chiếu (con trỏ) giữa các node của danh sách liên kết, nên có hiệu quả sử dụng không gian cao hơn. Tuy nhiên, mảng cần cấp phát đủ một vùng bộ nhớ liền kề ngay từ đầu, điều này có thể dẫn đến lãng phí bộ nhớ; việc mở rộng mảng cũng đòi hỏi thêm thời gian và không gian. Ngược lại, danh sách liên kết thực hiện cấp phát và giải phóng bộ nhớ động theo từng “node”, nên linh hoạt hơn.

Mặt khác, trong quá trình thực thi chương trình, **khi bộ nhớ liên tục được cấp phát và giải phóng, mức độ phân mảnh của bộ nhớ trống ngày càng nghiêm trọng**, dẫn đến hiệu quả sử dụng bộ nhớ giảm. Do sử dụng phương thức lưu trữ liền kề, mảng tương đối ít có khả năng gây phân mảnh bộ nhớ hơn. Ngược lại, các phần tử của danh sách liên kết được phân tán trong bộ nhớ, nên các thao tác chèn và xóa thường xuyên dễ gây phân mảnh bộ nhớ hơn.

## Hiệu quả sử dụng cache của các cấu trúc dữ liệu

Mặc dù cache có dung lượng nhỏ hơn nhiều so với bộ nhớ, nó nhanh hơn bộ nhớ rất nhiều và đóng vai trò quan trọng đối với tốc độ thực thi chương trình. Vì dung lượng cache có giới hạn và chỉ có thể lưu trữ một phần nhỏ dữ liệu được truy cập thường xuyên, khi CPU cố gắng truy cập dữ liệu không có trong cache, <u>cache miss</u> xảy ra, và CPU phải tải dữ liệu cần thiết từ bộ nhớ chậm hơn.

Rõ ràng, **càng ít “cache miss” thì hiệu quả đọc và ghi dữ liệu của CPU càng cao**, đồng thời hiệu năng chương trình càng tốt. Chúng ta gọi tỷ lệ dữ liệu mà CPU lấy thành công từ cache là <u>cache hit rate</u>, một chỉ số thường được dùng để đo lường hiệu quả của cache.

Để đạt hiệu quả cao nhất có thể, cache sử dụng các cơ chế tải dữ liệu sau:

- **Cache line**: Cache không lưu trữ và tải dữ liệu theo từng byte, mà theo các cache line. So với việc truyền từng byte, truyền theo cache line hiệu quả hơn.
- **Cơ chế prefetching**: Bộ xử lý cố gắng dự đoán các mẫu truy cập dữ liệu (ví dụ: truy cập tuần tự, truy cập nhảy với bước cố định, v.v.) và tải dữ liệu vào cache theo các mẫu cụ thể, từ đó cải thiện hit rate.
- **Tính cục bộ không gian**: Nếu một phần dữ liệu được truy cập, dữ liệu lân cận cũng có thể được truy cập trong tương lai gần. Vì vậy, khi cache tải một phần dữ liệu cụ thể, nó cũng tải dữ liệu lân cận để cải thiện hit rate.
- **Tính cục bộ thời gian**: Nếu một phần dữ liệu được truy cập, nhiều khả năng nó sẽ được truy cập lại trong tương lai gần. Cache tận dụng nguyên tắc này bằng cách giữ lại dữ liệu vừa được truy cập để cải thiện hit rate.

Trên thực tế, **mảng và danh sách liên kết khác nhau về mức độ hiệu quả khi sử dụng cache**, chủ yếu ở các khía cạnh sau:

- **Không gian chiếm dụng**: Các phần tử của danh sách liên kết chiếm nhiều không gian hơn các phần tử mảng, do đó cache chứa được ít dữ liệu hữu ích hơn.
- **Cache line**: Dữ liệu của danh sách liên kết nằm rải rác trong bộ nhớ, trong khi cache tải dữ liệu “theo line”, nên tỷ lệ dữ liệu không hợp lệ được tải vào cao hơn.
- **Cơ chế prefetching**: Các mẫu truy cập dữ liệu của mảng “dễ dự đoán” hơn danh sách liên kết, khiến hệ thống dễ đoán dữ liệu nào sẽ được tải tiếp theo hơn.
- **Tính cục bộ không gian**: Mảng được lưu trữ trong một vùng bộ nhớ tập trung, vì vậy dữ liệu gần dữ liệu đã tải có nhiều khả năng sớm được truy cập hơn.

Nhìn chung, **mảng có hit rate cao hơn, vì vậy thường có hiệu quả thao tác tốt hơn danh sách liên kết**. Điều này khiến các cấu trúc dữ liệu được triển khai dựa trên mảng trở nên phổ biến hơn khi giải các bài toán thuật toán.

Điều quan trọng cần lưu ý là **hiệu quả sử dụng cache cao không có nghĩa mảng vượt trội hơn danh sách liên kết trong mọi trường hợp**. Trong các ứng dụng thực tế, việc lựa chọn cấu trúc dữ liệu nào cần dựa trên yêu cầu cụ thể. Ví dụ, cả mảng và danh sách liên kết đều có thể triển khai cấu trúc dữ liệu “stack” (sẽ được thảo luận chi tiết trong chương tiếp theo), nhưng chúng phù hợp với những tình huống khác nhau.

- Khi giải các bài toán thuật toán, chúng ta thường ưu tiên triển khai stack dựa trên mảng, vì chúng mang lại hiệu quả thao tác cao hơn và khả năng truy cập ngẫu nhiên, đổi lại cần cấp phát trước một lượng không gian bộ nhớ nhất định cho mảng.
- Nếu lượng dữ liệu rất lớn, tính biến động cao và khó ước tính kích thước stack dự kiến, thì triển khai stack dựa trên danh sách liên kết sẽ phù hợp hơn. Danh sách liên kết có thể phân phối lượng lớn dữ liệu đến các vùng khác nhau trong bộ nhớ và tránh phần chi phí bổ sung do việc mở rộng mảng tạo ra.