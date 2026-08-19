# Tóm tắt

### Điểm mấu chốt cần nhớ

**Đánh giá hiệu năng thuật toán**

- Hiệu năng thời gian và hiệu năng không gian là hai tiêu chí đánh giá chủ yếu để đo lường mức độ ưu việt của thuật toán.
- Chúng ta có thể thông qua kiểm thử thực tế để đánh giá hiệu năng thuật toán, nhưng rất khó loại bỏ ảnh hưởng từ môi trường kiểm thử và tiêu tốn nhiều tài nguyên tính toán.
- Phân tích độ phức tạp có thể khắc phục các nhược điểm của kiểm thử thực tế; kết quả phân tích có thể áp dụng cho mọi nền tảng thực thi và có thể hé lộ hiệu năng của thuật toán dưới các quy mô dữ liệu khác nhau.

**Độ phức tạp thời gian**

- Độ phức tạp thời gian dùng để đo lường xu hướng tăng trưởng của thời gian thực thi theo lượng dữ liệu, có thể đánh giá hiệu năng thuật toán một cách hiệu quả; tuy nhiên trong một số trường hợp có thể mất tác dụng, ví dụ khi lượng dữ liệu đầu vào nhỏ hoặc khi độ phức tạp thời gian tương đương nhau, không thể so sánh chính xác mức độ hơn kém của các thuật toán.
- Độ phức tạp thời gian trường hợp xấu nhất sử dụng ký hiệu Big-$O$ ，tương ứng với cận trên tiệm cận của hàm số, phản ánh cấp bậc tăng trưởng của số lượng thao tác $T(n)$ khi $n$ tiến dần về dương vô cùng.
- Quy trình suy diễn độ phức tạp thời gian gồm hai bước: đầu tiên là thống kê số lượng thao tác, sau đó xác định cận trên tiệm cận.
- Các độ phức tạp thời gian thường gặp xếp từ thấp đến cao gồm có $O(1)$、$O(\log n)$、$O(n)$、$O(n \log n)$、$O(n^2)$、$O(2^n)$ và $O(n!)$ ，v.v.
- Độ phức tạp thời gian của một số thuật toán không cố định mà phụ thuộc vào sự phân bố của dữ liệu đầu vào. Độ phức tạp thời gian chia thành trường hợp xấu nhất, tốt nhất và trung bình; độ phức tạp thời gian trường hợp tốt nhất hầu như không được sử dụng vì dữ liệu đầu vào thường phải thoả mãn những điều kiện vô cùng khắt khe mới đạt được trường hợp này.
- Độ phức tạp thời gian trường hợp trung bình phản ánh hiệu năng vận hành của thuật toán dưới dữ liệu đầu vào ngẫu nhiên, sát nhất với hiệu năng thực tế của thuật toán trong ứng dụng đời thực. Việc tính toán độ phức tạp thời gian trung bình đòi hỏi phải thống kê phân bố dữ liệu đầu vào và tính kỳ vọng toán học tổng hợp.

**Độ phức tạp không gian**

- Tác dụng của độ phức tạp không gian tương tự như độ phức tạp thời gian, dùng để đo lường xu hướng tăng trưởng của không gian bộ nhớ mà thuật toán chiếm dụng theo quy mô dữ liệu.
- Không gian bộ nhớ liên quan trong quá trình chạy thuật toán có thể chia thành không gian đầu vào, không gian tạm thời và không gian đầu ra. Thông thường, không gian đầu vào không tính vào độ phức tạp không gian. Không gian tạm thời có thể chia thành dữ liệu tạm thời, khung ngăn xếp và không gian chỉ lệnh; trong đó khung ngăn xếp thường chỉ ảnh hưởng tới độ phức tạp không gian trong các hàm đệ quy.
- Chúng ta thường chỉ quan tâm đến độ phức tạp không gian trường hợp xấu nhất, tức là thống kê độ phức tạp không gian của thuật toán dưới dữ liệu đầu vào xấu nhất và ở thời điểm thực thi chiếm nhiều bộ nhớ nhất.
- Các độ phức tạp không gian thường gặp xếp từ thấp đến cao gồm có $O(1)$、$O(\log n)$、$O(n)$、$O(n^2)$ và $O(2^n)$ ，v.v.

### Hỏi & Đáp (Q & A)

**Q**：Độ phức tạp không gian của đệ quy đuôi có phải là $O(1)$ không?

Về mặt lý thuyết, độ phức tạp không gian của hàm đệ quy đuôi có thể được tối ưu về mức $O(1)$ 。Tuy nhiên tuyệt đại đa số các ngôn ngữ lập trình (như Java, Python, C++, Go, C#, v.v.) không hỗ trợ tự động tối ưu hoá đệ quy đuôi, do đó thông thường vẫn coi độ phức tạp không gian là $O(n)$ 。

**Q**：Sự khác biệt giữa hai thuật ngữ hàm (function) và phương thức (method) là gì?

<u>Hàm (function)</u> có thể được thực thi độc lập, tất cả các tham số đều được truyền vào một cách tường minh. <u>Phương thức (method)</u> gắn liền với một đối tượng, được truyền ngầm định cho đối tượng gọi nó và có thể thao tác trên dữ liệu chứa trong các thực thể (instance) của lớp.

Dưới đây lấy một vài ngôn ngữ lập trình phổ biến làm ví dụ minh hoạ:

- Ngôn ngữ C là ngôn ngữ lập trình thủ tục, không có khái niệm hướng đối tượng nên chỉ có hàm. Tuy nhiên chúng ta có thể mô phỏng lập trình hướng đối tượng bằng cách tạo cấu trúc (struct), và các hàm liên kết với struct tương đương với phương thức trong các ngôn ngữ lập trình khác.
- Java và C# là các ngôn ngữ lập trình hướng đối tượng, các khối mã (phương thức) thường đóng vai trò là một phần của một lớp nào đó. Phương thức tĩnh (static method) hoạt động tương tự như một hàm vì nó được liên kết với lớp chứ không thể truy cập các biến thực thể cụ thể.
- C++ và Python hỗ trợ đồng thời cả lập trình thủ tục (hàm) lẫn lập trình hướng đối tượng (phương thức).

**Q**：Hình minh hoạ "Các dạng độ phức tạp không gian thường gặp" có phản ánh kích thước tuyệt đối của không gian bị chiếm dụng không?

Không, hình minh hoạ đó thể hiện độ phức tạp không gian, phản ánh xu hướng tăng trưởng chứ không phải dung lượng tuyệt đối của không gian bộ nhớ bị chiếm dụng.

Giả sử lấy $n = 8$ ，bạn có thể nhận thấy giá trị của mỗi đường cong không khớp hoàn toàn với hàm số tương ứng. Điều này là do mỗi đường cong đều được cộng thêm một hằng số nhằm nén dải giá trị vào một khoảng nhìn trực quan và dễ chịu hơn.

Trong thực tế, do chúng ta thường không biết "hằng số" chi phí của mỗi phương pháp là bao nhiêu, nên thông thường không thể chỉ dựa vào độ phức tạp để chọn lời giải tối ưu cho trường hợp $n = 8$ 。Nhưng đối với $n = 8^5$ thì việc lựa chọn lại rất rõ ràng, vì khi đó xu hướng tăng trưởng đã chiếm vị thế chi phối tuyệt đối.

**Q**：Liệu có tồn tại trường hợp thiết kế thuật toán chấp nhận hy sinh thời gian (hoặc không gian) dựa trên ngữ cảnh sử dụng thực tế không?

Trong ứng dụng thực tế, phần lớn trường hợp người ta sẽ chọn hy sinh không gian để đổi lấy thời gian. Ví dụ như trong chỉ mục cơ sở dữ liệu (database index), chúng ta thường chọn xây dựng cây B+ hoặc chỉ mục băm (hash index), chiếm dụng lượng lớn không gian bộ nhớ để đổi lấy tốc độ truy vấn cực nhanh $O(\log n)$ hay thậm chí $O(1)$ 。

Trong các ngữ cảnh tài nguyên không gian bộ nhớ vô cùng đắt đỏ, người ta cũng sẽ chọn hy sinh thời gian để đổi lấy không gian. Chẳng hạn trong lập trình nhúng, bộ nhớ thiết bị rất hạn hẹp, các kỹ sư có thể từ bỏ bảng băm và chọn duyệt tuần tự trên mảng để tiết kiệm bộ nhớ, chấp nhận cái giá là tốc độ tìm kiếm bị chậm đi.
