# Bài tập

## Ôn tập khái niệm

### Mối quan hệ dữ liệu trong các tình huống hằng ngày

Dựa trên mối quan hệ giữa các dữ liệu, hãy chọn một trong ba loại “cấu trúc tuyến tính”, “cấu trúc cây” và “cấu trúc mạng” cho mỗi tình huống dưới đây, đồng thời giải thích lý do:

<!-- numbered-subquestions -->

1. Học sinh đứng thành một hàng; ta chỉ xét những người đứng ngay trước và ngay sau mỗi học sinh.
2. Một trường học được tổ chức theo các cấp: “trường → khối → lớp”.
3. Các con đường trong thành phố kết nối nhiều giao lộ. Một giao lộ có thể dẫn đến nhiều giao lộ khác, và các con đường có thể tạo thành các chu trình.

??? success "Đáp án"

    1. Đây là một cấu trúc tuyến tính. Ngoại trừ học sinh đầu tiên và cuối cùng, mỗi người đứng cạnh đúng một người phía trước và một người phía sau, nên các mối quan hệ mở rộng theo một đường thẳng duy nhất.

    2. Đây là một cấu trúc cây. Mỗi lớp thuộc một khối, và mỗi khối thuộc trường, nên các mối quan hệ hình thành các cấp từ trên xuống dưới.

    3. Đây là một cấu trúc mạng. Một giao lộ có thể kết nối với nhiều giao lộ khác, và các tuyến đường có thể tạo thành các chu trình, nên chúng không thể được sắp xếp theo một thứ tự duy nhất hoặc một hệ thống phân cấp chặt chẽ.

        Để xác định một cấu trúc, trước hết hãy xem xét mối quan hệ giữa các phần tử thay vì xem xét nó sử dụng bao nhiêu không gian trong bộ nhớ.

### Lưu trữ thứ tự logic trong bộ nhớ

Xét hai cách bố trí bộ nhớ đơn giản để lưu trữ thứ tự logic `A → B → C`:

- Bố trí A: `A, B, C` được lưu trong các ô nhớ lần lượt mang số `20, 21, 22`.
- Bố trí B: `A, B, C` được lưu trong các ô nhớ lần lượt mang số `20, 7, 31`. `A` ghi lại vị trí của `B`, còn `B` ghi lại vị trí của `C`.

<!-- numbered-subquestions -->

1. Bố trí nào sử dụng cách lưu trữ trong vùng nhớ liên tục, và bố trí nào sử dụng cách lưu trữ trong vùng nhớ phân tán?
2. Bố trí nào giống mảng hơn, và bố trí nào giống danh sách liên kết hơn?
3. Các số ô nhớ trong Bố trí B không theo thứ tự tăng dần. Tại sao bố trí này vẫn có thể biểu diễn thứ tự logic `A → B → C`?

??? success "Đáp án"

    1. Bố trí A sử dụng các ô nhớ liên tiếp, nên sử dụng cách lưu trữ trong vùng nhớ liên tục. Các node trong Bố trí B nằm rải rác ở những vị trí khác nhau, nên sử dụng cách lưu trữ trong vùng nhớ phân tán.

    2. Bố trí A giống mảng hơn, còn Bố trí B giống danh sách liên kết hơn.

    3. Thứ tự logic được xác định bởi các liên kết được ghi giữa các node, không phải bởi thứ tự số của các ô nhớ.
        Vị trí được lưu bởi `A` dẫn đến `B`, rồi vị trí được lưu bởi `B` dẫn đến `C`, vì vậy `A, B, C` vẫn có thể được truy cập theo đúng thứ tự.

        Điều này cũng cho thấy cấu trúc logic và cấu trúc vật lý là hai cách khác nhau để nhìn nhận cùng một dữ liệu.

### Kiểu dữ liệu và cấu trúc trong hồ sơ bài tập

Một nhóm học tập ghi lại, theo thứ tự chỗ ngồi, việc mỗi học sinh trong số bốn học sinh có nộp bài tập hay không:

`[true, false, true, true]`

<!-- numbered-subquestions -->

1. Kiểu dữ liệu cơ bản nào phù hợp với mỗi phần tử?
2. Bốn phần tử được sắp xếp thành một hàng theo thứ tự chỗ ngồi. Cách này sử dụng cấu trúc logic nào?
3. Giả sử sau đó nhóm ghi lại điểm bài tập của mỗi học sinh dưới dạng `[90, 0, 85, 100]`. Điều này có làm thay đổi “kiểu nội dung” hay “cách tổ chức” của dữ liệu không? Hãy giải thích lý do.

??? success "Đáp án"

    1. Mỗi phần tử chỉ biểu diễn “có” hoặc “không”, nên kiểu Boolean `bool` là phù hợp.

    2. Các phần tử được sắp xếp theo thứ tự chỗ ngồi, tạo thành một cấu trúc tuyến tính có thể được lưu trong một mảng.

    3. Kiểu nội dung thay đổi: các phần tử chuyển từ giá trị Boolean thành số nguyên. Cách tổ chức không thay đổi.
        Dữ liệu vẫn được sắp xếp thành một hàng theo thứ tự chỗ ngồi và vẫn có thể được lưu trong một mảng, vốn là một cấu trúc tuyến tính.

        Kiểu dữ liệu cơ bản mô tả “đang lưu trữ gì”, còn cấu trúc dữ liệu mô tả “dữ liệu được tổ chức như thế nào”.

## Bài tập lập trình

### Đếm số bit 1 trong biểu diễn nhị phân

Cho một số nguyên không âm `n`, hãy đếm số bit 1 trong biểu diễn nhị phân của số đó.

Hãy sử dụng các phép toán bit. Không chuyển biểu diễn nhị phân thành chuỗi và không sử dụng hàm dựng sẵn trực tiếp đếm số bit 1.

??? tip "Gợi ý"

    1. n & 1 trích xuất bit ngoài cùng bên phải của n, cho biết bit đó có phải là 1 hay không
    2. Dịch phải một bit sẽ loại bỏ bit ngoài cùng bên phải hiện tại; hầu hết các ngôn ngữ sử dụng toán tử >>
    3. Sau khi triển khai phương thức kiểm tra và dịch từng bit một, hãy nhận thấy rằng n & (n - 1) biến bit 1 ngoài cùng bên phải của n thành 0

[LeetCode](https://leetcode.com/problems/number-of-1-bits/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }