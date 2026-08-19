# Sắp xếp cơ số (Radix Sort)

Phần trước đã giới thiệu sắp xếp đếm, nó thích hợp cho tình huống lượng dữ liệu $n$ lớn nhưng phạm vi dữ liệu $m$ nhỏ. Giả sử chúng ta cần sắp xếp $n = 10^6$ mã số sinh viên, mà mỗi mã số là một chuỗi gồm $8$ chữ số, điều này đồng nghĩa với việc phạm vi dữ liệu $m = 10^8$ là rất lớn, việc sử dụng sắp xếp đếm sẽ đòi hỏi phải cấp phát một dung lượng bộ nhớ khổng lồ, trong khi sắp xếp cơ số có thể tránh được tình huống này.

Tư tưởng cốt lõi của <u>sắp xếp cơ số (radix sort)</u> hoàn toàn thống nhất với sắp xếp đếm, cũng thực hiện sắp xếp thông qua việc đếm số lượng. Trên cơ sở đó, sắp xếp cơ số tận dụng mối quan hệ luỹ tiến giữa các chữ số ở các hàng của con số, lần lượt sắp xếp theo từng hàng chữ số một, từ đó thu được kết quả sắp xếp cuối cùng.

## Quy trình thuật toán

Lấy dữ liệu mã số sinh viên làm ví dụ, giả sử chữ số ở hàng thấp nhất là hàng thứ $1$ ，và hàng cao nhất là hàng thứ $8$ ，quy trình của sắp xếp cơ số được thể hiện như hình dưới đây:

1. Khởi tạo thứ tự hàng chữ số $k = 1$ 。
2. Thực hiện "sắp xếp đếm" trên hàng thứ $k$ của mã số sinh viên. Sau khi hoàn tất, dữ liệu sẽ được sắp xếp theo thứ tự từ nhỏ đến lớn dựa trên chữ số ở hàng thứ $k$ 。
3. Tăng $k$ thêm $1$ ，sau đó quay lại bước `2.` tiếp tục lặp, cho đến khi tất cả các hàng chữ số đều được sắp xếp xong thì kết thúc.

![Quy trình thuật toán sắp xếp cơ số](radix_sort.assets/radix_sort_overview.png)

Dưới đây phân tích mã nguồn hiện thực. Đối với một con số $x$ trong hệ cơ số $d$ ，để lấy chữ số ở hàng thứ $k$ ký hiệu là $x_k$ ，chúng ta có thể sử dụng công thức tính toán sau:

$$
x_k = \lfloor\frac{x}{d^{k-1}}\rfloor \bmod d
$$

Trong đó $\lfloor a \rfloor$ biểu thị phép toán lấy phần nguyên làm tròn xuống của số thực $a$ ，còn $\bmod \: d$ biểu thị phép chia lấy phần dư cho $d$ 。Đối với dữ liệu mã số sinh viên, $d = 10$ và $k \in [1, 8]$ 。

Ngoài ra, chúng ta cần sửa đổi đôi chút mã nguồn sắp xếp đếm để nó có thể sắp xếp dựa trên chữ số ở hàng thứ $k$ của các con số:

```src
[file]{radix_sort}-[class]{}-[func]{radix_sort}
```

!!! question "Tại sao lại bắt đầu sắp xếp từ hàng chữ số thấp nhất?"

    Trong các vòng sắp xếp liên tiếp nhau, vòng sắp xếp sau sẽ ghi đè lên kết quả của vòng sắp xếp trước. Lấy ví dụ, nếu kết quả sắp xếp ở vòng thứ nhất là $a < b$ ，nhưng kết quả sắp xếp ở vòng thứ hai là $a > b$ ，thì kết quả của vòng thứ hai sẽ thay thế kết quả của vòng thứ nhất. Do hàng chữ số cao có mức độ ưu tiên lớn hơn hàng chữ số thấp, vì vậy bắt buộc phải sắp xếp hàng thấp trước rồi mới sắp xếp hàng cao sau.

## Đặc tính của thuật toán

So với sắp xếp đếm, sắp xếp cơ số thích hợp cho tình huống phạm vi giá trị lớn hơn, **nhưng với điều kiện tiên quyết là dữ liệu bắt buộc phải biểu diễn được dưới định dạng có số lượng chữ số cố định, và số lượng chữ số không được quá lớn**. Ví dụ, số thực dấu phẩy động không thích hợp để dùng sắp xếp cơ số, vì số lượng chữ số $k$ của nó quá lớn, có thể dẫn đến độ phức tạp thời gian $O(nk) \gg O(n^2)$ 。

- **Độ phức tạp thời gian là $O(nk)$、Sắp xếp không thích ứng**: Giả sử lượng dữ liệu là $n$ ，dữ liệu ở hệ cơ số $d$ ，số lượng chữ số tối đa là $k$ ，khi đó thực hiện sắp xếp đếm trên một hàng chữ số mất thời gian $O(n + d)$ ，sắp xếp toàn bộ $k$ hàng chữ số mất thời gian $O((n + d)k)$ 。Thông thường, $d$ và $k$ đều tương đối nhỏ, độ phức tạp thời gian tiệm cận $O(n)$ 。
- **Độ phức tạp không gian là $O(n + d)$、Sắp xếp không tại chỗ**: Tương tự như sắp xếp đếm, sắp xếp cơ số cần nhờ các mảng `res` và `counter` có độ dài lần lượt là $n$ và $d$ 。
- **Sắp xếp ổn định**: Khi thuật toán sắp xếp đếm bên trong ổn định thì sắp xếp cơ số cũng ổn định; nếu sắp xếp đếm không ổn định thì sắp xếp cơ số không thể đảm bảo thu được kết quả sắp xếp chính xác.
