# Bài tập

## Củng cố kiến thức

### Thời gian và không gian của vòng lặp và đệ quy

Hai đoạn mã dưới đây đều tính $1 + 2 + \dots + n$ (giả sử $n \ge 1$)。Hãy đặt `n` bằng 4, trả lời các câu hỏi theo đúng thứ tự thực thi thực tế của chương trình, sau đó so sánh hiệu năng của hai cách viết.

```src
[file]{complexity_exercises}-[class]{}-[func]{sum_iter}
```

<!-- numbered-subquestions -->

1. Khi truyền đầu vào `n = 4` để thực thi hàm lặp, sau khi kết thúc mỗi vòng lặp, biến tích luỹ `res` lần lượt nhận các giá trị nào?
2. Khi truyền đầu vào `n = 4` để thực thi hàm đệ quy, tham số `n` sẽ lần lượt nhận những giá trị nào? Khi bắt đầu trả về từ tầng sâu nhất, kết quả được tính ra như thế nào?
3. Độ phức tạp thời gian và độ phức tạp không gian của hai cách viết lần lượt là bao nhiêu? Kết hợp quá trình thực thi từ câu 1 và câu 2 để giải thích lý do.

??? success "Đáp án tham khảo"

    1. Biến vòng lặp `i` lần lượt nhận các giá trị `1, 2, 3, 4`，sau mỗi vòng kết thúc, `res` lần lượt biến đổi thành `1, 3, 6, 10`，do đó hàm lặp trả về 10。

    2. Tham số `n` lần lượt nhận các giá trị `4 → 3 → 2 → 1`。
        Tầng sâu nhất trả về 1, sau đó các tầng lần lượt nhận được `2 + 1 = 3`、`3 + 3 = 6`、`4 + 6 = 10`。
        Ở thời điểm sâu nhất, cả 4 lời gọi hàm đều chưa kết thúc.

    3. Cả hai đoạn mã đều thực hiện số vòng lặp hoặc số lời gọi hàm tỷ lệ thuận với $n$ ，do đó độ phức tạp thời gian đều là $O(n)$ 。
        Độ phức tạp không gian khác nhau: phiên bản lặp chỉ sử dụng một số lượng biến hằng số, nên là $O(1)$ ；
        phiên bản đệ quy trước khi chạm tới điều kiện dừng, các lời gọi hàm trước đó đều phải chờ kết quả trả về, do đó ngăn xếp lời gọi hàm đồng thời lưu giữ tối đa $n$ lời gọi,
        độ phức tạp không gian là $O(n)$ 。

        Khi phân tích độ phức tạp không gian, ngoài các biến được khai báo trong mã nguồn, còn cần phải tính đến không gian bị chiếm dụng bởi các lời gọi đệ quy.

### Độ phức tạp thời gian của ba đoạn mã

Ba đoạn mã dưới đây đều nhận đầu vào là số nguyên dương $n$ 。Hãy sắp xếp chúng theo thứ tự độ phức tạp thời gian từ thấp đến cao và ghi rõ độ phức tạp tương ứng của từng đoạn mã.

```src
[file]{complexity_exercises}-[class]{}-[func]{linear_loop}
```

??? success "Đáp án tham khảo"

    Thứ tự từ thấp đến cao là: Đoạn mã 3 $O(\log n)$、Đoạn mã 1 $O(n)$、Đoạn mã 2 $O(n^2)$。
    Đoạn mã 3 sau mỗi vòng lặp đều thu nhỏ $n$ còn một nửa so với trước, lặp khoảng $\log_2 n$ lần.
    Vòng lặp ở Đoạn mã 1 thực thi đúng $n$ lần. Vòng lặp bên trong của Đoạn mã 2 có số lần thực thi lần lượt là $n, n-1, \dots, 1$，tổng số lần là $n(n+1)/2$，do đó thuộc bậc bình phương.

### Phương pháp đảo ngược nào tiết kiệm không gian hơn?

Để đảo ngược toàn bộ các phần tử trong mảng `nums` ，có hai cách làm:

<!-- numbered-subquestions -->

1. Tạo một mảng mới `res` có cùng độ dài, sao chép các phần tử theo thứ tự đảo ngược rồi trả về;
2. Dùng hai chỉ số `i` và `j` lần lượt di chuyển từ hai đầu vào giữa, hoán đổi từng cặp `nums[i]` và `nums[j]` 。

    Độ phức tạp không gian của hai cách làm lần lượt là bao nhiêu? Cách nào thuộc thao tác “tại chỗ” (in-place)?

??? success "Đáp án tham khảo"

    1. Cần một mảng phụ trợ có độ dài bằng mảng đầu vào, độ phức tạp không gian là $O(n)$ 。

    2. Chỉ sử dụng hai biến chỉ số,
        độ phức tạp không gian là $O(1)$ ，thuộc thao tác tại chỗ.

        Cần lưu ý: việc đảo ngược tại chỗ sẽ làm thay đổi mảng đầu vào,
        chỉ nên ưu tiên sử dụng khi cho phép thay đổi dữ liệu đầu vào; nếu cần giữ nguyên mảng ban đầu, chi phí sao chép của cách thứ nhất là không thể tránh khỏi.

## Bài tập lập trình

### Số Fibonacci

Dãy số Fibonacci thoả mãn: $F(0)=0$、$F(1)=1$，và khi $n\ge2$ thì $F(n)=F(n-1)+F(n-2)$。

Cho số nguyên không âm `n`，hãy sử dụng vòng lặp để tính và trả về $F(n)$，không sử dụng đệ quy.

??? tip "Gợi ý giải bài"

    1. Xử lý riêng trường hợp n bằng 0 và 1 trước
    2. Khi tính số hạng tiếp theo chỉ cần hai số hạng liền trước, không cần lưu trữ toàn bộ dãy số
    3. Khi cập nhật hai biến số, chú ý không ghi đè quá sớm lên giá trị cũ mà vẫn còn dùng đến

[LeetCode](https://leetcode.com/problems/fibonacci-number/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" } [Giải thích lời giải](https://leetcode.cn/problems/fibonacci-number/solutions/2361746/509-fei-bo-na-qi-shu-dong-tai-gui-hua-qi-so8h/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }
