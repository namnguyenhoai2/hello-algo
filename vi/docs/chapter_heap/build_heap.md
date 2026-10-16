# Thao tác xây dựng heap

Trong một số trường hợp, chúng ta muốn xây dựng một heap bằng cách sử dụng tất cả phần tử của một danh sách, và quá trình này được gọi là “thao tác xây dựng heap”.

## Triển khai bằng cách chèn phần tử

Trước tiên, chúng ta tạo một heap rỗng, sau đó duyệt qua danh sách và lần lượt thực hiện “thao tác chèn phần tử” trên từng phần tử. Điều này có nghĩa là nối phần tử vào cuối heap, rồi thực hiện heapify “từ dưới lên trên” trên phần tử đó.

Mỗi khi một phần tử được chèn vào heap, độ dài của heap tăng thêm một. Vì các node được thêm vào cây nhị phân lần lượt từ trên xuống dưới, heap được xây dựng “từ trên xuống dưới”.

Với $n$ phần tử, thao tác chèn mỗi phần tử mất thời gian $O(\log{n})$, vì vậy độ phức tạp thời gian của phương pháp xây dựng heap này là $O(n \log n)$.

## Triển khai thông qua duyệt heapify

Trên thực tế, chúng ta có thể triển khai một phương pháp xây dựng heap hiệu quả hơn qua hai bước.

1. Thêm tất cả phần tử của danh sách vào heap theo nguyên trạng; lúc này, tính chất heap vẫn chưa được đảm bảo.
2. Duyệt heap theo thứ tự ngược (ngược với phép duyệt theo level-order), lần lượt thực hiện “heapify từ trên xuống dưới” trên từng node không phải lá.

**Sau khi heapify một node, cây con có gốc là node đó sẽ trở thành một sub-heap hợp lệ**. Vì chúng ta duyệt theo thứ tự ngược, heap được xây dựng “từ dưới lên trên”.

Lý do chọn cách duyệt theo thứ tự ngược là vì nó đảm bảo các cây con bên dưới node hiện tại đã là những sub-heap hợp lệ, nhờ đó việc heapify node hiện tại sẽ có hiệu quả.

Cần lưu ý rằng **vì các node lá không có node con, chúng vốn đã là các sub-heap hợp lệ và không cần heapify**. Như trong đoạn code dưới đây, node không phải lá cuối cùng là node cha của node cuối cùng; chúng ta bắt đầu từ node đó và thực hiện heapify trong khi duyệt theo thứ tự ngược:

```src
[file]{my_heap}-[class]{max_heap}-[func]{__init__}
```

## Phân tích độ phức tạp

Tiếp theo, hãy thử suy ra độ phức tạp thời gian của phương pháp xây dựng heap thứ hai này.

- Giả sử cây nhị phân đầy đủ có $n$ node, khi đó số node lá là $(n + 1) / 2$, trong đó $/$ là phép chia lấy phần nguyên. Do đó, số node cần heapify là $n / 2$.
- Trong quá trình heapify từ trên xuống dưới, mỗi node có thể đi xuống nhiều nhất đến một node lá, vì vậy số lần lặp tối đa là chiều cao của cây nhị phân, $\log n$.

Nhân hai giá trị này với nhau, ta được độ phức tạp thời gian $O(n \log n)$ cho quá trình xây dựng heap. **Tuy nhiên, ước tính này không chính xác vì nó không tính đến đặc điểm cây nhị phân có nhiều node ở các level thấp hơn đáng kể so với các level cao hơn**.

Hãy thực hiện một phép tính chính xác hơn. Để đơn giản hóa việc phân tích, giả sử đây là một “cây nhị phân hoàn hảo” có $n$ node và chiều cao $h$; giả định này không ảnh hưởng đến tính đúng đắn của kết quả.

![Số node ở mỗi level của cây nhị phân hoàn hảo](build_heap.assets/heapify_operations_count.png)

Như thể hiện trong hình trên, số lần lặp tối đa cho thao tác “heapify từ trên xuống dưới” của một node bằng khoảng cách từ node đó đến một node lá, chính là chiều cao của node đó. Do đó, chúng ta có thể tính tổng “số node × chiều cao của node” ở mỗi level để **thu được tổng số lần lặp heapify của tất cả node**.

$$
T(h) = 2^0h + 2^1(h-1) + 2^2(h-2) + \dots + 2^{(h-1)}\times1
$$

Để đơn giản hóa biểu thức trên, cần sử dụng một số phép biến đổi dãy số ở cấp trung học. Trước tiên, nhân $T(h)$ với $2$ để được:

$$
\begin{aligned}
T(h) & = 2^0h + 2^1(h-1) + 2^2(h-2) + \dots + 2^{h-1}\times1 \newline
2 T(h) & = 2^1h + 2^2(h-1) + 2^3(h-2) + \dots + 2^{h}\times1 \newline
\end{aligned}
$$

Sử dụng phép trừ các tổng đã dịch chuyển, lấy phương trình đầu tiên $T(h)$ trừ khỏi phương trình thứ hai $2 T(h)$, ta được:

$$
2T(h) - T(h) = T(h) = -2^0h + 2^1 + 2^2 + \dots + 2^{h-1} + 2^h
$$

Quan sát biểu thức trên, ta thấy $T(h)$ là một cấp số nhân, có thể tính trực tiếp bằng công thức tính tổng, từ đó thu được độ phức tạp thời gian:

$$
\begin{aligned}
T(h) & = 2 \frac{1 - 2^h}{1 - 2} - h \newline
& = 2^{h+1} - h - 2 \newline
& = O(2^h)
\end{aligned}
$$

Ngoài ra, một cây nhị phân hoàn hảo có chiều cao $h$ có $n = 2^{h+1} - 1$ node, vì vậy độ phức tạp là $O(2^h) = O(n)$. Phép suy ra này cho thấy **độ phức tạp thời gian của việc xây dựng heap từ một danh sách đầu vào là $O(n)$, đạt hiệu quả rất cao**.