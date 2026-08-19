# Bài tập

## Củng cố kiến thức

### Biểu diễn cùng một đồ thị bằng hai phương thức

Một đồ thị vô hướng có 4 đỉnh `A, B, C, D`, các cạnh là
`A-B, A-C, B-C, C-D`.

<!-- numbered-subquestions -->

1. Viết danh sách kề của nó;
2. Điền ma trận kề chỉ chứa 0 và 1;
3. Nếu muốn kiểm tra `A` và `D` có kết nối trực tiếp với nhau hay không, phương thức biểu diễn đồ thị nào chỉ cần xem đúng một vị trí lưu trữ?
4. Nếu đồ thị có rất nhiều đỉnh nhưng lại rất ít cạnh, phương thức biểu diễn nào thường tiết kiệm không gian hơn?

??? success "Đáp án tham khảo"

    1. Danh sách kề là:

        ```text
        A: B, C
        B: A, C
        C: A, B, D
        D: C
        ```

    2. Ma trận kề là:

        | | A | B | C | D |
        | --- | --- | --- | --- | --- |
        | A | 0 | 1 | 1 | 0 |
        | B | 1 | 0 | 1 | 0 |
        | C | 1 | 1 | 0 | 1 |
        | D | 0 | 0 | 1 | 0 |

    3. Ma trận kề có thể xem trực tiếp tại hàng `A`, cột `D`, do đó rất thích hợp để kiểm tra xem hai đỉnh bất kỳ có kết nối trực tiếp với nhau hay không.

    4. Khi có rất nhiều đỉnh nhưng ít cạnh, danh sách kề chỉ lưu trữ các cạnh thực sự tồn tại, thường tiết kiệm không gian hơn so với ma trận kề vốn phải dành sẵn vị trí cho mọi cặp đỉnh.

### Thứ tự truy cập của duyệt theo chiều rộng và chiều sâu

Một đồ thị vô hướng có các đỉnh `A, B, C, D, E`, các cạnh là
`A-B, A-C, B-D, C-D, D-E`.

Bắt đầu từ A, và quy định khi gặp nhiều đỉnh kề chưa được truy cập thì lựa chọn theo thứ tự bảng chữ cái:

<!-- numbered-subquestions -->

1. Viết thứ tự truy cập của duyệt theo chiều rộng (BFS);
2. Viết thứ tự truy cập của duyệt đệ quy theo chiều sâu (DFS);
3. Tại sao cả hai phương thức duyệt đều cần phải ghi lại các đỉnh đã được truy cập?

??? success "Đáp án tham khảo"

    1. Thứ tự truy cập của BFS là `A, B, C, D, E`. Nó truy cập các đỉnh B, C cách A một cạnh trước,
        sau đó mới truy cập các đỉnh xa hơn là D, E.

    2. Thứ tự truy cập của DFS là `A, B, D, C, E`. Nó lần lượt đi vào các đỉnh kề chưa được truy cập của đỉnh hiện tại,
        do đó trước tiên đi theo `A → B → D → C`; khi C không còn đỉnh kề mới nào thì quay lại D, rồi mới truy cập E.

    3. Trong đồ thị tồn tại chu trình (cycle), ví dụ `A-B-D-C-A`. Nếu không ghi lại các đỉnh đã truy cập,
        quá trình duyệt có thể lặp đi lặp lại việc truy cập cùng một nhóm đỉnh dọc theo chu trình, không thể kết thúc bình thường.

### Một lần BFS có thể truy cập toàn bộ đồ thị không?

Một đồ thị vô hướng có các đỉnh `A, B, C, D, E, F`, các cạnh chỉ có
`A-B, B-C, D-E`.

<!-- numbered-subquestions -->

1. Bắt đầu từ A thực hiện một lần BFS, có thể truy cập những đỉnh nào?
2. Dựa theo câu hỏi 1, lần BFS này đã truy cập toàn bộ các đỉnh trong đồ thị chưa? Tại sao?
3. Nếu quét toàn bộ các đỉnh theo thứ tự bảng chữ cái, mỗi khi gặp một đỉnh chưa được truy cập lại bắt đầu một lần BFS mới,
    thì điểm xuất phát của mỗi lần BFS là gì? Đồ thị này được chia thành mấy phần không liên thông với nhau (thành phần liên thông)?

??? success "Đáp án tham khảo"

    1. Xuất phát từ A chỉ có thể truy cập `A, B, C`.

    2. Chưa truy cập toàn bộ các đỉnh. `D, E` tạo thành một phần liên thông khác với nhau, F là một đỉnh đứng riêng lẻ;
        giữa chúng và A đều không có đường đi, do đó xuất phát từ A không thể đi tới được.

    3. Điểm xuất phát của ba lần BFS lần lượt là `A, D, F`, lần lượt truy cập
        `{A, B, C}`, `{D, E}` và `{F}`. Do đó đồ thị này có 3 thành phần liên thông.

## Bài tập lập trình

### Kiểm tra sự tồn tại của đường đi trong đồ thị vô hướng

Cho một đồ thị vô hướng chứa $n$ đỉnh, các đỉnh được đánh số từ $0$ đến $n-1$. Mỗi phần tử `[u, v]` trong mảng `edges` biểu thị giữa đỉnh `u` và `v` có một cạnh vô hướng.

Cho thêm điểm xuất phát `source` và điểm đích `destination`. Hãy dựa vào `edges` để thiết lập danh sách kề trước, sau đó sử dụng BFS hoặc DFS
để kiểm tra xem có tồn tại một đường đi từ `source` đến `destination` hay không: nếu tồn tại trả về `true`, ngược lại trả về `false`.
Đồ thị có thể chứa chu trình, và cũng có thể không liên thông.

??? tip "Gợi ý giải bài"

    1. Mỗi cạnh vô hướng cần phải thêm đồng thời ở cả hai chiều
    2. Trong đồ thị có thể chứa chu trình, bắt buộc phải ghi lại các đỉnh đã được truy cập
    3. Xuất phát từ source, nếu gặp destination thì trả về true, sau khi duyệt xong mà vẫn chưa gặp thì trả về false

[LeetCode](https://leetcode.com/problems/find-if-path-exists-in-graph/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }
