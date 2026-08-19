# Tóm tắt

### Điểm mấu chốt cần nhớ

- Đồ thị được cấu thành từ các đỉnh và các cạnh, có thể biểu diễn bằng tập hợp các đỉnh và tập hợp các cạnh.
- So với mối quan hệ tuyến tính (danh sách liên kết) và mối quan hệ chia để trị (cây), mối quan hệ mạng lưới (đồ thị) có độ tự do cao hơn nhiều, do đó cũng phức tạp hơn.
- Cạnh của đồ thị có hướng mang tính định hướng, trong đồ thị liên thông mọi đỉnh đều có thể đi tới được, mỗi cạnh của đồ thị có trọng số đều chứa một biến trọng số.
- Ma trận kề sử dụng ma trận để biểu diễn đồ thị, mỗi hàng (cột) đại diện cho một đỉnh, phần tử ma trận đại diện cho cạnh, dùng $1$ hoặc $0$ để biểu thị giữa hai đỉnh có cạnh nối hay không. Ma trận kề có hiệu năng rất cao trong các thao tác thêm, xoá, sửa, tra cứu, nhưng chiếm dụng nhiều không gian bộ nhớ.
- Danh sách kề sử dụng nhiều danh sách liên kết để biểu diễn đồ thị, danh sách liên kết thứ $i$ tương ứng với đỉnh $i$, lưu trữ toàn bộ các đỉnh kề của đỉnh đó. Danh sách kề tiết kiệm không gian bộ nhớ hơn so với ma trận kề, nhưng do phải duyệt danh sách liên kết để tìm cạnh nên hiệu năng thời gian thấp hơn.
- Khi danh sách liên kết trong danh sách kề quá dài, có thể chuyển đổi thành cây đỏ-đen hoặc bảng băm để nâng cao hiệu năng tra cứu.
- Xét từ góc độ tư tưởng thuật toán, ma trận kề thể hiện nguyên lý "đổi không gian lấy thời gian", danh sách kề thể hiện nguyên lý "đổi thời gian lấy không gian".
- Đồ thị có thể dùng để mô hình hoá nhiều hệ thống trong thế giới thực, như mạng xã hội, mạng lưới tàu điện ngầm, v.v.
- Cây là một trường hợp đặc biệt của đồ thị, việc duyệt cây cũng là một trường hợp đặc biệt của việc duyệt đồ thị.
- Duyệt đồ thị theo chiều rộng (BFS) là phương thức tìm kiếm từ gần đến xa, mở rộng từng lớp ra ngoài, thường được hiện thực bằng hàng đợi.
- Duyệt đồ thị theo chiều sâu (DFS) là phương thức tìm kiếm ưu tiên đi tới tận cùng, khi không còn đường đi nữa mới quay lui, thường được hiện thực bằng đệ quy.

### Hỏi & Đáp (Q & A)

**Q**: Định nghĩa đường đi là một chuỗi các đỉnh hay một chuỗi các cạnh?

Định nghĩa trên Wikipedia ở các phiên bản ngôn ngữ khác nhau có sự không nhất quán: bản tiếng Anh định nghĩa "đường đi là một chuỗi các cạnh", trong khi bản tiếng Trung định nghĩa "đường đi là một chuỗi các đỉnh". Dưới đây là nguyên văn bản tiếng Anh: In graph theory, a path in a graph is a finite or infinite sequence of edges which joins a sequence of vertices.

Trong cuốn sách này, đường đi được coi là một chuỗi các cạnh chứ không phải là chuỗi các đỉnh. Lý do là vì giữa hai đỉnh có thể tồn tại nhiều cạnh song song nối liền, khi đó mỗi cạnh sẽ tương ứng với một đường đi khác nhau.

**Q**: Trong đồ thị không liên thông có tồn tại các đỉnh không thể duyệt tới không?

Trong đồ thị không liên thông, xuất phát từ một đỉnh nào đó, sẽ có ít nhất một đỉnh không thể đi tới được. Việc duyệt toàn bộ đồ thị không liên thông đòi hỏi phải thiết lập nhiều điểm xuất phát khác nhau nhằm duyệt qua toàn bộ các thành phần liên thông của đồ thị.

**Q**: Trong danh sách kề, thứ tự của "toàn bộ các đỉnh kề với đỉnh đó" có yêu cầu gì không?

Có thể theo bất kỳ thứ tự nào. Nhưng trong ứng dụng thực tế, có thể cần phải sắp xếp theo quy tắc chỉ định, ví dụ theo thứ tự các đỉnh được thêm vào, hoặc theo thứ tự độ lớn của giá trị đỉnh, điều này giúp ích cho việc tìm kiếm nhanh đỉnh "mang giá trị cực trị nào đó".
