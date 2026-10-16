# Sắp xếp nổi bọt

<u>Sắp xếp nổi bọt</u> sắp xếp một mảng bằng cách liên tục so sánh và hoán đổi các phần tử liền kề. Quá trình này giống như những bong bóng nổi từ dưới lên trên, nên được gọi là sắp xếp nổi bọt.

Như trong hình bên dưới, quá trình nổi bọt có thể được mô phỏng bằng cách hoán đổi các phần tử: bắt đầu từ đầu bên trái của mảng và duyệt sang phải, so sánh từng cặp phần tử liền kề; nếu "phần tử bên trái > phần tử bên phải", hãy hoán đổi chúng. Sau khi duyệt xong, phần tử lớn nhất sẽ được đưa đến cuối cùng bên phải của mảng.

=== "<1>"
    ![Mô phỏng sắp xếp nổi bọt bằng cách hoán đổi các phần tử](bubble_sort.assets/bubble_operation_step1.png)

=== "<2>"
    ![bubble_operation_step2](bubble_sort.assets/bubble_operation_step2.png)

=== "<3>"
    ![bubble_operation_step3](bubble_sort.assets/bubble_operation_step3.png)

=== "<4>"
    ![bubble_operation_step4](bubble_sort.assets/bubble_operation_step4.png)

=== "<5>"
    ![bubble_operation_step5](bubble_sort.assets/bubble_operation_step5.png)

=== "<6>"
    ![bubble_operation_step6](bubble_sort.assets/bubble_operation_step6.png)

=== "<7>"
    ![bubble_operation_step7](bubble_sort.assets/bubble_operation_step7.png)

## Quy trình thuật toán

Giả sử mảng có độ dài $n$. Các bước của thuật toán sắp xếp nổi bọt được trình bày trong hình bên dưới.

1. Trước tiên, thực hiện quá trình "nổi bọt" trên $n$ phần tử, **hoán đổi phần tử lớn nhất của mảng đến đúng vị trí của nó**.
2. Tiếp theo, thực hiện quá trình "nổi bọt" trên $n - 1$ phần tử còn lại, **hoán đổi phần tử lớn thứ hai đến đúng vị trí của nó**.
3. Cứ tiếp tục như vậy. Sau $n - 1$ lượt "nổi bọt", **$n - 1$ phần tử lớn nhất đều đã được hoán đổi đến đúng vị trí của chúng**.
4. Phần tử duy nhất còn lại chắc chắn là phần tử nhỏ nhất và không cần sắp xếp, do đó quá trình sắp xếp mảng hoàn tất.

![Quy trình sắp xếp nổi bọt](bubble_sort.assets/bubble_sort_overview.png)

Mã ví dụ như sau:

```src
[file]{bubble_sort}-[class]{}-[func]{bubble_sort}
```

## Tối ưu hóa hiệu suất

Ta có thể nhận thấy rằng nếu không có phép hoán đổi nào xảy ra trong một lượt "nổi bọt", mảng đã được sắp xếp và thuật toán có thể trả về ngay lập tức. Do đó, ta có thể thêm một flag `flag` để phát hiện tình huống này và kết thúc ngay khi nó xảy ra.

Sau khi tối ưu hóa, độ phức tạp thời gian trong trường hợp xấu nhất và trường hợp trung bình của thuật toán sắp xếp nổi bọt vẫn là $O(n^2)$; tuy nhiên, khi mảng đầu vào đã được sắp xếp, độ phức tạp thời gian trong trường hợp tốt nhất sẽ trở thành $O(n)$.

```src
[file]{bubble_sort}-[class]{}-[func]{bubble_sort_with_flag}
```

## Đặc điểm của thuật toán

- **Độ phức tạp thời gian là $O(n^2)$; thích nghi**: Trong các lượt "nổi bọt" liên tiếp, phần mảng được duyệt có độ dài lần lượt là $n - 1$, $n - 2$, $\dots$, $2$, $1$, với tổng là $(n - 1) n / 2$. Sau khi áp dụng tối ưu hóa `flag`, độ phức tạp thời gian trong trường hợp tốt nhất có thể đạt $O(n)$.
- **Độ phức tạp không gian là $O(1)$, sắp xếp tại chỗ**: Các con trỏ $i$ và $j$ sử dụng một lượng không gian bổ sung không đổi.
- **Sắp xếp ổn định**: Các phần tử bằng nhau không được hoán đổi trong quá trình "nổi bọt".