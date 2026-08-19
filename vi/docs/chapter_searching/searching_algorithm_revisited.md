# Nhìn lại các thuật toán tìm kiếm

<u>Thuật toán tìm kiếm (searching algorithm)</u> được sử dụng để tìm kiếm một hoặc một nhóm phần tử thoả mãn điều kiện cụ thể trong các cấu trúc dữ liệu (chẳng hạn như mảng, danh sách liên kết, cây hoặc đồ thị).

Thuật toán tìm kiếm có thể chia thành hai nhóm chính dựa trên tư tưởng hiện thực:

- **Định vị phần tử mục tiêu bằng cách duyệt qua cấu trúc dữ liệu**, ví dụ như duyệt mảng, danh sách liên kết, cây và đồ thị.
- **Tận dụng cấu trúc tổ chức dữ liệu hoặc thông tin tiên nghiệm (tiền đề) của dữ liệu để tra cứu phần tử hiệu năng cao**, ví dụ như tìm kiếm nhị phân, tìm kiếm bằng bảng băm và tìm kiếm trên cây tìm kiếm nhị phân.

Không khó để nhận thấy rằng những khối kiến thức này đều đã được giới thiệu trong các chương trước, do đó thuật toán tìm kiếm không hề xa lạ với chúng ta. Trong phần này, chúng ta sẽ tiếp cận từ góc nhìn hệ thống hơn để nhìn nhận lại các thuật toán tìm kiếm.

## Tìm kiếm vét cạn

Tìm kiếm vét cạn (Brute-force search) định vị phần tử mục tiêu bằng cách duyệt qua từng phần tử của cấu trúc dữ liệu:

- "Tìm kiếm tuyến tính" áp dụng cho các cấu trúc dữ liệu tuyến tính như mảng và danh sách liên kết. Nó bắt đầu từ một đầu của cấu trúc dữ liệu, truy cập từng phần tử một cho đến khi tìm thấy phần tử mục tiêu hoặc đi đến đầu kia mà vẫn không tìm thấy.
- "Tìm kiếm theo chiều rộng" (BFS) và "tìm kiếm theo chiều sâu" (DFS) là hai chiến lược duyệt trên đồ thị và cây. Tìm kiếm theo chiều rộng bắt đầu từ nút ban đầu và tìm kiếm theo từng tầng, truy cập các nút từ gần đến xa. Tìm kiếm theo chiều sâu bắt đầu từ nút ban đầu, đi men theo một đường đi tới tận cùng, rồi quay lui và thử các đường đi khác cho đến khi duyệt xong toàn bộ cấu trúc dữ liệu.

Ưu điểm của tìm kiếm vét cạn là đơn giản và có tính tổng quát cao, **hoàn toàn không cần tiền xử lý dữ liệu hay phải dựa vào các cấu trúc dữ liệu phụ trợ**.

Tuy nhiên, **độ phức tạp thời gian của nhóm thuật toán này là $O(n)$**, trong đó $n$ là số lượng phần tử, do đó hiệu năng khá kém khi xử lý khối lượng dữ liệu lớn.

## Tìm kiếm thích ứng

Tìm kiếm thích ứng (Adaptive search) tận dụng các đặc tính riêng của dữ liệu (chẳng hạn như tính có thứ tự) để tối ưu hoá tiến trình tìm kiếm, từ đó định vị phần tử mục tiêu hiệu quả hơn:

- "Tìm kiếm nhị phân" tận dụng tính có thứ tự của dữ liệu để tra cứu hiệu năng cao, chỉ áp dụng cho mảng.
- "Tìm kiếm bằng bảng băm" sử dụng bảng băm để thiết lập ánh xạ khoá-giá trị (key-value) giữa dữ liệu tìm kiếm và dữ liệu mục tiêu, từ đó thực hiện thao tác truy vấn.
- "Tìm kiếm trên cây" hoạt động trên các cấu trúc cây đặc thù (như cây tìm kiếm nhị phân), dựa vào việc so sánh giá trị nút để nhanh chóng loại trừ các nhánh, từ đó định vị phần tử mục tiêu.

Ưu điểm của nhóm thuật toán này là hiệu năng rất cao, **độ phức tạp thời gian có thể đạt tới $O(\log n)$ thậm chí là $O(1)$**.

Tuy nhiên, **việc sử dụng các thuật toán này thường đòi hỏi phải tiền xử lý dữ liệu**. Ví dụ, tìm kiếm nhị phân cần phải sắp xếp mảng trước, trong khi tìm kiếm bằng bảng băm và tìm kiếm trên cây đều cần phải nhờ đến cấu trúc dữ liệu phụ trợ, việc duy trì các cấu trúc dữ liệu này cũng phát sinh thêm chi phí thời gian và không gian.

!!! tip

    Các thuật toán tìm kiếm thích ứng thường được gọi là thuật toán tra cứu (lookup algorithm), **chủ yếu dùng để nhanh chóng truy xuất phần tử mục tiêu trong các cấu trúc dữ liệu cụ thể**.

## Lựa chọn phương pháp tìm kiếm

Cho một tập dữ liệu có kích thước $n$, chúng ta có thể sử dụng nhiều phương pháp khác nhau như tìm kiếm tuyến tính, tìm kiếm nhị phân, tìm kiếm trên cây, tìm kiếm bằng bảng băm để tìm kiếm phần tử mục tiêu. Nguyên lý hoạt động của từng phương pháp được minh hoạ như hình dưới đây:

![Nhiều chiến lược tìm kiếm khác nhau](searching_algorithm_revisited.assets/searching_algorithms.png)

Hiệu năng thao tác và đặc tính của các phương pháp trên được tổng hợp trong bảng dưới đây:

<p align="center"> Bảng <id> &nbsp; So sánh hiệu năng các thuật toán tìm kiếm </p>

|              | Tìm kiếm tuyến tính | Tìm kiếm nhị phân | Tìm kiếm trên cây | Tìm kiếm bằng bảng băm |
| ------------ | -------- | ------------------ | ------------------ | --------------- |
| Tìm kiếm phần tử | $O(n)$   | $O(\log n)$        | $O(\log n)$        | $O(1)$          |
| Chèn phần tử   | $O(1)$   | $O(n)$             | $O(\log n)$        | $O(1)$          |
| Xoá phần tử   | $O(n)$   | $O(n)$             | $O(\log n)$        | $O(1)$          |
| Không gian phụ trợ | $O(1)$   | $O(1)$             | $O(n)$             | $O(n)$          |
| Tiền xử lý dữ liệu | Không cần | Sắp xếp $O(n \log n)$ | Dựng cây $O(n \log n)$ | Dựng bảng băm $O(n)$ |
| Dữ liệu có thứ tự | Không có thứ tự | Có thứ tự | Có thứ tự | Không có thứ tự |

Việc lựa chọn thuật toán tìm kiếm còn phụ thuộc vào quy mô dữ liệu, yêu cầu hiệu năng tìm kiếm, tần suất truy vấn và cập nhật dữ liệu, v.v.

**Tìm kiếm tuyến tính**

- Tính tổng quát cao, không cần bất kỳ thao tác tiền xử lý dữ liệu nào. Giả sử chúng ta chỉ cần tra cứu dữ liệu một lần duy nhất, thì thời gian tiền xử lý dữ liệu của ba phương pháp còn lại còn lâu hơn cả thời gian tìm kiếm tuyến tính.
- Thích hợp cho dữ liệu có dung lượng nhỏ, trong trường hợp này độ phức tạp thời gian ảnh hưởng rất ít tới hiệu năng thực tế.
- Thích hợp cho các tình huống tần suất cập nhật dữ liệu cao, vì phương pháp này không đòi hỏi bất kỳ sự bảo trì phụ trợ nào trên dữ liệu.

**Tìm kiếm nhị phân**

- Thích hợp cho lượng dữ liệu lớn, hiệu năng thể hiện ổn định, độ phức tạp thời gian trong trường hợp xấu nhất là $O(\log n)$.
- Lượng dữ liệu không thể quá lớn, vì việc lưu trữ mảng đòi hỏi không gian bộ nhớ liên tục.
- Không thích hợp cho các tình huống thêm và xoá dữ liệu với tần suất cao, vì chi phí duy trì mảng có thứ tự là rất lớn.

**Tìm kiếm bằng bảng băm**

- Thích hợp cho các tình huống đòi hỏi hiệu năng truy vấn cực cao, độ phức tạp thời gian trung bình là $O(1)$.
- Không thích hợp cho các tình huống cần dữ liệu có thứ tự hoặc tìm kiếm theo khoảng giá trị (range search), vì bảng băm không duy trì tính có thứ tự của dữ liệu.
- Phụ thuộc nhiều vào hàm băm và chiến lược xử lý xung đột băm, tiềm ẩn rủi ro suy giảm hiệu năng.
- Không thích hợp cho lượng dữ liệu quá lớn, vì bảng băm cần không gian phụ trợ để giảm thiểu xung đột nhằm cung cấp hiệu năng truy vấn tốt nhất.

**Tìm kiếm trên cây**

- Thích hợp cho lượng dữ liệu khổng lồ, vì các nút cây được lưu trữ phân tán trong bộ nhớ.
- Thích hợp cho các tình huống cần duy trì dữ liệu có thứ tự hoặc tìm kiếm theo khoảng giá trị.
- Trong quá trình liên tục thêm và xoá các nút, cây tìm kiếm nhị phân có thể bị lệch (thoái hoá), độ phức tạp thời gian suy giảm về $O(n)$.
- Nếu sử dụng cây AVL hoặc cây đỏ-đen, các thao tác có thể vận hành ổn định ở hiệu năng $O(\log n)$, nhưng các thao tác duy trì cân bằng cây sẽ phát sinh thêm chi phí.
