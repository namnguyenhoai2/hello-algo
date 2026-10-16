# Bài tập

## Ôn tập khái niệm

### Cách tìm kiếm nhị phân thu hẹp khoảng tìm kiếm

Tìm kiếm 16 trong mảng đã sắp xếp `[2, 5, 8, 12, 16, 23, 38]`.
Sử dụng khoảng đóng `[i, j]` và tính điểm giữa theo công thức
$m=i+(j-i)/2$, làm tròn xuống.

Ở mỗi vòng, hãy viết `(i, j, m)`, phần tử ở giữa và cách thu hẹp khoảng tiếp theo,
cho đến khi tìm thấy giá trị cần tìm.

??? success "Đáp án"

    Quá trình tìm kiếm diễn ra như sau:

    | Vòng | `(i, j, m)` | Phần tử ở giữa | Bước tiếp theo |
    | --- | --- | --- | --- |
    | 1 | `(0, 6, 3)` | 12 | `12 < 16`, đặt `i = 4` |
    | 2 | `(4, 6, 5)` | 23 | `23 > 16`, đặt `j = 4` |
    | 3 | `(4, 4, 4)` | 16 | Đã tìm thấy giá trị cần tìm; trả về chỉ số 4 |

    Vì mảng đã được sắp xếp, khi giá trị ở giữa nhỏ hơn giá trị cần tìm, có thể loại bỏ phần tử ở giữa và mọi phần tử bên trái nó.
    Khi giá trị ở giữa lớn hơn giá trị cần tìm, có thể loại bỏ phần tử ở giữa và mọi phần tử bên phải nó.

### Biên trái và biên phải của các phần tử trùng lặp

Tìm kiếm số 2 trong mảng `[1, 2, 2, 2, 4, 6]`.
Một học sinh sử dụng tìm kiếm nhị phân, trả về ngay sau khi tìm thấy giá trị cần tìm tại chỉ số 2 và nói:
"Chỉ số 2 là biên trái của số 2."

<!-- numbered-subquestions -->

1. Phát biểu của học sinh có đúng không? Biên trái và biên phải của 2 là gì? Hãy giải thích tại sao.
2. Khi tìm biên trái, nếu phần tử ở giữa bằng giá trị cần tìm thì nên tìm tiếp ở phía nào?
3. Khi tìm biên phải, nên tìm tiếp ở phía nào? Chỉ cần nêu hướng; không cần viết toàn bộ quá trình tìm kiếm.

??? success "Đáp án"

    1. Phát biểu của học sinh không đúng. Việc trả về ngay khi tìm thấy một số 2 chỉ đảm bảo rằng đã tìm thấy một lần xuất hiện nào đó của 2, chứ không đảm bảo đó là lần xuất hiện ngoài cùng bên trái hoặc bên phải.
        Trong trường hợp này, biên trái là chỉ số 1 và biên phải là chỉ số 3.

    2. Khi tìm biên trái, hãy tiếp tục tìm ở bên trái ngay cả khi phần tử ở giữa bằng 2.
        Ví dụ, với một khoảng đóng, đặt `j = m - 1`.

    3. Khi tìm biên phải, hãy tiếp tục tìm ở bên phải sau khi phần tử ở giữa bằng 2.
        Ví dụ, đặt `i = m + 1`.

### Chọn phương pháp tìm kiếm cho các loại dữ liệu khác nhau

Với mỗi tình huống dưới đây, hãy chọn một phương pháp phù hợp trong số "tìm kiếm tuyến tính", "tìm kiếm nhị phân" và "bảng băm", rồi giải thích lý do:

<!-- numbered-subquestions -->

1. Lặp lại việc tìm kiếm trong số $10^7$ số nguyên đã được sắp xếp và không bao giờ thay đổi, mà không xây dựng thêm cấu trúc dữ liệu nào.
2. Lặp lại việc kiểm tra xem một khóa có tồn tại trong một tập hợp thường xuyên có thao tác chèn và xóa hay không. Tập hợp không cần duy trì thứ tự sắp xếp và không cần tìm kiếm theo phạm vi.
3. Tìm kiếm một giá trị trong mảng chưa sắp xếp chỉ một lần.

??? success "Đáp án"

    1. Tìm kiếm nhị phân: dữ liệu đã được sắp xếp và ở trạng thái tĩnh, nên việc tìm kiếm mất $O(\log n)$ thời gian mà không cần thêm không gian.
    2. Bảng băm: khi hàm băm phân phối các khóa tương đối đồng đều giữa các bucket, thao tác chèn, xóa và tra cứu theo khóa đều mất trung bình $O(1)$ thời gian.
    3. Quét trực tiếp từ đầu đến cuối. Khi chỉ tìm kiếm một lần, việc sắp xếp mảng hoặc xây dựng bảng băm vẫn yêu cầu xử lý toàn bộ mảng trước,
        nên không phương pháp nào làm giảm tổng khối lượng công việc cho tác vụ đơn lẻ này.

        Lựa chọn phụ thuộc vào việc dữ liệu có được sắp xếp hay không, có cho phép xây dựng thêm cấu trúc hay không, cần thực hiện bao nhiêu lần tìm kiếm và cần hỗ trợ những thao tác nào.

## Bài tập lập trình

### Tìm kiếm nhị phân trong mảng đã sắp xếp

Cho một mảng số nguyên `nums` theo thứ tự tăng nghiêm ngặt và một giá trị cần tìm `target`, hãy sử dụng tìm kiếm nhị phân để tìm `target`. Nếu tồn tại, hãy trả về chỉ số của nó trong mảng; nếu không, trả về -1.

??? tip "Gợi ý"

    1. Khoảng ban đầu là left = 0 và right = n - 1; khoảng này không rỗng khi left <= right
    2. Tính điểm giữa bằng mid = left + (right - left) // 2
    3. Nếu `nums[mid]` nhỏ hơn `target`, hãy di chuyển biên trái đến `mid + 1`; nếu `nums[mid]` lớn hơn `target`, hãy di chuyển biên phải đến `mid - 1`; nếu chúng bằng nhau, trả về ngay

[LeetCode](https://leetcode.com/problems/binary-search/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }

### Vị trí chèn trong mảng đã sắp xếp

Cho một mảng số nguyên `nums` theo thứ tự tăng nghiêm ngặt và một giá trị cần tìm `target`.

Trả về chỉ số của `target` nếu nó đã có trong mảng. Nếu không, trả về vị trí chèn mà tại đó có thể chèn `target` mà vẫn giữ cho mảng theo thứ tự tăng nghiêm ngặt.
Vị trí chèn có thể là 0 hoặc bằng độ dài của mảng. Hãy sử dụng tìm kiếm nhị phân.

??? tip "Gợi ý"

    1. Kết quả có thể là 0 hoặc độ dài mảng n
    2. Với một khoảng đóng, nếu `nums[mid]` lớn hơn hoặc bằng `target`, hãy đặt `right = mid - 1` và tiếp tục kiểm tra xa hơn về bên trái; nếu không, hãy đặt `left = mid + 1`
    3. Khi vòng lặp kết thúc, left là vị trí chèn

[LeetCode](https://leetcode.com/problems/search-insert-position/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }