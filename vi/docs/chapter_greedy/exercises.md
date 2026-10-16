# Bài tập

## Ôn tập khái niệm

### Luôn chọn đồng xu lớn nhất có phải là tốt nhất không?

Các mệnh giá tiền xu là `[1, 7, 10]`, và số tiền mục tiêu là 14.

<!-- numbered-subquestions -->

1. Làm theo quy tắc “luôn chọn mệnh giá lớn nhất không vượt quá số tiền còn lại” và viết ra các đồng xu được chọn.
2. Có cách nào dùng ít đồng xu hơn không? Nếu có, hãy đưa ra một cách; nếu không, hãy giải thích lý do.
3. Ví dụ này có cho thấy chiến lược tham lam đúng với mọi tập mệnh giá tiền xu không?

??? success "Đáp án"

    1. Chiến lược tham lam chọn `10 + 1 + 1 + 1 + 1`, tổng cộng dùng 5 đồng xu.

    2. Có một cách dùng ít đồng xu hơn: `7 + 7`, chỉ dùng 2 đồng xu.

    3. Không. Phản ví dụ này cho thấy rằng, với các mệnh giá tiền xu tùy ý, việc liên tục chọn mệnh giá lớn nhất hiện có không nhất thiết tối thiểu hóa số lượng đồng xu.
        Lựa chọn lớn nhất trước mắt có thể ngăn cản một tổ hợp tốt hơn về sau.

### Nên đưa vật phẩm nào vào ba lô trước?

Một chiếc ba lô có sức chứa 4 kilôgam có thể chứa các vật phẩm sau. Có thể lấy một phần của vật phẩm,
và giá trị nhận được tỉ lệ thuận với khối lượng của vật phẩm:

- Vật phẩm A: khối lượng 4 kilôgam, giá trị 20.
- Vật phẩm B: khối lượng 3 kilôgam, giá trị 18.

<!-- numbered-subquestions -->

1. Giá trị trên mỗi kilôgam của từng vật phẩm là bao nhiêu? Nên đặt vật phẩm nào vào ba lô trước?
2. Hãy lấp đầy ba lô bằng chiến lược tham lam cho bài toán ba lô phân số. Giá trị cuối cùng là bao nhiêu?
3. Khi có thể chia nhỏ các vật phẩm và ba lô giới hạn tổng khối lượng, nên so sánh các vật phẩm dựa trên tổng giá trị hay giá trị trên mỗi kilôgam? Vì sao?

??? success "Đáp án"

    1. A có giá trị `20 ÷ 4 = 5` trên mỗi kilôgam, còn B có giá trị `18 ÷ 3 = 6` trên mỗi kilôgam,
        vì vậy nên đặt B vào ba lô trước, do B có giá trị trên mỗi đơn vị khối lượng cao hơn.

    2. Trước tiên, lấy toàn bộ B, sử dụng 3 kilôgam sức chứa và nhận được giá trị 18. Khi còn lại 1 kilôgam sức chứa,
        lấy 1 kilôgam A, nhận được giá trị 5. Giá trị cuối cùng là `18 + 5 = 23`.

    3. Ba lô giới hạn tổng khối lượng và các vật phẩm có thể được chia nhỏ, vì vậy nên so sánh chúng dựa trên giá trị trên mỗi đơn vị khối lượng.
        Mặc dù A có tổng giá trị cao hơn, giá trị trên mỗi kilôgam của A thấp hơn B. Nếu lấp đầy ba lô bằng A trước, giá trị nhận được chỉ là 20.

### Nên di chuyển con trỏ nào tiếp theo?

Các chiều cao của các vách ngăn là `[1, 8, 6, 2, 5]`. Sử dụng hai con trỏ, mỗi con trỏ ở một đầu, để tìm dung tích lớn nhất.
Dung tích bằng “chiều cao của vách ngăn thấp hơn × khoảng cách giữa chỉ số của hai vách ngăn”.

<!-- numbered-subquestions -->

1. Ban đầu, con trỏ trái ở chỉ số 0 và con trỏ phải ở chỉ số 4. Dung tích hiện tại là bao nhiêu? Nên di chuyển con trỏ nào tiếp theo?
2. Sau khi thực hiện bước di chuyển được chọn trong Câu hỏi 1, hai con trỏ đang ở những chỉ số nào? Dung tích hiện tại là bao nhiêu? Nên di chuyển con trỏ nào tiếp theo?
3. Với cặp vách ngăn hiện tại, bạn có thể di chuyển con trỏ ở vách ngăn thấp hơn hoặc con trỏ ở vách ngăn cao hơn. Bước di chuyển nào vẫn có thể tạo ra dung tích lớn hơn, và tại sao?

??? success "Đáp án"

    1. Dung tích hiện tại là `min(1, 5) × (4 - 0) = 4`. Vách ngăn bên trái thấp hơn, vì vậy hãy di chuyển con trỏ trái.

    2. Sau khi con trỏ trái di chuyển, hai con trỏ ở các chỉ số 1 và 4. Dung tích hiện tại là
        `min(8, 5) × (4 - 1) = 15`. Vách ngăn bên phải thấp hơn, vì vậy tiếp theo hãy di chuyển con trỏ phải.

    3. Di chuyển con trỏ ở vách ngăn thấp hơn là bước duy nhất vẫn có thể tạo ra dung tích lớn hơn. Nếu con trỏ của vách ngăn cao hơn di chuyển, khoảng cách chắc chắn giảm trong khi chiều cao vẫn bị giới hạn bởi vách ngăn thấp hơn không di chuyển,
        vì vậy dung tích chỉ có thể giữ nguyên hoặc giảm. Chỉ bằng cách di chuyển con trỏ ở vách ngăn thấp hơn, ta mới có thể tìm thấy một vách ngăn cao hơn.

## Bài tập lập trình

### Bài toán ba lô phân số

Bạn được cung cấp hai mảng có cùng độ dài `wgt` và `val`, trong đó `wgt[i] > 0` và `val[i] >= 0`. Ba lô có sức chứa `cap >= 0`.
Chỉ có một vật phẩm cho mỗi loại, nhưng có thể đặt bất kỳ phần nào của một vật phẩm vào ba lô.
Giá trị nhận được tỉ lệ thuận với phần khối lượng tổng của vật phẩm được đưa vào. Hãy sử dụng một thuật toán tham lam
và trả về tổng giá trị lớn nhất mà ba lô có thể chứa dưới dạng một số thực.

??? tip "Gợi ý"

    1. Trước tiên, tính giá trị trên mỗi đơn vị khối lượng của từng vật phẩm bằng val[i] / wgt[i], giữ lại phần thập phân của phép chia
    2. Đặt các vật phẩm có giá trị trên mỗi đơn vị khối lượng cao hơn vào ba lô trước
    3. Nếu sức chứa còn lại nhỏ hơn khối lượng của vật phẩm hiện tại, lấy đúng phần cần thiết để lấp đầy ba lô rồi dừng lại