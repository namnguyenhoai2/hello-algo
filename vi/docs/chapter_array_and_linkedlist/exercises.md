# Bài tập

## Ôn tập khái niệm

### Cách mảng và danh sách liên kết tìm một phần tử

Mảng và danh sách liên kết đơn đều lưu trữ `[A, B, C, D, E]` theo thứ tự. Bây giờ bạn cần truy cập phần tử thứ tư, `D`:

<!-- numbered-subquestions -->

1. Mảng có thể sử dụng trực tiếp chỉ mục nào?
2. Bắt đầu từ nút đầu `A`, những nút nào được duyệt theo thứ tự khi bạn lần theo `next`?
3. Khi phần tử được yêu cầu nằm càng xa về cuối, số bước thay đổi như thế nào đối với mỗi cấu trúc? Cấu trúc nào phù hợp hơn cho việc truy cập lặp lại theo vị trí, và vì sao?

??? success "Đáp án"

    1. Với indexing bắt đầu từ 0, phần tử thứ tư có chỉ mục là 3, nên mảng có thể truy cập trực tiếp `arr[3]`.

    2. Danh sách liên kết đơn phải bắt đầu từ đầu danh sách. Đường đi truy cập của nó là `A → B → C → D`, cần đi qua `next` ba lần.

    3. Mảng có thể xác định trực tiếp vị trí của một phần tử từ địa chỉ bắt đầu và chỉ mục của nó, nên việc truy cập theo vị trí có độ phức tạp thời gian là $O(1)$.
        Để truy cập nút thứ $k$, danh sách liên kết đơn phải bắt đầu từ nút đầu và lần theo `next` $k-1$ lần,
        mất $O(n)$ thời gian trong trường hợp xấu nhất.

        So sánh này chỉ xét việc truy cập theo vị trí; điều đó không có nghĩa là danh sách liên kết chậm hơn trong mọi thao tác.

### Cách mảng và danh sách liên kết chèn một phần tử

Mảng và danh sách liên kết đơn đều lưu trữ `A, B, C, D`. Bây giờ bạn cần chèn `X` sau `B`:

- Mảng có capacity là 5 và hiện đang là `[A, B, C, D, _]`.
- Danh sách liên kết là `A → B → C → D`, và bạn đã có một reference đến nút `B`.

<!-- numbered-subquestions -->

1. Mảng phải di chuyển những phần tử nào? Viết mảng sau khi chèn.
2. Danh sách liên kết nên cập nhật `X.next` và `B.next` theo thứ tự nào? Viết danh sách liên kết sau khi chèn.
3. Khi so sánh hiệu quả chèn, vì sao cần nêu rõ rằng “bạn đã có một reference đến nút B”?

??? success "Đáp án"

    1. Trước tiên, mảng di chuyển `D` sang phải một vị trí, sau đó di chuyển `C` sang phải một vị trí, rồi đặt `X` tại chỉ mục 2,
        tạo thành `[A, B, X, C, D]`.

    2. Ban đầu, `B.next` trỏ đến `C`. Trước tiên đặt `X.next = B.next`, khiến `X` trỏ đến `C`;
        sau đó đặt `B.next = X`. Kết quả là `A → B → X → C → D`.
        Nếu `B.next` bị ghi đè trước mà không lưu liên kết ban đầu, `C` có thể trở nên không thể truy cập.

    3. Khi đã biết vị trí của `B`, việc chèn vào danh sách liên kết chỉ thay đổi hai liên kết và mất thời gian $O(1)$.
        Nếu trước tiên phải tìm `B` từ đầu danh sách, riêng việc tìm kiếm đó có thể mất thời gian $O(n)$.

### Capacity của danh sách tăng như thế nào

Một danh sách dựa trên mảng hiện chứa `[A, B, C]`, có length là `size = 3` và capacity là `capacity = 4`.
Khi không còn đủ capacity, một mảng mới có capacity gấp đôi capacity cũ sẽ được tạo.

<!-- numbered-subquestions -->

1. Sau khi thêm `D` vào cuối, length và capacity của danh sách là bao nhiêu? Có cần mở rộng capacity không?
2. Khi tiếp theo thêm `E` vào cuối, capacity trở thành bao nhiêu? Có bao nhiêu phần tử hiện có phải được sao chép?
3. Length của mảng nền không thể thay đổi. Vậy tại sao capacity của danh sách dường như vẫn có thể tăng?

??? success "Đáp án"

    1. `D` vừa với vị trí trống cuối cùng. Nội dung hiện tại là `[A, B, C, D]`,
        với `size = 4` và `capacity = 4`, nên không cần mở rộng capacity.

    2. Khi thêm `E` vào cuối, không còn vị trí trống nào, nên phải tạo một mảng mới có capacity là 8.
        Bốn phần tử hiện có `A, B, C, D` được sao chép vào đó trước khi thêm `E`.
        Kết quả là `size = 5` và `capacity = 8`.

    3. Bản thân mảng ban đầu không tăng kích thước. Danh sách tạo một mảng mới lớn hơn, sao chép các phần tử hiện có,
        rồi dùng mảng mới làm vùng lưu trữ nền. Từ góc nhìn của người dùng, capacity đã tăng.

## Bài tập lập trình

### Cộng một vào số nguyên lớn được lưu dưới dạng mảng

Mảng `digits` lưu các chữ số thập phân của một số nguyên không âm từ trái sang phải. Ví dụ, `[3, 0, 8]` biểu diễn 308.
Số 0 được biểu diễn bằng `[0]`; với mọi đầu vào khác, chữ số đầu tiên không phải là 0.

Mô phỏng phép cộng theo cột trong hệ thập phân để cộng 1 vào số nguyên này, rồi trả về kết quả ở cùng định dạng mảng.
Bạn có thể sửa đổi trực tiếp `digits`. Nếu xuất hiện carry mới ở đầu, bạn có thể trả về một mảng dài hơn.

??? tip "Gợi ý"

    1. Bắt đầu với chữ số cuối cùng của mảng, giống như khi cộng theo cột thông thường
    2. Nếu chữ số hiện tại nhỏ hơn 9, hãy cộng 1 rồi trả về ngay
    3. Nếu chữ số hiện tại là 9, đổi nó thành 0; nếu mọi chữ số đều là 9, đặt 1 ở đầu

[LeetCode](https://leetcode.com/problems/plus-one/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }

### Đảo ngược danh sách liên kết đơn

Bạn được cung cấp nút đầu `head` của một danh sách liên kết đơn. Mỗi nút chứa một giá trị và một reference `next` đến nút tiếp theo.

Sử dụng cách tiếp cận lặp để đảo ngược tất cả liên kết giữa các nút, rồi trả về nút đầu mới.
Không tạo bất kỳ nút mới nào cho danh sách liên kết.

??? tip "Gợi ý"

    1. Trước tiên, hãy vẽ ba nút được nối với nhau cùng hai con trỏ prev và cur trên giấy
    2. Trước khi thay đổi cur.next, hãy lưu nút next ban đầu vào nxt
    3. Sau khi đảo ngược cur.next, đặt prev = cur rồi đặt cur = nxt để tiếp tục với nút tiếp theo trong danh sách ban đầu

[LeetCode](https://leetcode.com/problems/reverse-linked-list/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }