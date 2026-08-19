# Độ phức tạp không gian

<u>Độ phức tạp không gian (space complexity)</u> dùng để đo lường xu hướng tăng trưởng của không gian bộ nhớ mà thuật toán chiếm dụng khi quy mô dữ liệu ngày càng lớn. Khái niệm này rất tương đồng với độ phức tạp thời gian, chỉ cần thay "thời gian thực thi" bằng "không gian bộ nhớ chiếm dụng".

## Các loại không gian liên quan đến thuật toán

Không gian bộ nhớ mà thuật toán sử dụng trong quá trình thực thi chủ yếu bao gồm các loại sau:

- **Không gian đầu vào**: Dùng để lưu trữ dữ liệu đầu vào của thuật toán.
- **Không gian tạm thời**: Dùng để lưu trữ các biến, đối tượng, ngữ cảnh hàm và các dữ liệu phát sinh trong quá trình chạy thuật toán.
- **Không gian đầu ra**: Dùng để lưu trữ dữ liệu đầu ra của thuật toán.

Thông thường, phạm vi thống kê của độ phức tạp không gian là "không gian tạm thời" cộng với "không gian đầu ra".

Không gian tạm thời có thể chia nhỏ hơn thành ba phần:

- **Dữ liệu tạm thời**: Dùng để lưu các hằng số, biến số, đối tượng, v.v. trong quá trình chạy thuật toán.
- **Khung ngăn xếp (stack frame)**: Dùng để lưu dữ liệu ngữ cảnh của các hàm được gọi. Mỗi khi gọi một hàm, hệ thống sẽ tạo một khung ngăn xếp ở đỉnh ngăn xếp, và khi hàm trả về thì khung ngăn xếp đó sẽ được giải phóng.
- **Không gian chỉ lệnh**: Dùng để lưu các lệnh chương trình sau khi biên dịch, trong thống kê thực tế thường được bỏ qua không tính.

Khi phân tích độ phức tạp không gian của một chương trình, **chúng ta thường thống kê ba phần: dữ liệu tạm thời, khung ngăn xếp và dữ liệu đầu ra**, như minh hoạ trong hình dưới đây.

![Các loại không gian liên quan được thuật toán sử dụng](space_complexity.assets/space_types.png)

Đoạn mã liên quan như sau:

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
        A = 0                 # Dữ liệu tạm thời (hằng số, thường dùng chữ in hoa)
        b = 0                 # Dữ liệu tạm thời (biến)
        node = Node(0)        # Dữ liệu tạm thời (đối tượng)
        c = function()        # Khung ngăn xếp (gọi hàm)
        return A + b + c      # Dữ liệu đầu ra
    ```

=== "C++"

    ```cpp title=""
    struct Node {
        int val;
        Node *next;
        Node(int x) : val(x), next(nullptr) {}
    };

    int function() {
        // Thực hiện một số thao tác...
        return 0;
    }

    int algorithm(int n) {        // Dữ liệu đầu vào
        const int a = 0;          // Dữ liệu tạm thời (hằng số)
        int b = 0;                // Dữ liệu tạm thời (biến)
        Node* node = new Node(0); // Dữ liệu tạm thời (đối tượng)
        int c = function();       // Khung ngăn xếp (gọi hàm)
        return a + b + c;         // Dữ liệu đầu ra
    }
    ```

=== "Java"

    ```java title=""
    class Node {
        int val;
        Node next;
        Node(int x) { val = x; }
    }

    int function() {
        // Thực hiện một số thao tác...
        return 0;
    }

    int algorithm(int n) {        // Dữ liệu đầu vào
        final int a = 0;          // Dữ liệu tạm thời (hằng số)
        int b = 0;                // Dữ liệu tạm thời (biến)
        Node node = new Node(0);  // Dữ liệu tạm thời (đối tượng)
        int c = function();       // Khung ngăn xếp (gọi hàm)
        return a + b + c;         // Dữ liệu đầu ra
    }
    ```

=== "C#"

    ```csharp title=""
    class Node {
        int val;
        Node next;
        public Node(int x) { val = x; }
    }

    int Function() {
        // Thực hiện một số thao tác...
        return 0;
    }

    int Algorithm(int n) {        // Dữ liệu đầu vào
        const int a = 0;          // Dữ liệu tạm thời (hằng số)
        int b = 0;                // Dữ liệu tạm thời (biến)
        Node node = new Node(0);  // Dữ liệu tạm thời (đối tượng)
        int c = Function();       // Khung ngăn xếp (gọi hàm)
        return a + b + c;         // Dữ liệu đầu ra
    }
    ```

=== "Go"

    ```go title=""
    type node struct {
        val  int
        next *node
    }

    func newNode(val int) *node {
        return &node{val: val}
    }

    func function() int {
        // Thực hiện một số thao tác...
        return 0
    }

    func algorithm(n int) int { // Dữ liệu đầu vào
        const a = 0             // Dữ liệu tạm thời (hằng số)
        b := 0                  // Dữ liệu tạm thời (biến)
        newNode(0)              // Dữ liệu tạm thời (đối tượng)
        c := function()         // Khung ngăn xếp (gọi hàm)
        return a + b + c        // Dữ liệu đầu ra
    }
    ```

=== "Swift"

    ```swift title=""
    class Node {
        var val: Int
        var next: Node?
        init(x: Int) {
            val = x
        }
    }

    func function() -> Int {
        // Thực hiện một số thao tác...
        return 0
    }

    func algorithm(n: Int) -> Int { // Dữ liệu đầu vào
        let a = 0 // Dữ liệu tạm thời (hằng số)
        var b = 0 // Dữ liệu tạm thời (biến)
        let node = Node(x: 0) // Dữ liệu tạm thời (đối tượng)
        let c = function() // Khung ngăn xếp (gọi hàm)
        return a + b + c // Dữ liệu đầu ra
    }
    ```

=== "JS"

    ```javascript title=""
    function constFunc() {
        // Thực hiện một số thao tác...
        return 0;
    }

    function algorithm(n) {       // Dữ liệu đầu vào
        const a = 0;              // Dữ liệu tạm thời (hằng số)
        let b = 0;                // Dữ liệu tạm thời (biến)
        const node = new Object();// Dữ liệu tạm thời (đối tượng)
        const c = constFunc();    // Khung ngăn xếp (gọi hàm)
        return a + b + c;         // Dữ liệu đầu ra
    }
    ```

=== "TS"

    ```typescript title=""
    function constFunc(): number {
        // Thực hiện một số thao tác...
        return 0;
    }

    function algorithm(n: number): number { // Dữ liệu đầu vào
        const a = 0;                        // Dữ liệu tạm thời (hằng số)
        let b = 0;                          // Dữ liệu tạm thời (biến)
        const node = new Object();          // Dữ liệu tạm thời (đối tượng)
        const c = constFunc();              // Khung ngăn xếp (gọi hàm)
        return a + b + c;                   // Dữ liệu đầu ra
    }
    ```

=== "Dart"

    ```dart title=""
    class Node {
      int val;
      Node? next;
      Node(this.val, [this.next]);
    }

    int function() {
      // Thực hiện một số thao tác...
      return 0;
    }

    int algorithm(int n) {        // Dữ liệu đầu vào
      const int a = 0;            // Dữ liệu tạm thời (hằng số)
      int b = 0;                  // Dữ liệu tạm thời (biến)
      Node node = Node(0);        // Dữ liệu tạm thời (đối tượng)
      int c = function();         // Khung ngăn xếp (gọi hàm)
      return a + b + c;           // Dữ liệu đầu ra
    }
    ```

=== "Rust"

    ```rust title=""
    fn function() -> i32 {
        // Thực hiện một số thao tác...
        0
    }

    fn algorithm(n: i32) -> i32 { // Dữ liệu đầu vào
        let a = 0;                // Dữ liệu tạm thời (hằng số)
        let mut b = 0;            // Dữ liệu tạm thời (biến)
        let c = function();       // Khung ngăn xếp (gọi hàm)
        a + b + c                 // Dữ liệu đầu ra
    }
    ```

=== "C"

    ```c title=""
    struct Node {
        int val;
        struct Node *next;
    };

    typedef struct Node Node;

    Node *newNode(int val) {
        Node *node = (Node *)malloc(sizeof(Node));
        node->val = val;
        node->next = NULL;
        return node;
    }

    int function() {
        // Thực hiện một số thao tác...
        return 0;
    }

    int algorithm(int n) {     // Dữ liệu đầu vào
        const int a = 0;       // Dữ liệu tạm thời (hằng số)
        int b = 0;             // Dữ liệu tạm thời (biến)
        Node *node = newNode(0);// Dữ liệu tạm thời (đối tượng)
        int c = function();    // Khung ngăn xếp (gọi hàm)
        return a + b + c;      // Dữ liệu đầu ra
    }
    ```

=== "Kotlin"

    ```kotlin title=""
    class Node(var `val`: Int) {
        var next: Node? = null
    }

    fun function(): Int {
        // Thực hiện một số thao tác...
        return 0
    }

    fun algorithm(n: Int): Int { // Dữ liệu đầu vào
        val a = 0                // Dữ liệu tạm thời (hằng số)
        var b = 0                // Dữ liệu tạm thời (biến)
        val node = Node(0)       // Dữ liệu tạm thời (đối tượng)
        val c = function()       // Khung ngăn xếp (gọi hàm)
        return a + b + c         // Dữ liệu đầu ra
    }
    ```

=== "Ruby"

    ```ruby title=""
    class Node
        attr_accessor :val, :next

        def initialize(val)
            @val = val
            @next = nil
        end
    end

    def function
        # Thực hiện một số thao tác...
        0
    end

    def algorithm(n)            # Dữ liệu đầu vào
        a = 0                   # Dữ liệu tạm thời (hằng số, ruby quy ước hằng viết hoa)
        b = 0                   # Dữ liệu tạm thời (biến)
        node = Node.new(0)      # Dữ liệu tạm thời (đối tượng)
        c = function            # Khung ngăn xếp (gọi hàm)
        a + b + c               # Dữ liệu đầu ra
    end
    ```

=== "Zig"

    ```zig title=""
    const Node = struct {
        val: i32,
        next: ?*Node,
        pub fn init(val: i32) Node {
            return Node{ .val = val, .next = null };
        }
    };

    fn function() i32 {
        // Thực hiện một số thao tác...
        return 0;
    }

    fn algorithm(n: i32) i32 {  // Dữ liệu đầu vào
        _ = n;
        const a: i32 = 0;       // Dữ liệu tạm thời (hằng số)
        var b: i32 = 0;         // Dữ liệu tạm thời (biến)
        _ = b;
        b = 1;
        var node = Node.init(0);// Dữ liệu tạm thời (đối tượng)
        _ = node;
        const c = function();   // Khung ngăn xếp (gọi hàm)
        return a + b + c;       // Dữ liệu đầu ra
    }
    ```

## Phương pháp suy diễn

Phương pháp suy diễn độ phức tạp không gian nhìn chung tương tự như độ phức tạp thời gian, chỉ cần chuyển đối tượng thống kê từ "số lượng thao tác" sang "dung lượng không gian sử dụng".

Khác với độ phức tạp thời gian, **chúng ta thường chỉ quan tâm đến độ phức tạp không gian trường hợp xấu nhất**. Điều này là do không gian bộ nhớ là một yêu cầu phần cứng cứng nhắc, chúng ta bắt buộc phải đảm bảo luôn có đủ không gian bộ nhớ dự phòng trong mọi trường hợp dữ liệu đầu vào.

Quan sát đoạn mã dưới đây, chữ "xấu nhất" trong độ phức tạp không gian trường hợp xấu nhất mang hai tầng ý nghĩa:

1. **Lấy dữ liệu đầu vào xấu nhất làm chuẩn**: Khi $n < 10$, độ phức tạp không gian là $O(1)$; nhưng khi $n > 10$, mảng `nums` được khởi tạo chiếm dụng $O(n)$ không gian, do đó độ phức tạp không gian trường hợp xấu nhất là $O(n)$.
2. **Lấy mức sử dụng bộ nhớ đỉnh điểm (peak memory) trong quá trình thực thi làm chuẩn**: Ví dụ, trước khi thực hiện dòng mã cuối cùng, chương trình chiếm $O(1)$ không gian; khi khởi tạo mảng `nums`, chương trình chiếm $O(n)$ không gian, do đó độ phức tạp không gian trường hợp xấu nhất là $O(n)$.

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
        a := 0               // O(1)
        b := make([]int, 10000) // O(1)
        if n > 10 {
            nums := make([]int, n) // O(n)
            _ = nums
        }
        _ = a
        _ = b
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
        const a: number = 0;                   // O(1)
        const b: Array<number> = new Array(10000); // O(1)
        if (n > 10) {
            const nums: Array<number> = new Array(n); // O(n)
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
        let a = 0;                         // O(1)
        let b = [0; 10000];                // O(1)
        if n > 10 {
            let nums = vec![0; n as usize];// O(n)
        }
    }
    ```

=== "C"

    ```c title=""
    void algorithm(int n) {
        int a = 0;                          // O(1)
        int b[10000];                       // O(1)
        if (n > 10) {
            int *nums = (int *)malloc(sizeof(int) * n); // O(n)
            free(nums);
        }
    }
    ```

=== "Kotlin"

    ```kotlin title=""
    fun algorithm(n: Int) {
        val a = 0                     // O(1)
        val b = IntArray(10000)       // O(1)
        if (n > 10) {
            val nums = IntArray(n)    // O(n)
        }
    }
    ```

=== "Ruby"

    ```ruby title=""
    def algorithm(n)
        a = 0                 # O(1)
        b = Array.new(10000)  # O(1)
        if n > 10
            nums = Array.new(n) # O(n)
        end
    end
    ```

=== "Zig"

    ```zig title=""
    fn algorithm(n: usize, allocator: std.mem.Allocator) !void {
        var a: i32 = 0; // O(1)
        _ = a;
        var b: [10000]i32 = undefined; // O(1)
        _ = b;
        if (n > 10) {
            var nums = try allocator.alloc(i32, n); // O(n)
            defer allocator.free(nums);
        }
    }
    ```

Trong các hàm đệ quy, việc phân tích không gian cần tính đến khung ngăn xếp:

=== "Python"

    ```python title=""
    def function() -> int:
        # Thực hiện một số thao tác
        return 0

    def loop(n: int):
        """Độ phức tạp không gian của vòng lặp là O(1)"""
        for _ in range(n):
            function()

    def recur(n: int):
        """Độ phức tạp không gian của đệ quy là O(n)"""
        if n == 1:
            return
        return recur(n - 1)
    ```

=== "C++"

    ```cpp title=""
    int function() {
        // Thực hiện một số thao tác
        return 0;
    }
    /* Độ phức tạp không gian của vòng lặp là O(1) */
    void loop(int n) {
        for (int i = 0; i < n; i++) {
            function();
        }
    }
    /* Độ phức tạp không gian của đệ quy là O(n) */
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
    /* Độ phức tạp không gian của vòng lặp là O(1) */
    void loop(int n) {
        for (int i = 0; i < n; i++) {
            function();
        }
    }
    /* Độ phức tạp không gian của đệ quy là O(n) */
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
    /* Độ phức tạp không gian của vòng lặp là O(1) */
    void Loop(int n) {
        for (int i = 0; i < n; i++) {
            Function();
        }
    }
    /* Độ phức tạp không gian của đệ quy là O(n) */
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
    
    /* Độ phức tạp không gian của vòng lặp là O(1) */
    func loop(n int) {
        for i := 0; i < n; i++ {
            function()
        }
    }
    
    /* Độ phức tạp không gian của đệ quy là O(n) */
    func recur(n int) {
        if n == 1 {
            return
        }
        recur(n - 1)
    }
    ```

=== "Swift"

    ```swift title=""
    func function() -> Int {
        // Thực hiện một số thao tác
        return 0
    }

    /* Độ phức tạp không gian của vòng lặp là O(1) */
    func loop(n: Int) {
        for _ in 0 ..< n {
            function()
        }
    }

    /* Độ phức tạp không gian của đệ quy là O(n) */
    func recur(n: Int) {
        if n == 1 {
            return
        }
        recur(n: n - 1)
    }
    ```

=== "JS"

    ```javascript title=""
    function functionTmp() {
        // Thực hiện một số thao tác
        return 0;
    }
    /* Độ phức tạp không gian của vòng lặp là O(1) */
    function loop(n) {
        for (let i = 0; i < n; i++) {
            functionTmp();
        }
    }
    /* Độ phức tạp không gian của đệ quy là O(n) */
    function recur(n) {
        if (n === 1) return;
        return recur(n - 1);
    }
    ```

=== "TS"

    ```typescript title=""
    function functionTmp(): number {
        // Thực hiện một số thao tác
        return 0;
    }
    /* Độ phức tạp không gian của vòng lặp là O(1) */
    function loop(n: number): void {
        for (let i = 0; i < n; i++) {
            functionTmp();
        }
    }
    /* Độ phức tạp không gian của đệ quy là O(n) */
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
    /* Độ phức tạp không gian của vòng lặp là O(1) */
    void loop(int n) {
      for (int i = 0; i < n; i++) {
        function();
      }
    }
    /* Độ phức tạp không gian của đệ quy là O(n) */
    void recur(int n) {
      if (n == 1) return;
      recur(n - 1);
    }
    ```

=== "Rust"

    ```rust title=""
    fn function() -> i32 {
        // Thực hiện một số thao tác
        0
    }
    /* Độ phức tạp không gian của vòng lặp là O(1) */
    fn loop_fn(n: i32) {
        for _ in 0..n {
            function();
        }
    }
    /* Độ phức tạp không gian của đệ quy là O(n) */
    fn recur(n: i32) {
        if n == 1 {
            return;
        }
        recur(n - 1);
    }
    ```

=== "C"

    ```c title=""
    int function() {
        // Thực hiện một số thao tác
        return 0;
    }
    /* Độ phức tạp không gian của vòng lặp là O(1) */
    void loop(int n) {
        for (int i = 0; i < n; i++) {
            function();
        }
    }
    /* Độ phức tạp không gian của đệ quy là O(n) */
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
    /* Độ phức tạp không gian của vòng lặp là O(1) */
    fun loop(n: Int) {
        for (i in 0..<n) {
            function()
        }
    }
    /* Độ phức tạp không gian của đệ quy là O(n) */
    fun recur(n: Int) {
        if (n == 1) return
        recur(n - 1)
    }
    ```

=== "Ruby"

    ```ruby title=""
    def function
        # Thực hiện một số thao tác
        0
    end

    ### Độ phức tạp không gian của vòng lặp là O(1) ###
    def loop(n)
        (0...n).each do
            function
        end
    end

    ### Độ phức tạp không gian của đệ quy là O(n) ###
    def recur(n)
        return if n == 1
        recur(n - 1)
    end
    ```

=== "Zig"

    ```zig title=""
    fn function() i32 {
        // Thực hiện một số thao tác
        return 0;
    }
    // Độ phức tạp không gian của vòng lặp là O(1)
    fn loopFn(n: usize) void {
        var i: usize = 0;
        while (i < n) : (i += 1) {
            _ = function();
        }
    }
    // Độ phức tạp không gian của đệ quy là O(n)
    fn recur(n: usize) void {
        if (n == 1) return;
        recur(n - 1);
    }
    ```

Hai hàm `loop()` và `recur()` đều có độ phức tạp thời gian là $O(n)$, nhưng độ phức tạp không gian lại hoàn toàn khác nhau:

- Hàm `loop()` trong vòng lặp gọi $n$ lần `function()`, ở mỗi vòng hàm `function()` đều trả về và giải phóng khung ngăn xếp, do đó độ phức tạp không gian vẫn là $O(1)$.
- Hàm đệ quy `recur()` trong quá trình chạy sẽ đồng thời tồn tại $n$ hàm `recur()` chưa trả về, do đó chiếm dụng $O(n)$ không gian khung ngăn xếp.

## Các dạng thường gặp

Giả sử kích thước dữ liệu đầu vào là $n$, hình dưới đây thể hiện các dạng độ phức tạp không gian thường gặp (xếp từ thấp đến cao).

$$
\begin{aligned}
& O(1) < O(\log n) < O(n) < O(n^2) < O(2^n) \newline
& \text{Bậc hằng số} < \text{Bậc đối số} < \text{Bậc tuyến tính} < \text{Bậc bình phương} < \text{Bậc mũ}
\end{aligned}
$$

![Các dạng độ phức tạp không gian thường gặp](space_complexity.assets/space_complexity_common_types.png)

### Bậc hằng số $O(1)$

Bậc hằng số thường thấy ở các hằng số, biến số, đối tượng có số lượng độc lập với kích thước dữ liệu đầu vào $n$.

Cần lưu ý rằng bộ nhớ bị chiếm dụng do khởi tạo biến hoặc gọi hàm trong vòng lặp sẽ được giải phóng ngay khi bước sang vòng lặp tiếp theo, do đó không bị tích luỹ không gian và độ phức tạp không gian vẫn là $O(1)$:

```src
[file]{space_complexity}-[class]{}-[func]{constant}
```

### Bậc tuyến tính $O(n)$

Bậc tuyến tính thường thấy ở mảng, danh sách liên kết, ngăn xếp, hàng đợi, v.v., có số lượng phần tử tỷ lệ thuận với $n$:

```src
[file]{space_complexity}-[class]{}-[func]{linear}
```

Như minh hoạ dưới đây, độ sâu đệ quy của hàm này là $n$, tức là đồng thời tồn tại $n$ hàm `linear_recur()` chưa trả về, sử dụng không gian khung ngăn xếp có kích thước $O(n)$:

```src
[file]{space_complexity}-[class]{}-[func]{linear_recur}
```

![Độ phức tạp không gian bậc tuyến tính sinh ra bởi hàm đệ quy](space_complexity.assets/space_complexity_recursive_linear.png)

### Bậc bình phương $O(n^2)$

Bậc bình phương thường thấy ở ma trận và đồ thị, khi số lượng phần tử có mối quan hệ hàm bậc hai với $n$:

```src
[file]{space_complexity}-[class]{}-[func]{quadratic}
```

Như minh hoạ dưới đây, độ sâu đệ quy của hàm này là $n$, và trong mỗi hàm đệ quy đều khởi tạo một mảng có độ dài lần lượt là $n$, $n-1$, $\dots$, $2$, $1$, độ dài trung bình là $n / 2$, do đó tổng thể chiếm dụng $O(n^2)$ không gian:

```src
[file]{space_complexity}-[class]{}-[func]{quadratic_recur}
```

![Độ phức tạp không gian bậc bình phương sinh ra bởi hàm đệ quy](space_complexity.assets/space_complexity_recursive_quadratic.png)

### Bậc mũ $O(2^n)$

Bậc mũ thường thấy trong cây nhị phân. Quan sát hình dưới đây, một "cây nhị phân đầy đủ" có số tầng là $n$ sẽ có số lượng nút là $2^n - 1$, chiếm dụng $O(2^n)$ không gian:

```src
[file]{space_complexity}-[class]{}-[func]{build_tree}
```

![Độ phức tạp không gian bậc mũ sinh ra bởi cây nhị phân đầy đủ](space_complexity.assets/space_complexity_exponential.png)

### Bậc đối số $O(\log n)$

Bậc đối số thường thấy trong các thuật toán chia để trị. Ví dụ như thuật toán sắp xếp trộn (merge sort), với đầu vào là mảng có độ dài $n$, mỗi vòng đệ quy sẽ chia đôi mảng tại điểm giữa, tạo thành cây đệ quy có chiều cao là $\log n$ và sử dụng $O(\log n)$ không gian khung ngăn xếp.

Một ví dụ khác là chuyển đổi số thành chuỗi ký tự: với đầu vào là một số nguyên dương $n$, số chữ số của nó là $\lfloor \log_{10} n \rfloor + 1$, tương ứng độ dài chuỗi là $\lfloor \log_{10} n \rfloor + 1$, do đó độ phức tạp không gian là $O(\log_{10} n + 1) = O(\log n)$.

## Đánh đổi giữa thời gian và không gian

Trong điều kiện lý tưởng, chúng ta mong muốn cả độ phức tạp thời gian và độ phức tạp không gian của thuật toán đều đạt mức tối ưu. Tuy nhiên trong thực tế, việc tối ưu hoá đồng thời cả thời gian và không gian thường vô cùng khó khăn.

**Giảm độ phức tạp thời gian thường phải trả giá bằng việc tăng độ phức tạp không gian, và ngược lại**. Chúng ta gọi tư duy hy sinh không gian bộ nhớ để nâng cao tốc độ thực thi của thuật toán là "đổi không gian lấy thời gian"; ngược lại, được gọi là "đổi thời gian lấy không gian".

Việc lựa chọn hướng đi nào phụ thuộc vào khía cạnh mà chúng ta xem trọng hơn. Trong đa số trường hợp, thời gian quý giá hơn không gian bộ nhớ, vì vậy "đổi không gian lấy thời gian" thường là chiến lược phổ biến hơn. Dĩ nhiên, khi lượng dữ liệu cực lớn thì việc kiểm soát độ phức tạp không gian cũng đóng vai trò vô cùng hệ trọng.
