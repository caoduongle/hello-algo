# Tóm tắt

### Điểm mấu chốt cần nhớ

- Thuật toán tham lam thường dùng để giải quyết các bài toán tối ưu hoá, nguyên lý của nó là đưa ra quyết định tối ưu cục bộ ở mỗi giai đoạn ra quyết định, với kỳ vọng thu được lời giải tối ưu toàn cục.
- Thuật toán tham lam sẽ suy diễn lặp đưa ra hết lựa chọn tham lam này đến lựa chọn tham lam khác, mỗi vòng đều chuyển bài toán thành một bài toán con có quy mô nhỏ hơn, cho đến khi bài toán được giải quyết hoàn toàn.
- Thuật toán tham lam không chỉ hiện thực đơn giản mà còn có hiệu năng giải bài rất cao. So với quy hoạch động, độ phức tạp thời gian của thuật toán tham lam thông thường thấp hơn nhiều.
- Trong bài toán đổi tiền xu, đối với một số bộ mệnh giá tiền xu nhất định, thuật toán tham lam có thể đảm bảo tìm ra lời giải tối ưu; nhưng đối với một số bộ tiền xu khác thì không, thuật toán tham lam có thể tìm ra một lời giải rất tệ.
- Bài toán thích hợp giải bằng thuật toán tham lam sở hữu hai tính chất lớn: tính chất lựa chọn tham lam và cấu trúc con tối ưu. Tính chất lựa chọn tham lam đại diện cho tính hiệu quả của chiến lược tham lam.
- Đối với một số bài toán phức tạp, việc chứng minh tính chất lựa chọn tham lam không hề đơn giản. Tương đối mà nói, việc bác bỏ (chứng minh sai bằng phản ví dụ) dễ dàng hơn nhiều, chẳng hạn như bài toán đổi tiền xu.
- Giải bài toán tham lam chủ yếu chia làm ba bước: phân tích bài toán, xác định chiến lược tham lam, và chứng minh tính đúng đắn. Trong đó, xác định chiến lược tham lam là bước cốt lõi, còn chứng minh tính đúng đắn thường là điểm khó nhất.
- Bài toán cái túi phân số trên nền tảng của cái túi 0-1 cho phép chọn một phần của đồ vật, vì vậy có thể dùng thuật toán tham lam để giải. Tính đúng đắn của chiến lược tham lam có thể dùng phương pháp phản chứng để chứng minh.
- Bài toán dung lượng cực đại có thể dùng phương pháp vét cạn để giải với độ phức tạp thời gian là $O(n^2)$. Bằng cách thiết kế chiến lược tham lam dịch chuyển vách ngắn vào trong ở mỗi vòng, có thể tối ưu hoá độ phức tạp thời gian về $O(n)$.
- Trong bài toán cắt đoạn tích cực đại, chúng ta lần lượt suy ra hai chiến lược tham lam: các số nguyên $\geq 4$ đều nên tiếp tục chia nhỏ, và thừa số chia tối ưu nhất là $3$. Mã nguồn có chứa phép tính luỹ thừa, độ phức tạp thời gian phụ thuộc vào cách hiện thực phép luỹ thừa, thông thường là $O(1)$ hoặc $O(\log n)$.
