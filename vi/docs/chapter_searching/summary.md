# Tóm tắt

### Điểm mấu chốt cần nhớ

- Tìm kiếm nhị phân dựa trên tính có thứ tự của dữ liệu, thông qua vòng lặp từng bước thu hẹp một nửa khoảng tìm kiếm. Nó yêu cầu dữ liệu đầu vào phải được sắp xếp, và chỉ áp dụng cho mảng hoặc các cấu trúc dữ liệu xây dựng trên nền tảng mảng.
- Tìm kiếm vét cạn định vị dữ liệu bằng cách duyệt qua cấu trúc dữ liệu. Tìm kiếm tuyến tính áp dụng cho mảng và danh sách liên kết, tìm kiếm theo chiều rộng (BFS) và tìm kiếm theo chiều sâu (DFS) áp dụng cho đồ thị và cây. Nhóm thuật toán này có tính tổng quát cao, không cần tiền xử lý dữ liệu, nhưng độ phức tạp thời gian $O(n)$ tương đối cao.
- Tìm kiếm bằng bảng băm, tìm kiếm trên cây và tìm kiếm nhị phân thuộc về các phương pháp tìm kiếm hiệu năng cao, có thể nhanh chóng định vị phần tử mục tiêu trong các cấu trúc dữ liệu cụ thể. Nhóm thuật toán này có hiệu năng rất cao, độ phức tạp thời gian có thể đạt $O(\log n)$ thậm chí là $O(1)$ ，nhưng thường đòi hỏi phải nhờ đến cấu trúc dữ liệu phụ trợ.
- Trong thực tế, chúng ta cần phân tích cụ thể các yếu tố như quy mô dữ liệu, yêu cầu hiệu năng tìm kiếm, tần suất truy vấn và cập nhật dữ liệu để lựa chọn phương pháp tìm kiếm phù hợp.
- Tìm kiếm tuyến tính thích hợp cho dữ liệu nhỏ hoặc cập nhật thường xuyên; tìm kiếm nhị phân thích hợp cho dữ liệu lớn đã được sắp xếp; tìm kiếm bằng bảng băm thích hợp cho dữ liệu đòi hỏi hiệu năng truy vấn cao và không cần tìm kiếm theo khoảng; tìm kiếm trên cây thích hợp cho dữ liệu động quy mô lớn cần duy trì thứ tự và hỗ trợ tìm kiếm theo khoảng.
- Sử dụng tìm kiếm bằng bảng băm thay thế cho tìm kiếm tuyến tính là một chiến lược tối ưu hoá thời gian thực thi rất phổ biến, có thể giảm độ phức tạp thời gian từ $O(n)$ xuống $O(1)$ 。
