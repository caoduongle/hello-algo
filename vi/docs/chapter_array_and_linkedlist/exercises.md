# Bài tập

## Củng cố kiến thức

### Mảng và danh sách liên kết tìm phần tử như thế nào?

Cả mảng và danh sách liên kết đơn đều lưu trữ tuần tự `[A, B, C, D, E]`. Bây giờ cần đọc phần tử thứ 4 là `D`:

<!-- numbered-subquestions -->

1. Mảng có thể sử dụng trực tiếp chỉ số nào?
2. Bắt đầu từ nút đầu `A`, danh sách liên kết đơn phải lần lượt đi qua các nút nào theo `next`?
3. Khi vị trí của phần tử cần đọc càng nằm về phía cuối, số bước thực hiện của hai cấu trúc sẽ thay đổi như thế nào? Cấu trúc nào thích hợp hơn cho việc đọc lặp đi lặp lại theo vị trí? Vì sao?

??? success "Đáp án tham khảo"

    1. Nếu chỉ số bắt đầu từ 0, chỉ số của phần tử thứ 4 là 3, mảng có thể đọc trực tiếp `arr[3]`.

    2. Danh sách liên kết đơn bắt buộc phải bắt đầu từ nút đầu, lộ trình truy cập là `A → B → C → D`, cần tiến theo `next` 3 lần.

    3. Mảng có thể định vị trực tiếp phần tử dựa vào địa chỉ đầu và chỉ số, độ phức tạp thời gian truy cập theo vị trí là $O(1)$.
        Danh sách liên kết đơn khi truy cập nút thứ $k$ bắt buộc phải xuất phát từ nút đầu và tiến theo `next` $k-1$ lần,
        trong trường hợp xấu nhất cần thời gian $O(n)$.

        Ở đây chỉ so sánh thao tác đọc theo vị trí, không có nghĩa là danh sách liên kết chậm hơn ở mọi thao tác.

### Mảng và danh sách liên kết chèn phần tử như thế nào?

Cả mảng và danh sách liên kết đơn đều đang lưu trữ `A, B, C, D`. Bây giờ cần chèn `X` vào phía sau `B`:

- Mảng có sức chứa là 5, trạng thái hiện tại là `[A, B, C, D, _]`;
- Danh sách liên kết là `A → B → C → D`, và đã có sẵn tham chiếu trỏ đến nút `B`.

<!-- numbered-subquestions -->

1. Mảng cần di chuyển những phần tử nào? Hãy viết mảng sau khi chèn.
2. Danh sách liên kết nên sửa đổi `X.next` và `B.next` theo thứ tự nào? Hãy viết danh sách liên kết sau khi chèn.
3. Tại sao khi so sánh hiệu năng chèn, đề bài lại cần đặc biệt nêu rõ "đã có sẵn tham chiếu trỏ đến nút B"?

??? success "Đáp án tham khảo"

    1. Mảng trước hết phải dịch chuyển `D` sang phải một ô, sau đó dịch chuyển `C` sang phải một ô, cuối cùng đặt `X` vào chỉ số 2,
        thu được `[A, B, X, C, D]`.

    2. `B.next` ban đầu trỏ đến `C`. Cần gán `X.next = B.next` trước để `X` trỏ đến `C`;
        sau đó mới gán `B.next = X`. Kết quả là `A → B → X → C → D`.
        Nếu ghi đè `B.next` trước mà chưa lưu lại liên kết ban đầu, thì sẽ có thể làm mất dấu nút `C`.

    3. Khi đã biết vị trí của `B`, thao tác chèn trong danh sách liên kết chỉ cần sửa đổi hai liên kết và hoàn thành trong thời gian $O(1)$.
        Nếu còn phải duyệt tìm `B` từ đầu danh sách, thì bản thân quá trình tìm kiếm có thể tốn $O(n)$ thời gian.

### Sức chứa của danh sách tăng lên như thế nào?

Một danh sách hiện thực dựa trên mảng hiện đang có nội dung là `[A, B, C]`, độ dài `size = 3`, sức chứa `capacity = 4`.
Quy định khi sức chứa không đủ, mảng mới sẽ mở rộng sức chứa lên gấp 2 lần mảng cũ.

<!-- numbered-subquestions -->

1. Sau khi thêm `D` vào đuôi, độ dài và sức chứa của danh sách lần lượt là bao nhiêu? Có cần mở rộng dung lượng không?
2. Tiếp tục thêm `E` vào đuôi, sức chứa sẽ trở thành bao nhiêu? Cần sao chép bao nhiêu phần tử cũ?
3. Độ dài của mảng tầng dưới là cố định không đổi, tại sao sức chứa của danh sách nhìn từ ngoài lại có vẻ tăng lên được?

??? success "Đáp án tham khảo"

    1. `D` có thể đặt vừa vào vị trí trống cuối cùng. Lúc này nội dung là `[A, B, C, D]`,
        `size = 4`, `capacity = 4`, không cần mở rộng dung lượng.

    2. Khi tiếp tục thêm `E`, mảng đã hết chỗ trống, cần tạo một mảng mới có sức chứa là 8,
        sao chép 4 phần tử cũ `A, B, C, D` sang mảng mới, sau đó mới thêm `E`.
        Lúc này `size = 5`, `capacity = 8`.

    3. Bản thân mảng ban đầu không hề dài ra. Danh sách đã tạo ra một mảng mới lớn hơn, sao chép các phần tử cũ sang,
        sau đó đổi sang dùng mảng mới làm nơi lưu trữ bên dưới, do đó đối với người sử dụng thì sức chứa đã tăng lên.

## Bài tập lập trình

### Cộng một vào số nguyên lớn biểu diễn bằng mảng

Mảng `digits` lưu trữ các chữ số của một số nguyên không âm từ trái sang phải, ví dụ `[3, 0, 8]` biểu diễn số 308.
Số 0 được biểu diễn bằng `[0]`; chữ số đầu tiên của các đầu vào khác đều khác 0.

Hãy mô phỏng phép cộng đặt tính cột dọc trong hệ thập phân, tăng số nguyên này lên 1 và trả về kết quả dưới dạng mảng tương tự.
Có thể sửa trực tiếp trên mảng `digits`; nếu chữ số đầu tiên phát sinh nhớ sang hàng mới, có thể trả về một mảng dài hơn.

??? tip "Gợi ý giải bài"

    1. Giống như làm phép cộng đặt tính theo cột dọc, bắt đầu từ chữ số cuối cùng của mảng
    2. Khi chữ số hiện tại nhỏ hơn 9, cộng thêm 1 rồi có thể trả về kết quả ngay lập tức
    3. Khi chữ số hiện tại bằng 9, đổi nó thành 0; nếu tất cả các chữ số đều là 9, cần chèn thêm số 1 vào đầu mảng

[LeetCode](https://leetcode.com/problems/plus-one/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }

### Đảo ngược danh sách liên kết đơn

Cho nút đầu `head` của một danh sách liên kết đơn. Mỗi nút chứa một giá trị và con trỏ/tham chiếu `next` trỏ đến nút kế tiếp.

Hãy sử dụng phương pháp lặp để đảo ngược toàn bộ liên kết giữa các nút và trả về nút đầu của danh sách liên kết sau khi đảo ngược.
Yêu cầu không tạo thêm các nút danh sách liên kết mới.

??? tip "Gợi ý giải bài"

    1. Trước tiên hãy vẽ trên giấy ba nút liên kết nhau cùng hai con trỏ prev và cur
    2. Trước khi sửa cur.next, bắt buộc phải dùng nxt để lưu lại nút tiếp theo ban đầu
    3. Sau khi đảo ngược cur.next, gán prev = cur, rồi gán cur = nxt, tiếp tục xử lý nút tiếp theo trong danh sách liên kết gốc

[LeetCode](https://leetcode.com/problems/reverse-linked-list/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" } [Giải thích lời giải](https://leetcode.cn/problems/reverse-linked-list/solutions/2361282/206-fan-zhuan-lian-biao-shuang-zhi-zhen-r1jel/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }
