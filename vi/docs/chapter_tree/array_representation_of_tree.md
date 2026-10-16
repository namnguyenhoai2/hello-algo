# Biểu diễn cây nhị phân bằng mảng

Trong biểu diễn bằng danh sách liên kết, đơn vị lưu trữ của cây nhị phân là một nút `TreeNode`, và các nút được kết nối bằng con trỏ. Phần trước đã giới thiệu các thao tác cơ bản trên cây nhị phân trong biểu diễn này.

Vậy chúng ta có thể sử dụng một mảng để biểu diễn cây nhị phân không? Câu trả lời là có.

## Biểu diễn cây nhị phân hoàn hảo

Trước tiên, hãy phân tích một trường hợp đơn giản. Với một cây nhị phân hoàn hảo, chúng ta lưu trữ tất cả các nút trong một mảng theo thứ tự duyệt theo từng mức, trong đó mỗi nút tương ứng với một chỉ số mảng duy nhất.

Dựa trên đặc điểm của phép duyệt theo từng mức, chúng ta có thể suy ra một "công thức ánh xạ" giữa chỉ số của nút cha và chỉ số của các nút con: **Nếu chỉ số của một nút là $i$, thì chỉ số của nút con trái là $2i + 1$ và chỉ số của nút con phải là $2i + 2$**. Hình dưới đây minh họa mối quan hệ ánh xạ giữa các chỉ số nút khác nhau.

![Biểu diễn cây nhị phân hoàn hảo bằng mảng](array_representation_of_tree.assets/array_representation_binary_tree.png)

**Công thức ánh xạ đóng vai trò tương tự như các tham chiếu nút (con trỏ) trong danh sách liên kết**. Với bất kỳ nút nào trong mảng, chúng ta có thể truy cập nút con trái (phải) của nó bằng công thức ánh xạ.

## Biểu diễn mọi cây nhị phân

Cây nhị phân hoàn hảo là một trường hợp đặc biệt; ở các mức giữa của một cây nhị phân, thường có nhiều giá trị `None`. Vì chuỗi duyệt theo từng mức không bao gồm các giá trị `None` này, chúng ta không thể suy ra số lượng và cách phân bố các giá trị `None` chỉ dựa trên chuỗi này. **Điều này có nghĩa là nhiều cấu trúc cây nhị phân có thể tương ứng với cùng một chuỗi duyệt theo từng mức**.

Như minh họa trong hình dưới đây, với một cây nhị phân không hoàn hảo, phương pháp biểu diễn bằng mảng ở trên không thành công.

![Chuỗi duyệt theo từng mức tương ứng với nhiều khả năng cây nhị phân](array_representation_of_tree.assets/array_representation_without_empty.png)

Để giải quyết vấn đề này, **chúng ta có thể ghi rõ tất cả các giá trị `None` trong chuỗi duyệt theo từng mức**. Như minh họa trong hình dưới đây, khi thực hiện việc này, chuỗi duyệt theo từng mức có thể biểu diễn duy nhất một cây nhị phân. Mã ví dụ như sau:

=== "Python"

    ```python title=""
    # Biểu diễn cây nhị phân bằng mảng
    # Sử dụng None để biểu thị các vị trí trống
    tree = [1, 2, 3, 4, None, 6, 7, 8, 9, None, None, 12, None, None, 15]
    ```

=== "C++"

    ```cpp title=""
    /* Biểu diễn cây nhị phân bằng mảng */
    // Sử dụng giá trị số nguyên lớn nhất INT_MAX để đánh dấu các vị trí trống
    vector<int> tree = {1, 2, 3, 4, INT_MAX, 6, 7, 8, 9, INT_MAX, INT_MAX, 12, INT_MAX, INT_MAX, 15};
    ```

=== "Java"

    ```java title=""
    /* Biểu diễn cây nhị phân bằng mảng */
    // Sử dụng lớp bao Integer để có thể dùng null đánh dấu các vị trí trống
    Integer[] tree = { 1, 2, 3, 4, null, 6, 7, 8, 9, null, null, 12, null, null, 15 };
    ```

=== "C#"

    ```csharp title=""
    /* Biểu diễn cây nhị phân bằng mảng */
    // Sử dụng int có thể null (int?) để dùng null đánh dấu các vị trí trống
    int?[] tree = [1, 2, 3, 4, null, 6, 7, 8, 9, null, null, 12, null, null, 15];
    ```

=== "Go"

    ```go title=""
    /* Biểu diễn cây nhị phân bằng mảng */
    // Sử dụng slice có kiểu any, cho phép dùng nil để đánh dấu các vị trí trống
    tree := []any{1, 2, 3, 4, nil, 6, 7, 8, 9, nil, nil, 12, nil, nil, 15}
    ```

=== "Swift"

    ```swift title=""
    /* Biểu diễn cây nhị phân bằng mảng */
    // Sử dụng Int tùy chọn (Int?) để dùng nil đánh dấu các vị trí trống
    let tree: [Int?] = [1, 2, 3, 4, nil, 6, 7, 8, 9, nil, nil, 12, nil, nil, 15]
    ```

=== "JS"

    ```javascript title=""
    /* Biểu diễn cây nhị phân bằng mảng */
    // Sử dụng null để biểu thị các vị trí trống
    let tree = [1, 2, 3, 4, null, 6, 7, 8, 9, null, null, 12, null, null, 15];
    ```

=== "TS"

    ```typescript title=""
    /* Biểu diễn cây nhị phân bằng mảng */
    // Sử dụng null để biểu thị các vị trí trống
    let tree: (number | null)[] = [1, 2, 3, 4, null, 6, 7, 8, 9, null, null, 12, null, null, 15];
    ```

=== "Dart"

    ```dart title=""
    /* Biểu diễn cây nhị phân bằng mảng */
    // Sử dụng int có thể null (int?) để dùng null đánh dấu các vị trí trống
    List<int?> tree = [1, 2, 3, 4, null, 6, 7, 8, 9, null, null, 12, null, null, 15];
    ```

=== "Rust"

    ```rust title=""
    /* Biểu diễn cây nhị phân bằng mảng */
    // Sử dụng None để đánh dấu các vị trí trống
    let tree = [Some(1), Some(2), Some(3), Some(4), None, Some(6), Some(7), Some(8), Some(9), None, None, Some(12), None, None, Some(15)];
    ```

=== "C"

    ```c title=""
    /* Biểu diễn cây nhị phân bằng mảng */
    // Sử dụng giá trị int lớn nhất để đánh dấu các vị trí trống, do đó giá trị nút không được là INT_MAX
    int tree[] = {1, 2, 3, 4, INT_MAX, 6, 7, 8, 9, INT_MAX, INT_MAX, 12, INT_MAX, INT_MAX, 15};
    ```

=== "Kotlin"

    ```kotlin title=""
    /* Biểu diễn cây nhị phân bằng mảng */
    // Sử dụng null để biểu thị các vị trí trống
    val tree = arrayOf( 1, 2, 3, 4, null, 6, 7, 8, 9, null, null, 12, null, null, 15 )
    ```

=== "Ruby"

    ```ruby title=""
    ### Biểu diễn cây nhị phân bằng mảng ###
    # Sử dụng nil để biểu thị các vị trí trống
    tree = [1, 2, 3, 4, nil, 6, 7, 8, 9, nil, nil, 12, nil, nil, 15]
    ```

![Biểu diễn cây nhị phân bất kỳ bằng mảng](array_representation_of_tree.assets/array_representation_with_empty.png)

Cần lưu ý rằng **cây nhị phân đầy đủ đặc biệt phù hợp với biểu diễn bằng mảng**. Nhắc lại định nghĩa về cây nhị phân đầy đủ, `None` chỉ xuất hiện ở mức dưới cùng và về phía bên phải, **có nghĩa là tất cả các giá trị `None` phải xuất hiện ở cuối chuỗi duyệt theo từng mức**.

Điều này có nghĩa là khi sử dụng mảng để biểu diễn cây nhị phân đầy đủ, chúng ta có thể bỏ qua việc lưu trữ tất cả các giá trị `None`, rất thuận tiện. Hình dưới đây đưa ra một ví dụ.

![Biểu diễn cây nhị phân đầy đủ bằng mảng](array_representation_of_tree.assets/array_representation_complete_binary_tree.png)

Đoạn mã sau triển khai một cây nhị phân bằng biểu diễn mảng, bao gồm các thao tác sau:

- Với một nút, lấy giá trị, nút con trái (phải) và nút cha của nó.
- Lấy các chuỗi duyệt theo thứ tự trước, thứ tự giữa, thứ tự sau và theo từng mức.

```src
[file]{array_binary_tree}-[class]{array_binary_tree}-[func]{}
```

## Ưu điểm và hạn chế

Biểu diễn cây nhị phân bằng mảng có các ưu điểm sau:

- Mảng được lưu trữ trong vùng nhớ liên tục, thân thiện với cache, cho phép truy cập và duyệt nhanh hơn.
- Không cần lưu trữ con trỏ, giúp tiết kiệm không gian.
- Cho phép truy cập ngẫu nhiên đến các nút.

Tuy nhiên, biểu diễn bằng mảng cũng có một số hạn chế:

- Việc lưu trữ mảng yêu cầu vùng nhớ liên tục, nên không phù hợp để lưu trữ các cây có lượng dữ liệu lớn.
- Việc thêm hoặc xóa nút yêu cầu các thao tác chèn và xóa phần tử trong mảng, có hiệu suất thấp hơn.
- Khi cây nhị phân có nhiều giá trị `None`, tỷ lệ dữ liệu nút thực sự chứa trong mảng thấp, dẫn đến hiệu quả sử dụng không gian thấp hơn.