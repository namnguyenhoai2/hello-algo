# Các kiểu dữ liệu cơ bản

Khi nói về dữ liệu được lưu trữ trong máy tính, chúng ta nghĩ đến nhiều dạng khác nhau như văn bản, hình ảnh, video, âm thanh, mô hình 3D, v.v. Mặc dù các loại dữ liệu này được tổ chức theo những cách khác nhau, chúng đều được cấu thành từ nhiều kiểu dữ liệu cơ bản.

**Kiểu dữ liệu cơ bản là những kiểu mà CPU có thể trực tiếp thao tác**, và chúng được sử dụng trực tiếp trong các thuật toán, chủ yếu bao gồm những kiểu sau.

- Các kiểu số nguyên `byte`, `short`, `int`, `long`.
- Các kiểu số thực `float`, `double`, dùng để biểu diễn các số thập phân.
- Kiểu ký tự `char`, dùng để biểu diễn chữ cái, dấu câu và thậm chí cả emoji trong nhiều ngôn ngữ.
- Kiểu Boolean `bool`, dùng để biểu diễn các phán đoán "có" và "không".

**Các kiểu dữ liệu cơ bản được lưu trữ dưới dạng nhị phân trong máy tính**. Một chữ số nhị phân là một bit. Trong hầu hết các hệ điều hành hiện đại, $1$ byte gồm $8$ bit.

Phạm vi giá trị của các kiểu dữ liệu cơ bản phụ thuộc vào kích thước không gian mà chúng chiếm dụng. Dưới đây là một ví dụ sử dụng Java.

- Kiểu số nguyên `byte` chiếm $1$ byte = $8$ bit và có thể biểu diễn $2^{8}$ số.
- Kiểu số nguyên `int` chiếm $4$ byte = $32$ bit và có thể biểu diễn $2^{32}$ số.

Bảng sau liệt kê không gian chiếm dụng, phạm vi giá trị và giá trị mặc định của nhiều kiểu dữ liệu cơ bản trong Java. Bạn không cần ghi nhớ bảng này; chỉ cần nắm được những điểm chính và tra cứu khi cần.

<p align="center"> Bảng <id> &nbsp; Không gian chiếm dụng và phạm vi giá trị của các kiểu dữ liệu cơ bản </p>

| Kiểu       | Ký hiệu   | Không gian chiếm dụng | Giá trị nhỏ nhất            | Giá trị lớn nhất           | Giá trị mặc định  |
| ---------- | -------- | -------------- | ------------------------ | ----------------------- | -------------- |
| Số nguyên    | `byte`   | 1 byte         | $-2^7$ ($-128$)          | $2^7 - 1$ ($127$)       | $0$            |
|            | `short`  | 2 byte        | $-2^{15}$                | $2^{15} - 1$            | $0$            |
|            | `int`    | 4 byte        | $-2^{31}$                | $2^{31} - 1$            | $0$            |
|            | `long`   | 8 byte        | $-2^{63}$                | $2^{63} - 1$            | $0$            |
| Số thực      | `float`  | 4 byte        | $1.175 \times 10^{-38}$  | $3.403 \times 10^{38}$  | $0.0\text{f}$  |
|            | `double` | 8 byte        | $2.225 \times 10^{-308}$ | $1.798 \times 10^{308}$ | $0.0$          |
| Ký tự      | `char`   | 2 byte        | $0$                      | $2^{16} - 1$            | $0$            |
| Boolean    | `bool`   | 1 byte         | $\text{false}$           | $\text{true}$           | $\text{false}$ |

Lưu ý rằng bảng trên chỉ áp dụng cho các kiểu dữ liệu cơ bản của Java. Mỗi ngôn ngữ lập trình có định nghĩa kiểu riêng, vì vậy mức sử dụng không gian, phạm vi giá trị và giá trị mặc định của chúng có thể khác nhau.

- Trong Python, kiểu số nguyên `int` có thể có kích thước bất kỳ, chỉ bị giới hạn bởi bộ nhớ khả dụng; kiểu số thực `float` là số thực 64 bit độ chính xác kép; không có kiểu `char`, một ký tự đơn thực chất là một chuỗi `str` có độ dài 1.
- C và C++ không chỉ định rõ kích thước của các kiểu dữ liệu cơ bản, kích thước này thay đổi tùy theo implementation và nền tảng. Bảng trên tuân theo mô hình dữ liệu[ LP64 ](https://en.cppreference.com/w/cpp/language/types#Properties), được sử dụng trong các hệ điều hành Unix 64 bit, bao gồm Linux và macOS.
- Kích thước của kiểu ký tự `char` là 1 byte trong C và C++; trong hầu hết các ngôn ngữ lập trình, kích thước này phụ thuộc vào phương thức mã hóa ký tự cụ thể, như được trình bày chi tiết trong phần "Mã hóa ký tự".
- Mặc dù để biểu diễn một giá trị Boolean chỉ cần 1 bit ($0$ hoặc $1$), giá trị này thường được lưu dưới dạng 1 byte trong bộ nhớ. Điều này là vì CPU máy tính hiện đại thường sử dụng 1 byte làm đơn vị bộ nhớ nhỏ nhất có thể định địa chỉ.

Vậy mối quan hệ giữa các kiểu dữ liệu cơ bản và cấu trúc dữ liệu là gì? Chúng ta biết rằng cấu trúc dữ liệu là cách tổ chức và lưu trữ dữ liệu trong máy tính. Ở đây, trọng tâm nằm ở "cấu trúc", không phải "dữ liệu".

Nếu muốn biểu diễn "một hàng số", chúng ta thường nghĩ ngay đến việc sử dụng một mảng. Đó là vì cấu trúc tuyến tính của mảng có thể biểu diễn mối quan hệ liền kề và thứ tự giữa các số, nhưng việc nội dung được lưu trữ là số nguyên `int`, số thực `float` hay ký tự `char` không liên quan đến "cấu trúc dữ liệu".

Nói cách khác, **các kiểu dữ liệu cơ bản cung cấp "kiểu nội dung" của dữ liệu, còn cấu trúc dữ liệu cung cấp "cách tổ chức" dữ liệu**. Ví dụ, trong đoạn mã sau, chúng ta sử dụng cùng một cấu trúc dữ liệu (mảng) để lưu trữ và biểu diễn nhiều kiểu dữ liệu cơ bản khác nhau, bao gồm `int`, `float`, `char`, `bool`, v.v.

=== "Python"

    ```python title=""
    # Khởi tạo các mảng bằng nhiều kiểu dữ liệu cơ bản khác nhau
    numbers: list[int] = [0] * 5
    decimals: list[float] = [0.0] * 5
    # Trong Python, ký tự thực chất là các chuỗi có độ dài 1
    characters: list[str] = ['0'] * 5
    bools: list[bool] = [False] * 5
    # Danh sách Python có thể tự do lưu trữ nhiều kiểu dữ liệu cơ bản và các tham chiếu đối tượng
    data = [0, 0.0, 'a', False, ListNode(0)]
    ```

=== "C++"

    ```cpp title=""
    // Khởi tạo các mảng bằng nhiều kiểu dữ liệu cơ bản khác nhau
    int numbers[5];
    float decimals[5];
    char characters[5];
    bool bools[5];
    ```

=== "Java"

    ```java title=""
    // Khởi tạo các mảng bằng nhiều kiểu dữ liệu cơ bản khác nhau
    int[] numbers = new int[5];
    float[] decimals = new float[5];
    char[] characters = new char[5];
    boolean[] bools = new boolean[5];
    ```

=== "C#"

    ```csharp title=""
    // Khởi tạo các mảng bằng nhiều kiểu dữ liệu cơ bản khác nhau
    int[] numbers = new int[5];
    float[] decimals = new float[5];
    char[] characters = new char[5];
    bool[] bools = new bool[5];
    ```

=== "Go"

    ```go title=""
    // Khởi tạo các mảng bằng nhiều kiểu dữ liệu cơ bản khác nhau
    var numbers = [5]int{}
    var decimals = [5]float64{}
    var characters = [5]byte{}
    var bools = [5]bool{}
    ```

=== "Swift"

    ```swift title=""
    // Khởi tạo các mảng bằng nhiều kiểu dữ liệu cơ bản khác nhau
    let numbers = Array(repeating: 0, count: 5)
    let decimals = Array(repeating: 0.0, count: 5)
    let characters: [Character] = Array(repeating: "a", count: 5)
    let bools = Array(repeating: false, count: 5)
    ```

=== "JS"

    ```javascript title=""
    // Mảng JavaScript có thể tự do lưu trữ nhiều kiểu dữ liệu cơ bản và đối tượng khác nhau
    const array = [0, 0.0, 'a', false];
    ```

=== "TS"

    ```typescript title=""
    // Khởi tạo các mảng bằng nhiều kiểu dữ liệu cơ bản khác nhau
    const numbers: number[] = [];
    const characters: string[] = [];
    const bools: boolean[] = [];
    ```

=== "Dart"

    ```dart title=""
    // Khởi tạo các mảng bằng nhiều kiểu dữ liệu cơ bản khác nhau
    List<int> numbers = List.filled(5, 0);
    List<double> decimals = List.filled(5, 0.0);
    List<String> characters = List.filled(5, 'a');
    List<bool> bools = List.filled(5, false);
    ```

=== "Rust"

    ```rust title=""
    // Khởi tạo các mảng bằng nhiều kiểu dữ liệu cơ bản khác nhau
    let numbers: Vec<i32> = vec![0; 5];
    let decimals: Vec<f32> = vec![0.0; 5];
    let characters: Vec<char> = vec!['0'; 5];
    let bools: Vec<bool> = vec![false; 5];
    ```

=== "C"

    ```c title=""
    // Khởi tạo các mảng bằng nhiều kiểu dữ liệu cơ bản khác nhau
    int numbers[10];
    float decimals[10];
    char characters[10];
    bool bools[10];
    ```

=== "Kotlin"

    ```kotlin title=""
    // Khởi tạo các mảng bằng nhiều kiểu dữ liệu cơ bản khác nhau
    val numbers = IntArray(5)
    val decinals = FloatArray(5)
    val characters = CharArray(5)
    val bools = BooleanArray(5)
    ```

=== "Ruby"

    ```ruby title=""
    # Danh sách Ruby có thể tự do lưu trữ nhiều kiểu dữ liệu cơ bản và các tham chiếu đối tượng
    data = [0, 0.0, 'a', false, ListNode(0)]
    ```

??? pythontutor "Thực thi trực quan"

    https://pythontutor.com/render.html#code=class%20ListNode%3A%0A%20%20%20%20%22%22%22%E9%93%BE%E8%A1%A8%E8%8A%82%E7%82%B9%E7%B1%BB%22%22%22%0A%20%20%20%20def%20__init__%28self,%20val%3A%20int%29%3A%0A%20%20%20%20%20%20%20%20self.val%3A%20int%20%3D%20val%20%20%23%20%E8%8A%82%E7%82%B9%E5%80%BC%0A%20%20%20%20%20%20%20%20self.next%3A%20ListNode%20%7C%20None%20%3D%20None%20%20%23%20%E5%90%8E%E7%BB%A7%E8%8A%82%E7%82%B9%E5%BC%95%E7%94%A8%0A%0A%22%22%22Driver%20Code%22%22%22%0Aif%20__name__%20%3D%3D%20%22__main__%22%3A%0A%20%20%20%20%23%20%E4%BD%BF%E7%94%A8%E5%A4%9A%E7%A7%8D%E5%9F%BA%E6%9C%AC%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B%E6%9D%A5%E5%88%9D%E5%A7%8B%E5%8C%96%E6%95%B0%E7%BB%84%0A%20%20%20%20numbers%20%3D%20%5B0%5D%20*%205%0A%20%20%20%20decimals%20%3D%20%5B0.0%5D%20*%205%0A%20%20%20%20%23%20Python%20%E7%9A%84%E5%AD%97%E7%AC%A6%E5%AE%9E%E9%99%85%E4%B8%8A%E6%98%AF%E9%95%BF%E5%BA%A6%E4%B8%BA%201%20%E7%9A%84%E5%AD%97%E7%AC%A6%E4%B8%B2%0A%20%20%20%20characters%20%3D%20%5B'0'%5D%20*%205%0A%20%20%20%20bools%20%3D%20%5BFalse%5D%20*%205%0A%20%20%20%20%23%20Python%20%E7%9A%84%E5%88%97%E8%A1%A8%E5%8F%AF%E4%BB%A5%E8%87%AA%E7%94%B1%E5%AD%98%E5%82%A8%E5%90%84%E7%A7%8D%E5%9F%BA%E6%9C%AC%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B%E5%92%8C%E5%AF%B9%E8%B1%A1%E5%BC%95%E7%94%A8%0A%20%20%20%20data%20%3D%20%5B0,%200.0,%20'a',%20False,%20ListNode%280%29%5D&cumulative=false&curInstr=12&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=311&rawInputLstJSON=%5B%5D&textReferences=false