# Bài tập

## Ôn tập khái niệm

### Tìm kiếm sau khi xảy ra va chạm băm

Một hash table có 5 bucket và sử dụng hàm băm $h(x)=x \bmod 5$. Khi xảy ra va chạm, các phần tử được đặt lần lượt trong một danh sách bên trong bucket đó.  
Chèn `[1, 6, 11, 7]` theo thứ tự:

<!-- numbered-subquestions -->

1. Viết nội dung của các bucket 0–4.
2. Khi tìm kiếm 6, bucket nào được kiểm tra trước, và các phần tử được xét theo thứ tự nào?
3. Dựa trên nội dung bucket ở Câu 1, các lần chèn sau có ghi đè lên các lần chèn trước không? Hãy giải thích bằng phương pháp xử lý va chạm này.

??? success "Đáp án"

    1. Vì $1\bmod5=6\bmod5=11\bmod5=1$, còn $7\bmod5=2$, các bucket là:

        ```text
        0: []
        1: [1, 6, 11]
        2: [7]
        3: []
        4: []
        ```

    2. Tìm kiếm 6 trước tiên đi đến bucket 1, sau đó lần lượt so sánh 1 và 6. Giá trị cần tìm được thấy ở lần so sánh thứ hai.

    3. Các giá trị băm bằng nhau chỉ có nghĩa là các phần tử được đưa vào cùng một bucket, không có nghĩa là các phần tử bằng nhau. Separate chaining giữ lại tất cả các phần tử bị va chạm trong bucket
        và so sánh từng phần tử một trong quá trình tìm kiếm, vì vậy 1, 6 và 11 không ghi đè lên nhau.

### Các phần tử đi đâu sau khi hash table mở rộng?

Một hash table sử dụng separate chaining ban đầu có 5 bucket và hàm băm $h(x)=x\bmod5$.  
Các key `[1, 6, 11]` đều nằm trong bucket 1.

Bây giờ table được mở rộng thành 7 bucket, và hàm băm trở thành $h(x)=x\bmod7$:

<!-- numbered-subquestions -->

1. Tính số bucket mới cho 1, 6 và 11.
2. Những bucket nào chứa các phần tử sau khi mở rộng?
3. Trong quá trình mở rộng, có thể פשוט sao chép danh sách từ bucket 1 cũ sang bucket 1 mới không? Hãy giải thích bằng kết quả từ Câu 1 và Câu 2.

??? success "Đáp án"

    1. Số bucket mới là:

        - $1\bmod7=1$;
        - $6\bmod7=6$;
        - $11\bmod7=4$.

    2. Bucket 1 lưu 1, bucket 4 lưu 11, và bucket 6 lưu 6. Ba key không còn tập trung trong cùng một bucket.

    3. Không thể sao chép nguyên trạng danh sách. Số bucket được tính bằng cách lấy key modulo số lượng bucket. Khi số lượng bucket thay đổi từ 5 thành 7, số bucket của một key có thể thay đổi,
        vì vậy phải tính lại vị trí của mọi key. Nếu bucket 1 cũ được sao chép mà không thay đổi, các lần tìm kiếm sau đó sử dụng công thức mới sẽ đi đến bucket 6 với 6 và bucket 4 với 11
        và sẽ không tìm thấy chúng.

### 11 vẫn có thể được tìm thấy sau khi xóa 6 không?

Một hash table có 5 vị trí với các chỉ số `0–4` và sử dụng hàm băm $h(x)=x\bmod5$.  
Khi xảy ra va chạm, table tìm sang phải từ chỉ số do hàm băm tạo ra để tìm vị trí trống đầu tiên.

Chèn `[1, 6, 11]` theo thứ tự:

<!-- numbered-subquestions -->

1. Cuối cùng mỗi số được lưu tại chỉ số nào?
2. Khi tìm kiếm 11, những chỉ số nào được kiểm tra theo thứ tự?
3. Giả sử việc xóa 6 thay đổi trực tiếp vị trí của nó thành “vị trí trống chưa từng được sử dụng”, và quá trình tìm kiếm dừng lại mỗi khi gặp một vị trí trống. Điều gì xảy ra khi tìm kiếm 11 sau đó? Kết quả tìm kiếm này có chính xác không? Nếu có vấn đề, có thể tránh vấn đề đó bằng cách nào?

??? success "Đáp án"

    1. Số 1 được lưu tại chỉ số 1. Số 6 cũng ánh xạ đến chỉ số 1, nên sau khi xảy ra va chạm, nó được lưu tại chỉ số 2.
        Số 11 cũng bắt đầu tại chỉ số 1, bỏ qua các chỉ số 1 và 2 đang bị chiếm dụng, rồi cuối cùng được lưu tại chỉ số 3.

    2. Tìm kiếm 11 kiểm tra các chỉ số `1, 2, 3` theo thứ tự và tìm thấy nó tại chỉ số 3.

    3. Nếu chỉ số 2 được thay đổi để mang nghĩa “chưa từng được sử dụng”, quá trình tìm kiếm 11 sẽ kiểm tra chỉ số 1 rồi dừng lại ở chỉ số 2,
        kết luận sai rằng 11 không tồn tại. Khi xóa, nên để lại một marker “đã xóa”.
        Quá trình tìm kiếm khi gặp marker này sẽ tiếp tục đến chỉ số tiếp theo (quay vòng từ chỉ số 4 về chỉ số 0), trong khi một lần chèn sau đó vẫn có thể sử dụng lại vị trí này.

## Bài tập lập trình

### So sánh số lần xuất hiện của các ký tự trong hai chuỗi

Cho hai chuỗi `s` và `t` chỉ chứa các chữ cái tiếng Anh viết thường,
bạn có thể sắp xếp lại các ký tự trong `s` theo bất kỳ thứ tự nào, nhưng không được thêm, xóa hoặc thay thế ký tự.

Hãy xác định xem chuỗi sau khi sắp xếp lại có thể tạo thành `t` hay không. Trả về `true` nếu có thể và `false` nếu không thể.
Sử dụng hash table để ghi lại số lần xuất hiện của mỗi chữ cái. Không được sắp xếp các ký tự trong các chuỗi.

??? tip "Gợi ý"

    1. Nếu hai chuỗi có độ dài khác nhau, chúng không thể chứa mỗi ký tự với cùng số lần xuất hiện
    2. Sử dụng hash table để ghi lại số lần xuất hiện của mỗi chữ cái; tăng count tương ứng trong khi duyệt s
    3. Giảm count tương ứng trong khi duyệt t; hai chuỗi chứa mỗi ký tự với cùng số lần xuất hiện chỉ khi mọi count đều bằng 0 ở cuối

[LeetCode](https://leetcode.com/problems/valid-anagram/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }