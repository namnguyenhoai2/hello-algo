# Bài tập

## Ôn tập khái niệm

### Heap thay đổi như thế nào sau khi chèn 10?

Mảng `[9, 7, 8, 3, 5]` biểu diễn một max heap. Bây giờ hãy chèn số 10.

<!-- numbered-subquestions -->

1. Trước tiên, thêm 10 vào cuối mảng. Giá trị của nút cha của nó là bao nhiêu?
2. Bắt đầu từ nút mới, thực hiện heapify từ dưới lên và viết mảng sau mỗi lần hoán đổi.
3. Phần tử đầu của heap cuối cùng là gì? Tổng cộng có bao nhiêu lần hoán đổi?

??? success "Đáp án"

    1. Sau khi thêm 10, chỉ số của nó là 5, nên chỉ số của nút cha là
        $\lfloor(5-1)/2\rfloor=2$. Giá trị của nút cha là 8.

    2. Vì 10 lớn hơn 8, mảng sau lần hoán đổi đầu tiên là `[9, 7, 10, 3, 5, 8]`.
        Vì 10 cũng lớn hơn nút cha 9, mảng sau lần hoán đổi thứ hai là `[10, 7, 9, 3, 5, 8]`.
        Giá trị 10 hiện đã đạt đến nút gốc, nên quá trình heapify hoàn tất.

    3. Phần tử đầu cuối cùng là 10, và tổng cộng có 2 lần hoán đổi.

### Kiểm tra quan hệ cha–con trong min heap

Mảng `[1, 4, 3, 7, 6, 2]` biểu diễn một cây nhị phân hoàn chỉnh. Trong một min heap, mọi nút cha phải nhỏ hơn hoặc bằng các nút con của nó.
Với chỉ số $i$, chỉ số của nút con trái và nút con phải lần lượt là $2i+1$ và $2i+2$.

<!-- numbered-subquestions -->

1. Các nút con của chỉ số 2 có những chỉ số và giá trị nào?
2. Nút tại chỉ số 2 có giá trị 3. Nó có vi phạm quy tắc min heap với nút con của mình không? Nếu có, cần hoán đổi hai phần tử nào?
3. Dựa trên câu trả lời cho Câu hỏi 2, hãy viết mảng sau khi hoán đổi nếu quy tắc bị vi phạm; nếu không, hãy giải thích tại sao không cần hoán đổi. Cuối cùng, kiểm tra các quan hệ cha–con còn lại.

??? success "Đáp án"

    1. Nút con trái của chỉ số 2 ở chỉ số 5 và có giá trị 2. Chỉ số của nút con phải là 6, nhưng mảng có độ dài 6, nên nút con phải không tồn tại.

    2. Giá trị của nút cha là 3, lớn hơn giá trị 2 của nút con, nên vi phạm quy tắc min heap. Cần hoán đổi các phần tử tại chỉ số 2 và 5.

    3. Sau khi hoán đổi, mảng là `[1, 4, 2, 7, 6, 3]`. Kiểm tra từng quan hệ:
        `1 ≤ 4`, `1 ≤ 2`; `4 ≤ 7`, `4 ≤ 6`; và `2 ≤ 3`.
        Giờ đây mọi nút cha đều nhỏ hơn hoặc bằng các nút con của nó, nên quy tắc min heap được thỏa mãn.

### Giữ lại ba số lớn nhất bằng min heap

Để giữ lại 3 số lớn nhất từ luồng dữ liệu `[4, 1, 7, 3, 8]`, hãy duy trì một min heap chứa không quá 3 phần tử.

Trước tiên, lần lượt chèn 3 số đầu tiên vào min heap. Khi heap đã đầy, với mỗi số mới:
nếu số đó lớn hơn phần tử đầu, hãy xóa phần tử đầu và chèn số mới; nếu không, giữ nguyên heap.

Sau khi đọc mỗi số, hãy viết các số được giữ lại trong heap và phần tử đầu.
Viết các số được giữ lại dưới dạng một tập hợp; không cần ghi thứ tự của chúng trong mảng heap.

??? success "Đáp án"

    Kết quả sau khi đọc mỗi số là:

    | Số được đọc | Các số được giữ lại | Phần tử đầu |
    | --- | --- | --- |
    | 4 | `{4}` | 4 |
    | 1 | `{1, 4}` | 1 |
    | 7 | `{1, 4, 7}` | 1 |
    | 3 | `{3, 4, 7}` | 3 |
    | 8 | `{4, 7, 8}` | 4 |

    Khi heap đã đầy, phần tử đầu của nó là số nhỏ nhất trong các số hiện đang được giữ lại. Một số mới chỉ thay thế phần tử đầu khi nó lớn hơn phần tử đầu.
    Tập hợp cuối cùng `{4, 7, 8}` chứa chính xác 3 số lớn nhất.

## Bài tập lập trình

### Tìm phần tử lớn thứ K trong một mảng

Cho một mảng số nguyên `nums` và một số nguyên $k$, trong đó $1 \le k \le n$ và $n$ là độ dài của mảng, hãy trả về phần tử sẽ xuất hiện ở vị trí $k$ nếu mảng được sắp xếp từ lớn đến nhỏ.

Đếm các phần tử trùng lặp riêng biệt. Ví dụ, phần tử lớn thứ hai của `[5, 5, 2]` vẫn là 5. Sử dụng một min heap chứa không quá $k$ phần tử.

??? tip "Gợi ý"

    1. Phần tử lớn thứ k là phần tử nhỏ nhất trong k số lớn nhất
    2. Chèn từng số vào min heap và xóa giá trị nhỏ nhất bất cứ khi nào kích thước heap vượt quá k
    3. Sau khi duyệt qua mảng, heap chứa k số lớn nhất và phần tử đầu của nó là đáp án

[LeetCode](https://leetcode.com/problems/kth-largest-element-in-an-array/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }