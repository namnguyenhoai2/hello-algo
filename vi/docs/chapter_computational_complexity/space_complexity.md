# Độ phức tạp về không gian

<u>Độ phức tạp về không gian</u> đo lường xu hướng tăng của không gian bộ nhớ mà một thuật toán chiếm dụng khi kích thước dữ liệu tăng. Khái niệm này rất giống với độ phức tạp về thời gian, ngoại trừ việc “thời gian chạy” được thay bằng “không gian bộ nhớ đã chiếm dụng”.

## Không gian liên quan đến thuật toán

Không gian bộ nhớ được một thuật toán sử dụng trong quá trình thực thi chủ yếu bao gồm các loại sau:

- **Không gian đầu vào**: Dùng để lưu trữ dữ liệu đầu vào của thuật toán.
- **Không gian tạm thời**: Dùng để lưu trữ các biến, đối tượng, ngữ cảnh hàm và dữ liệu khác trong quá trình thực thi thuật toán.
- **Không gian đầu ra**: Dùng để lưu trữ dữ liệu đầu ra của thuật toán.

Nhìn chung, phạm vi thống kê độ phức tạp về không gian là “không gian tạm thời” cộng với “không gian đầu ra”.

Không gian tạm thời có thể được chia tiếp thành ba phần:

- **Dữ liệu tạm thời**: Dùng để lưu các hằng số, biến, đối tượng khác nhau, v.v. trong quá trình thực thi thuật toán.
- **Không gian khung ngăn xếp**: Dùng để lưu dữ liệu ngữ cảnh của các hàm được gọi. Hệ thống tạo một khung ngăn xếp ở đầu ngăn xếp mỗi khi một hàm được gọi, và giải phóng không gian khung ngăn xếp sau khi hàm trả về.
- **Không gian chỉ thị**: Dùng để lưu các chỉ thị chương trình đã biên dịch, thường được bỏ qua trong thống kê thực tế.

Khi phân tích độ phức tạp về không gian của một chương trình, **chúng ta thường xem xét ba phần: dữ liệu tạm thời, không gian khung ngăn xếp và dữ liệu đầu ra**, như trong hình dưới đây.

![Không gian liên quan đến thuật toán](space_complexity.assets/space_types.png)

Mã liên quan như sau:

=== "Python"

    ```python title=""
    class Node:
        """Lớp"""
        def __init__(self, x: int):
            self.val: int = x              # Giá trị nút
            self.next: Node | None = None  # Tham chiếu đến nút tiếp theo

    def function() -> int:
        """Hàm"""
        # Thực hiện một số thao tác...
        return 0

    def algorithm(n) -> int:  # Dữ liệu đầu vào
        A = 0                 # Dữ liệu tạm thời (hằng số, thường được biểu diễn bằng chữ in hoa)
        b = 0                 # Dữ liệu tạm thời (biến)
        node = Node(0)        # Dữ liệu tạm thời (đối tượng)
        c = function()        # Không gian khung ngăn xếp (lời gọi hàm)
        return A + b + c      # Dữ liệu đầu ra
    ```

=== "C++"

    ```cpp title=""
    /* Cấu trúc */
    struct Node {
        int val;
        Node *next;
        Node(int x) : val(x), next(nullptr) {}
    };

    /* Hàm */
    int func() {
        // Thực hiện một số thao tác...
        return 0;
    }

    int algorithm(int n) {        // Dữ liệu đầu vào
        const int a = 0;          // Dữ liệu tạm thời (hằng số)
        int b = 0;                // Dữ liệu tạm thời (biến)
        Node* node = new Node(0); // Dữ liệu tạm thời (đối tượng)
        int c = func();           // Không gian khung ngăn xếp (lời gọi hàm)
        return a + b + c;         // Dữ liệu đầu ra
    }
    ```

=== "Java"

    ```java title=""
    /* Lớp */
    class Node {
        int val;
        Node next;
        Node(int x) { val = x; }
    }

    /* Hàm */
    int function() {
        // Thực hiện một số thao tác...
        return 0;
    }

    int algorithm(int n) {        // Dữ liệu đầu vào
        final int a = 0;          // Dữ liệu tạm thời (hằng số)
        int b = 0;                // Dữ liệu tạm thời (biến)
        Node node = new Node(0);  // Dữ liệu tạm thời (đối tượng)
        int c = function();       // Không gian khung ngăn xếp (lời gọi hàm)
        return a + b + c;         // Dữ liệu đầu ra
    }
    ```

=== "C#"

    ```csharp title=""
    /* Lớp */
    class Node(int x) {
        int val = x;
        Node next;
    }

    /* Hàm */
    int Function() {
        // Thực hiện một số thao tác...
        return 0;
    }

    int Algorithm(int n) {        // Dữ liệu đầu vào
        const int a = 0;          // Dữ liệu tạm thời (hằng số)
        int b = 0;                // Dữ liệu tạm thời (biến)
        Node node = new(0);       // Dữ liệu tạm thời (đối tượng)
        int c = Function();       // Không gian khung ngăn xếp (lời gọi hàm)
        return a + b + c;         // Dữ liệu đầu ra
    }
    ```

=== "Go"

    ```go title=""
    /* Cấu trúc */
    type node struct {
        val  int
        next *node
    }

    /* Tạo cấu trúc nút */
    func newNode(val int) *node {
        return &node{val: val}
    }

    /* Hàm */
    func function() int {
        // Thực hiện một số thao tác...
        return 0
    }

    func algorithm(n int) int { // Dữ liệu đầu vào
        const a = 0             // Dữ liệu tạm thời (hằng số)
        b := 0                  // Dữ liệu tạm thời (biến)
        newNode(0)              // Dữ liệu tạm thời (đối tượng)
        c := function()         // Không gian khung ngăn xếp (lời gọi hàm)
        return a + b + c        // Dữ liệu đầu ra
    }
    ```

=== "Swift"

    ```swift title=""
    /* Lớp */
    class Node {
        var val: Int
        var next: Node?

        init(x: Int) {
            val = x
        }
    }

    /* Hàm */
    func function() -> Int {
        // Thực hiện một số thao tác...
        return 0
    }

    func algorithm(n: Int) -> Int { // Dữ liệu đầu vào
        let a = 0             // Dữ liệu tạm thời (hằng số)
        var b = 0             // Dữ liệu tạm thời (biến)
        let node = Node(x: 0) // Dữ liệu tạm thời (đối tượng)
        let c = function()    // Không gian khung ngăn xếp (lời gọi hàm)
        return a + b + c      // Dữ liệu đầu ra
    }
    ```

=== "JS"

    ```javascript title=""
    /* Lớp */
    class Node {
        val;
        next;
        constructor(val) {
            this.val = val === undefined ? 0 : val; // Giá trị nút
            this.next = null;                       // Tham chiếu đến nút tiếp theo
        }
    }

    /* Hàm */
    function constFunc() {
        // Thực hiện một số thao tác
        return 0;
    }

    function algorithm(n) {       // Dữ liệu đầu vào
        const a = 0;              // Dữ liệu tạm thời (hằng số)
        let b = 0;                // Dữ liệu tạm thời (biến)
        const node = new Node(0); // Dữ liệu tạm thời (đối tượng)
        const c = constFunc();    // Không gian khung ngăn xếp (lời gọi hàm)
        return a + b + c;         // Dữ liệu đầu ra
    }
    ```

=== "TS"

    ```typescript title=""
    /* Lớp */
    class Node {
        val: number;
        next: Node | null;
        constructor(val?: number) {
            this.val = val === undefined ? 0 : val; // Giá trị nút
            this.next = null;                       // Tham chiếu đến nút tiếp theo
        }
    }

    /* Hàm */
    function constFunc(): number {
        // Thực hiện một số thao tác
        return 0;
    }

    function algorithm(n: number): number { // Dữ liệu đầu vào
        const a = 0;                        // Dữ liệu tạm thời (hằng số)
        let b = 0;                          // Dữ liệu tạm thời (biến)
        const node = new Node(0);           // Dữ liệu tạm thời (đối tượng)
        const c = constFunc();              // Không gian khung ngăn xếp (lời gọi hàm)
        return a + b + c;                   // Dữ liệu đầu ra
    }
    ```

=== "Dart"

    ```dart title=""
    /* Lớp */
    class Node {
      int val;
      Node next;
      Node(this.val, [this.next]);
    }

    /* Hàm */
    int function() {
      // Thực hiện một số thao tác...
      return 0;
    }

    int algorithm(int n) {  // Dữ liệu đầu vào
      const int a = 0;      // Dữ liệu tạm thời (hằng số)
      int b = 0;            // Dữ liệu tạm thời (biến)
      Node node = Node(0);  // Dữ liệu tạm thời (đối tượng)
      int c = function();   // Không gian khung ngăn xếp (lời gọi hàm)
      return a + b + c;     // Dữ liệu đầu ra
    }
    ```

=== "Rust"

    ```rust title=""
    use std::rc::Rc;
    use std::cell::RefCell;

    /* Cấu trúc */
    struct Node {
        val: i32,
        next: Option<Rc<RefCell<Node>>>,
    }

    /* Tạo cấu trúc Node */
    impl Node {
        fn new(val: i32) -> Self {
            Self { val: val, next: None }
        }
    }

    /* Hàm */
    fn function() -> i32 {
        // Thực hiện một số thao tác...
        return 0;
    }

    fn algorithm(n: i32) -> i32 {       // Dữ liệu đầu vào
        const a: i32 = 0;               // Dữ liệu tạm thời (hằng số)
        let mut b = 0;                  // Dữ liệu tạm thời (biến)
        let node = Node::new(0);        // Dữ liệu tạm thời (đối tượng)
        let c = function();             // Không gian khung ngăn xếp (lời gọi hàm)
        return a + b + c;               // Dữ liệu đầu ra
    }
    ```

=== "C"

    ```c title=""
    /* Hàm */
    int func() {
        // Thực hiện một số thao tác...
        return 0;
    }

    int algorithm(int n) { // Dữ liệu đầu vào
        const int a = 0;   // Dữ liệu tạm thời (hằng số)
        int b = 0;         // Dữ liệu tạm thời (biến)
        int c = func();    // Không gian khung ngăn xếp (lời gọi hàm)
        return a + b + c;  // Dữ liệu đầu ra
    }
    ```

=== "Kotlin"

    ```kotlin title=""
    /* Lớp */
    class Node(var _val: Int) {
        var next: Node? = null
    }

    /* Hàm */
    fun function(): Int {
        // Thực hiện một số thao tác...
        return 0
    }

    fun algorithm(n: Int): Int { // Dữ liệu đầu vào
        val a = 0                // Dữ liệu tạm thời (hằng số)
        var b = 0                // Dữ liệu tạm thời (biến)
        val node = Node(0)       // Dữ liệu tạm thời (đối tượng)
        val c = function()       // Không gian khung ngăn xếp (lời gọi hàm)
        return a + b + c         // Dữ liệu đầu ra
    }
    ```

=== "Ruby"

    ```ruby title=""
    ### Lớp ###
    class Node
        attr_accessor :val      # Giá trị của Node
        attr_accessor :next     # Tham chiếu đến node tiếp theo

        def initialize(x)
            @val = x
        end
    end

    ### Hàm ###
    def function
        # Thực hiện một số thao tác...
        0
    end

    ### Thuật toán ###
    def algorithm(n)        # Dữ liệu đầu vào
        a = 0               # Dữ liệu tạm thời (hằng số)
        b = 0               # Dữ liệu tạm thời (biến)
        node = Node.new(0)  # Dữ liệu tạm thời (đối tượng)
        c = function        # Không gian frame ngăn xếp (lời gọi hàm)
        a + b + c           # Dữ liệu đầu ra
    end
    ```

## Phương pháp tính toán

Phương pháp tính độ phức tạp không gian nhìn chung tương tự như phương pháp tính độ phức tạp thời gian, ngoại trừ việc đại lượng được đo chuyển từ “số lượng thao tác” sang “lượng không gian được sử dụng”.

Không giống độ phức tạp thời gian, **chúng ta thường chỉ tập trung vào độ phức tạp không gian trong trường hợp xấu nhất**. Điều này là do không gian bộ nhớ là một yêu cầu bắt buộc, và chúng ta phải đảm bảo dành đủ không gian bộ nhớ cho mọi dữ liệu đầu vào.

Hãy quan sát đoạn mã sau. Ở đây, “trường hợp xấu nhất” trong độ phức tạp không gian trường hợp xấu nhất có hai ý nghĩa.

1. **Dựa trên dữ liệu đầu vào xấu nhất**: Khi $n < 10$, độ phức tạp không gian là $O(1)$; nhưng khi $n > 10$, mảng được khởi tạo `nums` chiếm không gian $O(n)$, vì vậy độ phức tạp không gian trong trường hợp xấu nhất là $O(n)$.
2. **Dựa trên lượng bộ nhớ đạt đỉnh trong quá trình thực thi thuật toán**: Ví dụ, trước khi thực thi dòng cuối cùng, chương trình chiếm không gian $O(1)$; khi khởi tạo mảng `nums`, chương trình chiếm không gian $O(n)$, vì vậy độ phức tạp không gian trong trường hợp xấu nhất là $O(n)$.

=== "Python"

    ```python title=""
    def algorithm(n: int):
        a = 0               # O(1)
        b = [0] * 10000     # O(1)
        if n > 10:
            nums = [0] * n  # O(n)
    ```

=== "C++"

    ```cpp title=""
    void algorithm(int n) {
        int a = 0;               // O(1)
        vector<int> b(10000);    // O(1)
        if (n > 10)
            vector<int> nums(n); // O(n)
    }
    ```

=== "Java"

    ```java title=""
    void algorithm(int n) {
        int a = 0;                   // O(1)
        int[] b = new int[10000];    // O(1)
        if (n > 10)
            int[] nums = new int[n]; // O(n)
    }
    ```

=== "C#"

    ```csharp title=""
    void Algorithm(int n) {
        int a = 0;                   // O(1)
        int[] b = new int[10000];    // O(1)
        if (n > 10) {
            int[] nums = new int[n]; // O(n)
        }
    }
    ```

=== "Go"

    ```go title=""
    func algorithm(n int) {
        a := 0                      // O(1)
        b := make([]int, 10000)     // O(1)
        var nums []int
        if n > 10 {
            nums := make([]int, n)  // O(n)
        }
        fmt.Println(a, b, nums)
    }
    ```

=== "Swift"

    ```swift title=""
    func algorithm(n: Int) {
        let a = 0 // O(1)
        let b = Array(repeating: 0, count: 10000) // O(1)
        if n > 10 {
            let nums = Array(repeating: 0, count: n) // O(n)
        }
    }
    ```

=== "JS"

    ```javascript title=""
    function algorithm(n) {
        const a = 0;                   // O(1)
        const b = new Array(10000);    // O(1)
        if (n > 10) {
            const nums = new Array(n); // O(n)
        }
    }
    ```

=== "TS"

    ```typescript title=""
    function algorithm(n: number): void {
        const a = 0;                   // O(1)
        const b = new Array(10000);    // O(1)
        if (n > 10) {
            const nums = new Array(n); // O(n)
        }
    }
    ```

=== "Dart"

    ```dart title=""
    void algorithm(int n) {
      int a = 0;                            // O(1)
      List<int> b = List.filled(10000, 0);  // O(1)
      if (n > 10) {
        List<int> nums = List.filled(n, 0); // O(n)
      }
    }
    ```

=== "Rust"

    ```rust title=""
    fn algorithm(n: i32) {
        let a = 0;                              // O(1)
        let b = [0; 10000];                     // O(1)
        if n > 10 {
            let nums = vec![0; n as usize];     // O(n)
        }
    }
    ```

=== "C"

    ```c title=""
    void algorithm(int n) {
        int a = 0;               // O(1)
        int b[10000];            // O(1)
        if (n > 10)
            int nums[n] = {0};   // O(n)
    }
    ```

=== "Kotlin"

    ```kotlin title=""
    fun algorithm(n: Int) {
        val a = 0                    // O(1)
        val b = IntArray(10000)      // O(1)
        if (n > 10) {
            val nums = IntArray(n)   // O(n)
        }
    }
    ```

=== "Ruby"

    ```ruby title=""
    def algorithm(n)
        a = 0                           # O(1)
        b = Array.new(10000)            # O(1)
        nums = Array.new(n) if n > 10   # O(n)
    end
    ```

**Trong các hàm đệ quy, cần tính cả không gian frame ngăn xếp**. Hãy quan sát đoạn mã sau:

=== "Python"

    ```python title=""
    def function() -> int:
        # Thực hiện một số thao tác
        return 0

    def loop(n: int):
        """Vòng lặp có độ phức tạp không gian là O(1)"""
        for _ in range(n):
            function()

    def recur(n: int):
        """Đệ quy có độ phức tạp không gian là O(n)"""
        if n == 1:
            return
        return recur(n - 1)
    ```

=== "C++"

    ```cpp title=""
    int func() {
        // Thực hiện một số thao tác
        return 0;
    }
    /* Vòng lặp có độ phức tạp không gian là O(1) */
    void loop(int n) {
        for (int i = 0; i < n; i++) {
            func();
        }
    }
    /* Đệ quy có độ phức tạp không gian là O(n) */
    void recur(int n) {
        if (n == 1) return;
        recur(n - 1);
    }
    ```

=== "Java"

    ```java title=""
    int function() {
        // Thực hiện một số thao tác
        return 0;
    }
    /* Vòng lặp có độ phức tạp không gian là O(1) */
    void loop(int n) {
        for (int i = 0; i < n; i++) {
            function();
        }
    }
    /* Đệ quy có độ phức tạp không gian là O(n) */
    void recur(int n) {
        if (n == 1) return;
        recur(n - 1);
    }
    ```

=== "C#"

    ```csharp title=""
    int Function() {
        // Thực hiện một số thao tác
        return 0;
    }
    /* Vòng lặp có độ phức tạp không gian là O(1) */
    void Loop(int n) {
        for (int i = 0; i < n; i++) {
            Function();
        }
    }
    /* Đệ quy có độ phức tạp không gian là O(n) */
    int Recur(int n) {
        if (n == 1) return 1;
        return Recur(n - 1);
    }
    ```

=== "Go"

    ```go title=""
    func function() int {
        // Thực hiện một số thao tác
        return 0
    }

    /* Vòng lặp có độ phức tạp không gian là O(1) */
    func loop(n int) {
        for i := 0; i < n; i++ {
            function()
        }
    }

    /* Đệ quy có độ phức tạp không gian là O(n) */
    func recur(n int) {
        if n == 1 {
            return
        }
        recur(n - 1)
    }
    ```

=== "Swift"

    ```swift title=""
    @discardableResult
    func function() -> Int {
        // Thực hiện một số thao tác
        return 0
    }

    /* Vòng lặp có độ phức tạp không gian là O(1) */
    func loop(n: Int) {
        for _ in 0 ..< n {
            function()
        }
    }

    /* Đệ quy có độ phức tạp không gian là O(n) */
    func recur(n: Int) {
        if n == 1 {
            return
        }
        recur(n: n - 1)
    }
    ```

=== "JS"

    ```javascript title=""
    function constFunc() {
        // Thực hiện một số thao tác
        return 0;
    }
    /* Vòng lặp có độ phức tạp không gian là O(1) */
    function loop(n) {
        for (let i = 0; i < n; i++) {
            constFunc();
        }
    }
    /* Đệ quy có độ phức tạp không gian là O(n) */
    function recur(n) {
        if (n === 1) return;
        return recur(n - 1);
    }
    ```

=== "TS"

    ```typescript title=""
    function constFunc(): number {
        // Thực hiện một số thao tác
        return 0;
    }
    /* Vòng lặp có độ phức tạp không gian là O(1) */
    function loop(n: number): void {
        for (let i = 0; i < n; i++) {
            constFunc();
        }
    }
    /* Đệ quy có độ phức tạp không gian là O(n) */
    function recur(n: number): void {
        if (n === 1) return;
        return recur(n - 1);
    }
    ```

=== "Dart"

    ```dart title=""
    int function() {
      // Thực hiện một số thao tác
      return 0;
    }
    /* Vòng lặp có độ phức tạp không gian là O(1) */
    void loop(int n) {
      for (int i = 0; i < n; i++) {
        function();
      }
    }
    /* Đệ quy có độ phức tạp không gian là O(n) */
    void recur(int n) {
      if (n == 1) return;
      recur(n - 1);
    }
    ```

=== "Rust"

    ```rust title=""
    fn function() -> i32 {
        // Thực hiện một số thao tác
        return 0;
    }
    /* Vòng lặp có độ phức tạp không gian là O(1) */
    fn loop(n: i32) {
        for i in 0..n {
            function();
        }
    }
    /* Đệ quy có độ phức tạp không gian là O(n) */
    fn recur(n: i32) {
        if n == 1 {
            return;
        }
        recur(n - 1);
    }
    ```

=== "C"

    ```c title=""
    int func() {
        // Thực hiện một số thao tác
        return 0;
    }
    /* Vòng lặp có độ phức tạp không gian là O(1) */
    void loop(int n) {
        for (int i = 0; i < n; i++) {
            func();
        }
    }
    /* Đệ quy có độ phức tạp không gian là O(n) */
    void recur(int n) {
        if (n == 1) return;
        recur(n - 1);
    }
    ```

=== "Kotlin"

    ```kotlin title=""
    fun function(): Int {
        // Thực hiện một số thao tác
        return 0
    }
    /* Vòng lặp có độ phức tạp không gian là O(1) */
    fun loop(n: Int) {
        for (i in 0..<n) {
            function()
        }
    }
    /* Đệ quy có độ phức tạp không gian là O(n) */
    fun recur(n: Int) {
        if (n == 1) return
        return recur(n - 1)
    }
    ```

=== "Ruby"

    ```ruby title=""
    def function
        # Thực hiện một số thao tác
        0
    end

    ### Vòng lặp có độ phức tạp không gian là O(1) ###
    def loop(n)
        (0...n).each { function }
    end

    ### Đệ quy có độ phức tạp không gian là O(n) ###
    def recur(n)
        return if n == 1
        recur(n - 1)
    end
    ```

Độ phức tạp thời gian của cả hai hàm `loop()` và `recur()` đều là $O(n)$, nhưng độ phức tạp không gian của chúng khác nhau.

- Hàm `loop()` gọi `function()` $n$ lần trong một vòng lặp. Ở mỗi lần lặp, `function()` trả về và giải phóng không gian của stack frame, vì vậy độ phức tạp không gian vẫn là $O(1)$.
- Hàm đệ quy `recur()` có $n$ instance `recur()` chưa trả về cùng tồn tại trong quá trình thực thi, do đó chiếm $O(n)$ không gian stack frame.

## Các loại phổ biến

Cho kích thước dữ liệu đầu vào là $n$. Hình sau đây minh họa các loại độ phức tạp không gian phổ biến (được sắp xếp từ thấp đến cao).

$$
\begin{aligned}
& O(1) < O(\log n) < O(n) < O(n^2) < O(2^n) \newline
& \text{Constant} < \text{Logarithmic} < \text{Linear} < \text{Quadratic} < \text{Exponential}
\end{aligned}
$$

![Các loại độ phức tạp không gian phổ biến](space_complexity.assets/space_complexity_common_types.png)

### Độ phức tạp hằng số $O(1)$

Độ phức tạp hằng số thường gặp ở các hằng số, biến và đối tượng có số lượng không phụ thuộc vào kích thước dữ liệu đầu vào $n$.

Cần lưu ý rằng bộ nhớ được sử dụng khi khởi tạo biến hoặc gọi hàm trong một vòng lặp sẽ được giải phóng khi bắt đầu lần lặp tiếp theo, vì vậy nó không tích lũy không gian và độ phức tạp không gian vẫn là $O(1)$:

```src
[file]{space_complexity}-[class]{}-[func]{constant}
```

### Độ phức tạp tuyến tính $O(n)$

Độ phức tạp tuyến tính thường gặp ở mảng, danh sách liên kết, stack, queue, v.v., trong đó số phần tử tỷ lệ với $n$:

```src
[file]{space_complexity}-[class]{}-[func]{linear}
```

Như minh họa trong hình sau, độ sâu đệ quy của hàm này là $n$, nghĩa là có $n$ hàm `linear_recur()` chưa trả về cùng tồn tại, sử dụng $O(n)$ không gian stack frame:

```src
[file]{space_complexity}-[class]{}-[func]{linear_recur}
```

![Độ phức tạp không gian tuyến tính do hàm đệ quy tạo ra](space_complexity.assets/space_complexity_recursive_linear.png)

### Độ phức tạp bậc hai $O(n^2)$

Độ phức tạp bậc hai thường gặp ở ma trận và đồ thị, trong đó số phần tử có quan hệ bậc hai với $n$:

```src
[file]{space_complexity}-[class]{}-[func]{quadratic}
```

Như minh họa trong hình sau, độ sâu đệ quy của hàm này là $n$, và một mảng được khởi tạo trong mỗi hàm đệ quy với độ dài lần lượt là $n$, $n-1$, $\dots$, $2$, $1$, có độ dài trung bình là $n / 2$, do đó tổng thể chiếm $O(n^2)$ không gian:

```src
[file]{space_complexity}-[class]{}-[func]{quadratic_recur}
```

![Độ phức tạp không gian bậc hai do hàm đệ quy tạo ra](space_complexity.assets/space_complexity_recursive_quadratic.png)

### Độ phức tạp lũy thừa $O(2^n)$

Độ phức tạp lũy thừa thường gặp ở cây nhị phân. Hãy quan sát hình sau: một "cây nhị phân đầy đủ" có $n$ tầng có $2^n - 1$ nút, chiếm $O(2^n)$ không gian:

```src
[file]{space_complexity}-[class]{}-[func]{build_tree}
```

![Độ phức tạp không gian lũy thừa do cây nhị phân đầy đủ tạo ra](space_complexity.assets/space_complexity_exponential.png)

### Độ phức tạp logarit $O(\log n)$

Độ phức tạp logarit thường gặp trong các thuật toán chia để trị. Ví dụ, merge sort: với một mảng đầu vào có độ dài $n$, mỗi lần đệ quy chia đôi mảng từ điểm giữa, tạo thành một cây đệ quy có chiều cao $\log n$, sử dụng $O(\log n)$ không gian stack frame.

Một ví dụ khác là chuyển đổi một số thành chuỗi. Với một số nguyên dương $n$, số đó có $\lfloor \log_{10} n \rfloor + 1$ chữ số, tức là độ dài chuỗi tương ứng là $\lfloor \log_{10} n \rfloor + 1$, vì vậy độ phức tạp không gian là $O(\log_{10} n + 1) = O(\log n)$.

## Đánh đổi thời gian và không gian

Lý tưởng nhất là độ phức tạp thời gian và độ phức tạp không gian của một thuật toán đều đạt mức tối ưu. Tuy nhiên, trên thực tế, việc tối ưu đồng thời cả độ phức tạp thời gian và độ phức tạp không gian thường rất khó.

**Việc giảm độ phức tạp thời gian thường phải trả giá bằng việc tăng độ phức tạp không gian, và ngược lại**. Hy sinh không gian bộ nhớ để cải thiện tốc độ thực thi được gọi là "đánh đổi không gian lấy thời gian"; ngược lại được gọi là "đánh đổi thời gian lấy không gian".

Việc lựa chọn phương pháp nào phụ thuộc vào khía cạnh mà chúng ta coi trọng hơn. Trong hầu hết trường hợp, thời gian quý giá hơn không gian, vì vậy "đánh đổi không gian lấy thời gian" thường là chiến lược phổ biến hơn. Dĩ nhiên, khi khối lượng dữ liệu rất lớn, việc kiểm soát độ phức tạp không gian cũng rất quan trọng.