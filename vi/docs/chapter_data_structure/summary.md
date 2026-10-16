# Tổng kết

### Nội dung ôn tập chính

- Các cấu trúc dữ liệu có thể được phân loại theo hai góc độ: cấu trúc logic và cấu trúc vật lý. Cấu trúc logic mô tả mối quan hệ logic giữa các phần tử dữ liệu, trong khi cấu trúc vật lý mô tả cách dữ liệu được lưu trữ trong bộ nhớ máy tính.
- Các cấu trúc logic phổ biến bao gồm cấu trúc tuyến tính, dạng cây và dạng mạng. Dựa trên cấu trúc logic, chúng ta thường phân loại cấu trúc dữ liệu thành tuyến tính (mảng, danh sách liên kết, ngăn xếp, hàng đợi) và phi tuyến tính (cây, đồ thị, heap). Việc triển khai hash table có thể liên quan đến cả cấu trúc dữ liệu tuyến tính và phi tuyến tính.
- Khi một chương trình chạy, dữ liệu được lưu trữ trong bộ nhớ máy tính. Mỗi vùng nhớ có một địa chỉ bộ nhớ tương ứng, và chương trình truy cập dữ liệu thông qua các địa chỉ bộ nhớ này.
- Cấu trúc vật lý chủ yếu được chia thành lưu trữ trong vùng nhớ liên tục (mảng) và lưu trữ trong vùng nhớ phân tán (danh sách liên kết). Tất cả cấu trúc dữ liệu đều được triển khai bằng mảng, danh sách liên kết hoặc sự kết hợp của cả hai.
- Các kiểu dữ liệu cơ bản trong máy tính bao gồm số nguyên `byte`, `short`, `int`, `long`, số dấu phẩy động `float`, `double`, ký tự `char` và giá trị Boolean `bool`. Phạm vi giá trị của chúng phụ thuộc vào kích thước vùng nhớ mà chúng chiếm dụng và phương thức biểu diễn của chúng.
- Dạng dấu-trị tuyệt đối (sign-magnitude), bù 1 (1's complement) và bù 2 (2's complement) là ba phương pháp mã hóa số trong máy tính, và chúng có thể được chuyển đổi lẫn nhau. Bit có trọng số lớn nhất của dạng dấu-trị tuyệt đối là bit dấu, còn các bit còn lại biểu diễn giá trị của số.
- Số nguyên được lưu trữ trong máy tính dưới dạng bù 2. Với biểu diễn bù 2, máy tính có thể xử lý phép cộng các số dương và số âm một cách thống nhất mà không cần thiết kế các mạch phần cứng đặc biệt cho phép trừ, đồng thời không xảy ra sự mơ hồ giữa số 0 dương và số 0 âm.
- Mã hóa số dấu phẩy động gồm 1 bit dấu, 8 bit số mũ và 23 bit phần định trị. Nhờ các bit số mũ, phạm vi của số dấu phẩy động lớn hơn nhiều so với số nguyên, nhưng phải đánh đổi bằng độ chính xác.
- ASCII là bộ ký tự tiếng Anh đầu tiên, có độ dài 1 byte và chứa tổng cộng 128 ký tự. GBK là bộ ký tự tiếng Trung thường được sử dụng, chứa hơn 20.000 ký tự tiếng Trung. Unicode hướng tới việc cung cấp một tiêu chuẩn bộ ký tự hoàn chỉnh, tập hợp các ký tự từ nhiều ngôn ngữ trên thế giới, qua đó giải quyết vấn đề văn bản bị lỗi do các phương thức mã hóa ký tự không nhất quán.
- UTF-8 là phương thức mã hóa Unicode phổ biến nhất và có khả năng tương thích tuyệt vời. Đây là phương thức mã hóa có độ dài thay đổi, có khả năng mở rộng tốt và giúp cải thiện hiệu quả sử dụng không gian lưu trữ. UTF-16 và UTF-32 là các phương thức mã hóa Unicode phổ biến. Khi mã hóa ký tự tiếng Trung, UTF-16 chiếm ít không gian hơn UTF-8. Các ngôn ngữ lập trình như Java và C# sử dụng mã hóa UTF-16 theo mặc định.

### Hỏi & Đáp

**Q**: Độ dài của kiểu `char` có phải là 1 byte không?

Độ dài của kiểu `char` được xác định bởi phương thức mã hóa mà ngôn ngữ lập trình sử dụng. Ví dụ, Java, JavaScript, TypeScript và C# đều sử dụng mã hóa UTF-16 (để lưu trữ các điểm mã Unicode), vì vậy kiểu `char` có độ dài 2 byte.

**Q**: Việc gọi các cấu trúc dữ liệu dựa trên mảng là “cấu trúc dữ liệu tĩnh” có gây mơ hồ không? Ngăn xếp cũng có thể thực hiện các thao tác “động” như push và pop.

Ngăn xếp thực sự có thể thực hiện các thao tác dữ liệu động, nhưng cấu trúc dữ liệu này vẫn là “tĩnh” (có độ dài cố định). Mặc dù các cấu trúc dữ liệu dựa trên mảng có thể thêm hoặc xóa phần tử một cách động, dung lượng của chúng vẫn cố định. Nếu lượng dữ liệu vượt quá kích thước được cấp phát trước, cần tạo một mảng mới lớn hơn và sao chép nội dung của mảng cũ sang mảng mới.

**Q**: Khi khởi tạo một ngăn xếp (hàng đợi), kích thước của nó không được chỉ định. Tại sao chúng vẫn là “cấu trúc dữ liệu tĩnh”?

Trong các ngôn ngữ lập trình bậc cao, chúng ta không cần chỉ định thủ công dung lượng ban đầu của ngăn xếp (hàng đợi); lớp sẽ tự động xử lý việc này. Ví dụ, dung lượng ban đầu của `ArrayList` trong Java thường là 10. Ngoài ra, thao tác mở rộng cũng được tự động triển khai. Xem phần “List” tiếp theo để biết chi tiết.

**Q**: Phương pháp chuyển đổi từ dạng dấu-trị tuyệt đối sang bù 2 là “đảo bit trước, sau đó cộng 1”. Vì vậy, chuyển đổi từ bù 2 sang dạng dấu-trị tuyệt đối phải là phép toán ngược lại, tức “trừ 1 trước, sau đó đảo bit”. Tuy nhiên, bù 2 cũng có thể được chuyển đổi sang dạng dấu-trị tuyệt đối bằng cách “đảo bit trước, sau đó cộng 1”. Tại sao lại như vậy?

Đó là vì việc chuyển đổi lẫn nhau giữa dạng dấu-trị tuyệt đối và bù 2 thực chất là quá trình tính “phần bù”. Trước tiên, hãy định nghĩa phần bù: giả sử $a + b = c$, khi đó ta nói $a$ là phần bù của $b$ đối với $c$, và ngược lại, $b$ là phần bù của $a$ đối với $c$.

Cho một số nhị phân 4 bit $n = 4$ là $0010$, nếu coi số này là dạng dấu-trị tuyệt đối (bỏ qua bit dấu), phần bù 2 của nó có thể được tính bằng cách “đảo bit trước, sau đó cộng 1”:

$$
0010 \rightarrow 1101 \rightarrow 1110
$$

Ta nhận thấy tổng của dạng dấu-trị tuyệt đối và bù 2 là $0010 + 1110 = 10000$, điều này có nghĩa là bù 2 $1110$ là “phần bù” của dạng dấu-trị tuyệt đối $0010$ đối với $10000$. **Điều này có nghĩa là phép “đảo bit trước, sau đó cộng 1” ở trên thực chất là quá trình tính phần bù đối với $10000$**.

Vậy “phần bù” của bù 2 $1110$ đối với $10000$ là gì? Chúng ta vẫn có thể sử dụng thao tác “đảo bit trước, sau đó cộng 1” để tính:

$$
1110 \rightarrow 0001 \rightarrow 0010
$$

Nói cách khác, dạng dấu-trị tuyệt đối và bù 2 là “phần bù” của nhau đối với $10000$, vì vậy phép chuyển đổi “dạng dấu-trị tuyệt đối sang bù 2” và “bù 2 sang dạng dấu-trị tuyệt đối” có thể được thực hiện bằng cùng một thao tác (đảo bit trước, sau đó cộng 1).

Tất nhiên, chúng ta cũng có thể sử dụng phép toán ngược để tìm dạng dấu-trị tuyệt đối của bù 2 $1110$, tức là “trừ 1 trước, sau đó đảo bit”:

$$
1110 \rightarrow 1101 \rightarrow 0010
$$

Tóm lại, cả “đảo bit trước, sau đó cộng 1” và “trừ 1 trước, sau đó đảo bit” đều tính phần bù đối với $10000$, và chúng tương đương nhau.

Về bản chất, thao tác “đảo bit” thực chất là tìm phần bù đối với $1111$ (vì “dạng dấu-trị tuyệt đối + bù 1 = 1111” luôn đúng); sau đó cộng 1 vào bù 1 sẽ thu được bù 2, tức phần bù đối với $10000$.

Ví dụ trên sử dụng $n = 4$, và có thể khái quát cho các số nhị phân có số lượng bit bất kỳ.