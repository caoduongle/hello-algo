# Tóm tắt

### Điểm mấu chốt cần nhớ

- Cây nhị phân là một cấu trúc dữ liệu phi tuyến tính, thể hiện logic chia để trị "một chia làm hai". Mỗi nút cây nhị phân bao gồm một giá trị và hai con trỏ, lần lượt trỏ tới nút con trái và nút con phải của nó.
- Đối với một nút nhất định trong cây nhị phân, cây tạo bởi nút con trái (phải) cùng các nút bên dưới nó được gọi là cây con trái (phải) của nút đó.
- Các thuật ngữ liên quan đến cây nhị phân bao gồm nút gốc, nút lá, tầng, bậc, cạnh, chiều cao và độ sâu, v.v.
- Các thao tác khởi tạo, chèn nút và xoá nút trong cây nhị phân có phương pháp thao tác tương tự như trên danh sách liên kết.
- Các loại cây nhị phân phổ biến bao gồm cây nhị phân hoàn hảo, cây nhị phân hoàn chỉnh, cây nhị phân đầy đủ và cây nhị phân cân bằng. Cây nhị phân hoàn hảo là trạng thái lý tưởng nhất, trong khi danh sách liên kết là trạng thái thoái hoá tồi tệ nhất.
- Cây nhị phân có thể biểu diễn bằng mảng bằng cách sắp xếp các giá trị nút và các vị trí ô trống theo thứ tự duyệt theo tầng, đồng thời hiện thực hoá con trỏ dựa trên mối quan hệ ánh xạ chỉ số giữa nút cha và các nút con.
- Duyệt cây nhị phân theo tầng là một phương pháp tìm kiếm theo chiều rộng (BFS), thể hiện cách thức duyệt từng tầng một theo hình thức "mở rộng từng vòng từ trong ra ngoài", thường được hiện thực thông qua hàng đợi.
- Duyệt tiền thứ tự, trung thứ tự và hậu thứ tự đều thuộc về tìm kiếm theo chiều sâu (DFS), thể hiện cách thức duyệt "đi đến tận cùng rồi mới quay lui tiếp tục", thường được hiện thực bằng đệ quy.
- Cây tìm kiếm nhị phân là một cấu trúc dữ liệu tìm kiếm phần tử hiệu năng cao, các thao tác tìm kiếm, chèn và xoá của nó đều có độ phức tạp thời gian là $O(\log n)$. Khi cây tìm kiếm nhị phân thoái hoá thành danh sách liên kết, độ phức tạp thời gian của các thao tác sẽ suy giảm về $O(n)$.
- Cây AVL, còn gọi là cây tìm kiếm nhị phân cân bằng, thông qua các thao tác quay cây để đảm bảo cây vẫn duy trì trạng thái cân bằng sau khi liên tục chèn và xoá các nút.
- Các thao tác quay cây AVL bao gồm quay phải, quay trái, quay phải-trái và quay trái-phải. Sau khi chèn hoặc xoá nút, cây AVL sẽ thực hiện các thao tác quay từ đáy lên đỉnh để đưa cây trở lại trạng thái cân bằng.

### Hỏi & Đáp (Q & A)

**Q**: Đối với một cây nhị phân chỉ có duy nhất một nút, chiều cao của cây và độ sâu của nút gốc đều bằng $0$ đúng không?

Đúng vậy, bởi vì chiều cao và độ sâu thường được định nghĩa là "số lượng cạnh đi qua".

**Q**: Trong cây nhị phân, việc chèn và xoá thường được hoàn thành bởi một chuỗi thao tác phối hợp, "chuỗi thao tác" ở đây chỉ điều gì? Có thể hiểu là giải phóng tài nguyên của các nút con không?

Lấy cây tìm kiếm nhị phân làm ví dụ, thao tác xoá nút phải chia thành 3 trường hợp để xử lý, trong đó mỗi trường hợp đều cần thực hiện nhiều bước thao tác nút liên hoàn.

**Q**: Tại sao duyệt DFS trên cây nhị phân lại có ba thứ tự: tiền, trung, hậu, và chúng có tác dụng gì?

Tương tự như việc duyệt mảng theo chiều xuôi và chiều ngược, duyệt tiền thứ tự, trung thứ tự và hậu thứ tự là ba phương pháp duyệt cây nhị phân giúp chúng ta thu được kết quả duyệt theo một thứ tự đặc thù nhất định. Ví dụ trong cây tìm kiếm nhị phân, do độ lớn các nút thoả mãn `giá trị nút con trái < giá trị nút gốc < giá trị nút con phải`, nên chúng ta chỉ cần duyệt cây theo thứ tự ưu tiên "trái $\rightarrow$ gốc $\rightarrow$ phải" là có thể thu được một dãy nút đã sắp xếp theo thứ tự tăng dần.

**Q**: Thao tác quay phải xử lý mối quan hệ giữa các nút mất cân bằng `node`, `child`, `grand_child`, vậy liên kết ban đầu giữa nút cha của `node` và `node` có cần bảo trì không? Sau khi quay phải chẳng phải liên kết đó sẽ bị đứt sao?

Chúng ta cần nhìn nhận vấn đề này từ góc nhìn đệ quy. Thao tác quay phải `right_rotate(root)` nhận vào nút gốc của cây con, và cuối cùng `return child` sẽ trả về nút gốc mới của cây con sau khi quay. Việc kết nối giữa nút gốc của cây con và nút cha của nó được hoàn tất sau khi hàm này trả về, không thuộc phạm vi xử lý bên trong của hàm quay phải.

**Q**: Trong C++, các hàm được phân chia vào các khối `private` và `public`, điều này có sự cân nhắc gì? Tại sao lại đặt hàm `height()` và hàm `updateHeight()` lần lượt vào `public` và `private`?

Chủ yếu dựa vào phạm vi sử dụng của phương thức: nếu phương thức chỉ dùng bên trong nội bộ lớp thì được thiết kế là `private`. Ví dụ, người dùng gọi riêng lẻ hàm `updateHeight()` là vô nghĩa, nó chỉ là một bước phụ trợ bên trong thao tác chèn hoặc xoá. Còn `height()` là để truy cập chiều cao của nút, tương tự như `vector.size()`, do đó được thiết lập là `public` để thuận tiện sử dụng từ bên ngoài.

**Q**: Làm thế nào để xây dựng một cây tìm kiếm nhị phân từ một tập dữ liệu đầu vào? Việc lựa chọn nút gốc có quan trọng không?

Đúng vậy, phương pháp xây dựng cây đã được cung cấp trong phương thức `build_tree()` của mã nguồn cây tìm kiếm nhị phân. Về việc lựa chọn nút gốc, chúng ta thường sắp xếp dữ liệu đầu vào trước, sau đó lấy phần tử ở điểm giữa làm nút gốc, rồi đệ quy xây dựng cây con trái và cây con phải. Cách làm này có thể tối đa hoá việc đảm bảo tính cân bằng của cây.

**Q**: Trong Java, việc so sánh chuỗi có nhất thiết phải dùng phương thức `equals()` không?

Trong Java, đối với các kiểu dữ liệu cơ bản, `==` dùng để so sánh giá trị của hai biến có bằng nhau không. Đối với kiểu tham chiếu (reference type), nguyên lý hoạt động của hai ký hiệu này là khác nhau:

- `==`: Dùng để so sánh hai biến có cùng trỏ tới một đối tượng hay không, tức là vị trí của chúng trong bộ nhớ có giống nhau không.
- `equals()`: Dùng để so sánh giá trị nội dung của hai đối tượng có bằng nhau không.

Do đó, nếu muốn so sánh giá trị, chúng ta nên dùng `equals()`. Tuy nhiên, các chuỗi khởi tạo thông qua `String a = "hi"; String b = "hi";` đều được lưu trữ trong hồ hằng số chuỗi (string constant pool), chúng cùng trỏ tới một đối tượng duy nhất, do đó cũng có thể dùng `a == b` để so sánh nội dung hai chuỗi này.

**Q**: Trước khi duyệt theo chiều rộng đến tầng đáy cùng, số lượng nút trong hàng đợi có phải là $2^h$ không?

Đúng vậy, ví dụ một cây nhị phân hoàn hảo có chiều cao $h = 2$ thì tổng số nút là $n = 7$, khi đó số nút ở tầng đáy cùng là $4 = 2^h = (n + 1) / 2$.
