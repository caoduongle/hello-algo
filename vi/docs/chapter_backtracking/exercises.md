# Bài tập

## Củng cố kiến thức

### Thuật toán hoán vị này có bị bỏ sót kết quả không?

Một thuật toán quay lui thử sinh ra toàn bộ các hoán vị theo thứ tự `1, 2, 3`. Mỗi khi chọn một số `x`, nó sẽ:

1. Thêm `x` vào cuối đường đi hiện tại;
2. Đánh dấu `x` là "đã sử dụng";
3. Đệ quy điền vào vị trí tiếp theo.

Sau khi đệ quy trả về, bạn học sinh chỉ xoá `x` khỏi cuối đường đi, rồi tiếp tục thử số tiếp theo.

<!-- numbered-subquestions -->

1. Thuật toán sẽ thu được hoán vị nào đầu tiên? Nó có thể thu được toàn bộ 6 hoán vị không?
2. Trước khi đệ quy quay về tầng trước, việc chỉ xoá con số ở cuối đường đi đã đủ chưa? Nếu chưa đủ, còn cần làm gì nữa? Hãy giải thích lý do.

??? success "Đáp án tham khảo"

    1. Thuật toán trước tiên thu được `[1, 2, 3]`, nhưng không thể thu được toàn bộ các hoán vị. Mặc dù khi quay về đường đi đã ngắn lại,
        nhưng các dấu đánh dấu của các số 1, 2, 3 vẫn đều là "đã sử dụng", các nhánh phía sau sẽ không còn số nào để chọn.

    2. Chưa đủ. Sau khi xoá `x` ở cuối đường đi, bắt buộc còn phải đánh dấu lại `x` là "chưa sử dụng".
        Đường đi hiện tại và các dấu đánh dấu đã sử dụng cùng nhau mô tả trạng thái tìm kiếm; khi đưa ra lựa chọn đã sửa đổi cả hai nơi, thì khi quay lui cũng bắt buộc phải khôi phục cả hai nơi,
        như vậy các nhánh khác mới có thể chọn lại `x`.

### Thứ tự lựa chọn các con số có quan trọng không?

Cho mảng đã sắp xếp `[2, 3, 5]` và giá trị mục tiêu 5, mỗi số có thể chọn lặp lại nhiều lần.
Thuật toán quy định các con số trong mỗi đường đi tìm kiếm chỉ được phép xuất hiện theo thứ tự từ nhỏ đến lớn.

<!-- numbered-subquestions -->

1. Có thể thu được những tổ hợp khác nhau nào?
2. Tại sao cùng một nhóm số lại không cần tìm kiếm lặp lại theo các thứ tự khác nhau? Ràng buộc "từ nhỏ đến lớn" đóng vai trò gì?
3. Khi đường đi hiện tại là `[3]`, còn thiếu 2, số ứng viên tiếp theo là 3. Tại sao lúc này có thể dừng kiểm tra toàn bộ các số ứng viên phía sau ở tầng này?

??? success "Đáp án tham khảo"

    1. Các tổ hợp khác nhau là `[2, 3]` và `[5]`.

    2. Bài toán này coi `[2, 3]` và `[3, 2]` là cùng một tổ hợp, thứ tự lựa chọn các con số không tạo ra đáp án mới.
        Quy định các con số trong đường đi xuất hiện từ nhỏ đến lớn giúp trực tiếp bỏ qua các tổ hợp trùng lặp như `[3, 2]` trong quá trình tìm kiếm.

    3. Hiện tại còn thiếu 2, trong khi số ứng viên 3 đã lớn hơn 2. Do mảng đã được sắp xếp sẵn,
        các số ứng viên đứng sau 3 sẽ chỉ càng lớn hơn, đều không thể thêm vào tổ hợp hiện tại, vì vậy có thể kết thúc ngay việc kiểm tra ở tầng này.

### Quân hậu tiếp theo có thể đặt vào những vị trí nào?

Đặt các quân hậu theo từng hàng trên bàn cờ `4 × 4`, chỉ số hàng và cột đều bắt đầu từ 0.
Hiện tại đã đặt các quân hậu tại `(0, 1)` và `(1, 3)`, bây giờ cần đặt quân hậu tiếp theo trên hàng 2.

<!-- numbered-subquestions -->

1. Những cột nào sẽ bị loại trừ do "cùng cột"?
2. Trong các cột còn lại, những vị trí nào sẽ bị loại trừ do "cùng đường chéo"?
3. Hàng 2 còn lại những vị trí nào có thể thử?

??? success "Đáp án tham khảo"

    1. Cột 1 và cột 3 đã có quân hậu, do đó các vị trí `(2, 1)` và `(2, 3)` bị loại trừ.

    2. Trong các vị trí còn lại, `(2, 2)` nằm trên cùng đường chéo với `(1, 3)` nên cũng bị loại trừ.
        Vị trí `(2, 0)` không cùng cột và cũng không cùng đường chéo với cả hai quân hậu đã có.

    3. Vị trí duy nhất có thể thử ở hàng 2 là `(2, 0)`.

        Bước này chỉ cho thấy vị trí đặt hiện tại là hợp lệ; nếu sau đó không thể hoàn thành bàn cờ, thuật toán vẫn phải quay lui và thử các lựa chọn khác trước đó.

## Bài tập lập trình

### Hoán vị không chứa phần tử trùng lặp

Mảng số nguyên `nums` chứa ít nhất một phần tử, và các phần tử trong đó đôi một khác nhau.
Hãy liệt kê toàn bộ các thứ tự có thể tạo thành khi sử dụng mỗi phần tử đúng một lần, và trả về mỗi thứ tự dưới dạng một mảng.
Không yêu cầu thứ tự trước sau giữa các hoán vị trong kết quả.
Hãy sử dụng quay lui, và dùng mảng boolean để ghi lại xem phần tử tại mỗi vị trí đã được chọn vào hoán vị hiện tại hay chưa.

??? tip "Gợi ý giải bài"

    1. Độ sâu đệ quy biểu thị đang điền vào vị trí thứ mấy trong hoán vị
    2. Mỗi tầng chỉ thử các phần tử chưa được sử dụng
    3. Khi độ dài đường đi đạt tới độ dài của `nums`, thêm một bản sao của nó vào đáp án

[LeetCode](https://leetcode.com/problems/permutations/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" } [Giải thích lời giải](https://leetcode.cn/problems/permutations/solutions/2363882/46-quan-pai-lie-hui-su-qing-xi-tu-jie-by-6o7h/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }

> **Lưu ý:** Lời giải trong liên kết áp dụng hoán đổi phần tử mảng để lần lượt đưa các phần tử đã chọn lên đầu mảng; bài tập này sử dụng mảng boolean để ghi nhận từng phần tử đã chọn hay chưa. Cả hai phương pháp đều tránh được việc chọn lặp lại cùng một phần tử, nhưng cấu trúc mã nguồn khác nhau.
