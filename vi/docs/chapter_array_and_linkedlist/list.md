# Danh sách

<u>Danh sách (list)</u> là một khái niệm cấu trúc dữ liệu trừu tượng, biểu thị một tập hợp các phần tử có thứ tự, hỗ trợ các thao tác như truy cập, sửa đổi, thêm, xoá và duyệt phần tử mà người dùng không cần bận tâm đến vấn đề giới hạn sức chứa. Danh sách có thể được hiện thực dựa trên danh sách liên kết hoặc mảng.

- Danh sách liên kết về bản chất tự nhiên có thể coi như một danh sách: nó hỗ trợ đầy đủ các thao tác thêm, xoá, tra cứu, sửa đổi phần tử, đồng thời có thể mở rộng dung lượng động một cách linh hoạt.
- Mảng cũng hỗ trợ các thao tác thêm, xoá, tra cứu, sửa đổi phần tử, nhưng do độ dài cố định nên chỉ có thể coi như một danh sách có giới hạn độ dài.

Khi dùng mảng để hiện thực danh sách, **đặc tính độ dài không đổi sẽ làm giảm tính thực tiễn của danh sách**. Điều này là do thông thường chúng ta không thể xác định trước cần lưu trữ bao nhiêu dữ liệu, từ đó rất khó chọn được độ dài danh sách phù hợp. Nếu độ dài quá nhỏ sẽ khó đáp ứng được nhu cầu sử dụng; nếu độ dài quá lớn lại gây lãng phí không gian bộ nhớ.

Để giải quyết vấn đề này, chúng ta có thể sử dụng <u>mảng động (dynamic array)</u> để hiện thực danh sách. Nó kế thừa trọn vẹn mọi ưu điểm của mảng, đồng thời có thể tự động mở rộng dung lượng linh hoạt trong quá trình chương trình vận hành.

Trên thực tế, **danh sách do thư viện chuẩn của nhiều ngôn ngữ lập trình cung cấp được hiện thực dựa trên mảng động**, ví dụ như `list` trong Python, `ArrayList` trong Java, `vector` trong C++, `List` trong C#, v.v. Trong các phần thảo luận tiếp theo, chúng ta sẽ coi "danh sách" và "mảng động" là hai khái niệm tương đương nhau.

## Các thao tác thường dùng trên danh sách

### Khởi tạo danh sách

Chúng ta thường sử dụng hai cách khởi tạo: "không có giá trị ban đầu" và "có sẵn giá trị ban đầu":

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
    // Cần lưu ý, vector trong C++ tương đương với nums được mô tả trong bài này
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
    // Có giá trị ban đầu (lưu ý kiểu phần tử mảng cần là lớp bao Integer[] của int[])
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
    var nums1 []int
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
    // C không cung cấp mảng động tích hợp sẵn
    ```

=== "Kotlin"

    ```kotlin title="list.kt"
    /* Khởi tạo danh sách */
    // Không có giá trị ban đầu
    val nums1 = ArrayList<Int>()
    // Có giá trị ban đầu
    val nums = mutableListOf(1, 3, 2, 5, 4)
    ```

=== "Ruby"

    ```ruby title="list.rb"
    # Khởi tạo danh sách
    # Không có giá trị ban đầu
    nums1 = []
    # Có giá trị ban đầu
    nums = [1, 3, 2, 5, 4]
    ```

=== "Zig"

    ```zig title="list.zig"
    // Khởi tạo danh sách
    // Không có giá trị ban đầu
    var nums1 = std.ArrayList(i32).init(std.heap.page_allocator);
    defer nums1.deinit();
    // Có giá trị ban đầu
    var nums = std.ArrayList(i32).init(std.heap.page_allocator);
    defer nums.deinit();
    try nums.appendSlice(&[_]i32{ 1, 3, 2, 5, 4 });
    ```

??? pythontutor "Trực quan hoá thực thi"

    https://pythontutor.com/render.html#code=%22%22%22Driver%20Code%22%22%22%0Aif%20__name__%20%3D%3D%20%22__main__%22%3A%0A%20%20%20%20%23%20%E5%88%9D%E5%A7%8B%E5%8C%96%E5%88%97%E8%A1%A8%0A%20%20%20%20%23%20%E6%97%A0%E5%88%9D%E5%A7%8B%E5%8C%96%E5%80%BC%0A%20%20%20%20nums1%20%3D%20%5B%5D%0A%20%20%20%20%23%20%E6%9C%89%E5%88%9D%E5%A7%8B%E5%80%BC%0A%20%20%20%20nums%20%3D%20%5B1,%203,%202,%205,%204%5D&cumulative=false&curInstr=4&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=311&rawInputLstJSON=%5B%5D&textReferences=false

### Truy cập phần tử

Danh sách về bản chất là mảng, do đó có thể truy cập và cập nhật phần tử trong thời gian $O(1)$ với hiệu năng rất cao.

=== "Python"

    ```python title="list.py"
    # Truy cập phần tử
    num: int = nums[1]  # Truy cập phần tử tại chỉ số 1

    # Cập nhật phần tử
    nums[1] = 0    # Cập nhật phần tử tại chỉ số 1 thành 0
    ```

=== "C++"

    ```cpp title="list.cpp"
    /* Truy cập phần tử */
    int num = nums[1];  // Truy cập phần tử tại chỉ số 1

    /* Cập nhật phần tử */
    nums[1] = 0;  // Cập nhật phần tử tại chỉ số 1 thành 0
    ```

=== "Java"

    ```java title="list.java"
    /* Truy cập phần tử */
    int num = nums.get(1);  // Truy cập phần tử tại chỉ số 1

    /* Cập nhật phần tử */
    nums.set(1, 0);  // Cập nhật phần tử tại chỉ số 1 thành 0
    ```

=== "C#"

    ```csharp title="list.cs"
    /* Truy cập phần tử */
    int num = nums[1];  // Truy cập phần tử tại chỉ số 1

    /* Cập nhật phần tử */
    nums[1] = 0;  // Cập nhật phần tử tại chỉ số 1 thành 0
    ```

=== "Go"

    ```go title="list_test.go"
    /* Truy cập phần tử */
    num := nums[1]  // Truy cập phần tử tại chỉ số 1

    /* Cập nhật phần tử */
    nums[1] = 0     // Cập nhật phần tử tại chỉ số 1 thành 0
    ```

=== "Swift"

    ```swift title="list.swift"
    /* Truy cập phần tử */
    let num = nums[1] // Truy cập phần tử tại chỉ số 1

    /* Cập nhật phần tử */
    nums[1] = 0 // Cập nhật phần tử tại chỉ số 1 thành 0
    ```

=== "JS"

    ```javascript title="list.js"
    /* Truy cập phần tử */
    const num = nums[1];  // Truy cập phần tử tại chỉ số 1

    /* Cập nhật phần tử */
    nums[1] = 0;  // Cập nhật phần tử tại chỉ số 1 thành 0
    ```

=== "TS"

    ```typescript title="list.ts"
    /* Truy cập phần tử */
    const num: number = nums[1];  // Truy cập phần tử tại chỉ số 1

    /* Cập nhật phần tử */
    nums[1] = 0;  // Cập nhật phần tử tại chỉ số 1 thành 0
    ```

=== "Dart"

    ```dart title="list.dart"
    /* Truy cập phần tử */
    int num = nums[1];  // Truy cập phần tử tại chỉ số 1

    /* Cập nhật phần tử */
    nums[1] = 0;  // Cập nhật phần tử tại chỉ số 1 thành 0
    ```

=== "Rust"

    ```rust title="list.rs"
    /* Truy cập phần tử */
    let num: i32 = nums[1];  // Truy cập phần tử tại chỉ số 1
    /* Cập nhật phần tử */
    nums[1] = 0;             // Cập nhật phần tử tại chỉ số 1 thành 0
    ```

=== "C"

    ```c title="list.c"
    // C không cung cấp mảng động tích hợp sẵn
    ```

=== "Kotlin"

    ```kotlin title="list.kt"
    /* Truy cập phần tử */
    val num = nums[1]       // Truy cập phần tử tại chỉ số 1
    /* Cập nhật phần tử */
    nums[1] = 0             // Cập nhật phần tử tại chỉ số 1 thành 0
    ```

=== "Ruby"

    ```ruby title="list.rb"
    # Truy cập phần tử
    num = nums[1] # Truy cập phần tử tại chỉ số 1
    # Cập nhật phần tử
    nums[1] = 0 # Cập nhật phần tử tại chỉ số 1 thành 0
    ```

=== "Zig"

    ```zig title="list.zig"
    // Truy cập phần tử
    const num: i32 = nums.items[1]; // Truy cập phần tử tại chỉ số 1
    // Cập nhật phần tử
    nums.items[1] = 0; // Cập nhật phần tử tại chỉ số 1 thành 0
    ```

??? pythontutor "Trực quan hoá thực thi"

    https://pythontutor.com/render.html#code=%22%22%22Driver%20Code%22%22%22%0Aif%20__name__%20%3D%3D%20%22__main__%22%3A%0A%20%20%20%20%23%20%E5%88%9D%E5%A7%8B%E5%8C%96%E5%88%97%E8%A1%A8%0A%20%20%20%20nums%20%3D%20%5B1,%203,%202,%205,%204%5D%0A%0A%20%20%20%20%23%20%E8%AE%BF%E9%97%AE%E5%85%83%E7%B4%A0%0A%20%20%20%20num%20%3D%20nums%5B1%5D%20%20%23%20%E8%AE%BF%E9%97%AE%E7%B4%A2%E5%BC%95%201%20%E5%A4%84%E7%9A%84%E5%85%83%E7%B4%A0%0A%0A%20%20%20%20%23%20%E6%9B%B4%E6%96%B0%E5%85%83%E7%B4%A0%0A%20%20%20%20nums%5B1%5D%20%3D%200%20%20%20%20%23%20%E5%B0%86%E7%B4%A2%E5%BC%95%201%20%E5%A4%84%E7%9A%84%E5%85%83%E7%B4%A0%E6%9B%B4%E6%96%B0%E4%B8%BA%200&cumulative=false&curInstr=3&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=311&rawInputLstJSON=%5B%5D&textReferences=false

### Chèn và xoá phần tử

So với mảng, danh sách có thể tự do thêm và xoá phần tử. Việc thêm phần tử vào cuối danh sách có độ phức tạp thời gian là $O(1)$ ，nhưng thao tác chèn và xoá phần tử ở giữa vẫn có hiệu năng tương tự như mảng với độ phức tạp thời gian là $O(n)$ 。

=== "Python"

    ```python title="list.py"
    # Xoá sạch danh sách
    nums.clear()

    # Thêm phần tử vào cuối danh sách
    nums.append(1)
    nums.append(3)
    nums.append(2)
    nums.append(5)
    nums.append(4)

    # Chèn phần tử vào giữa danh sách
    nums.insert(3, 6)  # Chèn số 6 vào chỉ số 3

    # Xoá phần tử
    nums.pop(3)        # Xoá phần tử tại chỉ số 3
    ```

=== "C++"

    ```cpp title="list.cpp"
    /* Xoá sạch danh sách */
    nums.clear();

    /* Thêm phần tử vào cuối danh sách */
    nums.push_back(1);
    nums.push_back(3);
    nums.push_back(2);
    nums.push_back(5);
    nums.push_back(4);

    /* Chèn phần tử vào giữa danh sách */
    nums.insert(nums.begin() + 3, 6);  // Chèn số 6 vào chỉ số 3

    /* Xoá phần tử */
    nums.erase(nums.begin() + 3);      // Xoá phần tử tại chỉ số 3
    ```

=== "Java"

    ```java title="list.java"
    /* Xoá sạch danh sách */
    nums.clear();

    /* Thêm phần tử vào cuối danh sách */
    nums.add(1);
    nums.add(3);
    nums.add(2);
    nums.add(5);
    nums.add(4);

    /* Chèn phần tử vào giữa danh sách */
    nums.add(3, 6);  // Chèn số 6 vào chỉ số 3

    /* Xoá phần tử */
    nums.remove(3);  // Xoá phần tử tại chỉ số 3
    ```

=== "C#"

    ```csharp title="list.cs"
    /* Xoá sạch danh sách */
    nums.Clear();

    /* Thêm phần tử vào cuối danh sách */
    nums.Add(1);
    nums.Add(3);
    nums.Add(2);
    nums.Add(5);
    nums.Add(4);

    /* Chèn phần tử vào giữa danh sách */
    nums.Insert(3, 6);  // Chèn số 6 vào chỉ số 3

    /* Xoá phần tử */
    nums.RemoveAt(3);  // Xoá phần tử tại chỉ số 3
    ```

=== "Go"

    ```go title="list_test.go"
    /* Xoá sạch danh sách */
    nums = nil

    /* Thêm phần tử vào cuối danh sách */
    nums = append(nums, 1)
    nums = append(nums, 3)
    nums = append(nums, 2)
    nums = append(nums, 5)
    nums = append(nums, 4)

    /* Chèn phần tử vào giữa danh sách */
    nums = append(nums[:3], append([]int{6}, nums[3:]...)...) // Chèn số 6 vào chỉ số 3

    /* Xoá phần tử */
    nums = append(nums[:3], nums[4:]...) // Xoá phần tử tại chỉ số 3
    ```

=== "Swift"

    ```swift title="list.swift"
    /* Xoá sạch danh sách */
    nums.removeAll()

    /* Thêm phần tử vào cuối danh sách */
    nums.append(1)
    nums.append(3)
    nums.append(2)
    nums.append(5)
    nums.append(4)

    /* Chèn phần tử vào giữa danh sách */
    nums.insert(6, at: 3) // Chèn số 6 vào chỉ số 3

    /* Xoá phần tử */
    nums.remove(at: 3) // Xoá phần tử tại chỉ số 3
    ```

=== "JS"

    ```javascript title="list.js"
    /* Xoá sạch danh sách */
    nums.length = 0;

    /* Thêm phần tử vào cuối danh sách */
    nums.push(1);
    nums.push(3);
    nums.push(2);
    nums.push(5);
    nums.push(4);

    /* Chèn phần tử vào giữa danh sách */
    nums.splice(3, 0, 6);

    /* Xoá phần tử */
    nums.splice(3, 1);
    ```

=== "TS"

    ```typescript title="list.ts"
    /* Xoá sạch danh sách */
    nums.length = 0;

    /* Thêm phần tử vào cuối danh sách */
    nums.push(1);
    nums.push(3);
    nums.push(2);
    nums.push(5);
    nums.push(4);

    /* Chèn phần tử vào giữa danh sách */
    nums.splice(3, 0, 6);

    /* Xoá phần tử */
    nums.splice(3, 1);
    ```

=== "Dart"

    ```dart title="list.dart"
    /* Xoá sạch danh sách */
    nums.clear();

    /* Thêm phần tử vào cuối danh sách */
    nums.add(1);
    nums.add(3);
    nums.add(2);
    nums.add(5);
    nums.add(4);

    /* Chèn phần tử vào giữa danh sách */
    nums.insert(3, 6); // Chèn số 6 vào chỉ số 3

    /* Xoá phần tử */
    nums.removeAt(3); // Xoá phần tử tại chỉ số 3
    ```

=== "Rust"

    ```rust title="list.rs"
    /* Xoá sạch danh sách */
    nums.clear();

    /* Thêm phần tử vào cuối danh sách */
    nums.push(1);
    nums.push(3);
    nums.push(2);
    nums.push(5);
    nums.push(4);

    /* Chèn phần tử vào giữa danh sách */
    nums.insert(3, 6);  // Chèn số 6 vào chỉ số 3

    /* Xoá phần tử */
    nums.remove(3);     // Xoá phần tử tại chỉ số 3
    ```

=== "C"

    ```c title="list.c"
    // C không cung cấp mảng động tích hợp sẵn
    ```

=== "Kotlin"

    ```kotlin title="list.kt"
    /* Xoá sạch danh sách */
    nums.clear()

    /* Thêm phần tử vào cuối danh sách */
    nums.add(1)
    nums.add(3)
    nums.add(2)
    nums.add(5)
    nums.add(4)

    /* Chèn phần tử vào giữa danh sách */
    nums.add(3, 6)  // Chèn số 6 vào chỉ số 3

    /* Xoá phần tử */
    nums.removeAt(3) // Xoá phần tử tại chỉ số 3
    ```

=== "Ruby"

    ```ruby title="list.rb"
    # Xoá sạch danh sách
    nums.clear

    # Thêm phần tử vào cuối danh sách
    nums.push(1)
    nums.push(3)
    nums.push(2)
    nums.push(5)
    nums.push(4)

    # Chèn phần tử vào giữa danh sách
    nums.insert(3, 6) # Chèn số 6 vào chỉ số 3

    # Xoá phần tử
    nums.delete_at(3) # Xoá phần tử tại chỉ số 3
    ```

=== "Zig"

    ```zig title="list.zig"
    // Xoá sạch danh sách
    nums.clearRetainingCapacity();

    // Thêm phần tử vào cuối danh sách
    try nums.append(1);
    try nums.append(3);
    try nums.append(2);
    try nums.append(5);
    try nums.append(4);

    // Chèn phần tử vào giữa danh sách
    try nums.insert(3, 6); // Chèn số 6 vào chỉ số 3

    // Xoá phần tử
    _ = nums.orderedRemove(3); // Xoá phần tử tại chỉ số 3
    ```

??? pythontutor "Trực quan hoá thực thi"

    https://pythontutor.com/render.html#code=%22%22%22Driver%20Code%22%22%22%0Aif%20__name__%20%3D%3D%20%22__main__%22%3A%0A%20%20%20%20#%20%E5%88%9D%E5%A7%8B%E5%8C%96%E5%88%97%E8%A1%A8%0A%20%20%20%20nums%20%3D%20%5B1,%203,%202,%205,%204%5D%0A%0A%20%20%20%20#%20%E6%B8%85%E7%A9%BA%E5%88%97%E8%A1%A8%0A%20%20%20%20nums.clear%28%29%0A%0A%20%20%20%20#%20%E5%B0%BE%E9%83%A8%E6%B7%BB%E5%8A%A0%E5%85%83%E7%B4%A0%0A%20%20%20%20nums.append%281%29%0A%20%20%20%20nums.append%283%29%0A%20%20%20%20nums.append%282%29%0A%20%20%20%20nums.append%285%29%0A%20%20%20%20nums.append%284%29%0A%0A%20%20%20%20#%20%E4%B8%AD%E9%97%B4%E6%8F%92%E5%85%A5%E5%85%83%E7%B4%A0%0A%20%20%20%20nums.insert%283,%206%29%0A%0A%20%20%20%20#%20%E5%88%A0%E9%99%A4%E5%85%83%E7%B4%A0%0A%20%20%20%20nums.pop%283%29&cumulative=false&curInstr=12&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=311&rawInputLstJSON=%5B%5D&textReferences=false

### Duyệt danh sách

Tương tự như mảng, danh sách có thể duyệt thông qua chỉ số hoặc duyệt trực tiếp từng phần tử:

=== "Python"

    ```python title="list.py"
    # Duyệt danh sách qua chỉ số
    count = 0
    for i in range(len(nums)):
        count += nums[i]

    # Duyệt trực tiếp từng phần tử của danh sách
    for x in nums:
        count += x
    ```

=== "C++"

    ```cpp title="list.cpp"
    /* Duyệt danh sách qua chỉ số */
    int count = 0;
    for (int i = 0; i < nums.size(); i++) {
        count += nums[i];
    }

    /* Duyệt trực tiếp từng phần tử của danh sách */
    count = 0;
    for (int x : nums) {
        count += x;
    }
    ```

=== "Java"

    ```java title="list.java"
    /* Duyệt danh sách qua chỉ số */
    int count = 0;
    for (int i = 0; i < nums.size(); i++) {
        count += nums.get(i);
    }

    /* Duyệt trực tiếp từng phần tử của danh sách */
    count = 0;
    for (int x : nums) {
        count += x;
    }
    ```

=== "C#"

    ```csharp title="list.cs"
    /* Duyệt danh sách qua chỉ số */
    int count = 0;
    for (int i = 0; i < nums.Count; i++) {
        count += nums[i];
    }

    /* Duyệt trực tiếp từng phần tử của danh sách */
    count = 0;
    for (int x in nums) {
        count += x;
    }
    ```

=== "Go"

    ```go title="list_test.go"
    /* Duyệt danh sách qua chỉ số */
    count := 0
    for i := 0; i < len(nums); i++ {
        count += nums[i]
    }

    /* Duyệt trực tiếp từng phần tử của danh sách */
    count = 0
    for _, x := range nums {
        count += x
    }
    ```

=== "Swift"

    ```swift title="list.swift"
    /* Duyệt danh sách qua chỉ số */
    var count = 0
    for i in nums.indices {
        count += nums[i]
    }

    /* Duyệt trực tiếp từng phần tử của danh sách */
    count = 0
    for x in nums {
        count += x
    }
    ```

=== "JS"

    ```javascript title="list.js"
    /* Duyệt danh sách qua chỉ số */
    let count = 0;
    for (let i = 0; i < nums.length; i++) {
        count += nums[i];
    }

    /* Duyệt trực tiếp từng phần tử của danh sách */
    count = 0;
    for (const x of nums) {
        count += x;
    }
    ```

=== "TS"

    ```typescript title="list.ts"
    /* Duyệt danh sách qua chỉ số */
    let count = 0;
    for (let i = 0; i < nums.length; i++) {
        count += nums[i];
    }

    /* Duyệt trực tiếp từng phần tử của danh sách */
    count = 0;
    for (const x of nums) {
        count += x;
    }
    ```

=== "Dart"

    ```dart title="list.dart"
    /* Duyệt danh sách qua chỉ số */
    int count = 0;
    for (int i = 0; i < nums.length; i++) {
      count += nums[i];
    }

    /* Duyệt trực tiếp từng phần tử của danh sách */
    count = 0;
    for (int x in nums) {
      count += x;
    }
    ```

=== "Rust"

    ```rust title="list.rs"
    /* Duyệt danh sách qua chỉ số */
    let mut count = 0;
    for i in 0..nums.len() {
        count += nums[i];
    }

    /* Duyệt trực tiếp từng phần tử của danh sách */
    count = 0;
    for x in &nums {
        count += x;
    }
    ```

=== "C"

    ```c title="list.c"
    // C không cung cấp mảng động tích hợp sẵn
    ```

=== "Kotlin"

    ```kotlin title="list.kt"
    /* Duyệt danh sách qua chỉ số */
    var count = 0
    for (i in nums.indices) {
        count += nums[i]
    }

    /* Duyệt trực tiếp từng phần tử của danh sách */
    count = 0
    for (x in nums) {
        count += x
    }
    ```

=== "Ruby"

    ```ruby title="list.rb"
    # Duyệt danh sách qua chỉ số
    count = 0
    for i in 0...(nums.length)
        count += nums[i]
    end

    # Duyệt trực tiếp từng phần tử của danh sách
    count = 0
    for x in nums
        count += x
    end
    ```

=== "Zig"

    ```zig title="list.zig"
    // Duyệt danh sách qua chỉ số
    var count: i32 = 0;
    var i: usize = 0;
    while (i < nums.items.len) : (i += 1) {
        count += nums.items[i];
    }

    // Duyệt trực tiếp từng phần tử của danh sách
    count = 0;
    for (nums.items) |x| {
        count += x;
    }
    ```

??? pythontutor "Trực quan hoá thực thi"

    https://pythontutor.com/render.html#code=%22%22%22Driver%20Code%22%22%22%0Aif%20__name__%20%3D%3D%20%22__main__%22%3A%0A%20%20%20%20#%20%E5%88%9D%E5%A7%8B%E5%8C%96%E5%88%97%E8%A1%A8%0A%20%20%20%20nums%20%3D%20%5B1,%203,%202,%205,%204%5D%0A%0A%20%20%20%20#%20%E9%80%9A%E8%BF%87%E7%B4%A2%E5%BC%95%E9%81%8D%E5%8E%86%E5%88%97%E8%A1%A8%0A%20%20%20%20count%20%3D%200%0A%20%20%20%20for%20i%20in%20range%28len%28nums%29%29%3A%0A%20%20%20%20%20%20%20%20count%20%2B%3D%20nums%5Bi%5D%0A%0A%20%20%20%20#%20%E7%9B%B4%E6%8E%A5%E9%81%8D%E5%8E%86%E5%88%97%E8%A1%A8%E5%85%83%E7%B4%A0%0A%20%20%20%20count%20%3D%200%0A%20%20%20%20for%20x%20in%20nums%3A%0A%20%20%20%20%20%20%20%20count%20%2B%3D%20x&cumulative=false&curInstr=16&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=311&rawInputLstJSON=%5B%5D&textReferences=false

### Ghép nối danh sách

Cho một danh sách mới `nums1` ，chúng ta có thể ghép nối nó vào đuôi của danh sách ban đầu.

=== "Python"

    ```python title="list.py"
    # Ghép nối hai danh sách
    nums1: list[int] = [6, 8, 7, 10, 9]
    nums += nums1  # Ghép danh sách nums1 vào sau nums
    ```

=== "C++"

    ```cpp title="list.cpp"
    /* Ghép nối hai danh sách */
    vector<int> nums1 = { 6, 8, 7, 10, 9 };
    // Ghép danh sách nums1 vào sau nums
    nums.insert(nums.end(), nums1.begin(), nums1.end());
    ```

=== "Java"

    ```java title="list.java"
    /* Ghép nối hai danh sách */
    List<Integer> nums1 = new ArrayList<>(Arrays.asList(new Integer[] { 6, 8, 7, 10, 9 }));
    nums.addAll(nums1);  // Ghép danh sách nums1 vào sau nums
    ```

=== "C#"

    ```csharp title="list.cs"
    /* Ghép nối hai danh sách */
    List<int> nums1 = [6, 8, 7, 10, 9];
    nums.AddRange(nums1);  // Ghép danh sách nums1 vào sau nums
    ```

=== "Go"

    ```go title="list_test.go"
    /* Ghép nối hai danh sách */
    nums1 := []int{6, 8, 7, 10, 9}
    nums = append(nums, nums1...)  // Ghép danh sách nums1 vào sau nums
    ```

=== "Swift"

    ```swift title="list.swift"
    /* Ghép nối hai danh sách */
    let nums1 = [6, 8, 7, 10, 9]
    nums.append(contentsOf: nums1) // Ghép danh sách nums1 vào sau nums
    ```

=== "JS"

    ```javascript title="list.js"
    /* Ghép nối hai danh sách */
    const nums1 = [6, 8, 7, 10, 9];
    nums.push(...nums1);  // Ghép danh sách nums1 vào sau nums
    ```

=== "TS"

    ```typescript title="list.ts"
    /* Ghép nối hai danh sách */
    const nums1: number[] = [6, 8, 7, 10, 9];
    nums.push(...nums1);  // Ghép danh sách nums1 vào sau nums
    ```

=== "Dart"

    ```dart title="list.dart"
    /* Ghép nối hai danh sách */
    List<int> nums1 = [6, 8, 7, 10, 9];
    nums.addAll(nums1);  // Ghép danh sách nums1 vào sau nums
    ```

=== "Rust"

    ```rust title="list.rs"
    /* Ghép nối hai danh sách */
    let nums1: Vec<i32> = vec![6, 8, 7, 10, 9];
    nums.extend(nums1);
    ```

=== "C"

    ```c title="list.c"
    // C không cung cấp mảng động tích hợp sẵn
    ```

=== "Kotlin"

    ```kotlin title="list.kt"
    /* Ghép nối hai danh sách */
    val nums1 = intArrayOf(6, 8, 7, 10, 9).toMutableList()
    nums.addAll(nums1)  // Ghép danh sách nums1 vào sau nums
    ```

=== "Ruby"

    ```ruby title="list.rb"
    # Ghép nối hai danh sách
    nums1 = [6, 8, 7, 10, 9]
    nums += nums1
    ```

=== "Zig"

    ```zig title="list.zig"
    // Ghép nối hai danh sách
    var nums1 = std.ArrayList(i32).init(std.heap.page_allocator);
    defer nums1.deinit();
    try nums1.appendSlice(&[_]i32{ 6, 8, 7, 10, 9 });
    try nums.appendSlice(nums1.items); // Ghép danh sách nums1 vào sau nums
    ```

??? pythontutor "Trực quan hoá thực thi"

    https://pythontutor.com/render.html#code=%22%22%22Driver%20Code%22%22%22%0Aif%20__name__%20%3D%3D%20%22__main__%22%3A%0A%20%20%20%20%23%20%E5%88%9D%E5%A7%8B%E5%8C%96%E5%88%97%E8%A1%A8%0A%20%20%20%20nums%20%3D%20%5B1,%203,%202,%205,%204%5D%0A%20%20%20%20%0A%20%20%20%20%23%20%E6%8B%BC%E6%8E%A5%E4%B8%A4%E4%B8%AA%E5%88%97%E8%A1%A8%0A%20%20%20%20nums1%20%3D%20%5B6,%208,%207,%2010,%209%5D%0A%20%20%20%20nums%20%2B%3D%20nums1%20%20%23%20%E5%B0%86%E5%88%97%E8%A1%A8%20nums1%20%E6%8B%BC%E6%8E%A5%E5%88%B0%20nums%20%E4%B9%8B%E5%90%8E&cumulative=false&curInstr=3&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=311&rawInputLstJSON=%5B%5D&textReferences=false

### Sắp xếp danh sách

Sau khi sắp xếp danh sách, chúng ta có thể áp dụng các thuật toán "tìm kiếm nhị phân" và "hai con trỏ" thường xuyên xuất hiện trong các bài toán thuật toán dạng mảng.

=== "Python"

    ```python title="list.py"
    # Sắp xếp danh sách
    nums.sort()  # Sau khi sắp xếp, các phần tử trong danh sách xếp từ nhỏ đến lớn
    ```

=== "C++"

    ```cpp title="list.cpp"
    /* Sắp xếp danh sách */
    sort(nums.begin(), nums.end());  // Sau khi sắp xếp, các phần tử trong danh sách xếp từ nhỏ đến lớn
    ```

=== "Java"

    ```java title="list.java"
    /* Sắp xếp danh sách */
    Collections.sort(nums);  // Sau khi sắp xếp, các phần tử trong danh sách xếp từ nhỏ đến lớn
    ```

=== "C#"

    ```csharp title="list.cs"
    /* Sắp xếp danh sách */
    nums.Sort(); // Sau khi sắp xếp, các phần tử trong danh sách xếp từ nhỏ đến lớn
    ```

=== "Go"

    ```go title="list_test.go"
    /* Sắp xếp danh sách */
    sort.Ints(nums)  // Sau khi sắp xếp, các phần tử trong danh sách xếp từ nhỏ đến lớn
    ```

=== "Swift"

    ```swift title="list.swift"
    /* Sắp xếp danh sách */
    nums.sort() // Sau khi sắp xếp, các phần tử trong danh sách xếp từ nhỏ đến lớn
    ```

=== "JS"

    ```javascript title="list.js"
    /* Sắp xếp danh sách */
    nums.sort((a, b) => a - b); // Sau khi sắp xếp, các phần tử trong danh sách xếp từ nhỏ đến lớn
    ```

=== "TS"

    ```typescript title="list.ts"
    /* Sắp xếp danh sách */
    nums.sort((a, b) => a - b); // Sau khi sắp xếp, các phần tử trong danh sách xếp từ nhỏ đến lớn
    ```

=== "Dart"

    ```dart title="list.dart"
    /* Sắp xếp danh sách */
    nums.sort(); // Sau khi sắp xếp, các phần tử trong danh sách xếp từ nhỏ đến lớn
    ```

=== "Rust"

    ```rust title="list.rs"
    /* Sắp xếp danh sách */
    nums.sort(); // Sau khi sắp xếp, các phần tử trong danh sách xếp từ nhỏ đến lớn
    ```

=== "C"

    ```c title="list.c"
    // C không cung cấp mảng động tích hợp sẵn
    ```

=== "Kotlin"

    ```kotlin title="list.kt"
    /* Sắp xếp danh sách */
    nums.sort() // Sau khi sắp xếp, các phần tử trong danh sách xếp từ nhỏ đến lớn
    ```

=== "Ruby"

    ```ruby title="list.rb"
    # Sắp xếp danh sách
    nums = nums.sort { |a, b| a <=> b } # Sau khi sắp xếp, các phần tử trong danh sách xếp từ nhỏ đến lớn
    ```

=== "Zig"

    ```zig title="list.zig"
    // Sắp xếp danh sách
    std.mem.sort(i32, nums.items, {}, comptime std.sort.asc(i32)); // Sau khi sắp xếp, các phần tử trong danh sách xếp từ nhỏ đến lớn
    ```

??? pythontutor "Trực quan hoá thực thi"

    https://pythontutor.com/render.html#code=%22%22%22Driver%20Code%22%22%22%0Aif%20__name__%20%3D%3D%20%22__main__%22%3A%0A%20%20%20%20%23%20%E5%88%9D%E5%A7%8B%E5%8C%96%E5%88%97%E8%A1%A8%0A%20%20%20%20nums%20%3D%20%5B1,%203,%202,%205,%204%5D%0A%20%20%20%20%0A%20%20%20%20%23%20%E6%8E%92%E5%BA%8F%E5%88%97%E8%A1%A8%0A%20%20%20%20nums.sort%28%29%20%20%23%20%E6%8E%92%E5%BA%8F%E5%90%8E%EF%BC%8C%E5%88%97%E8%A1%A8%E5%85%83%E7%B4%A0%E4%BB%8E%E5%B0%8F%E5%88%B0%E5%A4%A7%E6%8E%92%E5%88%97&cumulative=false&curInstr=3&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=311&rawInputLstJSON=%5B%5D&textReferences=false

## Hiện thực danh sách

Nhiều ngôn ngữ lập trình tích hợp sẵn danh sách, ví dụ như Java, C++, Python, v.v. Việc hiện thực chúng tương đối phức tạp và việc thiết lập các tham số cũng được tính toán rất kỹ lưỡng, ví dụ như dung lượng ban đầu, hệ số nhân khi mở rộng dung lượng, v.v. Bạn đọc quan tâm có thể tra cứu mã nguồn của ngôn ngữ để tìm hiểu sâu hơn.

Để hiểu sâu hơn về nguyên lý hoạt động của danh sách, chúng ta hãy cùng thử hiện thực một phiên bản danh sách đơn giản, bao gồm ba điểm thiết kế cốt lõi sau:

- **Dung lượng ban đầu**: Chọn một dung lượng ban đầu hợp lý cho mảng. Trong ví dụ này, chúng ta chọn 10 làm dung lượng ban đầu.
- **Ghi nhận số lượng**: Khai báo một biến `size` để ghi lại số lượng phần tử hiện tại trong danh sách, và cập nhật theo thời gian thực mỗi khi chèn hoặc xoá phần tử. Dựa vào biến này, chúng ta có thể định vị phần đuôi của danh sách, cũng như phán đoán xem có cần mở rộng dung lượng hay không.
- **Cơ chế mở rộng dung lượng**: Nếu danh sách đã đầy khi chèn phần tử mới, cần phải tiến hành mở rộng dung lượng. Trước tiên tạo một mảng mới lớn hơn dựa trên hệ số nhân mở rộng, sau đó lần lượt di chuyển toàn bộ phần tử của mảng hiện tại sang mảng mới. Trong ví dụ này, chúng ta quy định mỗi lần mở rộng dung lượng mảng lên gấp 2 lần kích thước trước đó.

```src
[file]{my_list}-[class]{my_list}-[func]{}
```
