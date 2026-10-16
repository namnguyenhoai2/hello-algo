# Bài tập

## Ôn tập khái niệm

### Một vài vòng đầu của Selection Sort và Bubble Sort

Cho mảng `[4, 2, 5, 1, 3]`, hãy sắp xếp mảng theo thứ tự tăng dần trong cả hai phần dưới đây.

<!-- numbered-subquestions -->

1. Mô phỏng hai vòng đầu tiên của selection sort. Viết mảng sau mỗi vòng và xác định những vị trí nào hiện đã được cố định.
2. Mô phỏng vòng đầu tiên của bubble sort. Viết mảng kết quả và số lần hoán đổi, đồng thời xác định vị trí nào hiện đã được cố định.

??? success "Đáp án"

    1. Hai vòng đầu tiên là:

        | Vòng | Mảng | Giải thích |
        | --- | --- | --- |
        | 1 | `[1, 2, 5, 4, 3]` | Phần tử nhỏ nhất, 1, được hoán đổi với phần tử đầu tiên |
        | 2 | `[1, 2, 5, 4, 3]` | Giá trị 2 đã ở tại chỉ số 1, nên không cần hoán đổi |

        Hai vị trí đầu tiên hiện đã được cố định. Các vòng sau chỉ cần tìm phần tử nhỏ nhất trong `[5, 4, 3]`.

    2. So sánh các phần tử liền kề theo thứ tự: hoán đổi 4 và 2; không hoán đổi 4 và 5; hoán đổi 5 và 1; sau đó hoán đổi 5 và 3.
        Kết quả là `[2, 4, 1, 3, 5]`, sau 3 lần hoán đổi. Phần tử lớn nhất, 5, đã được đưa về cuối mảng, nên vị trí cuối cùng hiện đã được cố định.

### Các phần tử bằng nhau có thể thay đổi thứ tự tương đối không?

Trong mảng $[2_a, 2_b, 1]$, $2_a$ và $2_b$ có giá trị bằng nhau, nhưng chỉ số dưới của chúng đánh dấu thứ tự ban đầu.

<!-- numbered-subquestions -->

1. Viết mảng sau vòng đầu tiên của selection sort. Thứ tự tương đối của $2_a$ và $2_b$ có thay đổi không?
2. Viết mảng sau vòng đầu tiên của bubble sort. Thứ tự tương đối của $2_a$ và $2_b$ có thay đổi không?
3. Dựa trên hai câu hỏi đầu, hãy giải thích hai thuật toán sắp xếp khác nhau như thế nào trong việc bảo toàn thứ tự ban đầu của các phần tử bằng nhau.

??? success "Đáp án"

    1. Trong vòng đầu tiên, selection sort chọn phần tử nhỏ nhất, 1, rồi hoán đổi phần tử đó với phần tử đầu tiên, $2_a$, tạo ra
        $[1, 2_b, 2_a]$. Thứ tự tương đối đã thay đổi vì $2_a$ đã di chuyển ra sau $2_b$.

    2. Bubble sort trước tiên so sánh $2_a$ và $2_b$. Vì chúng bằng nhau nên không hoán đổi chúng. Sau đó, nó so sánh $2_b$ và 1 rồi hoán đổi chúng,
        tạo ra $[2_a, 1, 2_b]$ sau vòng đầu tiên. $2_a$ vẫn đứng trước $2_b$, nên thứ tự tương đối của chúng không thay đổi.

    3. Trong ví dụ này, selection sort thay đổi thứ tự ban đầu của các phần tử bằng nhau. Bubble sort chỉ hoán đổi các phần tử liền kề khi phần tử bên trái lớn hơn phần tử bên phải.
        Các phần tử bằng nhau không bị hoán đổi, nên thứ tự tương đối ban đầu của chúng được bảo toàn.

### So sánh Counting Sort và Radix Sort

Một trường học cần sắp xếp nhiều mã số học sinh, mỗi mã có đúng 8 chữ số. Hãy trả lời các câu hỏi sau:

<!-- numbered-subquestions -->

1. Radix sort cần bao nhiêu vòng khi bắt đầu từ chữ số có trọng số nhỏ nhất?
2. Nếu các mã số học sinh được xử lý trực tiếp dưới dạng số nguyên bằng counting sort, tại sao mảng đếm cần nhiều phần tử không bao giờ được sử dụng?
3. Dựa trên hai câu hỏi đầu, bạn sẽ chọn counting sort hay radix sort để sắp xếp nhiều mã số học sinh có độ dài cố định 8 chữ số? Tại sao?

??? success "Đáp án"

    1. Một mã số học sinh có 8 chữ số, nên cần 8 vòng, từ chữ số có trọng số nhỏ nhất đến chữ số có trọng số lớn nhất. Mỗi vòng chỉ nhóm các giá trị từ 0–9.

    2. Cách đếm trực tiếp sẽ yêu cầu một phần tử cho mọi giá trị 8 chữ số có thể có, nhưng chỉ một phần nhỏ trong số đó thực sự được cấp cho học sinh.
        Phần lớn các phần tử trong mảng đếm sẽ vẫn bằng 0.

    3. Radix sort là lựa chọn tốt hơn. Nó tận dụng việc độ dài là cố định và mỗi chữ số chỉ có 10 giá trị có thể có, nên chỉ cần 8 vòng nhóm ổn định.
        Counting sort, nếu sử dụng toàn bộ mã số 8 chữ số làm chỉ số số nguyên, sẽ cần các phần tử trong mảng đếm cho nhiều giá trị không xuất hiện.

## Bài tập lập trình

### Sắp xếp một mảng bằng Merge Sort

Cho mảng số nguyên `nums`, hãy tự triển khai merge sort, sắp xếp các phần tử theo thứ tự không giảm và trả về kết quả. Không gọi hàm sắp xếp tích hợp sẵn của ngôn ngữ.

??? tip "Gợi ý"

    1. Một khoảng có độ dài tối đa 1 vốn đã được sắp xếp
    2. Chia khoảng thành hai nửa tại điểm giữa và đệ quy sắp xếp cả hai nửa
    3. Sử dụng hai con trỏ để trộn hai nửa đã sắp xếp, sau đó ghi kết quả trở lại mảng ban đầu

[LeetCode](https://leetcode.com/problems/sort-an-array/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }

### Sắp xếp một mảng số nguyên bằng Counting Sort

Cho mảng số nguyên `nums` và số nguyên không âm $K$. Mọi phần tử trong mảng đều nằm trong khoảng từ $0$ đến $K$.

Hãy triển khai counting sort, ghi kết quả trở lại `nums` theo thứ tự không giảm và trả về `nums`.
Không xác định thứ tự bằng cách so sánh các phần tử và không gọi hàm sắp xếp tích hợp sẵn của ngôn ngữ.

??? tip "Gợi ý"

    1. Vì mọi phần tử đều nằm trong khoảng từ 0 đến K, hãy sử dụng trực tiếp giá trị của mỗi phần tử làm chỉ số trong mảng đếm
    2. Duyệt nums một lần và tăng bộ đếm tại vị trí tương ứng
    3. Sau đó, duyệt mảng đếm từ 0 đến K; nếu giá trị x xuất hiện một số lần nhất định, hãy ghi x vào nums trong số lần liên tiếp tương ứng