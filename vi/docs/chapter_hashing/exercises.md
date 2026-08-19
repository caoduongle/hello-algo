# Bài tập

## Củng cố kiến thức

### Tra cứu như thế nào sau khi xảy ra đụng độ băm?

Một bảng băm có 5 ngăn, hàm băm là $h(x)=x \bmod 5$, khi đụng độ sẽ lần lượt đưa các phần tử vào danh sách trong ngăn đó.
Lần lượt chèn `[1, 6, 11, 7]`:

<!-- numbered-subquestions -->

1. Viết nội dung bên trong các ngăn từ 0 đến 4;
2. Khi tìm kiếm 6, chương trình sẽ truy cập vào ngăn nào trước và lần lượt kiểm tra các phần tử nào?
3. Dựa theo nội dung các ngăn đã viết ở câu 1, các phần tử chèn sau có ghi đè lên các phần tử chèn trước không? Hãy giải thích lý do kết hợp với phương pháp xử lý đụng độ này.

??? success "Đáp án tham khảo"

    1. Vì $1\bmod5=6\bmod5=11\bmod5=1$, còn $7\bmod5=2$, nội dung các ngăn là:

        ```text
        0: []
        1: [1, 6, 11]
        2: [7]
        3: []
        4: []
        ```

    2. Khi tìm kiếm 6, trước hết sẽ vào ngăn 1, sau đó lần lượt so sánh 1, 6, ở lần so sánh thứ hai sẽ tìm thấy mục tiêu.

    3. Giá trị băm giống nhau chỉ biểu thị chúng rơi vào cùng một ngăn, chứ không có nghĩa là các phần tử này bằng nhau. Phương pháp nối chuỗi lưu giữ toàn bộ các phần tử đụng độ trong ngăn,
        khi tra cứu sẽ so sánh lần lượt từng phần tử, do đó 1, 6, 11 không ghi đè lẫn nhau.

### Sau khi mở rộng dung lượng bảng băm, các phần tử sẽ đi đâu?

Một bảng băm sử dụng phương pháp nối chuỗi ban đầu có 5 ngăn, hàm băm là $h(x)=x\bmod5$.
Các khoá `[1, 6, 11]` đều nằm trong ngăn số 1.

Bây giờ mở rộng bảng băm thành 7 ngăn, hàm băm tương ứng chuyển thành $h(x)=x\bmod7$:

<!-- numbered-subquestions -->

1. Lần lượt tính số hiệu ngăn mới cho 1, 6, 11.
2. Sau khi mở rộng, những ngăn nào sẽ chứa phần tử?
3. Khi mở rộng dung lượng, có thể sao chép nguyên trạng danh sách từ ngăn 1 cũ sang ngăn 1 mới không? Hãy giải thích lý do kết hợp với kết quả ở câu 1 và câu 2.

??? success "Đáp án tham khảo"

    1. Số hiệu ngăn mới lần lượt là:

        - $1\bmod7=1$;
        - $6\bmod7=6$;
        - $11\bmod7=4$.

    2. Ngăn 1 chứa 1, ngăn 4 chứa 11, ngăn 6 chứa 6. Ba khoá này không còn bị dồn vào cùng một ngăn nữa.

    3. Không thể sao chép nguyên trạng. Số hiệu ngăn được tính bằng "khoá chia lấy dư cho số lượng ngăn". Sau khi số lượng ngăn đổi từ 5 sang 7, số hiệu ngăn mới của cùng một khoá có thể thay đổi,
        do đó bắt buộc phải tính toán lại vị trí (rehash) cho từng khoá. Nếu sao chép nguyên xi ngăn 1 cũ sang, sau này khi tra cứu 6 và 11 theo công thức mới,
        chương trình sẽ lần lượt tìm đến ngăn 6 và ngăn 4, dẫn đến không thể tìm thấy chúng.

### Sau khi xoá 6 thì có còn tìm thấy 11 không?

Một bảng băm có 5 vị trí, chỉ số từ `0~ 4`, hàm băm là $h(x)=x\bmod5$.
Khi xảy ra đụng độ, từ chỉ số do hàm băm tính ra sẽ tìm kiếm vị trí trống đầu tiên về phía bên phải.

Lần lượt chèn `[1, 6, 11]`:

<!-- numbered-subquestions -->

1. Ba số cuối cùng lần lượt được đặt vào chỉ số nào?
2. Khi tìm kiếm 11, chương trình sẽ lần lượt kiểm tra các chỉ số nào?
3. Nếu khi xoá 6 mà trực tiếp đổi vị trí của nó thành "vị trí trống chưa từng sử dụng", trong khi thao tác tìm kiếm hễ gặp vị trí trống là dừng lại,
    thì khi tìm kiếm 11 chuyện gì sẽ xảy ra? Kết quả tìm kiếm này có chính xác không? Nếu có vấn đề, làm thế nào để khắc phục?

??? success "Đáp án tham khảo"

    1. 1 đặt tại chỉ số 1. 6 cũng ánh xạ vào chỉ số 1, sau khi đụng độ sẽ được đặt vào chỉ số 2.
        11 cũng bắt đầu từ chỉ số 1, lần lượt bỏ qua các chỉ số 1, 2 đã bị chiếm dụng, cuối cùng đặt tại chỉ số 3.

    2. Khi tìm kiếm 11, chương trình lần lượt kiểm tra các chỉ số `1, 2, 3` và tìm thấy nó tại chỉ số 3.

    3. Nếu đổi chỉ số 2 thành vị trí trống "chưa từng sử dụng", khi tìm kiếm 11 sau khi kiểm tra chỉ số 1 sẽ dừng lại ngay tại chỉ số 2,
        từ đó kết luận sai rằng 11 không tồn tại. Khi xoá cần để lại dấu mốc "đã xoá" (tombstone):
        khi tìm kiếm gặp dấu mốc này sẽ tiếp tục kiểm tra chỉ số tiếp theo (vượt qua chỉ số 4 sẽ quay lại chỉ số 0), trong khi các thao tác chèn sau này vẫn có thể tái sử dụng vị trí này.

## Bài tập lập trình

### So sánh cấu thành ký tự của hai chuỗi

Cho hai chuỗi ký tự `s` và `t` chỉ chứa các chữ cái tiếng Anh in thường.
Có thể tuỳ ý điều chỉnh vị trí các ký tự trong `s`, nhưng không được thêm, xoá hoặc thay thế ký tự.

Hãy kiểm tra xem sau khi điều chỉnh có thể thu được `t` hay không; nếu được trả về `true`, ngược lại trả về `false`.
Hãy sử dụng bảng băm để đếm số lần xuất hiện của từng chữ cái, không sắp xếp các ký tự trong chuỗi.

??? tip "Gợi ý giải bài"

    1. Hai chuỗi có độ dài khác nhau thì cấu thành ký tự của chúng chắc chắn khác nhau
    2. Dùng bảng băm để ghi lại số lượng của từng chữ cái; khi quét qua s thì tăng biến đếm tương ứng lên 1
    3. Khi quét qua t thì giảm biến đếm tương ứng đi 1; cấu thành ký tự chỉ giống nhau khi toàn bộ biến đếm cuối cùng đều bằng 0

[LeetCode](https://leetcode.com/problems/valid-anagram/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" } [Giải thích lời giải](https://leetcode.cn/problems/valid-anagram/solutions/2362065/242-you-xhao-de-zi-mu-yi-wei-ci-ha-xi-bi-cch7/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }
