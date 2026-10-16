# Tóm tắt

### Nội dung ôn tập chính

- Mảng và danh sách liên kết là hai cấu trúc dữ liệu nền tảng, đại diện cho hai cách khác nhau để lưu trữ dữ liệu trong bộ nhớ máy tính: lưu trữ liên tục và lưu trữ phân tán. Ưu điểm và nhược điểm của chúng bổ trợ cho nhau.
- Mảng hỗ trợ truy cập ngẫu nhiên và sử dụng ít bộ nhớ hơn; tuy nhiên, việc chèn và xóa phần tử không hiệu quả, đồng thời độ dài không thể thay đổi sau khi khởi tạo.
- Danh sách liên kết đạt hiệu quả cao khi chèn và xóa node bằng cách sửa đổi các tham chiếu (pointer), đồng thời có thể điều chỉnh độ dài linh hoạt; tuy nhiên, việc truy cập node kém hiệu quả và mức tiêu thụ bộ nhớ cao hơn. Các loại danh sách liên kết phổ biến gồm danh sách liên kết đơn, danh sách liên kết vòng và danh sách liên kết đôi.
- Danh sách là một tập hợp các phần tử có thứ tự, hỗ trợ chèn, xóa, tìm kiếm và sửa đổi, thường được triển khai dựa trên mảng động. Danh sách giữ lại các ưu điểm của mảng, đồng thời cho phép điều chỉnh độ dài linh hoạt.
- Sự xuất hiện của danh sách đã cải thiện đáng kể tính thực tiễn của mảng, nhưng cũng có thể gây lãng phí một phần không gian bộ nhớ.
- Trong quá trình chương trình thực thi, dữ liệu chủ yếu được lưu trữ trong bộ nhớ. Mảng có hiệu quả sử dụng không gian bộ nhớ cao hơn, trong khi danh sách liên kết linh hoạt hơn trong việc sử dụng bộ nhớ.
- Cache cung cấp cho CPU khả năng truy cập dữ liệu nhanh thông qua các cơ chế như cache line, prefetching, locality theo không gian và locality theo thời gian, từ đó cải thiện đáng kể hiệu suất thực thi của chương trình.
- Vì mảng có tỷ lệ cache hit cao hơn nên nhìn chung hiệu quả hơn danh sách liên kết. Khi lựa chọn cấu trúc dữ liệu, cần lựa chọn phù hợp dựa trên yêu cầu và tình huống cụ thể.

### Hỏi & Đáp

**Q**: Việc lưu trữ một mảng trên stack thay vì trên heap có ảnh hưởng đến hiệu quả về thời gian và không gian không?

Mảng được lưu trữ trên stack và trên heap đều nằm trong vùng nhớ liên tục, vì vậy hiệu quả thao tác dữ liệu về cơ bản là như nhau. Tuy nhiên, stack và heap có những đặc điểm riêng, dẫn đến các khác biệt sau.

1. Hiệu quả cấp phát và giải phóng: Stack là một vùng bộ nhớ tương đối nhỏ, việc cấp phát được compiler tự động xử lý; heap tương đối lớn hơn và có thể được cấp phát động trong code, đồng thời dễ bị phân mảnh hơn. Vì vậy, các thao tác cấp phát và giải phóng trên heap thường chậm hơn trên stack.
2. Giới hạn kích thước: Bộ nhớ stack tương đối nhỏ, còn kích thước heap nhìn chung bị giới hạn bởi bộ nhớ khả dụng. Vì vậy, heap phù hợp hơn để lưu trữ các mảng lớn.
3. Tính linh hoạt: Kích thước của mảng trên stack phải được xác định tại thời điểm biên dịch, trong khi kích thước của mảng trên heap có thể được xác định động trong runtime.

**Q**: Tại sao mảng yêu cầu các phần tử có cùng kiểu, trong khi danh sách liên kết lại không nhấn mạnh yêu cầu này?

Danh sách liên kết được tạo thành từ các node, các node được kết nối thông qua các tham chiếu (pointer), và mỗi node có thể lưu trữ các kiểu dữ liệu khác nhau, chẳng hạn như `int`, `double`, `string`, `object`, v.v.

Ngược lại, các phần tử của mảng phải có cùng kiểu để vị trí của chúng có thể được xác định bằng cách tính offset. Ví dụ, nếu một mảng chứa cả kiểu `int` và `long`, trong đó mỗi phần tử lần lượt chiếm 4 byte và 8 byte, thì không thể sử dụng công thức sau để tính offset, vì mảng chứa hai “kích thước phần tử” khác nhau.

```shell
# địa chỉ phần tử = địa chỉ cơ sở của mảng (địa chỉ của phần tử đầu tiên) + kích thước phần tử * chỉ số phần tử
```


**Q**: Sau khi xóa node `P`, chúng ta có cần đặt `P.next` thành `None` không?

Không cần sửa đổi `P.next`. Xét từ góc độ danh sách liên kết, khi duyệt từ node đầu đến node cuối, chúng ta sẽ không còn gặp `P`. Điều này có nghĩa là node `P` đã được xóa khỏi danh sách liên kết, và tại thời điểm này, `P` trỏ đến đâu không quan trọng—nó sẽ không ảnh hưởng đến danh sách liên kết.

Từ góc độ thuật toán và giải quyết bài toán, việc giữ pointer được kết nối là không vấn đề miễn là logic chương trình chính xác. Từ góc độ triển khai standard library, việc chủ động ngắt kết nối sẽ an toàn và rõ ràng hơn. Nếu không ngắt kết nối và node đã xóa không được thu hồi đúng cách, điều này có thể ảnh hưởng đến việc thu hồi các node kế tiếp.

**Q**: Trong danh sách liên kết, độ phức tạp thời gian của thao tác chèn và xóa là $O(1)$. Tuy nhiên, cả thao tác chèn và xóa đều cần $O(n)$ thời gian để tìm phần tử; tại sao độ phức tạp thời gian lại không phải là $O(n)$?

Nếu trước tiên tìm phần tử rồi mới xóa, độ phức tạp thời gian thực sự là $O(n)$. Tuy nhiên, ưu điểm chèn và xóa trong $O(1)$ của danh sách liên kết có thể được thể hiện trong các ứng dụng khác. Ví dụ, deque rất phù hợp để triển khai bằng danh sách liên kết; khi đó, chúng ta duy trì các biến pointer luôn trỏ đến node đầu và node cuối, với mỗi thao tác chèn và xóa đều có độ phức tạp $O(1)$.

**Q**: Trong sơ đồ “Định nghĩa danh sách liên kết và các phương thức lưu trữ”, node pointer màu xanh nhạt chiếm một địa chỉ bộ nhớ riêng hay chia đều với giá trị của node?

Sơ đồ này là biểu diễn định tính; để biểu diễn định lượng, cần phân tích dựa trên tình huống cụ thể.

- Các kiểu giá trị node khác nhau chiếm lượng không gian khác nhau, chẳng hạn như `int`, `long`, `double` và các đối tượng instance, v.v.
- Lượng không gian bộ nhớ mà các biến pointer chiếm dụng phụ thuộc vào hệ điều hành và môi trường biên dịch được sử dụng, thường là 8 byte hoặc 4 byte.

**Q**: Việc thêm một phần tử vào cuối danh sách có phải luôn là $O(1)$ không?

Nếu việc thêm phần tử khiến độ dài danh sách bị vượt quá, trước tiên danh sách phải được mở rộng rồi mới thêm phần tử. Hệ thống sẽ cấp phát một vùng bộ nhớ mới và di chuyển tất cả phần tử từ danh sách ban đầu sang đó; khi này, độ phức tạp thời gian trở thành $O(n)$.

**Q**: “Sự xuất hiện của danh sách đã cải thiện đáng kể tính thực tiễn của mảng, nhưng có thể gây lãng phí một phần không gian bộ nhớ”—sự lãng phí không gian này có phải nói đến phần bộ nhớ do các biến bổ sung như capacity, length và hệ số mở rộng chiếm dụng không?

Sự lãng phí không gian này chủ yếu có hai khía cạnh: một mặt, danh sách thường đặt một độ dài ban đầu mà chúng ta có thể không cần sử dụng hết; mặt khác, để tránh việc mở rộng thường xuyên, việc mở rộng thường nhân với một hệ số, chẳng hạn như $\times 1.5$. Do đó, sẽ có nhiều vị trí trống mà thông thường chúng ta không thể lấp đầy hoàn toàn.

**Q**: Trong Python, sau khi khởi tạo `n = [1, 2, 3]`, địa chỉ của 3 phần tử này là liên tục, nhưng khi khởi tạo `m = [2, 1, 3]`, chúng ta nhận thấy id của mỗi phần tử không liên tục; thay vào đó, chúng giống với các phần tử trong `n`. Vì địa chỉ của các phần tử này không liên tục, `m` có còn là một mảng không?

Nếu thay thế các phần tử của list bằng các node danh sách liên kết `n = [n1, n2, n3, n4, n5]`, thông thường 5 object node này cũng được phân tán trong bộ nhớ. Tuy nhiên, với một chỉ số của list, chúng ta vẫn có thể lấy địa chỉ bộ nhớ của node trong $O(1)$ thời gian, từ đó truy cập node tương ứng. Điều này là vì mảng lưu trữ các tham chiếu đến node, chứ không lưu trữ chính các node.

Không giống nhiều ngôn ngữ khác, các số trong Python được bọc thành object, còn list không lưu trữ chính các số mà lưu trữ các tham chiếu đến số. Vì vậy, chúng ta nhận thấy các số giống nhau trong hai mảng có cùng id, và địa chỉ bộ nhớ của các số này không nhất thiết phải liên tục.

**Q**: C++ STL có `std::list`, vốn đã triển khai danh sách liên kết đôi, nhưng có vẻ một số sách về thuật toán không sử dụng trực tiếp nó. Có giới hạn nào không?

Một mặt, chúng ta thường ưu tiên sử dụng mảng để triển khai thuật toán và chỉ sử dụng danh sách liên kết khi cần thiết, chủ yếu vì hai lý do.

- Overhead về không gian: Vì mỗi phần tử cần thêm hai pointer (một pointer đến phần tử trước và một pointer đến phần tử sau), `std::list` thường tiêu tốn nhiều không gian hơn `std::vector`.
- Không thân thiện với cache: Vì dữ liệu không được lưu trữ liên tục, `std::list` có hiệu suất sử dụng cache thấp hơn. Nhìn chung, `std::vector` có hiệu năng tốt hơn.

Mặt khác, các trường hợp cần danh sách liên kết chủ yếu liên quan đến cây nhị phân và đồ thị. Stack và queue thường sử dụng `stack` và `queue` do ngôn ngữ lập trình cung cấp, thay vì danh sách liên kết.

**Q**: Thao tác `res = [[0]] * n` có tạo ra một list 2D trong đó mỗi `[0]` là độc lập không?

Không, chúng không độc lập. Trong list 2D này, tất cả `[0]` thực chất đều là các tham chiếu đến cùng một object. Nếu sửa đổi một phần tử, chúng ta sẽ nhận thấy tất cả phần tử tương ứng đều thay đổi theo.

Nếu muốn mỗi `[0]` trong list 2D là độc lập, chúng ta có thể sử dụng `res = [[0] for _ in range(n)]` để đạt được điều này. Nguyên lý của cách tiếp cận này là khởi tạo $n$ object list `[0]` độc lập.

**Q**: Thao tác `res = [0] * n` có tạo ra một list trong đó mỗi số nguyên 0 là độc lập không?

Trong list này, tất cả số 0 nguyên đều tham chiếu đến cùng một object. Điều này là vì Python sử dụng cơ chế caching cho các số nguyên nhỏ (thường từ -5 đến 256) nhằm tối đa hóa việc tái sử dụng object và cải thiện hiệu năng.

Mặc dù tất cả đều tham chiếu đến cùng một object, chúng ta vẫn có thể sửa đổi từng phần tử trong list một cách độc lập. Điều này là vì số nguyên trong Python là “object bất biến”. Khi sửa đổi một phần tử, thực chất chúng ta chuyển phần tử đó sang tham chiếu đến một object khác, thay vì thay đổi chính object ban đầu.

Tuy nhiên, khi các phần tử trong danh sách là “đối tượng có thể thay đổi” (mutable objects), chẳng hạn như list, dictionary hoặc các instance của class, việc sửa đổi trực tiếp một phần tử sẽ làm thay đổi chính đối tượng đó, và tất cả các phần tử tham chiếu đến đối tượng đó cũng sẽ có cùng thay đổi.