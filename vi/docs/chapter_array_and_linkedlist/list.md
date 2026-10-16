# Danh sách

Một <u>danh sách</u> là một khái niệm cấu trúc dữ liệu trừu tượng, biểu diễn một tập hợp các phần tử có thứ tự và hỗ trợ các thao tác như truy cập, sửa đổi, chèn, xóa và duyệt phần tử mà không yêu cầu người dùng phải quan tâm đến giới hạn dung lượng. Danh sách có thể được triển khai dựa trên linked list hoặc array.

- Linked list có thể được xem tự nhiên như một danh sách: nó hỗ trợ chèn, xóa, tìm kiếm và cập nhật, đồng thời có thể tăng kích thước linh hoạt khi cần.
- Array cũng hỗ trợ chèn, xóa, tìm kiếm và cập nhật, nhưng vì có độ dài cố định nên chỉ có thể được xem là một danh sách có giới hạn dung lượng.

Khi danh sách được triển khai bằng array, **độ dài cố định khiến nó kém thực tế hơn**. Nguyên nhân là chúng ta thường không thể xác định trước lượng dữ liệu cần lưu trữ, nên khó chọn được dung lượng phù hợp. Nếu dung lượng quá nhỏ, nó có thể không đáp ứng được nhu cầu; nếu quá lớn, không gian bộ nhớ sẽ bị lãng phí.

Để giải quyết vấn đề này, chúng ta có thể sử dụng <u>dynamic array</u> để triển khai danh sách. Nó kế thừa mọi ưu điểm của array, đồng thời hỗ trợ thay đổi kích thước động trong quá trình thực thi chương trình.

Trên thực tế, **các kiểu danh sách do standard library của nhiều ngôn ngữ lập trình cung cấp được triển khai bằng dynamic array**, chẳng hạn như `list` trong Python, `ArrayList` trong Java, `vector` trong C++ và `List` trong C#. Trong phần thảo luận tiếp theo, chúng ta sẽ xem “list” và “dynamic array” là các khái niệm tương đương.

## Các thao tác phổ biến với danh sách

### Khởi tạo danh sách

Thông thường, chúng ta khởi tạo danh sách theo một trong hai cách: rỗng hoặc với các giá trị được xác định trước:

=== "Python"

    ```python title="list.py"
    # Khởi tạo danh sách
    # Không có giá trị ban đầu
    nums1: list[int] = []
    # Có giá trị ban đầu
    nums: list[int] = [1, 3, 2, 5, 4]
    ```

=== "C++"

    ```cpp title="list.cpp"
    /* Khởi tạo danh sách */
    // Lưu ý rằng vector trong C++ tương đương với nums được mô tả trong bài viết này
    // Không có giá trị ban đầu
    vector<int> nums1;
    // Có giá trị ban đầu
    vector<int> nums = { 1, 3, 2, 5, 4 };
    ```

=== "Java"

    ```java title="list.java"
    /* Khởi tạo danh sách */
    // Không có giá trị ban đầu
    List<Integer> nums1 = new ArrayList<>();
    // Có giá trị ban đầu (lưu ý rằng các phần tử của array nên sử dụng wrapper class Integer[] thay vì int[])
    Integer[] numbers = new Integer[] { 1, 3, 2, 5, 4 };
    List<Integer> nums = new ArrayList<>(Arrays.asList(numbers));
    ```

=== "C#"

    ```csharp title="list.cs"
    /* Khởi tạo danh sách */
    // Không có giá trị ban đầu
    List<int> nums1 = [];
    // Có giá trị ban đầu
    int[] numbers = [1, 3, 2, 5, 4];
    List<int> nums = [.. numbers];
    ```

=== "Go"

    ```go title="list_test.go"
    /* Khởi tạo danh sách */
    // Không có giá trị ban đầu
    nums1 := []int{}
    // Có giá trị ban đầu
    nums := []int{1, 3, 2, 5, 4}
    ```

=== "Swift"

    ```swift title="list.swift"
    /* Khởi tạo danh sách */
    // Không có giá trị ban đầu
    let nums1: [Int] = []
    // Có giá trị ban đầu
    var nums = [1, 3, 2, 5, 4]
    ```

=== "JS"

    ```javascript title="list.js"
    /* Khởi tạo danh sách */
    // Không có giá trị ban đầu
    const nums1 = [];
    // Có giá trị ban đầu
    const nums = [1, 3, 2, 5, 4];
    ```

=== "TS"

    ```typescript title="list.ts"
    /* Khởi tạo danh sách */
    // Không có giá trị ban đầu
    const nums1: number[] = [];
    // Có giá trị ban đầu
    const nums: number[] = [1, 3, 2, 5, 4];
    ```

=== "Dart"

    ```dart title="list.dart"
    /* Khởi tạo danh sách */
    // Không có giá trị ban đầu
    List<int> nums1 = [];
    // Có giá trị ban đầu
    List<int> nums = [1, 3, 2, 5, 4];
    ```

=== "Rust"

    ```rust title="list.rs"
    /* Khởi tạo danh sách */
    // Không có giá trị ban đầu
    let nums1: Vec<i32> = Vec::new();
    // Có giá trị ban đầu
    let nums: Vec<i32> = vec![1, 3, 2, 5, 4];
    ```

=== "C"

    ```c title="list.c"
    // C không cung cấp dynamic array dựng sẵn
    ```

=== "Kotlin"

    ```kotlin title="list.kt"
    /* Khởi tạo danh sách */
    // Không có giá trị ban đầu
    var nums1 = listOf<Int>()
    // Có giá trị ban đầu
    var numbers = arrayOf(1, 3, 2, 5, 4)
    var nums = numbers.toMutableList()
    ```

=== "Ruby"

    ```ruby title="list.rb"
    # Khởi tạo danh sách
    # Không có giá trị ban đầu
    nums1 = []
    # Có giá trị ban đầu
    nums = [1, 3, 2, 5, 4]
    ```

??? pythontutor "Trực quan hóa mã"

    https://pythontutor.com/render.html#code=%22%22%22Driver%20Code%22%22%22%0Aif%20__name__%20%3D%3D%20%22__main__%22%3A%0A%20%20%20%20%23%20%E5%88%9D%E5%A7%8B%E5%8C%96%E5%88%97%E8%A1%A8%0A%20%20%20%20%23%20%E6%97%A0%E5%88%9D%E5%A7%8B%E5%80%BC%0A%20%20%20%20nums1%20%3D%20%5B%5D%0A%20%20%20%20%23%20%E6%9C%89%E5%88%9D%E5%A7%8B%E5%80%BC%0A%20%20%20%20nums%20%3D%20%5B1,%203,%202,%205,%204%5D&cumulative=false&curInstr=4&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=311&rawInputLstJSON=%5B%5D&textReferences=false

### Truy cập phần tử

Vì danh sách về bản chất là một array, chúng ta có thể truy cập và cập nhật các phần tử với độ phức tạp thời gian $O(1)$, nên rất hiệu quả.

=== "Python"

    ```python title="list.py"
    # Truy cập một phần tử
    num: int = nums[1]  # Truy cập phần tử tại chỉ mục 1

    # Cập nhật một phần tử
    nums[1] = 0    # Cập nhật phần tử tại chỉ mục 1 thành 0
    ```

=== "C++"

    ```cpp title="list.cpp"
    /* Truy cập một phần tử */
    int num = nums[1];  // Truy cập phần tử tại chỉ mục 1

    /* Cập nhật một phần tử */
    nums[1] = 0;  // Cập nhật phần tử tại chỉ mục 1 thành 0
    ```

=== "Java"

    ```java title="list.java"
    /* Truy cập một phần tử */
    int num = nums.get(1);  // Truy cập phần tử tại chỉ mục 1

    /* Cập nhật một phần tử */
    nums.set(1, 0);  // Cập nhật phần tử tại chỉ mục 1 thành 0
    ```

=== "C#"

    ```csharp title="list.cs"
    /* Truy cập một phần tử */
    int num = nums[1];  // Truy cập phần tử tại chỉ mục 1

    /* Cập nhật một phần tử */
    nums[1] = 0;  // Cập nhật phần tử tại chỉ mục 1 thành 0
    ```

=== "Go"

    ```go title="list_test.go"
    /* Truy cập một phần tử */
    num := nums[1]  // Truy cập phần tử tại chỉ mục 1

    /* Cập nhật một phần tử */
    nums[1] = 0     // Cập nhật phần tử tại chỉ mục 1 thành 0
    ```

=== "Swift"

    ```swift title="list.swift"
    /* Truy cập một phần tử */
    let num = nums[1] // Truy cập phần tử tại chỉ mục 1

    /* Cập nhật một phần tử */
    nums[1] = 0 // Cập nhật phần tử tại chỉ mục 1 thành 0
    ```

=== "JS"

    ```javascript title="list.js"
    /* Truy cập một phần tử */
    const num = nums[1];  // Truy cập phần tử tại chỉ mục 1

    /* Cập nhật một phần tử */
    nums[1] = 0;  // Cập nhật phần tử tại chỉ mục 1 thành 0
    ```

=== "TS"

    ```typescript title="list.ts"
    /* Truy cập một phần tử */
    const num: number = nums[1];  // Truy cập phần tử tại chỉ mục 1

    /* Cập nhật một phần tử */
    nums[1] = 0;  // Cập nhật phần tử tại chỉ mục 1 thành 0
    ```

=== "Dart"

    ```dart title="list.dart"
    /* Truy cập một phần tử */
    int num = nums[1];  // Truy cập phần tử tại chỉ mục 1

    /* Cập nhật một phần tử */
    nums[1] = 0;  // Cập nhật phần tử tại chỉ mục 1 thành 0
    ```

=== "Rust"

    ```rust title="list.rs"
    /* Truy cập một phần tử */
    let num: i32 = nums[1];  // Truy cập phần tử tại chỉ mục 1
    /* Cập nhật một phần tử */
    nums[1] = 0;             // Cập nhật phần tử tại chỉ mục 1 thành 0
    ```

=== "C"

    ```c title="list.c"
    // C không cung cấp dynamic array dựng sẵn
    ```

=== "Kotlin"

    ```kotlin title="list.kt"
    /* Truy cập một phần tử */
    val num = nums[1]       // Truy cập phần tử tại chỉ mục 1
    /* Cập nhật một phần tử */
    nums[1] = 0             // Cập nhật phần tử tại chỉ mục 1 thành 0
    ```

=== "Ruby"

    ```ruby title="list.rb"
    # Truy cập một phần tử
    num = nums[1] # Truy cập phần tử tại chỉ mục 1
    # Cập nhật một phần tử
    nums[1] = 0 # Cập nhật phần tử tại chỉ mục 1 thành 0
    ```

??? pythontutor "Trực quan hóa mã"

    https://pythontutor.com/render.html#code=%22%22%22Driver%20Code%22%22%22%0Aif%20__name__%20%3D%3D%20%22__main__%22%3A%0A%20%20%20%20%23%20%E5%88%9D%E5%A7%8B%E5%8C%96%E5%88%97%E8%A1%A8%0A%20%20%20%20nums%20%3D%20%5B1,%203,%202,%205,%204%5D%0A%0A%20%20%20%20%23%20%E8%AE%BF%E9%97%AE%E5%85%83%E7%B4%A0%0A%20%20%20%20num%20%3D%20nums%5B1%5D%20%20%23%20%E8%AE%BF%E9%97%AE%E7%B4%A2%E5%BC%95%201%20%E5%A4%84%E7%9A%84%E5%85%83%E7%B4%A0%0A%0A%20%20%20%20%23%20%E6%9B%B4%E6%96%B0%E5%85%83%E7%B4%A0%0A%20%20%20%20nums%5B1%5D%20%3D%200%20%20%20%20%23%20%E5%B0%86%E7%B4%A2%E5%BC%95%201%20%E5%A4%84%E7%9A%84%E5%85%83%E7%B4%A0%E6%9B%B4%E6%96%B0%E4%B8%BA%200&cumulative=false&curInstr=3&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=311&rawInputLstJSON=%5B%5D&textReferences=false

### Chèn và xóa phần tử

So với array, danh sách có thể tự do thêm và xóa phần tử. Việc thêm một phần tử vào cuối danh sách có độ phức tạp thời gian là $O(1)$, nhưng việc chèn và xóa phần tử vẫn có hiệu suất tương đương array, với độ phức tạp thời gian là $O(n)$.

=== "Python"

    ```python title="list.py"
    # Xóa toàn bộ danh sách
    nums.clear()

    # Thêm phần tử vào cuối
    nums.append(1)
    nums.append(3)
    nums.append(2)
    nums.append(5)
    nums.append(4)

    # Chèn một phần tử vào giữa
    nums.insert(3, 6)  # Chèn số 6 tại chỉ mục 3

    # Xóa một phần tử
    nums.pop(3)        # Xóa phần tử tại chỉ mục 3
    ```

=== "C++"

    ```cpp title="list.cpp"
    /* Xóa toàn bộ danh sách */
    nums.clear();

    /* Thêm phần tử vào cuối */
    nums.push_back(1);
    nums.push_back(3);
    nums.push_back(2);
    nums.push_back(5);
    nums.push_back(4);

    /* Chèn một phần tử vào giữa */
    nums.insert(nums.begin() + 3, 6);  // Chèn số 6 tại chỉ mục 3

    /* Xóa một phần tử */
    nums.erase(nums.begin() + 3);      // Xóa phần tử tại chỉ mục 3
    ```

=== "Java"

    ```java title="list.java"
    /* Xóa toàn bộ danh sách */
    nums.clear();

    /* Thêm phần tử vào cuối */
    nums.add(1);
    nums.add(3);
    nums.add(2);
    nums.add(5);
    nums.add(4);

    /* Chèn một phần tử vào giữa */
    nums.add(3, 6);  // Chèn số 6 tại chỉ mục 3

    /* Xóa một phần tử */
    nums.remove(3);  // Xóa phần tử tại chỉ mục 3
    ```

=== "C#"

    ```csharp title="list.cs"
    /* Xóa toàn bộ danh sách */
    nums.Clear();

    /* Thêm phần tử vào cuối */
    nums.Add(1);
    nums.Add(3);
    nums.Add(2);
    nums.Add(5);
    nums.Add(4);

    /* Chèn một phần tử vào giữa */
    nums.Insert(3, 6);  // Chèn số 6 tại chỉ mục 3

    /* Xóa một phần tử */
    nums.RemoveAt(3);  // Xóa phần tử tại chỉ mục 3
    ```

=== "Go"

    ```go title="list_test.go"
    /* Xóa danh sách */
    nums = nil

    /* Thêm các phần tử vào cuối */
    nums = append(nums, 1)
    nums = append(nums, 3)
    nums = append(nums, 2)
    nums = append(nums, 5)
    nums = append(nums, 4)

    /* Chèn một phần tử vào giữa */
    nums = append(nums[:3], append([]int{6}, nums[3:]...)...) // Chèn số 6 tại chỉ mục 3

    /* Xóa một phần tử */
    nums = append(nums[:3], nums[4:]...) // Xóa phần tử tại chỉ mục 3
    ```

=== "Swift"

    ```swift title="list.swift"
    /* Xóa danh sách */
    nums.removeAll()

    /* Thêm các phần tử vào cuối */
    nums.append(1)
    nums.append(3)
    nums.append(2)
    nums.append(5)
    nums.append(4)

    /* Chèn một phần tử vào giữa */
    nums.insert(6, at: 3) // Chèn số 6 tại chỉ mục 3

    /* Xóa một phần tử */
    nums.remove(at: 3) // Xóa phần tử tại chỉ mục 3
    ```

=== "JS"

    ```javascript title="list.js"
    /* Xóa danh sách */
    nums.length = 0;

    /* Thêm các phần tử vào cuối */
    nums.push(1);
    nums.push(3);
    nums.push(2);
    nums.push(5);
    nums.push(4);

    /* Chèn một phần tử vào giữa */
    nums.splice(3, 0, 6); // Chèn số 6 tại chỉ mục 3

    /* Xóa một phần tử */
    nums.splice(3, 1);  // Xóa phần tử tại chỉ mục 3
    ```

=== "TS"

    ```typescript title="list.ts"
    /* Xóa danh sách */
    nums.length = 0;

    /* Thêm các phần tử vào cuối */
    nums.push(1);
    nums.push(3);
    nums.push(2);
    nums.push(5);
    nums.push(4);

    /* Chèn một phần tử vào giữa */
    nums.splice(3, 0, 6); // Chèn số 6 tại chỉ mục 3

    /* Xóa một phần tử */
    nums.splice(3, 1);  // Xóa phần tử tại chỉ mục 3
    ```

=== "Dart"

    ```dart title="list.dart"
    /* Xóa danh sách */
    nums.clear();

    /* Thêm các phần tử vào cuối */
    nums.add(1);
    nums.add(3);
    nums.add(2);
    nums.add(5);
    nums.add(4);

    /* Chèn một phần tử vào giữa */
    nums.insert(3, 6); // Chèn số 6 tại chỉ mục 3

    /* Xóa một phần tử */
    nums.removeAt(3); // Xóa phần tử tại chỉ mục 3
    ```

=== "Rust"

    ```rust title="list.rs"
    /* Xóa danh sách */
    nums.clear();

    /* Thêm các phần tử vào cuối */
    nums.push(1);
    nums.push(3);
    nums.push(2);
    nums.push(5);
    nums.push(4);

    /* Chèn một phần tử vào giữa */
    nums.insert(3, 6);  // Chèn số 6 tại chỉ mục 3

    /* Xóa một phần tử */
    nums.remove(3);    // Xóa phần tử tại chỉ mục 3
    ```

=== "C"

    ```c title="list.c"
    // C không cung cấp mảng động tích hợp sẵn
    ```

=== "Kotlin"

    ```kotlin title="list.kt"
    /* Xóa danh sách */
    nums.clear();

    /* Thêm các phần tử vào cuối */
    nums.add(1);
    nums.add(3);
    nums.add(2);
    nums.add(5);
    nums.add(4);

    /* Chèn một phần tử vào giữa */
    nums.add(3, 6);  // Chèn số 6 tại chỉ mục 3

    /* Xóa một phần tử */
    nums.remove(3);  // Xóa phần tử tại chỉ mục 3
    ```

=== "Ruby"

    ```ruby title="list.rb"
    # Xóa danh sách
    nums.clear

    # Thêm các phần tử vào cuối
    nums << 1
    nums << 3
    nums << 2
    nums << 5
    nums << 4

    # Chèn một phần tử vào giữa
    nums.insert(3, 6) # Chèn số 6 tại chỉ mục 3

    # Xóa một phần tử
    nums.delete_at(3) # Xóa phần tử tại chỉ mục 3
    ```

??? pythontutor "Code Visualization"

    https://pythontutor.com/render.html#code=%22%22%22Driver%20Code%22%22%22%0Aif%20__name__%20%3D%3D%20%22__main__%22%3A%0A%20%20%20%20%23%20%E6%9C%89%E5%88%9D%E5%A7%8B%E5%80%BC%0A%20%20%20%20nums%20%3D%20%5B1,%203,%202,%205,%204%5D%0A%20%20%20%20%0A%20%20%20%20%23%20%E6%B8%85%E7%A9%BA%E5%88%97%E8%A1%A8%0A%20%20%20%20nums.clear%28%29%0A%20%20%20%20%0A%20%20%20%20%23%20%E5%9C%A8%E5%B0%BE%E9%83%A8%E6%B7%BB%E5%8A%A0%E5%85%83%E7%B4%A0%0A%20%20%20%20nums.append%281%29%0A%20%20%20%20nums.append%283%29%0A%20%20%20%20nums.append%282%29%0A%20%20%20%20nums.append%285%29%0A%20%20%20%20nums.append%284%29%0A%20%20%20%20%0A%20%20%20%20%23%20%E5%9C%A8%E4%B8%AD%E9%97%B4%E6%8F%92%E5%85%A5%E5%85%83%E7%B4%A0%0A%20%20%20%20nums.insert%283,%206%29%20%20%23%20%E5%9C%A8%E7%B4%A2%E5%BC%95%203%20%E5%A4%84%E6%8F%92%E5%85%A5%E6%95%B0%E5%AD%97%206%0A%20%20%20%20%0A%20%20%20%20%23%20%E5%88%A0%E9%99%A4%E5%85%83%E7%B4%A0%0A%20%20%20%20nums.pop%283%29%20%20%20%20%20%20%20%20%23%20%E5%88%A0%E9%99%A4%E7%B4%A2%E5%BC%95%203%20%E5%A4%84%E7%9A%84%E5%85%83%E7%B4%A0&cumulative=false&curInstr=3&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=311&rawInputLstJSON=%5B%5D&textReferences=false

### Duyệt qua danh sách

Giống như mảng, danh sách có thể được duyệt theo chỉ mục hoặc bằng cách lặp trực tiếp qua các phần tử.

=== "Python"

    ```python title="list.py"
    # Duyệt danh sách theo chỉ mục
    count = 0
    for i in range(len(nums)):
        count += nums[i]

    # Duyệt trực tiếp qua các phần tử của danh sách
    for num in nums:
        count += num
    ```

=== "C++"

    ```cpp title="list.cpp"
    /* Duyệt danh sách theo chỉ mục */
    int count = 0;
    for (int i = 0; i < nums.size(); i++) {
        count += nums[i];
    }

    /* Duyệt trực tiếp qua các phần tử của danh sách */
    count = 0;
    for (int num : nums) {
        count += num;
    }
    ```

=== "Java"

    ```java title="list.java"
    /* Duyệt danh sách theo chỉ mục */
    int count = 0;
    for (int i = 0; i < nums.size(); i++) {
        count += nums.get(i);
    }

    /* Duyệt trực tiếp qua các phần tử của danh sách */
    for (int num : nums) {
        count += num;
    }
    ```

=== "C#"

    ```csharp title="list.cs"
    /* Duyệt danh sách theo chỉ mục */
    int count = 0;
    for (int i = 0; i < nums.Count; i++) {
        count += nums[i];
    }

    /* Duyệt trực tiếp qua các phần tử của danh sách */
    count = 0;
    foreach (int num in nums) {
        count += num;
    }
    ```

=== "Go"

    ```go title="list_test.go"
    /* Duyệt danh sách theo chỉ mục */
    count := 0
    for i := 0; i < len(nums); i++ {
        count += nums[i]
    }

    /* Duyệt trực tiếp qua các phần tử của danh sách */
    count = 0
    for _, num := range nums {
        count += num
    }
    ```

=== "Swift"

    ```swift title="list.swift"
    /* Duyệt danh sách theo chỉ mục */
    var count = 0
    for i in nums.indices {
        count += nums[i]
    }

    /* Duyệt trực tiếp qua các phần tử của danh sách */
    count = 0
    for num in nums {
        count += num
    }
    ```

=== "JS"

    ```javascript title="list.js"
    /* Duyệt danh sách theo chỉ mục */
    let count = 0;
    for (let i = 0; i < nums.length; i++) {
        count += nums[i];
    }

    /* Duyệt trực tiếp qua các phần tử của danh sách */
    count = 0;
    for (const num of nums) {
        count += num;
    }
    ```

=== "TS"

    ```typescript title="list.ts"
    /* Duyệt danh sách theo chỉ mục */
    let count = 0;
    for (let i = 0; i < nums.length; i++) {
        count += nums[i];
    }

    /* Duyệt trực tiếp qua các phần tử của danh sách */
    count = 0;
    for (const num of nums) {
        count += num;
    }
    ```

=== "Dart"

    ```dart title="list.dart"
    /* Duyệt danh sách theo chỉ mục */
    int count = 0;
    for (var i = 0; i < nums.length; i++) {
        count += nums[i];
    }

    /* Duyệt trực tiếp qua các phần tử của danh sách */
    count = 0;
    for (var num in nums) {
        count += num;
    }
    ```

=== "Rust"

    ```rust title="list.rs"
    // Duyệt danh sách theo chỉ mục
    let mut _count = 0;
    for i in 0..nums.len() {
        _count += nums[i];
    }

    // Duyệt trực tiếp qua các phần tử của danh sách
    _count = 0;
    for num in &nums {
        _count += num;
    }
    ```

=== "C"

    ```c title="list.c"
    // C không cung cấp mảng động tích hợp sẵn
    ```

=== "Kotlin"

    ```kotlin title="list.kt"
    /* Duyệt danh sách theo chỉ mục */
    var count = 0
    for (i in nums.indices) {
        count += nums[i]
    }

    /* Duyệt trực tiếp qua các phần tử của danh sách */
    for (num in nums) {
        count += num
    }
    ```

=== "Ruby"

    ```ruby title="list.rb"
    # Duyệt danh sách theo chỉ mục
    count = 0
    for i in 0...nums.length
        count += nums[i]
    end

    # Duyệt trực tiếp qua các phần tử của danh sách
    count = 0
    for num in nums
        count += num
    end
    ```

??? pythontutor "Code Visualization"

    https://pythontutor.com/render.html#code=%22%22%22Driver%20Code%22%22%22%0Aif%20__name__%20%3D%3D%20%22__main__%22%3A%0A%20%20%20%20%23%20%E5%88%9D%E5%A7%8B%E5%8C%96%E5%88%97%E8%A1%A8%0A%20%20%20%20nums%20%3D%20%5B1,%203,%202,%205,%204%5D%0A%20%20%20%20%0A%20%20%20%20%23%20%E9%80%9A%E8%BF%87%E7%B4%A2%E5%BC%95%E9%81%8D%E5%8E%86%E5%88%97%E8%A1%A8%0A%20%20%20%20count%20%3D%200%0A%20%20%20%20for%20i%20in%20range%28len%28nums%29%29%3A%0A%20%20%20%20%20%20%20%20count%20%2B%3D%20nums%5Bi%5D%0A%0A%20%20%20%20%23%20%E7%9B%B4%E6%8E%A5%E9%81%8D%E5%8E%86%E5%88%97%E8%A1%A8%E5%85%83%E7%B4%A0%0A%20%20%20%20for%20num%20in%20nums%3A%0A%20%20%20%20%20%20%20%20count%20%2B%3D%20num&cumulative=false&curInstr=3&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=311&rawInputLstJSON=%5B%5D&textReferences=false

### Nối các danh sách

Với một danh sách mới `nums1`, chúng ta có thể nối nó vào cuối danh sách ban đầu.

=== "Python"

    ```python title="list.py"
    # Nối hai danh sách
    nums1: list[int] = [6, 8, 7, 10, 9]
    nums += nums1  # Nối danh sách nums1 vào cuối nums
    ```

=== "C++"

    ```cpp title="list.cpp"
    /* Nối hai danh sách */
    vector<int> nums1 = { 6, 8, 7, 10, 9 };
    // Nối danh sách nums1 vào cuối nums
    nums.insert(nums.end(), nums1.begin(), nums1.end());
    ```

=== "Java"

    ```java title="list.java"
    /* Nối hai danh sách */
    List<Integer> nums1 = new ArrayList<>(Arrays.asList(new Integer[] { 6, 8, 7, 10, 9 }));
    nums.addAll(nums1);  // Nối danh sách nums1 vào cuối nums
    ```

=== "C#"

    ```csharp title="list.cs"
    /* Nối hai danh sách */
    List<int> nums1 = [6, 8, 7, 10, 9];
    nums.AddRange(nums1);  // Nối danh sách nums1 vào cuối nums
    ```

=== "Go"

    ```go title="list_test.go"
    /* Nối hai danh sách */
    nums1 := []int{6, 8, 7, 10, 9}
    nums = append(nums, nums1...)  // Nối danh sách nums1 vào cuối nums
    ```

=== "Swift"

    ```swift title="list.swift"
    /* Nối hai danh sách */
    let nums1 = [6, 8, 7, 10, 9]
    nums.append(contentsOf: nums1) // Nối danh sách nums1 vào cuối nums
    ```

=== "JS"

    ```javascript title="list.js"
    /* Nối hai danh sách */
    const nums1 = [6, 8, 7, 10, 9];
    nums.push(...nums1);  // Nối danh sách nums1 vào cuối nums
    ```

=== "TS"

    ```typescript title="list.ts"
    /* Nối hai danh sách */
    const nums1: number[] = [6, 8, 7, 10, 9];
    nums.push(...nums1);  // Nối danh sách nums1 vào cuối nums
    ```

=== "Dart"

    ```dart title="list.dart"
    /* Nối hai danh sách */
    List<int> nums1 = [6, 8, 7, 10, 9];
    nums.addAll(nums1);  // Nối danh sách nums1 vào cuối nums
    ```

=== "Rust"

    ```rust title="list.rs"
    /* Nối hai danh sách */
    let nums1: Vec<i32> = vec![6, 8, 7, 10, 9];
    nums.extend(nums1);
    ```

=== "C"

    ```c title="list.c"
    // C không cung cấp mảng động tích hợp sẵn
    ```

=== "Kotlin"

    ```kotlin title="list.kt"
    /* Nối hai danh sách */
    val nums1 = intArrayOf(6, 8, 7, 10, 9).toMutableList()
    nums.addAll(nums1)  // Nối danh sách nums1 vào cuối nums
    ```

=== "Ruby"

    ```ruby title="list.rb"
    # Nối hai danh sách
    nums1 = [6, 8, 7, 10, 9]
    nums += nums1
    ```

??? pythontutor "Trực quan hóa mã"

    https://pythontutor.com/render.html#code=%22%22%22Driver%20Code%22%22%22%0Aif%20__name__%20%3D%3D%20%22__main__%22%3A%0A%20%20%20%20%23%20%E5%88%9D%E5%A7%8B%E5%8C%96%E5%88%97%E8%A1%A8%0A%20%20%20%20nums%20%3D%20%5B1,%203,%202,%205,%204%5D%0A%20%20%20%20%0A%20%20%20%20%23%20%E6%8B%BC%E6%8E%A5%E4%B8%A4%E4%B8%AA%E5%88%97%E8%A1%A8%0A%20%20%20%20nums1%20%3D%20%5B6,%208,%207,%2010,%209%5D%0A%20%20%20%20nums%20%2B%3D%20nums1%20%20%23%20%E5%B0%86%E5%88%97%E8%A1%A8%20nums1%20%E6%8B%BC%E6%8E%A5%E5%88%B0%20nums%20%E4%B9%8B%E5%90%8E&cumulative=false&curInstr=3&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=311&rawInputLstJSON=%5B%5D&textReferences=false

### Sắp xếp một danh sách

Sau khi sắp xếp một danh sách, chúng ta có thể sử dụng các thuật toán "tìm kiếm nhị phân" (binary search) và "hai con trỏ" (two-pointer), vốn thường xuất hiện trong các bài toán thuật toán mảng.

=== "Python"

    ```python title="list.py"
    # Sắp xếp một danh sách
    nums.sort()  # Sau khi sắp xếp, các phần tử trong danh sách được xếp từ nhỏ đến lớn
    ```

=== "C++"

    ```cpp title="list.cpp"
    /* Sắp xếp một danh sách */
    sort(nums.begin(), nums.end());  // Sau khi sắp xếp, các phần tử trong danh sách được xếp từ nhỏ đến lớn
    ```

=== "Java"

    ```java title="list.java"
    /* Sắp xếp một danh sách */
    Collections.sort(nums);  // Sau khi sắp xếp, các phần tử trong danh sách được xếp từ nhỏ đến lớn
    ```

=== "C#"

    ```csharp title="list.cs"
    /* Sắp xếp một danh sách */
    nums.Sort(); // Sau khi sắp xếp, các phần tử trong danh sách được xếp từ nhỏ đến lớn
    ```

=== "Go"

    ```go title="list_test.go"
    /* Sắp xếp một danh sách */
    sort.Ints(nums)  // Sau khi sắp xếp, các phần tử trong danh sách được xếp từ nhỏ đến lớn
    ```

=== "Swift"

    ```swift title="list.swift"
    /* Sắp xếp một danh sách */
    nums.sort() // Sau khi sắp xếp, các phần tử trong danh sách được xếp từ nhỏ đến lớn
    ```

=== "JS"

    ```javascript title="list.js"
    /* Sắp xếp một danh sách */
    nums.sort((a, b) => a - b);  // Sau khi sắp xếp, các phần tử trong danh sách được xếp từ nhỏ đến lớn
    ```

=== "TS"

    ```typescript title="list.ts"
    /* Sắp xếp một danh sách */
    nums.sort((a, b) => a - b);  // Sau khi sắp xếp, các phần tử trong danh sách được xếp từ nhỏ đến lớn
    ```

=== "Dart"

    ```dart title="list.dart"
    /* Sắp xếp một danh sách */
    nums.sort(); // Sau khi sắp xếp, các phần tử trong danh sách được xếp từ nhỏ đến lớn
    ```

=== "Rust"

    ```rust title="list.rs"
    /* Sắp xếp một danh sách */
    nums.sort(); // Sau khi sắp xếp, các phần tử trong danh sách được xếp từ nhỏ đến lớn
    ```

=== "C"

    ```c title="list.c"
    // C không cung cấp mảng động tích hợp sẵn
    ```

=== "Kotlin"

    ```kotlin title="list.kt"
    /* Sắp xếp một danh sách */
    nums.sort() // Sau khi sắp xếp, các phần tử trong danh sách được xếp từ nhỏ đến lớn
    ```

=== "Ruby"

    ```ruby title="list.rb"
    # Sắp xếp một danh sách
    nums = nums.sort { |a, b| a <=> b } # Sau khi sắp xếp, các phần tử trong danh sách được xếp từ nhỏ đến lớn
    ```

??? pythontutor "Trực quan hóa mã"

    https://pythontutor.com/render.html#code=%22%22%22Driver%20Code%22%22%22%0Aif%20__name__%20%3D%3D%20%22__main__%22%3A%0A%20%20%20%20%23%20%E5%88%9D%E5%A7%8B%E5%8C%96%E5%88%97%E8%A1%A8%0A%20%20%20%20nums%20%3D%20%5B1,%203,%202,%205,%204%5D%0A%20%20%20%20%0A%20%20%20%20%23%20%E6%8E%92%E5%BA%8F%E5%88%97%E8%A1%A8%0A%20%20%20%20nums.sort%28%29%20%20%23%20%E6%8E%92%E5%BA%8F%E5%90%8E%EF%BC%8C%E5%88%97%E8%A1%A8%E5%85%83%E7%B4%A0%E4%BB%8E%E5%B0%8F%E5%88%B0%E5%A4%A7%E6%8E%92%E5%88%97&cumulative=false&curInstr=3&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=311&rawInputLstJSON=%5B%5D&textReferences=false

## Cài đặt List

Nhiều ngôn ngữ lập trình có danh sách tích hợp sẵn, chẳng hạn như Java, C++ và Python. Cách triển khai của chúng khá phức tạp, với các tham số được cân nhắc cẩn thận, chẳng hạn như sức chứa ban đầu, hệ số mở rộng, v.v. Bạn đọc quan tâm có thể tham khảo mã nguồn để tìm hiểu thêm.

Để hiểu sâu hơn về cách hoạt động của danh sách, chúng ta thử triển khai một danh sách đơn giản với ba yếu tố thiết kế chính:

- **Sức chứa ban đầu**: Chọn sức chứa ban đầu hợp lý cho mảng nền. Trong ví dụ này, chúng ta chọn 10 làm sức chứa ban đầu.
- **Theo dõi kích thước**: Khai báo một biến `size` để ghi lại số phần tử hiện tại trong danh sách và cập nhật biến này theo thời gian thực khi các phần tử được chèn và xóa. Dựa trên biến này, chúng ta có thể xác định vị trí cuối danh sách và quyết định liệu có cần mở rộng hay không.
- **Cơ chế mở rộng**: Khi sức chứa của danh sách đầy trong lúc chèn một phần tử, chúng ta cần mở rộng danh sách. Chúng ta tạo một mảng lớn hơn dựa trên hệ số mở rộng, sau đó lần lượt chuyển tất cả phần tử từ mảng hiện tại sang mảng mới. Trong ví dụ này, chúng ta quy định rằng mỗi lần mảng sẽ được mở rộng thành kích thước gấp 2 lần kích thước trước đó.

```src
[file]{my_list}-[class]{my_list}-[func]{}
```
