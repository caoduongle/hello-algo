# Bài tập

## Củng cố kiến thức

### Mối quan hệ dữ liệu trong các tình huống đời sống

Dựa trên mối quan hệ giữa các dữ liệu, hãy chọn một trong các cấu trúc "cấu trúc tuyến tính, cấu trúc dạng cây, cấu trúc dạng mạng" cho ba tình huống dưới đây và giải thích lý do:

<!-- numbered-subquestions -->

1. Các bạn học sinh xếp thành một hàng dọc, mỗi người chỉ quan tâm đến người đứng ngay trước và người đứng ngay sau mình;
2. Trường học được quản lý phân tầng theo cấu trúc "Trường học → Khối lớp → Lớp học";
3. Đường phố đô thị kết nối nhiều nút giao thông, một ngã tư có thể dẫn đến nhiều ngã tư khác và có thể tạo thành các tuyến đường vòng tròn khép kín.

??? success "Đáp án tham khảo"

    1. Là cấu trúc tuyến tính. Ngoại trừ người đứng đầu và người đứng cuối hàng, mỗi người đều chỉ liền kề với đúng một người phía trước và một người phía sau, mối quan hệ mở rộng dọc theo một đường thẳng.

    2. Là cấu trúc dạng cây. Mỗi lớp học thuộc về một khối lớp, mỗi khối lớp lại thuộc về trường học, mối quan hệ mở rộng phân tầng từ trên xuống dưới.

    3. Là cấu trúc dạng mạng. Một ngã tư có thể kết nối tới nhiều ngã tư khác và các tuyến đường có thể tạo thành vòng tròn khép kín, không thể sắp xếp thành một thứ tự đơn lẻ hay phân tầng thứ bậc nghiêm ngặt.

        Khi xác định cấu trúc, trước tiên nên quan sát mối quan hệ giữa các phần tử, chứ không nên xem xét trước việc nó chiếm bao nhiêu không gian trong bộ nhớ.

### Thứ tự logic được lưu vào bộ nhớ như thế nào?

Để lưu trữ thứ tự logic `A → B → C`，hiện có hai phương án bố trí bộ nhớ đơn giản hoá như sau:

- Phương án A: `A、B、C` lần lượt được đặt vào các ô nhớ có số hiệu `20、21、22`；
- Phương án B: `A、B、C` lần lượt được đặt vào các ô nhớ có số hiệu `20、7、31`，trong đó `A` ghi lại vị trí của `B`，`B` ghi lại vị trí của `C`。

<!-- numbered-subquestions -->

1. Phương án nào thuộc lưu trữ trong không gian liên tục? Phương án nào thuộc lưu trữ trong không gian phân tán?
2. Hai phương án lần lượt gần với mảng hay danh sách liên kết hơn?
3. Các số hiệu ô nhớ trong phương án B không được sắp xếp theo thứ tự độ lớn, tại sao nó vẫn có thể biểu diễn được thứ tự logic `A → B → C`？

??? success "Đáp án tham khảo"

    1. Phương án A sử dụng các ô nhớ liên tục, thuộc lưu trữ trong không gian liên tục; các nút trong phương án B phân tán ở nhiều vị trí khác nhau, thuộc lưu trữ trong không gian phân tán.

    2. Phương án A gần với mảng hơn, phương án B gần với danh sách liên kết hơn.

    3. Thứ tự logic được quyết định bởi mối liên kết được ghi lại giữa các nút, chứ không phụ thuộc vào độ lớn của số hiệu ô nhớ.
        Từ vị trí do `A` ghi lại có thể tìm thấy `B`，rồi từ vị trí do `B` ghi lại có thể tìm thấy `C`，do đó vẫn có thể lần lượt truy cập `A、B、C` theo đúng thứ tự.

        Điều này cũng chứng minh rằng cấu trúc logic và cấu trúc vật lý là hai góc độ quan sát khác nhau đối với cùng một tập dữ liệu.

### Kiểu dữ liệu và cấu trúc trong bảng ghi bài tập

Một nhóm học tập ghi lại tình trạng nộp bài tập của 4 bạn học sinh theo thứ tự chỗ ngồi, thu được:

`[true, false, true, true]`

<!-- numbered-subquestions -->

1. Mỗi phần tử thích hợp sử dụng kiểu dữ liệu cơ bản nào?
2. 4 phần tử này được xếp thành một hàng theo thứ tự chỗ ngồi, đang sử dụng cấu trúc logic nào?
3. Nếu sau này chuyển sang ghi điểm bài tập của mỗi bạn `[90, 0, 85, 100]`，thì điều thay đổi là "kiểu nội dung" hay "phương thức tổ chức" của dữ liệu? Hãy giải thích lý do.

??? success "Đáp án tham khảo"

    1. Mỗi phần tử chỉ biểu thị "đúng" hoặc "sai", thích hợp sử dụng kiểu Boolean `bool`。

    2. Các phần tử này được sắp xếp theo thứ tự chỗ ngồi, tạo thành cấu trúc tuyến tính, có thể lưu trữ bằng mảng.

    3. Điều thay đổi là kiểu nội dung: các phần tử đã chuyển từ giá trị Boolean thành số nguyên. Phương thức tổ chức không hề thay đổi,
        các dữ liệu này vẫn được xếp thành một hàng theo thứ tự chỗ ngồi, vẫn có thể sử dụng cấu trúc tuyến tính của mảng.

        Kiểu dữ liệu cơ bản mô tả "lưu cái gì", còn cấu trúc dữ liệu mô tả "dữ liệu được tổ chức như thế nào".

## Bài tập lập trình

### Đếm số bit 1 trong biểu diễn nhị phân

Cho một số nguyên không âm `n`，hãy đếm xem trong biểu diễn nhị phân của nó có tổng cộng bao nhiêu bit 1.

Yêu cầu sử dụng phép toán bit để giải, không chuyển biểu diễn nhị phân thành chuỗi ký tự, và không sử dụng các hàm tích hợp sẵn trực tiếp đếm bit 1.

??? tip "Gợi ý giải bài"

    1. Phép toán `n & 1` có thể lấy ra bit ngoài cùng bên phải của `n`，dùng nó để kiểm tra xem bit này có phải là 1 hay không
    2. Dịch phải một bit biểu thị việc loại bỏ bit nhị phân ngoài cùng bên phải hiện tại; đa số các ngôn ngữ sử dụng toán tử `>>`
    3. Sau khi hoàn thành phương pháp kiểm tra từng bit và dịch phải, hãy quan sát tiếp: `n & (n - 1)` sẽ biến bit 1 ngoài cùng bên phải trong `n` thành 0

[LeetCode](https://leetcode.com/problems/number-of-1-bits/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" } [Giải thích lời giải](https://leetcode.cn/problems/number-of-1-bits/solutions/2361978/191-wei-1-de-ge-shu-wei-yun-suan-qing-xi-40rw/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }
