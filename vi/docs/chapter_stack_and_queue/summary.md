# Tóm tắt

### Điểm mấu chốt cần nhớ

- Ngăn xếp là một cấu trúc dữ liệu tuân theo nguyên lý vào sau ra trước (LIFO), có thể được hiện thực bằng mảng hoặc danh sách liên kết.
- Xét về hiệu năng thời gian, ngăn xếp hiện thực bằng mảng có hiệu năng trung bình cao hơn, nhưng trong quá trình mở rộng dung lượng, độ phức tạp thời gian của một lần đẩy vào (push) đơn lẻ sẽ suy giảm xuống $O(n)$ 。Trái lại, ngăn xếp hiện thực bằng danh sách liên kết đem lại hiệu năng ổn định hơn.
- Xét về hiệu năng không gian, ngăn xếp hiện thực bằng mảng có thể gây ra một mức độ lãng phí không gian nhất định. Tuy nhiên cần lưu ý rằng, nút danh sách liên kết chiếm nhiều không gian bộ nhớ hơn so với phần tử mảng.
- Hàng đợi là một cấu trúc dữ liệu tuân theo nguyên lý vào trước ra trước (FIFO), tương tự cũng có thể hiện thực bằng mảng hoặc danh sách liên kết. Kết luận so sánh về hiệu năng thời gian và không gian của hàng đợi cũng tương đồng với kết luận của ngăn xếp nêu trên.
- Hàng đợi hai đầu là một dạng hàng đợi có độ tự do cao hơn, cho phép thực hiện thao tác thêm và xoá phần tử ở cả hai đầu.

### Hỏi & Đáp (Q & A)

**Q**：Chức năng tiến tới (forward) và lùi lại (backward) của trình duyệt có phải được hiện thực bằng danh sách liên kết đôi không?

Chức năng tiến/lùi của trình duyệt về bản chất là sự thể hiện của "ngăn xếp". Khi người dùng truy cập một trang mới, trang đó sẽ được thêm vào đỉnh ngăn xếp; khi người dùng nhấp nút lùi lại, trang đó sẽ được lấy ra khỏi đỉnh ngăn xếp. Việc sử dụng hàng đợi hai đầu có thể giúp dễ dàng hiện thực một số thao tác bổ sung bên lề, như đã được đề cập trong phần "Hàng đợi hai đầu".

**Q**：Sau khi lấy ra khỏi ngăn xếp (pop), có cần giải phóng bộ nhớ của nút vừa lấy ra không?

Nếu sau đó vẫn cần sử dụng lại nút vừa lấy ra, thì không cần giải phóng bộ nhớ. Nếu sau đó không dùng tới nữa, các ngôn ngữ như Java và Python có cơ chế thu dọn rác tự động (garbage collection) nên không cần giải phóng bộ nhớ thủ công; trong khi đó trong C và C++ thì cần phải giải phóng bộ nhớ thủ công.

**Q**：Hàng đợi hai đầu trông giống như hai ngăn xếp ghép lại với nhau, vậy công dụng của nó là gì?

Hàng đợi hai đầu tựa như sự kết hợp giữa ngăn xếp và hàng đợi, hoặc như hai ngăn xếp ghép đầu đuôi lại với nhau. Nó thể hiện logic của ngăn xếp + hàng đợi, do đó có thể thực hiện mọi ứng dụng của cả ngăn xếp lẫn hàng đợi, đồng thời linh hoạt hơn.

**Q**：Chức năng hoàn tác (Undo) và làm lại (Redo) được hiện thực cụ thể như thế nào?

Sử dụng hai ngăn xếp, ngăn xếp `A` dùng cho việc hoàn tác (undo), ngăn xếp `B` dùng cho việc làm lại (redo):

1. Mỗi khi người dùng thực hiện một thao tác mới, đẩy thao tác đó vào ngăn xếp `A` và xoá rỗng ngăn xếp `B` 。
2. Khi người dùng thực hiện "Hoàn tác" (undo), lấy thao tác gần nhất ra khỏi ngăn xếp `A` và đẩy thao tác đó vào ngăn xếp `B` 。
3. Khi người dùng thực hiện "Làm lại" (redo), lấy thao tác gần nhất ra khỏi ngăn xếp `B` và đẩy thao tác đó vào ngăn xếp `A` 。
