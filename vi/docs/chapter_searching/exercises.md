# Bài tập

## Củng cố kiến thức

### Tìm kiếm nhị phân thu hẹp khoảng tìm kiếm như thế nào?

Tìm kiếm số 16 trong mảng đã sắp xếp `[2, 5, 8, 12, 16, 23, 38]`。
Sử dụng khoảng đóng hai đầu `[i, j]`，trung điểm tính theo công thức
$m=i+(j-i)/2$（làm tròn xuống）。

Hãy viết `(i, j, m)`，phần tử trung điểm và bước thu hẹp khoảng tiếp theo trong mỗi vòng lặp，
cho đến khi tìm thấy mục tiêu。

??? success "Đáp án tham khảo"

    Tiến trình tìm kiếm qua từng vòng như sau:

    | Vòng | `(i, j, m)` | Phần tử trung điểm | Bước tiếp theo |
    | --- | --- | --- | --- |
    | 1 | `(0, 6, 3)` | 12 | `12 < 16`，gán `i = 4` |
    | 2 | `(4, 6, 5)` | 23 | `23 > 16`，gán `j = 4` |
    | 3 | `(4, 4, 4)` | 16 | Tìm thấy mục tiêu, trả về chỉ số 4 |

    Mảng có thứ tự, do đó khi giá trị trung điểm nhỏ hơn mục tiêu thì có thể loại trừ trung điểm và toàn bộ phần bên trái của nó;
    khi giá trị trung điểm lớn hơn mục tiêu thì có thể loại trừ trung điểm và toàn bộ phần bên phải của nó.

### Biên trái và biên phải của phần tử trùng lặp

Tìm kiếm số 2 trong mảng `[1, 2, 2, 2, 4, 6]`。
Một bạn học sinh sử dụng tìm kiếm nhị phân, sau khi tìm thấy mục tiêu tại chỉ số 2 liền lập tức trả về kết quả và nói:
"Chỉ số 2 chính là biên trái của số 2."

<!-- numbered-subquestions -->

1. Cách nói của bạn học sinh này có đúng không? Biên trái và biên phải của số 2 lần lượt là bao nhiêu? Hãy giải thích lý do.
2. Khi tìm kiếm biên trái, nếu phần tử trung điểm bằng mục tiêu, tiếp theo nên tiếp tục tìm kiếm ở phía nào?
3. Khi tìm kiếm biên phải thì lại nên tiếp tục tìm kiếm ở phía nào? Chỉ cần nêu rõ phương hướng, không cần viết toàn bộ tiến trình tìm kiếm.

??? success "Đáp án tham khảo"

    1. Cách nói của bạn học sinh này không đúng. Việc trả về ngay sau khi tìm thấy một số 2 chỉ đảm bảo tìm thấy một số 2 nào đó, chứ không đảm bảo tìm thấy số 2 ngoài cùng bên trái hay ngoài cùng bên phải.
        Trong bài toán này, biên trái là chỉ số 1, biên phải là chỉ số 3.

    2. Khi tìm kiếm biên trái, ngay cả khi phần tử trung điểm bằng 2, vẫn phải tiếp tục tìm kiếm ở phía bên trái,
        ví dụ trong cách viết khoảng đóng hai đầu thì gán `j = m - 1`。

    3. Khi tìm kiếm biên phải, sau khi phần tử trung điểm bằng 2 thì nên tiếp tục tìm kiếm ở phía bên phải,
        ví dụ gán `i = m + 1`。

### Nên chọn phương pháp tìm kiếm nào cho các dạng dữ liệu khác nhau?

Hãy lựa chọn phương pháp phù hợp từ "tìm kiếm tuần tự (tuyến tính), tìm kiếm nhị phân, bảng băm" cho ba tình huống dưới đây và giải thích lý do:

<!-- numbered-subquestions -->

1. Tìm kiếm lặp đi lặp lại trong $10^7$ số nguyên đã sắp xếp và không còn thay đổi, không thiết lập thêm cấu trúc dữ liệu phụ trợ;
2. Kiểm tra lặp đi lặp lại xem một khoá (key) nhất định có tồn tại trong tập dữ liệu thường xuyên thêm và xoá hay không, không yêu cầu duy trì thứ tự và cũng không tìm kiếm theo khoảng;
3. Chỉ tìm kiếm duy nhất một lần một giá trị nào đó trong mảng chưa sắp xếp.

??? success "Đáp án tham khảo"

    1. Tìm kiếm nhị phân: Dữ liệu có thứ tự và tĩnh, độ phức tạp $O(\log n)$ và không tốn thêm không gian bộ nhớ.
    2. Bảng băm: Khi hàm băm có thể phân tán các khoá tương đối đồng đều vào các bucket, các thao tác thêm, xoá và tìm kiếm theo khoá đều có độ phức tạp thời gian trung bình là $O(1)$。
    3. Duyệt tuần tự trực tiếp từ đầu đến cuối: Khi chỉ tìm kiếm duy nhất một lần, việc sắp xếp mảng hay xây dựng bảng băm đều phải xử lý toàn bộ mảng trước,
        hoàn toàn không làm giảm tổng khối lượng công việc cho nhiệm vụ đơn lẻ này.

        Việc lựa chọn phụ thuộc vào việc dữ liệu có thứ tự hay không, có cho phép dựng thêm cấu trúc dữ liệu phụ trợ hay không, số lần truy vấn cũng như các thao tác cần thực hiện.

## Bài tập lập trình

### Tìm kiếm nhị phân trong mảng có thứ tự

Cho mảng số nguyên `nums` được sắp xếp theo thứ tự tăng dần nghiêm ngặt và giá trị mục tiêu `target`。Hãy sử dụng tìm kiếm nhị phân để tìm `target`: nếu tồn tại, trả về chỉ số mảng của nó; nếu không tồn tại, trả về -1。

??? tip "Gợi ý giải bài"

    1. Khoảng ban đầu là left = 0, right = n - 1, điều kiện không rỗng là left <= right
    2. Sử dụng mid = left + (right - left) // 2 để tính trung điểm
    3. Nếu `nums[mid]` nhỏ hơn `target`, dịch chuyển biên trái sang `mid + 1`; nếu `nums[mid]` lớn hơn `target`, dịch chuyển biên phải sang `mid - 1`; nếu bằng nhau thì trả về ngay lập tức

[LeetCode](https://leetcode.com/problems/binary-search/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" } [Giải thích lời giải](https://leetcode.cn/problems/binary-search/solutions/1692151/by-jyd-i7xr/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }

### Vị trí chèn trong mảng có thứ tự

Cho mảng số nguyên `nums` được sắp xếp theo thứ tự tăng dần nghiêm ngặt và giá trị mục tiêu `target`。

Nếu `target` đã tồn tại trong mảng, trả về chỉ số của nó; ngược lại, trả về vị trí chèn `target` vào mảng sao cho mảng vẫn duy trì thứ tự tăng dần nghiêm ngặt. Kết quả có thể là 0, hoặc có thể bằng độ dài của mảng. Hãy sử dụng tìm kiếm nhị phân.

??? tip "Gợi ý giải bài"

    1. Kết quả có thể là 0, hoặc có thể là độ dài mảng n
    2. Khi sử dụng khoảng đóng hai đầu, nếu `nums[mid]` lớn hơn hoặc bằng `target`, gán `right = mid - 1` và tiếp tục kiểm tra các vị trí xa hơn về bên trái; ngược lại gán `left = mid + 1`
    3. Khi vòng lặp kết thúc, left chính là vị trí chèn

[LeetCode](https://leetcode.com/problems/search-insert-position/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }
