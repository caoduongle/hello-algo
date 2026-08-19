# Mảng

<u>Mảng (array)</u> là một cấu trúc dữ liệu tuyến tính lưu trữ các phần tử có cùng kiểu dữ liệu trong các ô nhớ liên tục. Chúng ta gọi vị trí của phần tử trong mảng là <u>chỉ số (index)</u> của phần tử đó. Hình dưới đây minh hoạ các khái niệm chính và phương thức lưu trữ của mảng.

![Định nghĩa và phương thức lưu trữ của mảng](array.assets/array_definition.png)

## Các thao tác thường dùng trên mảng

### Khởi tạo mảng

Chúng ta có thể tuỳ chọn hai cách khởi tạo mảng theo nhu cầu: không có giá trị khởi tạo và có sẵn giá trị khởi tạo. Trong trường hợp không chỉ định giá trị ban đầu, hầu hết các ngôn ngữ lập trình sẽ khởi tạo các phần tử mảng bằng $0$ ：

=== "Python"

    ```python title="array.py"
    # Khởi tạo mảng
    arr: list[int] = [0] * 5  # [ 0, 0, 0, 0, 0 ]
    nums: list[int] = [1, 3, 2, 5, 4]
    ```

=== "C++"

    ```cpp title="array.cpp"
    /* Khởi tạo mảng */
    // Lưu trữ trên stack
    int arr[5];
    int nums[5] = { 1, 3, 2, 5, 4 };
    // Lưu trữ trên heap (cần giải phóng bộ nhớ thủ công)
    int* arr1 = new int[5];
    int* nums1 = new int[5] { 1, 3, 2, 5, 4 };
    ```

=== "Java"

    ```java title="array.java"
    /* Khởi tạo mảng */
    int[] arr = new int[5]; // { 0, 0, 0, 0, 0 }
    int[] nums = { 1, 3, 2, 5, 4 };
    ```

=== "C#"

    ```csharp title="array.cs"
    /* Khởi tạo mảng */
    int[] arr = new int[5]; // [ 0, 0, 0, 0, 0 ]
    int[] nums = [1, 3, 2, 5, 4];
    ```

=== "Go"

    ```go title="array.go"
    /* Khởi tạo mảng */
    var arr [5]int
    // Trong Go, khi chỉ định độ dài ([5]int) là mảng, khi không chỉ định độ dài ([]int) là slice
    // Do mảng trong Go được thiết kế để xác định độ dài tại thời điểm biên dịch, nên chỉ có thể dùng hằng số để chỉ định độ dài
    // Để thuận tiện cho việc hiện thực phương thức mở rộng dung lượng extend(), dưới đây coi slice như mảng
    nums := []int{1, 3, 2, 5, 4}
    ```

=== "Swift"

    ```swift title="array.swift"
    /* Khởi tạo mảng */
    let arr = Array(repeating: 0, count: 5) // [0, 0, 0, 0, 0]
    let nums = [1, 3, 2, 5, 4]
    ```

=== "JS"

    ```javascript title="array.js"
    /* Khởi tạo mảng */
    var arr = new Array(5).fill(0);
    var nums = [1, 3, 2, 5, 4];
    ```

=== "TS"

    ```typescript title="array.ts"
    /* Khởi tạo mảng */
    let arr: number[] = new Array(5).fill(0);
    let nums: number[] = [1, 3, 2, 5, 4];
    ```

=== "Dart"

    ```dart title="array.dart"
    /* Khởi tạo mảng */
    List<int> arr = List.filled(5, 0); // [0, 0, 0, 0, 0]
    List<int> nums = [1, 3, 2, 5, 4];
    ```

=== "Rust"

    ```rust title="array.rs"
    /* Khởi tạo mảng */
    let arr: [i32; 5] = [0; 5]; // [0, 0, 0, 0, 0]
    let slice: &[i32] = &[0; 5];
    // Trong Rust, khi chỉ định độ dài ([i32; 5]) là mảng, khi không chỉ định độ dài (&[i32]) là slice
    // Do mảng trong Rust được thiết kế để xác định độ dài tại thời điểm biên dịch, nên chỉ có thể dùng hằng số để chỉ định độ dài
    // Vector là kiểu dữ liệu thường dùng làm mảng động trong Rust
    // Để thuận tiện cho việc hiện thực phương thức mở rộng dung lượng extend(), dưới đây coi vector như mảng
    let nums: Vec<i32> = vec![1, 3, 2, 5, 4];
    ```

=== "C"

    ```c title="array.c"
    /* Khởi tạo mảng */
    int arr[5] = { 0 }; // { 0, 0, 0, 0, 0 }
    int nums[5] = { 1, 3, 2, 5, 4 };
    ```

=== "Kotlin"

    ```kotlin title="array.kt"
    /* Khởi tạo mảng */
    var arr = IntArray(5) // { 0, 0, 0, 0, 0 }
    var nums = intArrayOf(1, 3, 2, 5, 4)
    ```

=== "Ruby"

    ```ruby title="array.rb"
    # Khởi tạo mảng
    arr = Array.new(5, 0)
    nums = [1, 3, 2, 5, 4]
    ```

??? pythontutor "Trực quan hoá thực thi"

    https://pythontutor.com/render.html#code=%23%20%E5%88%9D%E5%A7%8B%E5%8C%96%E6%95%B0%E7%BB%84%0Aarr%20%3D%20%5B0%5D%20*%205%20%20%23%20%5B%200,%200,%200,%200,%200%20%5D%0Anums%20%3D%20%5B1,%203,%202,%205,%204%5D&cumulative=false&curInstr=0&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=311&rawInputLstJSON=%5B%5D&textReferences=false

### Truy cập phần tử

Các phần tử trong mảng được lưu trữ trong các ô nhớ liên tục, điều này có nghĩa là việc tính toán địa chỉ bộ nhớ của một phần tử mảng là cực kỳ dễ dàng. Cho trước địa chỉ bộ nhớ của mảng (địa chỉ bộ nhớ của phần tử đầu tiên) và chỉ số của một phần tử nào đó, chúng ta có thể sử dụng công thức trong hình dưới đây để tính toán địa chỉ bộ nhớ của phần tử đó, từ đó truy cập trực tiếp vào phần tử.

![Tính toán địa chỉ bộ nhớ của phần tử mảng](array.assets/array_memory_location_calculation.png)

Quan sát hình trên, ta thấy chỉ số của phần tử đầu tiên trong mảng là $0$ ，điều này có vẻ hơi phản trực giác vì đếm từ $1$ sẽ tự nhiên hơn. Nhưng đứng từ góc độ công thức tính địa chỉ, **chỉ số về bản chất là độ lệch (offset) của địa chỉ bộ nhớ**。Độ lệch địa chỉ của phần tử đầu tiên là $0$ ，do đó chỉ số của nó là $0$ là hoàn toàn hợp lý.

Việc truy cập phần tử trong mảng diễn ra vô cùng hiệu quả, chúng ta có thể truy cập ngẫu nhiên bất kỳ phần tử nào trong mảng với thời gian $O(1)$ 。

```src
[file]{array}-[class]{}-[func]{random_access}
```

### Chèn phần tử

Các phần tử mảng nằm "san sát nhau" trong bộ nhớ, giữa chúng không còn khoảng trống nào để lưu thêm bất kỳ dữ liệu nào. Như minh hoạ trong hình dưới đây, nếu muốn chèn một phần tử vào giữa mảng, chúng ta cần phải dịch chuyển toàn bộ các phần tử phía sau vị trí đó lùi lại một vị trí, sau đó mới gán phần tử mới vào chỉ số đó.

![Ví dụ chèn phần tử vào mảng](array.assets/array_insert_element.png)

Cần lưu ý rằng do độ dài của mảng là cố định, việc chèn thêm một phần tử chắc chắn sẽ dẫn đến việc phần tử ở cuối mảng bị "mất đi". Chúng ta sẽ thảo luận giải pháp cho vấn đề này trong chương "Danh sách".

```src
[file]{array}-[class]{}-[func]{insert}
```

### Xoá phần tử

Tương tự, như minh hoạ trong hình dưới đây, nếu muốn xoá phần tử tại chỉ số $i$ ，chúng ta cần phải dịch chuyển toàn bộ các phần tử phía sau chỉ số $i$ tiến lên trước một vị trí.

![Ví dụ xoá phần tử trong mảng](array.assets/array_remove_element.png)

Xin lưu ý rằng sau khi xoá phần tử xong, phần tử ở vị trí cuối cùng ban đầu trở nên "vô nghĩa", nên chúng ta không cần phải cố ý sửa đổi nó.

```src
[file]{array}-[class]{}-[func]{remove}
```

Nhìn chung, các thao tác chèn và xoá trong mảng có những nhược điểm sau:

- **Độ phức tạp thời gian cao**: Độ phức tạp thời gian trung bình của thao tác chèn và xoá trong mảng đều là $O(n)$ ，trong đó $n$ là độ dài của mảng.
- **Mất mát phần tử**: Do độ dài của mảng không thể thay đổi, nên sau khi chèn phần tử, các phần tử vượt quá giới hạn độ dài của mảng sẽ bị mất.
- **Lãng phí bộ nhớ**: Chúng ta có thể khởi tạo một mảng tương đối dài và chỉ dùng phần đầu, như vậy khi chèn dữ liệu, các phần tử cuối bị mất đi đều là phần tử "vô nghĩa", nhưng làm như vậy sẽ gây lãng phí một phần không gian bộ nhớ.

### Duyệt mảng

Trong hầu hết các ngôn ngữ lập trình, chúng ta vừa có thể duyệt mảng thông qua chỉ số, vừa có thể duyệt trực tiếp từng phần tử trong mảng:

```src
[file]{array}-[class]{}-[func]{traverse}
```

### Tìm kiếm phần tử

Việc tìm kiếm một phần tử được chỉ định trong mảng đòi hỏi phải duyệt qua mảng, ở mỗi vòng lặp kiểm tra xem giá trị phần tử có khớp hay không, nếu khớp thì trả về chỉ số tương ứng.

Vì mảng là một cấu trúc dữ liệu tuyến tính, nên thao tác tìm kiếm nói trên được gọi là "tìm kiếm tuyến tính" (linear search).

```src
[file]{array}-[class]{}-[func]{find}
```

### Mở rộng dung lượng mảng

Trong các môi trường hệ thống phức tạp, chương trình rất khó đảm bảo rằng khoảng không gian bộ nhớ nằm ngay sau mảng là khả dụng, do đó không thể mở rộng dung lượng mảng một cách an toàn tại chỗ. Vì vậy trong đa số ngôn ngữ lập trình, **độ dài của mảng là không thể thay đổi (bất biến)**。

Nếu muốn mở rộng dung lượng mảng, chúng ta cần phải tạo một mảng mới lớn hơn, sau đó lần lượt sao chép các phần tử từ mảng cũ sang mảng mới. Đây là một thao tác có độ phức tạp $O(n)$ ，và rất tốn thời gian khi kích thước mảng lớn. Mã nguồn như sau:

```src
[file]{array}-[class]{}-[func]{extend}
```

## Ưu điểm và hạn chế của mảng

Mảng được lưu trữ trong không gian bộ nhớ liên tục và các phần tử có cùng kiểu dữ liệu. Phương thức này chứa đựng thông tin tiên nghiệm phong phú, giúp hệ thống có thể tận dụng các thông tin đó để tối ưu hoá hiệu năng thao tác trên cấu trúc dữ liệu:

- **Hiệu năng không gian cao**: Mảng cấp phát một khối bộ nhớ liên tục cho dữ liệu, không tốn thêm chi phí cấu trúc bổ sung.
- **Hỗ trợ truy cập ngẫu nhiên**: Mảng cho phép truy cập bất kỳ phần tử nào trong thời gian $O(1)$ 。
- **Tính cục bộ bộ nhớ đệm (Cache locality)**: Khi truy cập một phần tử mảng, máy tính không chỉ nạp riêng phần tử đó mà còn nạp cả các dữ liệu xung quanh vào bộ nhớ đệm, nhờ đó tận dụng bộ nhớ đệm tốc độ cao để đẩy nhanh tốc độ thực thi của các thao tác tiếp theo.

Lưu trữ trong không gian liên tục là con dao hai lưỡi, nó tồn tại những hạn chế sau:

- **Hiệu năng chèn và xoá thấp**: Khi mảng có nhiều phần tử, thao tác chèn và xoá đòi hỏi phải dịch chuyển một lượng lớn phần tử.
- **Độ dài không thể thay đổi**: Mảng sau khi khởi tạo thì độ dài đã cố định; việc mở rộng dung lượng mảng đòi hỏi phải sao chép toàn bộ dữ liệu sang mảng mới với chi phí rất lớn.
- **Lãng phí không gian**: Nếu kích thước mảng cấp phát vượt quá nhu cầu thực tế, thì phần không gian dư thừa sẽ bị lãng phí.

## Các ứng dụng điển hình của mảng

Mảng là một cấu trúc dữ liệu nền tảng và vô cùng phổ biến, vừa được ứng dụng liên tục trong các thuật toán khác nhau, vừa có thể dùng để hiện thực hoá các cấu trúc dữ liệu phức tạp:

- **Truy cập ngẫu nhiên**: Nếu muốn rút ngẫu nhiên một số mẫu dữ liệu, chúng ta có thể dùng mảng để lưu trữ và tạo một dãy ngẫu nhiên, thực hiện lấy mẫu ngẫu nhiên dựa trên chỉ số.
- **Sắp xếp và tìm kiếm**: Mảng là cấu trúc dữ liệu được sử dụng phổ biến nhất cho các thuật toán sắp xếp và tìm kiếm. Sắp xếp nhanh (quicksort), sắp xếp trộn (merge sort), tìm kiếm nhị phân (binary search) v.v. đều chủ yếu được thực hiện trên mảng.
- **Bảng tra cứu (Lookup table)**: Khi cần tra cứu nhanh một phần tử hoặc mối quan hệ tương ứng của nó, có thể dùng mảng làm bảng tra cứu. Chẳng hạn nếu muốn ánh xạ ký tự sang mã ASCII, chúng ta có thể lấy giá trị mã ASCII của ký tự làm chỉ số, và phần tử tương ứng được lưu tại vị trí đó trong mảng.
- **Học máy (Machine Learning)**: Trong mạng nơ-ron sử dụng lượng lớn các phép tính đại số tuyến tính giữa vectơ, ma trận và tensor, những dữ liệu này đều được xây dựng dưới dạng mảng. Mảng là cấu trúc dữ liệu được sử dụng thường xuyên nhất trong lập trình mạng nơ-ron.
- **Hiện thực hoá cấu trúc dữ liệu**: Mảng có thể dùng để hiện thực ngăn xếp, hàng đợi, bảng băm, đống (heap), đồ thị, v.v. Ví dụ, biểu diễn ma trận kề của đồ thị thực chất là một mảng hai chiều.
