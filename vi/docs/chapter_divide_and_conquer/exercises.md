# Bài tập

## Củng cố kiến thức

### Những tác vụ nào phù hợp với chia để trị?

Một bạn học sinh muốn dùng phương pháp "chia làm hai nửa trước, giải quyết riêng rẽ từng nửa, sau đó gộp kết quả lại" để hoàn thành các tác vụ dưới đây.
Hãy phán đoán xem chúng thuộc loại "phù hợp với chia để trị", "có thể dùng chia để trị, nhưng không làm giảm tổng khối lượng công việc" hay "hai nửa không thể giải quyết độc lập", và giải thích lý do:

<!-- numbered-subquestions -->

1. Sắp xếp một mảng chưa có thứ tự;
2. Tìm giá trị lớn nhất trong một mảng;
3. Thực hiện theo thứ tự một chuỗi các thao tác ngăn xếp `push(x)`, `pop()`, và xuất ra các phần tử thu được sau mỗi lần `pop()`.

??? success "Đáp án tham khảo"

    1. Phù hợp: Chia đôi mảng, sắp xếp độc lập hai nửa, gộp lại trong thời gian $O(n)$ — đây chính là sắp xếp trộn.
    2. Có thể dùng chia để trị, nhưng không làm giảm tổng khối lượng công việc: Hai nửa trái phải vẫn phải kiểm tra tổng cộng toàn bộ $n$ phần tử,
        tương tự như duyệt tuần tự trực tiếp đều mất thời gian $O(n)$.
    3. Hai nửa không thể giải quyết độc lập: Nội dung ngăn xếp tại thời điểm bắt đầu nửa sau phụ thuộc vào kết quả thực thi của nửa trước,
        hai nửa không thể hoàn thành độc lập khi chưa biết kết quả của nhau.

### Thuật toán luỹ thừa nhanh (Fast Power) giảm thiểu tính toán như thế nào?

Hàm đệ quy dưới đây sử dụng chia để trị để tính $x^n$:

```src
[file]{fast_power}-[class]{}-[func]{fast_pow}
```

Đặt `x = 3`, `n = 5`, dùng hàm này để tính toán:

<!-- numbered-subquestions -->

1. Khi gọi đệ quy, tham số `n` lần lượt nhận những giá trị nào?
2. Bắt đầu trả về từ tầng sâu nhất, mỗi tầng lần lượt trả về giá trị gì?
3. Tại sao phải lưu trước kết quả đệ quy vào biến `half`, thay vì gọi cùng một bài toán con ở hai vế của phép nhân?

??? success "Đáp án tham khảo"

    1. Tham số lần lượt là `5 → 2 → 1 → 0`, mỗi lần đều giảm số mũ đi một nửa cho đến khi chạm điều kiện dừng.

    2. Khi `n = 0` trả về 1; khi `n = 1` trả về $1 \times 1 \times 3 = 3$;
        khi `n = 2` trả về $3 \times 3 = 9$; khi `n = 5` trả về $9 \times 9 \times 3 = 243$.

    3. Nếu gọi bài toán con giống nhau ở hai vế của phép nhân, hai lần đệ quy sẽ thực hiện các phép tính hoàn toàn trùng lặp.
        Việc lưu kết quả vào biến `half` trước giúp mỗi tầng chỉ cần gọi đệ quy một lần, độ sâu đệ quy khoảng $\log n$;
        nếu gọi hai lần sẽ gây ra lượng lớn các phép tính lặp thừa thãi.

### Tách cây con trái và phải từ dãy duyệt

Một cây nhị phân không có các nút trùng lặp, có dãy duyệt tiền thứ tự và duyệt trung thứ tự lần lượt là:

- Duyệt tiền thứ tự: `[A, B, D, E, C]`
- Duyệt trung thứ tự: `[D, B, E, A, C]`

Chỉ hoàn thành việc bóc tách ở tầng nút gốc này, không cần tiếp tục đệ quy và cũng không cần vẽ toàn bộ cây:

<!-- numbered-subquestions -->

1. Nút gốc là nút nào?
2. Cây con trái và cây con phải tương ứng với đoạn nào trong duyệt trung thứ tự?
3. Cây con trái và cây con phải tương ứng với đoạn nào trong duyệt tiền thứ tự? Nút gốc có những nút con trực tiếp nào?

??? success "Đáp án tham khảo"

    1. Nút đầu tiên của duyệt tiền thứ tự là nút gốc, do đó nút gốc là `A`.

    2. `A` chia duyệt trung thứ tự thành hai phần: cây con trái là `[D, B, E]`, cây con phải là `[C]`.

    3. Cây con trái có 3 nút, do đó 3 phần tử tiền thứ tự đứng sau nút gốc `A` thuộc về cây con trái,
        tức là `[B, D, E]`; phần tử `[C]` còn lại thuộc về cây con phải.
        Vì vậy nút con trái của nút gốc là `B`, nút con phải là `C`.

## Bài tập lập trình

### Luỹ thừa nhanh (Fast Power)

Cho số thực `x` và số nguyên `n`, hãy tính $x^n$ mà không gọi hàm luỹ thừa tích hợp sẵn của ngôn ngữ.
Yêu cầu sử dụng chia để trị bằng đệ quy: mỗi lần thu nhỏ số mũ đi một nửa, và tái sử dụng kết quả bài toán con đã tính toán.
Quy ước $x^0=1$, bao gồm cả khi `x = 0`; khi `n < 0` đảm bảo `x != 0`, kết quả có thể quy đổi thành $(1/x)^{-n}$.

??? tip "Gợi ý giải bài"

    1. Khi n bằng 0 kết quả là 1
    2. Sau khi tính x luỹ thừa n // 2 thì lưu vào biến half, không gọi đệ quy lần thứ hai
    3. Khi n < 0, trước tiên đổi x thành 1 / x, sau đó đổi n thành -n; khi dùng C++ hoặc Java, có thể ép kiểu n sang số nguyên 64-bit để tránh tràn số khi lấy số đối của số nguyên 32-bit nhỏ nhất

[LeetCode](https://leetcode.com/problems/powx-n/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" } [Giải thích lời giải](https://leetcode.cn/problems/powx-n/solutions/241471/50-powx-n-kuai-su-mi-qing-xi-tu-jie-by-jyd/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }
