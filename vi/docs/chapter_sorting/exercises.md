# Bài tập

## Củng cố kiến thức

### Các vòng đầu tiên của sắp xếp chọn và sắp xếp nổi bọt

Cho mảng `[4, 2, 5, 1, 3]`, các câu hỏi dưới đây đều sắp xếp theo thứ tự từ nhỏ đến lớn.

<!-- numbered-subquestions -->

1. Mô phỏng hai vòng đầu tiên của sắp xếp chọn, viết mảng sau mỗi vòng và chỉ ra những vị trí nào đã được xác định cố định tại thời điểm này.
2. Mô phỏng vòng đầu tiên của sắp xếp nổi bọt, viết trạng thái mảng và số lần hoán đổi, đồng thời chỉ ra vị trí nào đã được xác định cố định.

??? success "Đáp án tham khảo"

    1. Hai vòng đầu tiên là:

        | Vòng | Trạng thái mảng | Giải thích |
        | --- | --- | --- |
        | 1 | `[1, 2, 5, 4, 3]` | Phần tử nhỏ nhất 1 hoán đổi với phần tử đầu tiên |
        | 2 | `[1, 2, 5, 4, 3]` | Giá trị 2 đã nằm tại chỉ số 1, không cần hoán đổi |

        Lúc này hai vị trí đầu tiên đã được xác định cố định, các vòng tiếp theo chỉ cần tiếp tục chọn phần tử nhỏ nhất trong `[5, 4, 3]`.

    2. Lần lượt so sánh các phần tử liền kề: 4 hoán đổi với 2, 4 không hoán đổi với 5, 5 hoán đổi với 1, 5 hoán đổi với 3,
        thu được `[2, 4, 1, 3, 5]`, tổng cộng 3 lần hoán đổi; phần tử lớn nhất 5 đã được đưa về cuối mảng, do đó vị trí cuối cùng đã được xác định cố định.

### Thứ tự trước sau của các phần tử bằng nhau có bị thay đổi không?

Trong mảng $[2_a, 2_b, 1]$, $2_a$ và $2_b$ có giá trị bằng nhau, nhưng dùng chỉ số dưới để đánh dấu thứ tự ban đầu.

<!-- numbered-subquestions -->

1. Viết mảng sau khi kết thúc vòng 1 của sắp xếp chọn. Thứ tự tương đối của $2_a$ và $2_b$ có bị thay đổi không?
2. Viết mảng sau khi kết thúc vòng 1 của sắp xếp nổi bọt. Thứ tự tương đối của $2_a$ và $2_b$ có bị thay đổi không?
3. Dựa theo hai câu hỏi trước, hãy giải thích sự khác biệt giữa hai thuật toán sắp xếp trong việc duy trì thứ tự ban đầu của các phần tử bằng nhau.

??? success "Đáp án tham khảo"

    1. Vòng 1 của sắp xếp chọn tìm ra phần tử nhỏ nhất 1 và hoán đổi với phần tử đầu tiên $2_a$, thu được
        $[1, 2_b, 2_a]$. $2_a$ đã bị chuyển ra sau $2_b$, thứ tự tương đối giữa chúng đã bị thay đổi.

    2. Sắp xếp nổi bọt trước tiên so sánh $2_a$ và $2_b$, vì hai phần tử bằng nhau nên không hoán đổi; sau đó so sánh $2_b$ và 1 rồi hoán đổi,
        sau khi kết thúc vòng 1 mảng là $[2_a, 1, 2_b]$. $2_a$ vẫn đứng trước $2_b$, thứ tự tương đối không bị thay đổi.

    3. Trong ví dụ này, sắp xếp chọn làm thay đổi thứ tự ban đầu của các phần tử bằng nhau; sắp xếp nổi bọt chỉ hoán đổi hai phần tử liền kề khi
        phần tử bên trái lớn hơn phần tử bên phải. Các phần tử bằng nhau không bị hoán đổi, do đó duy trì được thứ tự trước sau ban đầu của chúng.

### So sánh sắp xếp đếm và sắp xếp cơ số

Nhà trường cần sắp xếp rất nhiều mã số sinh viên cố định 8 chữ số. Hãy trả lời các câu hỏi:

<!-- numbered-subquestions -->

1. Sắp xếp cơ số bắt đầu từ hàng chữ số thấp nhất cần xử lý bao nhiêu vòng?
2. Nếu coi trực tiếp mã số sinh viên là số nguyên để dùng sắp xếp đếm, tại sao lại phải chuẩn bị một lượng lớn vị trí đếm không hề được sử dụng?
3. Dựa theo hai câu hỏi trước, nếu phải chọn một trong hai giữa sắp xếp đếm và sắp xếp cơ số để xử lý lượng lớn mã số sinh viên cố định 8 chữ số, bạn sẽ chọn thuật toán nào? Tại sao?

??? success "Đáp án tham khảo"

    1. Mã số sinh viên có 8 chữ số, do đó từ hàng thấp nhất đến hàng cao nhất cần xử lý tổng cộng 8 vòng; mỗi vòng chỉ phân nhóm theo các chữ số từ 0~ 9.

    2. Việc đếm trực tiếp đòi hỏi phải dành sẵn vị trí cho toàn bộ các giá trị 8 chữ số có thể xảy ra ($10^8$), nhưng sinh viên thực tế chỉ sử dụng một phần rất nhỏ trong số đó,
        phần lớn các vị trí đếm sẽ luôn mang giá trị 0.

    3. Nên chọn sắp xếp cơ số. Nó tận dụng đặc điểm "số lượng chữ số cố định, mỗi chữ số chỉ có 10 giá trị từ 0 đến 9", chỉ cần lặp lại 8 vòng phân nhóm ổn định.
        Sắp xếp đếm nếu dùng toàn bộ mã số sinh viên 8 chữ số làm chỉ số mảng thì sẽ phải dự trù vị trí đếm cho lượng lớn các giá trị trên thực tế không hề xuất hiện.

## Bài tập lập trình

### Sắp xếp mảng bằng sắp xếp trộn

Cho mảng số nguyên `nums`, hãy tự mình hiện thực sắp xếp trộn để sắp xếp các phần tử trong mảng theo thứ tự không giảm và trả về mảng kết quả. Không gọi hàm sắp xếp tích hợp sẵn của ngôn ngữ.

??? tip "Gợi ý giải bài"

    1. Khoảng có độ dài không vượt quá 1 vốn đã có thứ tự sẵn
    2. Chia đôi khoảng tại điểm giữa, và lần lượt gọi đệ quy sắp xếp cả hai nửa
    3. Sử dụng hai con trỏ để trộn hai nửa đã sắp xếp, sau đó ghi kết quả ngược lại mảng ban đầu

[LeetCode](https://leetcode.com/problems/sort-an-array/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }

### Sắp xếp mảng số nguyên bằng sắp xếp đếm

Cho mảng số nguyên `nums` và số nguyên không âm $K$, mỗi phần tử trong mảng đều nằm trong khoảng từ $0$ đến $K$.

Hãy hiện thực sắp xếp đếm, ghi kết quả theo thứ tự không giảm vào lại `nums` và trả về `nums`.
Không sử dụng phép so sánh độ lớn giữa các phần tử để xác định thứ tự, và không gọi hàm sắp xếp tích hợp sẵn của ngôn ngữ.

??? tip "Gợi ý giải bài"

    1. Vì mỗi phần tử đều nằm trong khoảng từ 0 đến K, có thể trực tiếp dùng giá trị phần tử làm chỉ số cho mảng đếm
    2. Quét qua nums lần thứ nhất, tăng giá trị đếm tại vị trí tương ứng lên 1
    3. Sau đó quét mảng đếm từ 0 đến K; giá trị x xuất hiện bao nhiêu lần thì liên tiếp ghi bấy nhiêu giá trị x vào nums
