# Phân loại cấu trúc dữ liệu

Các cấu trúc dữ liệu phổ biến bao gồm mảng, danh sách liên kết, stack, queue, bảng băm, cây, heap và đồ thị. Chúng có thể được phân loại theo hai khía cạnh: “cấu trúc logic” và “cấu trúc vật lý”.

## Cấu trúc logic: Tuyến tính và phi tuyến

**Cấu trúc logic thể hiện các mối quan hệ logic giữa các phần tử dữ liệu**. Trong mảng và danh sách liên kết, dữ liệu được sắp xếp theo một thứ tự nhất định, thể hiện mối quan hệ tuyến tính giữa các phần tử; trong cây, dữ liệu được sắp xếp theo thứ bậc từ trên xuống dưới, thể hiện mối quan hệ giữa nút cha và nút hậu duệ; đồ thị được tạo thành từ các nút và cạnh, phản ánh các mối quan hệ mạng phức tạp.

Như minh họa trong hình bên dưới, cấu trúc logic có thể được chia thành hai loại chính: “tuyến tính” và “phi tuyến”. Cấu trúc tuyến tính trực quan hơn, cho thấy dữ liệu được sắp xếp tuyến tính theo các mối quan hệ logic; cấu trúc phi tuyến thì ngược lại, được sắp xếp theo cách phi tuyến.

- **Cấu trúc dữ liệu tuyến tính**: Mảng, danh sách liên kết, stack, queue, bảng băm, trong đó các phần tử có mối quan hệ tuần tự một-một.
- **Cấu trúc dữ liệu phi tuyến**: Cây, heap, đồ thị, bảng băm.

Cấu trúc dữ liệu phi tuyến có thể được chia tiếp thành cấu trúc cây và cấu trúc mạng.

- **Cấu trúc cây**: Cây, heap, bảng băm, trong đó các phần tử có mối quan hệ một-nhiều.
- **Cấu trúc mạng**: Đồ thị, trong đó các phần tử có mối quan hệ nhiều-nhiều.

![Cấu trúc dữ liệu tuyến tính và phi tuyến](classification_of_data_structure.assets/classification_logic_structure.png)

## Cấu trúc vật lý: Liền kề và phân tán

**Khi một chương trình thuật toán chạy, dữ liệu được xử lý chủ yếu được lưu trữ trong bộ nhớ**. Hình bên dưới minh họa một thanh bộ nhớ, trong đó mỗi ô vuông màu đen chứa một vùng nhớ. Ta có thể hình dung bộ nhớ như một bảng tính Excel khổng lồ, trong đó mỗi ô có thể lưu trữ một lượng dữ liệu nhất định.

**Hệ thống truy cập dữ liệu tại vị trí đích thông qua địa chỉ bộ nhớ**. Như minh họa trong hình bên dưới, máy tính đánh số cho từng ô trong bảng tính theo các quy tắc cụ thể, bảo đảm mỗi vùng nhớ có một địa chỉ bộ nhớ duy nhất. Nhờ các địa chỉ này, chương trình có thể truy cập dữ liệu trong bộ nhớ.

![Thanh bộ nhớ, vùng nhớ, địa chỉ bộ nhớ](classification_of_data_structure.assets/computer_memory_location.png)

!!! tip

    Cần lưu ý rằng việc so sánh bộ nhớ với bảng tính Excel chỉ là một phép tương tự đơn giản hóa. Cách bộ nhớ thực sự hoạt động phức tạp hơn nhiều, liên quan đến các khái niệm như không gian địa chỉ, quản lý bộ nhớ, cơ chế cache, bộ nhớ ảo và bộ nhớ vật lý.

Bộ nhớ là tài nguyên dùng chung cho tất cả chương trình. Khi một vùng nhớ bị một chương trình chiếm dụng, thông thường vùng nhớ đó không thể được các chương trình khác sử dụng cùng lúc. **Vì vậy, trong quá trình thiết kế cấu trúc dữ liệu và thuật toán, tài nguyên bộ nhớ là một yếu tố quan trọng cần cân nhắc**. Ví dụ, lượng bộ nhớ cực đại mà một thuật toán sử dụng không được vượt quá dung lượng bộ nhớ trống còn lại của hệ thống; nếu thiếu các khối bộ nhớ lớn liền kề, thì cấu trúc dữ liệu được chọn phải có khả năng được lưu trữ trong các vùng nhớ phân tán.

Như minh họa trong hình bên dưới, **cấu trúc vật lý phản ánh cách dữ liệu được lưu trữ trong bộ nhớ máy tính**. Cấu trúc này có thể được chia thành lưu trữ trong không gian liền kề (mảng) và lưu trữ trong không gian phân tán (danh sách liên kết). Ở cấp độ thấp, cấu trúc vật lý quyết định cách dữ liệu được truy cập, cập nhật, chèn và xóa. Hai cấu trúc vật lý này thể hiện các đặc điểm bổ trợ cho nhau về hiệu quả thời gian và hiệu quả không gian.

![Lưu trữ trong không gian liền kề và lưu trữ trong không gian phân tán](classification_of_data_structure.assets/classification_phisical_structure.png)

Cần lưu ý rằng **tất cả cấu trúc dữ liệu đều được triển khai dựa trên mảng, danh sách liên kết hoặc sự kết hợp của cả hai**. Ví dụ, stack và queue có thể được triển khai bằng mảng hoặc danh sách liên kết; trong khi việc triển khai bảng băm có thể bao gồm cả mảng và danh sách liên kết.

- **Có thể được triển khai dựa trên mảng**: Stack, queue, bảng băm, cây, heap, đồ thị, ma trận, tensor (mảng có số chiều $\geq 3$), v.v.
- **Có thể được triển khai dựa trên danh sách liên kết**: Stack, queue, bảng băm, cây, heap, đồ thị, v.v.

Sau khi khởi tạo, danh sách liên kết vẫn có thể điều chỉnh độ dài trong quá trình chương trình thực thi, vì vậy chúng còn được gọi là “cấu trúc dữ liệu động”. Sau khi khởi tạo, độ dài của mảng không thể thay đổi, vì vậy chúng còn được gọi là “cấu trúc dữ liệu tĩnh”. Cần lưu ý rằng mảng có thể thay đổi độ dài bằng cách cấp phát lại bộ nhớ, nhờ đó vẫn giữ được một mức độ linh hoạt nhất định.

!!! tip

    Nếu bạn cảm thấy khó hiểu cấu trúc vật lý, bạn nên đọc chương tiếp theo trước, sau đó xem lại phần này.