# Bài tập

## Củng cố kiến thức

### Mỗi lần chọn đồng xu lớn nhất có chắc chắn là tốt nhất không?

Mệnh giá tiền xu là `[1, 7, 10]`, số tiền mục tiêu là 14.

<!-- numbered-subquestions -->

1. Thực hiện theo quy tắc "mỗi lần chọn mệnh giá lớn nhất không vượt quá số tiền còn lại", hãy viết các đồng xu được chọn;
2. Có tồn tại phương án sử dụng ít đồng xu hơn không? Nếu có, hãy viết ra một phương án; nếu không, hãy giải thích lý do;
3. Điều này có thể chứng minh chiến lược tham lam đúng với mọi bộ mệnh giá tiền xu không?

??? success "Đáp án tham khảo"

    1. Tham lam lần lượt chọn `10 + 1 + 1 + 1 + 1`, tổng cộng 5 đồng xu.

    2. Tồn tại phương án sử dụng ít đồng xu hơn: `7 + 7`, chỉ cần 2 đồng xu.

    3. Không thể. Phản ví dụ này chứng minh rằng, đối với bộ mệnh giá tiền xu bất kỳ, việc mỗi lần chọn mệnh giá lớn nhất hiện có không nhất thiết thu được số lượng đồng xu ít nhất;
        lựa chọn lớn nhất trước mắt có thể phá vỡ các tổ hợp tốt hơn phía sau.

### Nên cho đồ vật nào vào túi trước?

Một chiếc túi có dung tích 4 kg có thể chứa các đồ vật dưới đây, đồ vật cho phép chỉ lấy một phần,
giá trị thu được tỷ lệ thuận với trọng lượng:

- Đồ vật A: trọng lượng 4 kg, giá trị 20;
- Đồ vật B: trọng lượng 3 kg, giá trị 18.

<!-- numbered-subquestions -->

1. Giá trị trên mỗi kg của hai đồ vật lần lượt là bao nhiêu? Nên cho đồ vật nào vào túi trước?
2. Cho đồ vật vào đầy túi theo chiến lược tham lam của cái túi phân số, giá trị cuối cùng là bao nhiêu?
3. Trong trường hợp đồ vật có thể chia nhỏ và túi giới hạn tổng trọng lượng, khi chọn đồ vật nên so sánh tổng giá trị hay giá trị trên mỗi kg? Tại sao?

??? success "Đáp án tham khảo"

    1. A có giá trị trên mỗi kg là `20 ÷ 4 = 5`, B có giá trị trên mỗi kg là `18 ÷ 3 = 6`,
        vì vậy nên cho đồ vật B có đơn giá cao hơn vào trước.

    2. Trước hết cho toàn bộ B vào túi, chiếm 3 kg và thu được giá trị 18; còn dư 1 kg dung tích,
        tiếp tục cho 1 kg của đồ vật A vào, thu được giá trị 5. Giá trị cuối cùng là `18 + 5 = 23`.

    3. Chiếc túi giới hạn tổng trọng lượng và đồ vật có thể chia nhỏ, vì vậy nên so sánh giá trị trên mỗi đơn vị trọng lượng.
        Mặc dù tổng giá trị của A cao hơn, nhưng giá trị trên mỗi kg lại thấp hơn B; nếu cho đầy A trước thì chỉ thu được giá trị 20.

### Hai con trỏ bước tiếp theo dịch chuyển như thế nào?

Chiều cao của các vách ngăn là `[1, 8, 6, 2, 5]`, sử dụng hai con trỏ ở hai đầu để tìm dung tích lớn nhất.
Dung tích bằng "chiều cao của vách ngăn ngắn hơn trong hai vách × khoảng cách chỉ số giữa hai vách ngăn".

<!-- numbered-subquestions -->

1. Ban đầu con trỏ trái ở chỉ số 0, con trỏ phải ở chỉ số 4, dung tích hiện tại là bao nhiêu? Bước tiếp theo nên dịch chuyển con trỏ nào?
2. Sau khi dịch chuyển một lần theo lựa chọn ở câu 1, hai con trỏ lần lượt nằm ở chỉ số nào? Lúc này dung tích là bao nhiêu? Bước tiếp theo lại nên dịch chuyển con trỏ nào?
3. Trong cặp vách ngăn hiện tại, có thể dịch chuyển con trỏ tương ứng với vách ngắn hơn hoặc dịch chuyển con trỏ tương ứng với vách dài hơn. Lựa chọn dịch chuyển nào vẫn có khả năng thu được dung tích lớn hơn? Tại sao?

??? success "Đáp án tham khảo"

    1. Dung tích hiện tại là `min(1, 5) × (4 - 0) = 4`. Vách ngăn bên trái ngắn hơn, vì vậy dịch chuyển con trỏ trái.

    2. Sau khi dịch chuyển con trỏ trái, hai con trỏ lần lượt nằm ở chỉ số 1 và 4. Dung tích hiện tại là
        `min(8, 5) × (4 - 1) = 15`. Vách ngăn bên phải ngắn hơn, vì vậy bước tiếp theo dịch chuyển con trỏ phải.

    3. Chỉ có dịch chuyển con trỏ tương ứng với vách ngắn hơn thì mới có khả năng thu được dung tích lớn hơn. Sau khi dịch chuyển vách dài hơn, khoảng cách giữa hai vách chắc chắn rút ngắn lại, trong khi chiều cao của bình chứa vẫn bị giới hạn bởi vách ngắn chưa dịch chuyển,
        chỉ có thể giữ nguyên hoặc nhỏ đi. Do đó dung tích không thể vượt quá trước khi dịch chuyển; chỉ khi dịch chuyển vách ngắn thì mới có cơ hội gặp vách ngăn cao hơn.

## Bài tập lập trình

### Cái túi phân số

Cho hai mảng cùng độ dài `wgt` và `val`, trong đó `wgt[i] > 0`, `val[i] >= 0`, dung tích túi `cap >= 0`.
Mỗi loại đồ vật chỉ có duy nhất một cái, nhưng cho phép chỉ cho vào một phần của nó,
giá trị thu được tính theo tỷ lệ trọng lượng cho vào so với tổng trọng lượng của đồ vật đó. Hãy sử dụng thuật toán tham lam,
và trả về tổng giá trị lớn nhất mà chiếc túi có thể chứa được dưới dạng số thực.

??? tip "Gợi ý giải bài"

    1. Trước hết tính giá trị trên một đơn vị trọng lượng val[i] / wgt[i] của mỗi đồ vật, kết quả phép chia phải giữ lại phần thập phân
    2. Đồ vật có đơn giá càng cao thì càng được cho vào túi trước
    3. Nếu dung tích còn lại nhỏ hơn trọng lượng đồ vật hiện tại, chỉ cần cho vào phần vừa đủ để lấp đầy túi rồi kết thúc
