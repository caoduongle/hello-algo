# Tóm tắt

### Điểm mấu chốt cần nhớ

- Thuật toán quay lui về bản chất là phương pháp vét cạn, thông qua việc duyệt theo chiều sâu không gian lời giải để tìm kiếm các lời giải thoả mãn điều kiện. Trong quá trình tìm kiếm, khi gặp lời giải thoả mãn điều kiện thì ghi nhận lại, cho đến khi tìm thấy tất cả các lời giải hoặc duyệt xong toàn bộ thì kết thúc.
- Quá trình tìm kiếm của thuật toán quay lui bao gồm hai phần: thử và quay lui. Nó thông qua tìm kiếm theo chiều sâu để thử các lựa chọn khác nhau; khi gặp tình huống không thoả mãn điều kiện ràng buộc thì huỷ bỏ lựa chọn ở bước trước, lùi về trạng thái cũ và tiếp tục thử các lựa chọn khác. Thử và quay lui là hai thao tác có hướng ngược nhau.
- Các bài toán quay lui thường chứa nhiều điều kiện ràng buộc, chúng có thể được tận dụng để thực hiện thao tác cắt tỉa. Cắt tỉa có thể kết thúc sớm các nhánh tìm kiếm không cần thiết, giúp nâng cao vượt bậc hiệu năng tìm kiếm.
- Thuật toán quay lui chủ yếu dùng để giải quyết các bài toán tìm kiếm và bài toán thoả mãn ràng buộc. Các bài toán tối ưu hoá tổ hợp mặc dù có thể giải bằng thuật toán quay lui, nhưng thường tồn tại những cách giải có hiệu năng cao hơn hoặc hiệu quả tốt hơn.
- Bài toán hoán vị nhằm mục đích tìm kiếm tất cả các hoán vị khả dĩ của các phần tử trong tập hợp cho trước. Chúng ta nhờ một mảng để ghi lại xem mỗi phần tử đã được chọn hay chưa, cắt tỉa các nhánh tìm kiếm chọn lặp lại cùng một phần tử, đảm bảo mỗi phần tử chỉ được chọn đúng một lần.
- Trong bài toán hoán vị, nếu tập hợp tồn tại các phần tử trùng lặp thì kết quả cuối cùng sẽ xuất hiện các hoán vị trùng lặp. Chúng ta cần ràng buộc các phần tử có giá trị bằng nhau chỉ được phép chọn đúng một lần trong mỗi vòng, điều này thường được hiện thực nhờ một tập hợp băm (HashSet).
- Mục tiêu của bài toán tổng tập con là tìm tất cả các tập con trong tập hợp cho trước có tổng bằng giá trị mục tiêu. Tập hợp không phân biệt thứ tự phần tử, trong khi quá trình tìm kiếm lại xuất ra kết quả theo mọi thứ tự dẫn đến việc sinh ra các tập con trùng lặp. Chúng ta sắp xếp dữ liệu trước khi quay lui, và thiết lập một biến để chỉ định điểm bắt đầu duyệt của mỗi vòng, từ đó cắt tỉa các nhánh tìm kiếm sinh ra tập con trùng lặp.
- Đối với bài toán tổng tập con, các phần tử bằng nhau trong mảng sẽ sinh ra các tập hợp trùng lặp. Chúng ta tận dụng điều kiện tiên quyết mảng đã sắp xếp để kiểm tra xem hai phần tử liền kề có bằng nhau không để thực hiện cắt tỉa, từ đó đảm bảo các phần tử bằng nhau chỉ được chọn đúng một lần trong mỗi vòng.
- Bài toán $n$ quân hậu nhằm tìm kiếm các phương án đặt $n$ quân hậu trên bàn cờ kích thước $n \times n$ sao cho hai quân hậu bất kỳ đều không thể tấn công lẫn nhau. Điều kiện ràng buộc của bài toán gồm ràng buộc hàng, ràng buộc cột, ràng buộc đường chéo chính và đường chéo phụ. Để thoả mãn ràng buộc hàng, chúng ta áp dụng chiến lược đặt theo từng hàng, đảm bảo mỗi hàng chỉ đặt đúng một quân hậu.
- Cách xử lý ràng buộc cột và ràng buộc đường chéo tương tự nhau. Đối với ràng buộc cột, chúng ta dùng một mảng để ghi lại mỗi cột đã có quân hậu hay chưa, từ đó xác định ô cờ được chọn có hợp lệ không. Đối với ràng buộc đường chéo, chúng ta nhờ hai mảng để lần lượt ghi lại xem trên đường chéo chính và đường chéo phụ đó đã có quân hậu hay chưa; điểm mấu chốt là tìm ra quy luật chỉ số hàng - cột mà các ô cờ nằm trên cùng một đường chéo chính (phụ) thoả mãn.

### Hỏi & Đáp (Q & A)

**Q**: Hiểu mối quan hệ giữa quay lui và đệ quy như thế nào?

Tổng thể mà nói, quay lui là một "chiến lược thuật toán", trong khi đệ quy giống như một "công cụ" hơn:

- Thuật toán quay lui thường được hiện thực dựa trên đệ quy. Tuy nhiên, quay lui chỉ là một trong các tình huống ứng dụng của đệ quy, là sự vận dụng của đệ quy trong các bài toán tìm kiếm.
- Cấu trúc của đệ quy thể hiện mô thức giải bài toán "phân rã bài toán con", thường được dùng để giải quyết các bài toán chia để trị, quay lui, quy hoạch động (đệ quy có nhớ - memoized recursion), v.v.
