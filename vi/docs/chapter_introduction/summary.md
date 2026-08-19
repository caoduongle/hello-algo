# Tóm tắt

### Điểm mấu chốt cần nhớ

- Thuật toán hiện diện ở khắp mọi nơi trong đời sống hàng ngày, không phải là mảng kiến thức cao siêu xa vời. Trên thực tế, chúng ta đã tiếp thu rất nhiều thuật toán trong vô thức để giải quyết các vấn đề lớn nhỏ trong cuộc sống.
- Nguyên lý tra từ điển hoàn toàn tương đồng với thuật toán tìm kiếm nhị phân. Thuật toán tìm kiếm nhị phân thể hiện tư tưởng thuật toán quan trọng: chia để trị.
- Quy trình xếp bài tây rất giống với thuật toán sắp xếp chèn. Thuật toán sắp xếp chèn rất thích hợp để sắp xếp các tập dữ liệu nhỏ.
- Các bước trả tiền thừa về bản chất là thuật toán tham lam, tại mỗi bước đều đưa ra lựa chọn có vẻ là tốt nhất ở thời điểm hiện tại.
- Thuật toán là một tập hợp các chỉ thị hoặc các bước thao tác nhằm giải quyết một vấn đề cụ thể trong khoảng thời gian hữu hạn, còn cấu trúc dữ liệu là phương thức tổ chức và lưu trữ dữ liệu trong máy tính.
- Cấu trúc dữ liệu và thuật toán gắn kết chặt chẽ với nhau. Cấu trúc dữ liệu là nền tảng của thuật toán, còn thuật toán thổi hồn vào cấu trúc dữ liệu.
- Chúng ta có thể so sánh cấu trúc dữ liệu và thuật toán với việc lắp ráp các khối đồ chơi: các khối đại diện cho dữ liệu, hình dạng và cách ghép nối các khối đại diện cho cấu trúc dữ liệu, còn các bước lắp ráp tương ứng với thuật toán.

### Hỏi & Đáp (Q & A)

**Q**：Là một lập trình viên, trong công việc hàng ngày tôi chưa từng phải tự tay dùng thuật toán để giải quyết vấn đề, các thuật toán thông dụng đều đã được ngôn ngữ lập trình đóng gói sẵn và chỉ việc gọi ra dùng; liệu điều này có đồng nghĩa với việc các bài toán trong công việc của chúng ta chưa phức tạp đến mức cần đến thuật toán?

Nếu ví các kỹ năng làm việc cụ thể như những “chiêu thức” võ công, thì các môn học nền tảng lại giống như phần “nội công”.

Tôi cho rằng ý nghĩa của việc học thuật toán (cũng như các môn học nền tảng khác) không nằm ở chỗ bạn phải tự tay hiện thực hoá lại chúng từ đầu trong công việc, mà là dựa trên nền tảng kiến thức đã học để có thể đưa ra những phản xạ và phán đoán mang tính chuyên môn khi giải quyết vấn đề, từ đó nâng cao chất lượng tổng thể của công việc. Lấy một ví dụ đơn giản, mỗi ngôn ngữ lập trình đều có sẵn hàm sắp xếp tích hợp:

- Nếu chúng ta chưa từng học cấu trúc dữ liệu và giải thuật, khi gặp bất kỳ tập dữ liệu nào, chúng ta cũng có thể ném toàn bộ cho hàm sắp xếp này xử lý. Mã chạy trơn tru, hiệu năng ổn định, thoạt nhìn không có vấn đề gì cả.
- Nhưng nếu đã học thuật toán, chúng ta sẽ biết rằng độ phức tạp thời gian của hàm sắp xếp tích hợp sẵn là $O(n \log n)$ ；trong khi nếu dữ liệu đầu vào là các số nguyên có số chữ số cố định (chẳng hạn như mã số sinh viên), chúng ta có thể áp dụng thuật toán “sắp xếp cơ số” (radix sort) với hiệu năng vượt trội hơn hẳn, đưa độ phức tạp thời gian xuống còn $O(nk)$ ，trong đó $k$ là số chữ số. Khi quy mô dữ liệu đủ lớn, lượng thời gian thực thi tiết kiệm được sẽ tạo ra giá trị rất lớn (giảm chi phí tài nguyên, cải thiện trải nghiệm người dùng, v.v.).

Trong lĩnh vực kỹ thuật công nghệ, một lượng lớn các bài toán rất khó để đạt tới lời giải tối ưu tuyệt đối, và nhiều vấn đề chỉ đang được giải quyết ở mức “tạm ổn”. Mức độ khó dễ của một bài toán một mặt phụ thuộc vào bản chất của chính vấn đề đó, mặt khác lại phụ thuộc vào vốn tri thức của người nhìn nhận vấn đề. Tri thức của một người càng hoàn thiện, kinh nghiệm càng phong phú thì phân tích vấn đề sẽ càng sâu sắc, và bài toán sẽ được giải quyết một cách thanh thoát, tao nhã hơn.
