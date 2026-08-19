# Bài tập

## Củng cố kiến thức

### Ngăn xếp và hàng đợi sẽ lấy phần tử nào ra trước?

Chuẩn bị một ngăn xếp rỗng `S` và một hàng đợi rỗng `Q`，lần lượt thực hiện cùng một chuỗi thao tác dưới đây cho cả hai:

Bước 1: Thêm `A`；
Bước 2: Thêm `B`；
Bước 3: Lấy ra một phần tử và ghi lại；
Bước 4: Thêm `C`；
Bước 5: Liên tục lấy ra và ghi lại cho đến khi vật chứa rỗng.

Hãy viết thứ tự các phần tử được lấy ra từ `S` và `Q`，đồng thời dùng nguyên lý "vào sau ra trước" hoặc "vào trước ra trước" để giải thích sự khác biệt.

??? success "Đáp án tham khảo"

    Thứ tự lấy ra của ngăn xếp `S` là `B、C、A`：sau khi thêm `A、B`，phần tử được thêm vào gần nhất là `B` sẽ được lấy ra trước, sau đó thêm `C`，
    từ đó lần lượt lấy ra `C、A`，thể hiện đặc tính "vào sau ra trước".

    Thứ tự lấy ra của hàng đợi `Q` là `A、B、C`：sau khi thêm `A、B`，phần tử được thêm vào sớm nhất là `A` sẽ được lấy ra trước,
    sau đó thêm `C`，từ đó lần lượt lấy ra `B、C`，thể hiện đặc tính "vào trước ra trước".

### Cuối hàng đợi vượt quá giới hạn cuối mảng thì xử lý thế nào?

Dùng một mảng vòng có độ dài 5 để hiện thực hàng đợi, các chỉ số của mảng là `0～4`。
Hiện tại `front = 3`、`size = 2`，các phần tử `A、B` trong hàng đợi lần lượt nằm tại chỉ số 3 và 4.

<!-- numbered-subquestions -->

1. Khi thực hiện "thêm `C` vào hàng đợi", `C` nên được đặt vào chỉ số nào? Sau khi thêm, `size` bằng bao nhiêu?
2. Tiếp tục thực hiện một lần lấy phần tử ra khỏi hàng đợi, phần tử nào sẽ được lấy ra? Giá trị mới của `front` và `size` lần lượt là bao nhiêu?
3. Lúc này thứ tự logic từ đầu hàng đến cuối hàng là gì? Khi lấy phần tử ra khỏi hàng đợi có cần di chuyển các phần tử khác trong mảng không? Vì sao?

??? success "Đáp án tham khảo"

    1. Vị trí của phần tử mới là
        `(front + size) % 5 = (3 + 2) % 5 = 0`，
        do đó `C` được đặt tại chỉ số 0. Sau khi thêm vào hàng đợi, `size = 3`。

    2. Thao tác ra khỏi hàng đợi sẽ lấy phần tử ở đầu hàng hiện tại là `A`。Chỉ số đầu hàng mới là
        `(3 + 1) % 5 = 4`，vì vậy `front = 4`、`size = 2`。

    3. Thứ tự logic của các phần tử hợp lệ là `B、C`，trong đó `B` nằm tại chỉ số 4, còn `C` nằm tại chỉ số 0.
        Khi ra khỏi hàng đợi chỉ cần di chuyển `front` và cập nhật `size`，mảng vòng sử dụng phép chia lấy dư để đưa chỉ số quay trở lại đầu mảng,
        do đó không cần phải dịch chuyển toàn bộ các phần tử khác về phía trước.

### Các thao tác ở hai đầu của hàng đợi hai đầu

Quy định: `push_first` biểu thị thêm vào đầu hàng, `push_last` biểu thị thêm vào cuối hàng,
`pop_first` biểu thị lấy ra ở đầu hàng, `pop_last` biểu thị lấy ra ở cuối hàng.

Đối với một hàng đợi hai đầu rỗng `deq`，lần lượt thực hiện:

1. `push_last(A)`
2. `push_last(B)`
3. `push_first(C)`
4. `pop_last()`
5. `push_last(D)`
6. `pop_first()`

<!-- numbered-subquestions -->

1. Hai phần tử được lấy ra lần lượt là gì?
2. Sau khi hoàn thành toàn bộ các thao tác, từ đầu hàng đến cuối hàng còn lại những phần tử nào?
3. Xem xét 6 bước thao tác trên: một hàng đợi thông thường (chỉ cho phép thêm vào cuối hàng và xoá ở đầu hàng) có thể hoàn thành toàn bộ các thao tác này không? Nếu không, hãy chỉ ra các thao tác không thể thực hiện; sau đó giải thích hàng đợi hai đầu có thể hoàn thành hay không và tại sao.

??? success "Đáp án tham khảo"

    Sau 3 bước đầu tiên, hàng đợi hai đầu từ đầu hàng đến cuối hàng là `[C, A, B]`。

    <!-- numbered-subquestions -->

    1. `pop_last()` lấy ra `B`；sau khi thêm `D`，hàng đợi là `[C, A, D]`，
        `pop_first()` tiếp tục lấy ra `C`。

    2. Cuối cùng còn lại `[A, D]`。

    3. Hàng đợi thông thường (chỉ cho phép thêm ở cuối và xoá ở đầu) không thể hoàn thành toàn bộ các thao tác:
        Bước 3 `push_first(C)` yêu cầu thêm vào đầu hàng, bước 4 `pop_last()` yêu cầu xoá ở cuối hàng, cả hai đều vượt quá phạm vi thao tác của loại hàng đợi này.
        Hàng đợi hai đầu cho phép thêm và xoá ở cả hai đầu, do đó có thể hoàn thành trọn vẹn cả 6 bước thao tác trên.

## Bài tập lập trình

### Kiểm tra tính hợp lệ của chuỗi dấu ngoặc

Cho một chuỗi ký tự `s` chỉ chứa ba loại dấu ngoặc `()`、`[]`、`{}`，hãy sử dụng ngăn xếp để kiểm tra xem chuỗi đó có hợp lệ hay không.

Một chuỗi hợp lệ phải đồng thời thoả mãn: mỗi dấu ngoặc đóng phải khớp kiểu với dấu ngoặc mở chưa được ghép đôi gần nhất,
và sau khi duyệt xong toàn bộ chuỗi thì không còn dấu ngoặc mở nào chưa được ghép đôi. Trả về giá trị boolean biểu thị kết quả kiểm tra.

??? tip "Gợi ý giải bài"

    1. Có thể xây dựng một bảng ánh xạ "từ dấu ngoặc đóng sang dấu ngoặc mở tương ứng"
    2. Khi gặp dấu ngoặc đóng, trước tiên kiểm tra xem ngăn xếp có rỗng hay không, sau đó kiểm tra xem phần tử ở đỉnh ngăn xếp có khớp hay không
    3. Sau khi kết thúc quá trình duyệt, ngăn xếp cũng bắt buộc phải rỗng

[LeetCode](https://leetcode.com/problems/valid-parentheses/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" } [Giải thích lời giải](https://leetcode.cn/problems/valid-parentheses/solutions/9185/valid-parentheses-fu-zhu-zhan-fa-by-jin407891080/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }
