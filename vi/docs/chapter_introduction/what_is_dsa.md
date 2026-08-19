# Thuật toán là gì

## Định nghĩa thuật toán

<u>Thuật toán (algorithm)</u> là một tập hợp các chỉ thị hoặc các bước thao tác nhằm giải quyết một vấn đề cụ thể trong một khoảng thời gian hữu hạn. Thuật toán sở hữu các đặc trưng sau:

- Vấn đề cần giải quyết được xác định rõ ràng, có định nghĩa rõ ràng về đầu vào và đầu ra.
- Có tính khả thi, có thể hoàn thành trong số bước, khoảng thời gian và dung lượng bộ nhớ hữu hạn.
- Mỗi bước thực hiện đều có ý nghĩa xác định; với cùng một đầu vào và điều kiện thực thi như nhau, đầu ra luôn luôn không đổi.

## Định nghĩa cấu trúc dữ liệu

<u>Cấu trúc dữ liệu (data structure)</u> là phương thức tổ chức và lưu trữ dữ liệu, bao gồm nội dung dữ liệu, mối quan hệ giữa các phần tử dữ liệu và các phương thức thao tác trên dữ liệu. Cấu trúc dữ liệu hướng tới các mục tiêu thiết kế sau:

- Chiếm dụng càng ít không gian càng tốt nhằm tiết kiệm bộ nhớ máy tính.
- Thao tác dữ liệu càng nhanh càng tốt, bao gồm các thao tác truy cập, thêm mới, xoá, cập nhật dữ liệu, v.v.
- Cung cấp cách biểu diễn dữ liệu và thông tin logic súc tích, giúp thuật toán thực thi hiệu quả.

**Thiết kế cấu trúc dữ liệu là một quá trình ngập tràn sự đánh đổi**. Nếu muốn cải thiện một khía cạnh nào đó, chúng ta thường phải chấp nhận nhượng bộ ở một khía cạnh khác. Dưới đây là hai ví dụ điển hình:

- Danh sách liên kết so với mảng thì thuận tiện hơn nhiều trong các thao tác thêm và xoá dữ liệu, nhưng lại phải hy sinh tốc độ truy cập dữ liệu.
- Đồ thị so với danh sách liên kết thì cung cấp thông tin logic phong phú hơn nhiều, nhưng đòi hỏi phải chiếm dụng dung lượng bộ nhớ lớn hơn.

## Mối quan hệ giữa cấu trúc dữ liệu và thuật toán

Như minh hoạ trong hình dưới đây, cấu trúc dữ liệu và thuật toán có mối liên hệ mật thiết và gắn kết chặt chẽ với nhau, thể hiện cụ thể ở ba khía cạnh sau:

- Cấu trúc dữ liệu là nền tảng của thuật toán. Cấu trúc dữ liệu cung cấp cho thuật toán dữ liệu được lưu trữ có cấu trúc cũng như các phương thức để thao tác trên dữ liệu đó.
- Thuật toán thổi hồn vào cấu trúc dữ liệu. Bản thân cấu trúc dữ liệu chỉ thuần tuý lưu trữ thông tin dữ liệu; chỉ khi kết hợp với thuật toán thì mới có thể giải quyết được các vấn đề cụ thể.
- Thuật toán thường có thể được hiện thực dựa trên các cấu trúc dữ liệu khác nhau, nhưng hiệu năng thực thi có thể chênh lệch rất lớn; lựa chọn cấu trúc dữ liệu phù hợp chính là chìa khoá quyết định.

![Mối quan hệ giữa cấu trúc dữ liệu và thuật toán](what_is_dsa.assets/relationship_between_data_structure_and_algorithm.png)

Cấu trúc dữ liệu và thuật toán tựa như việc lắp ráp các khối đồ chơi (building blocks) như hình dưới đây. Một bộ đồ chơi lắp ráp, bên cạnh việc chứa nhiều mảnh ghép rời rạc, còn đi kèm một bản hướng dẫn lắp ráp chi tiết. Chúng ta làm theo từng bước trong bản hướng dẫn là có thể ráp thành một mô hình đồ chơi tinh xảo.

![Lắp ráp các khối đồ chơi](what_is_dsa.assets/assembling_blocks.png)

Mối quan hệ đối ứng chi tiết giữa cả hai được thể hiện trong bảng dưới đây.

<p align="center"> Bảng <id> &nbsp; Phép so sánh giữa cấu trúc dữ liệu và thuật toán với việc lắp ráp các khối đồ chơi </p>

| Cấu trúc dữ liệu và thuật toán | Lắp ráp khối đồ chơi |
| ------------------------------ | -------------------- |
| Dữ liệu đầu vào                | Các khối đồ chơi chưa lắp ghép |
| Cấu trúc dữ liệu               | Hình thức tổ chức các khối đồ chơi, bao gồm hình dạng, kích thước, cách ghép nối, v.v. |
| Thuật toán                     | Chuỗi các bước thao tác để lắp ghép các khối thành mô hình mục tiêu |
| Dữ liệu đầu ra                 | Mô hình đồ chơi hoàn chỉnh |

Một điều đáng lưu ý là cấu trúc dữ liệu và giải thuật hoàn toàn độc lập với ngôn ngữ lập trình. Chính vì vậy, cuốn sách này có thể cung cấp mã nguồn hiện thực dựa trên rất nhiều ngôn ngữ lập trình khác nhau.

!!! tip "Cách gọi tắt quen thuộc"

    Trong các cuộc thảo luận thực tế, chúng ta thường gọi tắt “cấu trúc dữ liệu và giải thuật” là “thuật toán”. Chẳng hạn như các bài toán thuật toán trên LeetCode ai cũng biết, trên thực tế đều kiểm tra đồng thời kiến thức của cả hai mảng cấu trúc dữ liệu và thuật toán.
