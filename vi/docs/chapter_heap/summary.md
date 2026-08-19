# Tóm tắt

### Điểm mấu chốt cần nhớ

- Đống là một cây nhị phân hoàn chỉnh, tuỳ theo điều kiện thiết lập mà được chia thành đống cực đại và đống cực tiểu. Phần tử đỉnh đống của đống cực đại (cực tiểu) luôn là lớn nhất (nhỏ nhất).
- Hàng đợi ưu tiên được định nghĩa là một hàng đợi có sắp xếp theo thứ tự ưu tiên khi lấy ra, thông thường được hiện thực bằng đống.
- Các thao tác thường dùng trên đống cùng độ phức tạp thời gian tương ứng bao gồm: thêm phần tử vào đống $O(\log n)$, lấy phần tử đỉnh đống ra khỏi đống $O(\log n)$, và truy cập phần tử đỉnh đống $O(1)$.
- Cây nhị phân hoàn chỉnh rất thích hợp để biểu diễn bằng mảng, do đó chúng ta thường sử dụng mảng để lưu trữ đống.
- Thao tác vun đống (heapify) được dùng để duy trì tính chất của đống, xuất hiện trong cả thao tác thêm vào đống và lấy ra khỏi đống.
- Thao tác nhập $n$ phần tử và thiết lập đống (build heap) có thể tối ưu hoá độ phức tạp thời gian xuống còn $O(n)$, vô cùng hiệu quả.
- Top-k là một bài toán thuật toán kinh điển, có thể giải quyết hiệu quả bằng cấu trúc dữ liệu đống với độ phức tạp thời gian là $O(n \log k)$.

### Hỏi & Đáp (Q & A)

**Q**: "Đống" (heap) trong cấu trúc dữ liệu và "vùng nhớ heap" trong quản lý bộ nhớ có phải là cùng một khái niệm không?

Cả hai không phải là cùng một khái niệm, chỉ là tình cờ có cùng tên gọi là "đống" (heap). Vùng nhớ heap trong bộ nhớ máy tính là một phần của quá trình cấp phát bộ nhớ động (dynamic memory allocation), chương trình trong thời gian chạy có thể sử dụng nó để lưu trữ dữ liệu. Chương trình có thể yêu cầu một dung lượng bộ nhớ heap nhất định để lưu trữ các cấu trúc phức tạp như đối tượng và mảng. Khi những dữ liệu này không còn cần thiết nữa, chương trình cần phải giải phóng vùng bộ nhớ đó để ngăn ngừa hiện tượng rò rỉ bộ nhớ (memory leak). So với vùng nhớ stack (ngăn xếp), việc quản lý và sử dụng vùng nhớ heap đòi hỏi phải cẩn trọng hơn, nếu sử dụng không đúng cách có thể dẫn đến rò rỉ bộ nhớ và con trỏ lơ lửng (dangling/wild pointer).
