# Bài tập

## Củng cố kiến thức

### Khi nào thích hợp sử dụng quy hoạch động?

Một bạn học sinh nói: "Chỉ cần viết được công thức truy hồi là nên sử dụng quy hoạch động."
Hãy phán đoán xem ba nhiệm vụ dưới đây nhiệm vụ nào phù hợp hơn với quy hoạch động, quay lui, hay sử dụng vòng lặp/công thức toán học mà không cần lập bảng `dp`, và nêu ra một lý do then chốt.

<!-- numbered-subquestions -->

1. Sử dụng các mệnh giá tiền xu `[1, 3, 4]` để đổi số tiền 6, tìm số lượng đồng xu ít nhất, mỗi loại tiền xu có thể dùng lặp lại nhiều lần;
2. Xuất ra toàn bộ hoán vị của `[1, 2, 3]`;
3. Tính $1 + 2 + \dots + n$.

    Đối với nhiệm vụ bạn đánh giá là phù hợp với quy hoạch động, hãy giải thích thêm `dp[i]` biểu thị điều gì.

??? success "Đáp án tham khảo"

    1. Thích hợp với quy hoạch động. Đặt `dp[i]` biểu thị số lượng đồng xu ít nhất cần thiết để đổi số tiền `i`.
        Đối với mỗi đồng xu `c` không vượt quá `i`, đều có thể lấy `dp[i-c] + 1` làm đáp án ứng viên,
        sau đó lấy giá trị nhỏ nhất trong các giá trị ứng viên này. Các lựa chọn khác nhau sẽ liên tục gặp lại cùng một số tiền, và lời giải tối ưu của số tiền lớn hơn cũng có thể được cấu thành từ lời giải tối ưu của số tiền nhỏ hơn.
        Đáp án cho số tiền 6 là 2, tức `3 + 3`.

    2. Nên sử dụng quay lui. Đề bài yêu cầu sinh ra lần lượt toàn bộ 6 hoán vị, quay lui có thể thử một lựa chọn một cách có hệ thống, tiếp tục tìm kiếm,
        sau đó huỷ bỏ lựa chọn và thử các nhánh khác. Cho dù áp dụng phương pháp nào thì khi xuất ra các hoán vị này trên thực tế đều không thể bỏ qua việc liệt kê vét cạn.

    3. Chỉ cần dùng vòng lặp hoặc công thức cấp số cộng là đủ. Mặc dù có thể viết được `S(i) = S(i-1) + i`, nhưng khi tính `S(i)` chỉ phụ thuộc vào một giá trị nhỏ hơn duy nhất là `S(i-1)`,
        mỗi tổng bộ phận chỉ cần tính đúng một lần, không tồn tại các bài toán con trùng lặp, do đó không cần thiết lập bảng `dp`. "Viết được công thức truy hồi" không đồng nghĩa với việc "cần dùng quy hoạch động".

### Một ô trong bảng cái túi được tính như thế nào?

Cái túi 0-1: Trọng lượng đồ vật `wgt = [1, 2, 3]`, giá trị `val = [5, 11, 15]`, dung tích túi 4.
`dp[i][c]` biểu thị giá trị lớn nhất có thể đạt được khi chỉ xét $i$ đồ vật đầu tiên và giới hạn dung tích túi là $c$;
không yêu cầu phải xếp vừa khít đầy túi.

Bây giờ chỉ tính trạng thái `dp[3][4]`. Đã biết `dp[2][4] = 16`, `dp[2][1] = 5`:

<!-- numbered-subquestions -->

1. Khi không chọn đồ vật thứ 3, giá trị ứng viên là bao nhiêu?
2. Khi chọn đồ vật thứ 3, dung tích còn lại là bao nhiêu, và giá trị ứng viên là bao nhiêu?
3. `dp[3][4]` nên nhận giá trị nào? Tương ứng với việc đã chọn những đồ vật nào?

??? success "Đáp án tham khảo"

    1. Khi không chọn đồ vật thứ 3, kế thừa kết quả của hai đồ vật trước đó, giá trị ứng viên là `dp[2][4] = 16`.

    2. Đồ vật thứ 3 có trọng lượng là 3, sau khi cho vào túi thì dung tích còn lại là $4-3=1$; giá trị ứng viên là
        `dp[2][1] + 15 = 5 + 15 = 20`.

    3. So sánh 16 và 20, thu được `dp[3][4] = 20`. Nó tương ứng với việc chọn đồ vật thứ 1 và thứ 3,
        tổng trọng lượng là $1+3=4$, tổng giá trị là $5+15=20$.

        Việc tính toán trạng thái này thể hiện một lần so sánh "chọn hay không chọn" của bài toán cái túi 0-1.

### Dung tích túi nên được cập nhật theo thứ tự nào?

Một bài toán cái túi 0-1 chỉ có duy nhất một đồ vật: trọng lượng là 2, giá trị là 5; dung tích túi là 4.
Mỗi đồ vật được chọn tối đa một lần, mảng một chiều ban đầu là `dp = [0, 0, 0, 0, 0]`.

Một bạn học sinh khi xử lý đồ vật này đã cập nhật dung tích theo thứ tự từ 2 đến 4:

- Sau khi cập nhật `dp[2]` thu được 5;
- Sau khi cập nhật `dp[3]` cũng thu được 5;
- Khi cập nhật `dp[4]` lại sử dụng giá trị `dp[2]` vừa tính được, dẫn đến thu được `dp[4] = 10`.

<!-- numbered-subquestions -->

1. Kết quả `dp[4] = 10` này có đúng không? Tại sao?
2. Căn cứ theo điều kiện "mỗi đồ vật được chọn tối đa một lần", `dp[4]` nên bằng bao nhiêu?
3. Khi xử lý mỗi đồ vật, dung tích nên được cập nhật từ lớn đến nhỏ hay từ nhỏ đến lớn? Làm như vậy tránh được vấn đề gì?

??? success "Đáp án tham khảo"

    1. Kết quả này không đúng. Giá trị 10 tương đương với việc đã cho đồ vật có giá trị 5 này vào túi hai lần,
        vi phạm điều kiện "mỗi đồ vật được chọn tối đa một lần".

    2. Trong túi tối đa chỉ có thể đặt một đồ vật này, vì vậy `dp[4]` chính xác phải là 5.

    3. Dung tích nên được cập nhật từ lớn đến nhỏ, tức lần lượt xử lý 4, 3, 2.
        Làm như vậy thì khi tính `dp[c]`, giá trị `dp[c-2]` đọc được vẫn là kết quả trước khi xử lý đồ vật hiện tại,
        không làm cho đồ vật hiện tại bị sử dụng lặp lại trong cùng một vòng.

## Bài tập lập trình

### Số phương án leo cầu thang

Một chiếc cầu thang có tổng cộng `n` bậc. Mỗi lần bạn chỉ có thể bước lên 1 bậc hoặc 2 bậc, và bắt buộc phải tới chính xác bậc thứ `n`.
Hãy tính xem có tổng cộng bao nhiêu cách bước khác nhau. Quy định `n >= 1`, cách bước chỉ phân biệt theo chuỗi các bước 1 bậc hay 2 bậc.
Hãy hoàn thành bằng mảng quy hoạch động một chiều, tạm thời chưa dùng cách viết tối ưu không gian chỉ giữ lại hai trạng thái.

??? tip "Gợi ý giải bài"

    1. Bước cuối cùng để tới bậc thứ i chỉ có thể là bước 1 bậc hoặc 2 bậc
    2. Do đó có dp[i] = dp[i-1] + dp[i-2]
    3. Xử lý trước trường hợp n là 1 và 2, sau đó bắt đầu điền bảng từ bậc thứ 3

[LeetCode](https://leetcode.com/problems/climbing-stairs/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" } [Giải thích lời giải](https://leetcode.cn/problems/climbing-stairs/solutions/2361764/70-pa-lou-ti-dong-tai-gui-hua-qing-xi-tu-ruwa/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }

> **Lưu ý:** Lời giải trong liên kết giải thích trạng thái và chuyển trạng thái của dp một chiều, nhưng mã nguồn đưa ra sử dụng biến cuộn để nén không gian; bài tập này yêu cầu hiện thực bảng dp một chiều trước, biến cuộn chỉ là phần tối ưu nâng cao tuỳ chọn.

### Cái túi 0-1

Cho hai mảng cùng độ dài `wgt` và `val`, đồ vật thứ `i` có trọng lượng là số nguyên dương `wgt[i]` và giá trị là số nguyên không âm `val[i]`,
dung tích túi `cap` là số nguyên không âm. Mỗi đồ vật được chọn tối đa một lần, trong điều kiện tổng trọng lượng không vượt quá `cap`,
hãy tìm tổng giá trị lớn nhất có thể cho vào túi. Hãy hiện thực bằng quy hoạch động một chiều.

??? tip "Gợi ý giải bài"

    1. Khởi tạo mảng dp có độ dài cap + 1, trong đó dp[c] biểu thị giá trị lớn nhất khi giới hạn dung tích là c
    2. Khi xử lý đồ vật i, so sánh giữa việc "không chọn nó" dp[c] với việc "chọn nó" dp[c-wgt[i]] + val[i]
    3. Dung tích bắt buộc phải cập nhật từ lớn đến nhỏ để tránh chọn lặp lại đồ vật hiện tại trong cùng một vòng
