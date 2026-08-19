# Tóm tắt

### Điểm mấu chốt cần nhớ

- Quy hoạch động thực hiện phân rã bài toán, và thông qua việc lưu trữ lời giải của các bài toán con để tránh tính toán trùng lặp, nâng cao hiệu năng tính toán.
- Nếu không xét đến yếu tố thời gian, tất cả các bài toán quy hoạch động đều có thể giải bằng quay lui (tìm kiếm vét cạn), nhưng cây đệ quy tồn tại lượng lớn bài toán con gối nhau dẫn đến hiệu năng cực kỳ thấp. Bằng việc đưa vào danh sách ghi nhớ, chúng ta có thể lưu lại toàn bộ lời giải bài toán con đã tính, đảm bảo mỗi bài toán con gối nhau chỉ được tính đúng một lần.
- Tìm kiếm có nhớ là cách giải đệ quy từ đỉnh xuống đáy, trong khi quy hoạch động tương ứng là cách giải suy diễn lặp từ đáy lên đỉnh, giống như việc "điền vào bảng". Do trạng thái hiện tại chỉ phụ thuộc vào một số trạng thái cục bộ, chúng ta có thể triệt tiêu một chiều của bảng $dp$ ，từ đó giảm độ phức tạp không gian.
- Phân rã bài toán con là một tư tưởng thuật toán mang tính tổng quát, có các đặc tính khác nhau trong chia để trị, quy hoạch động và quay lui.
- Bài toán quy hoạch động có ba đặc trưng lớn: bài toán con gối nhau, cấu trúc con tối ưu, và tính không nhớ (không hệ luỵ).
- Nếu lời giải tối ưu của bài toán ban đầu có thể kiến tạo từ lời giải tối ưu của các bài toán con thì bài toán đó sở hữu cấu trúc con tối ưu.
- Tính không nhớ chỉ việc đối với một trạng thái xác định, sự phát triển trong tương lai của nó chỉ liên quan tới trạng thái đó, mà không liên quan tới toàn bộ các trạng thái đã trải qua trong quá khứ. Nhiều bài toán tối ưu hoá tổ hợp không có tính không nhớ nên không thể dùng quy hoạch động để giải nhanh được.

**Bài toán cái túi**

- Bài toán cái túi là một trong những bài toán quy hoạch động điển hình nhất, có các biến thể như cái túi 0-1, cái túi hoàn toàn, cái túi nhiều lựa chọn, v.v.
- Định nghĩa trạng thái của cái túi 0-1 là giá trị lớn nhất của $i$ đồ vật đầu tiên trong túi có dung tích là $c$ 。Dựa trên hai quyết định không cho vào túi và cho vào túi, có thể tìm ra cấu trúc con tối ưu và xây dựng phương trình chuyển trạng thái. Trong tối ưu hoá không gian, do mỗi trạng thái phụ thuộc vào trạng thái ngay phía trên và phía trên bên trái, vì vậy cần duyệt ngược danh sách để tránh việc trạng thái phía trên bên trái bị ghi đè.
- Bài toán cái túi hoàn toàn không giới hạn số lượng chọn của mỗi loại đồ vật, vì vậy việc chuyển trạng thái khi chọn cho đồ vật vào túi sẽ khác với bài toán cái túi 0-1. Do trạng thái phụ thuộc vào trạng thái ngay phía trên và bên trái, vì vậy trong tối ưu hoá không gian nên duyệt xuôi.
- Bài toán đổi tiền xu là một biến thể của bài toán cái túi hoàn toàn. Nó chuyển từ tìm giá trị "lớn nhất" sang tìm số lượng đồng xu "ít nhất", do đó hàm $\max()$ trong phương trình chuyển trạng thái được đổi thành $\min()$ 。Từ việc hướng tới "không vượt quá" dung tích túi sang hướng tới ghép "chính xác" số tiền mục tiêu, vì vậy sử dụng $amt + 1$ để biểu thị lời giải không hợp lệ "không thể đổi được số tiền mục tiêu".
- Bài toán đổi tiền xu II chuyển từ tìm "số lượng đồng xu ít nhất" sang tìm "số lượng tổ hợp đồng xu", phương trình chuyển trạng thái tương ứng đổi từ $\min()$ sang toán tử tính tổng.

**Bài toán khoảng cách chỉnh sửa**

- Khoảng cách chỉnh sửa (Levenshtein distance) dùng để đo lường độ tương đồng giữa hai chuỗi ký tự, được định nghĩa là số bước chỉnh sửa ít nhất để chuyển từ chuỗi này sang chuỗi kia, các thao tác chỉnh sửa gồm chèn, xoá, thay thế.
- Định nghĩa trạng thái của bài toán khoảng cách chỉnh sửa là số bước chỉnh sửa ít nhất cần thiết để chuyển $i$ ký tự đầu tiên của $s$ thành $j$ ký tự đầu tiên của $t$ 。Khi $s[i-1] \ne t[j-1]$ ，có ba quyết định: chèn, xoá, thay thế, mỗi quyết định đều có bài toán con còn lại tương ứng. Dựa vào đó có thể tìm ra cấu trúc con tối ưu và xây dựng phương trình chuyển trạng thái. Khi $s[i-1] = t[j-1]$ ，không cần chỉnh sửa ký tự hiện tại.
- Trong khoảng cách chỉnh sửa, trạng thái phụ thuộc vào trạng thái ngay phía trên, bên trái và phía trên bên trái của nó, do đó sau khi tối ưu hoá không gian thì cả duyệt xuôi lẫn duyệt ngược đều không thể thực hiện chuyển trạng thái chính xác nếu chỉ dùng mảng đơn thuần. Vì vậy, chúng ta dùng một biến để lưu tạm thời trạng thái phía trên bên trái, từ đó chuyển về tình huống tương đương bài toán cái túi hoàn toàn, có thể thực hiện duyệt xuôi sau khi tối ưu không gian.
