# Bài tập

## Củng cố kiến thức

### Số 10 sau khi thêm vào đống được điều chỉnh như thế nào?

Mảng `[9, 7, 8, 3, 5]` biểu diễn một đống cực đại. Bây giờ thêm số 10 vào đống:

<!-- numbered-subquestions -->

1. Trước hết thêm 10 vào cuối mảng, giá trị của nút cha của nó là bao nhiêu?
2. Bắt đầu từ nút mới thực hiện vun đống từ dưới lên trên (vun lên), hãy viết mảng sau mỗi lần hoán đổi.
3. Phần tử đỉnh đống cuối cùng là gì? Tổng cộng đã thực hiện mấy lần hoán đổi?

??? success "Đáp án tham khảo"

    1. 10 thêm vào sau có chỉ số là 5, chỉ số nút cha của nó là
        $\lfloor(5-1)/2\rfloor=2$, giá trị của nút cha là 8.

    2. 10 lớn hơn 8, sau lần hoán đổi thứ nhất mảng là `[9, 7, 10, 3, 5, 8]`;
        10 lại lớn hơn nút cha 9, sau lần hoán đổi thứ hai mảng là `[10, 7, 9, 3, 5, 8]`.
        Lúc này 10 đã lên tới nút gốc, quá trình vun đống kết thúc.

    3. Phần tử đỉnh đống cuối cùng là 10, tổng cộng hoán đổi 2 lần.

### Kiểm tra quan hệ cha con trong đống cực tiểu

Mảng `[1, 4, 3, 7, 6, 2]` biểu diễn một cây nhị phân hoàn chỉnh. Đống cực tiểu yêu cầu mọi nút cha đều không được lớn hơn các nút con của nó.
Đối với chỉ số $i$, chỉ số nút con trái và phải lần lượt là $2i+1$ và $2i+2$.

<!-- numbered-subquestions -->

1. Chỉ số và giá trị các nút con của chỉ số 2 lần lượt là gì?
2. Nút tại chỉ số 2 có giá trị là 3, nó cùng các nút con có vi phạm quy tắc đống cực tiểu không? Nếu vi phạm, nên hoán đổi hai phần tử nào?
3. Dựa theo câu hỏi 2: nếu vi phạm quy tắc, hãy viết mảng sau khi hoán đổi; nếu không vi phạm, hãy giải thích tại sao không cần hoán đổi. Cuối cùng hãy kiểm tra các quan hệ cha con còn lại.

??? success "Đáp án tham khảo"

    1. Nút con trái của chỉ số 2 có chỉ số là 5, giá trị là 2; chỉ số nút con phải là 6 nhưng độ dài mảng là 6, do đó nút con phải không tồn tại.

    2. Giá trị nút cha 3 lớn hơn giá trị nút con 2, vi phạm quy tắc đống cực tiểu, nên hoán đổi phần tử tại chỉ số 2 và chỉ số 5.

    3. Sau khi hoán đổi ta được mảng `[1, 4, 2, 7, 6, 3]`. Lần lượt kiểm tra:
        `1 ≤ 4`, `1 ≤ 2`; `4 ≤ 7`, `4 ≤ 6`; `2 ≤ 3`.
        Toàn bộ các nút cha đều không lớn hơn các nút con của chúng, do đó hiện tại đã thoả mãn quy tắc đống cực tiểu.

### Dùng đống cực tiểu để giữ lại 3 số lớn nhất

Để giữ lại 3 số lớn nhất từ luồng dữ liệu `[4, 1, 7, 3, 8]`, có thể duy trì một đống cực tiểu có kích thước không vượt quá 3.

Trước tiên lần lượt đưa 3 số đầu tiên vào đống cực tiểu. Sau khi đống đầy, mỗi khi đọc một số mới:
nếu số đó lớn hơn đỉnh đống thì xoá đỉnh đống và đưa số mới vào; ngược lại giữ nguyên đống.

Hãy viết các số được giữ lại trong đống và phần tử đỉnh đống sau mỗi lần đọc số mới.
Chỉ cần viết các số được giữ lại dưới dạng tập hợp, không yêu cầu viết thứ tự sắp xếp của chúng trong mảng đống.

??? success "Đáp án tham khảo"

    Kết quả sau mỗi lần đọc số mới như sau:

    | Số được đọc | Các số được giữ lại | Đỉnh đống |
    | --- | --- | --- |
    | 4 | `{4}` | 4 |
    | 1 | `{1, 4}` | 1 |
    | 7 | `{1, 4, 7}` | 1 |
    | 3 | `{3, 4, 7}` | 3 |
    | 8 | `{4, 7, 8}` | 4 |

    Sau khi đống đầy, đỉnh đống luôn là số nhỏ nhất trong các số đang được giữ lại. Chỉ khi số mới lớn hơn đỉnh đống thì mới thay thế đỉnh đống bằng số mới.
    Tập hợp `{4, 7, 8}` được giữ lại cuối cùng chính là 3 số lớn nhất.

## Bài tập lập trình

### Tìm phần tử lớn thứ k trong mảng

Cho mảng số nguyên `nums` và số nguyên $k$, trong đó $1 \le k \le n$, $n$ là độ dài mảng. Sau khi sắp xếp mảng theo thứ tự từ lớn đến nhỏ, hãy trả về phần tử nằm ở vị trí thứ $k$.

Các phần tử trùng lặp cần được đếm riêng rẽ. Ví dụ, phần tử lớn thứ 2 của `[5, 5, 2]` vẫn là 5. Hãy sử dụng một đống cực tiểu có kích thước không vượt quá $k$ để hoàn thành bài toán.

??? tip "Gợi ý giải bài"

    1. Phần tử lớn thứ k chính là phần tử nhỏ nhất trong k số lớn nhất
    2. Mỗi số trước tiên đưa vào đống cực tiểu, khi kích thước vượt quá k thì lấy phần tử nhỏ nhất ra
    3. Sau khi duyệt xong toàn bộ mảng, đống giữ lại k số lớn nhất và đỉnh đống chính là đáp án

[LeetCode](https://leetcode.com/problems/kth-largest-element-in-an-array/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" } [Giải thích lời giải](https://leetcode.cn/problems/kth-largest-element-in-an-array/solutions/2361969/215-shu-zu-zhong-de-di-k-ge-zui-da-yuan-d786p/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }

> **Lưu ý:** Lời giải trong liên kết giải thích bằng thuật toán sắp xếp nhanh (Quick sort) và chọn nhanh (Quick select), không sử dụng đống; trong bài tập này vui lòng thực hiện bằng đống cực tiểu có kích thước không vượt quá k theo hướng dẫn tại mục 8.3 của bài đọc.
