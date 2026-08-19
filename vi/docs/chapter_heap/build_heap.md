# Thao tác thiết lập đống (Vun đống)

Trong một số tình huống, chúng ta mong muốn sử dụng toàn bộ các phần tử của một danh sách để xây dựng nên một đống, quá trình này được gọi là "thao tác thiết lập đống" (vun đống / build heap).

## Hiện thực nhờ thao tác thêm vào đống

Trước tiên chúng ta tạo một đống rỗng, sau đó duyệt qua danh sách, lần lượt thực hiện "thao tác thêm vào đống" cho từng phần tử, tức là trước tiên thêm phần tử vào cuối đống, rồi thực hiện "vun đống từ đáy lên đỉnh" (vun lên) cho phần tử đó.

Mỗi khi có một phần tử được thêm vào đống, độ dài của đống sẽ tăng thêm 1. Do các nút được lần lượt thêm vào cây nhị phân từ trên đỉnh xuống dưới đáy, nên đống được xây dựng theo kiểu "từ trên xuống dưới".

Giả sử số lượng phần tử là $n$ ，thao tác thêm vào đống của mỗi phần tử mất thời gian $O(\log{n})$ ，do đó phương pháp thiết lập đống này có độ phức tạp thời gian là $O(n \log n)$ 。

## Hiện thực thông qua duyệt và vun đống

Trên thực tế, chúng ta có thể hiện thực một phương pháp thiết lập đống hiệu quả hơn nhiều, bao gồm hai bước:

1. Đưa toàn bộ các phần tử của danh sách nguyên trạng vào đống, lúc này tính chất của đống vẫn chưa được thoả mãn.
2. Duyệt ngược đống (thứ tự ngược của duyệt theo tầng), lần lượt thực hiện "vun đống từ đỉnh xuống đáy" (vun xuống) cho từng nút không phải là nút lá.

**Mỗi khi vun đống xong một nút, cây con lấy nút đó làm nút gốc sẽ trở thành một đống con hợp lệ**. Và do duyệt theo thứ tự ngược, nên đống được xây dựng theo kiểu "từ dưới lên trên".

Lý do chọn duyệt ngược là vì cách này có thể đảm bảo các cây con bên dưới nút hiện tại đã là các đống con hợp lệ, nhờ đó việc vun đống nút hiện tại mới thực sự phát huy tác dụng.

Cần nói rõ rằng, **do các nút lá không có nút con nào nên bản thân chúng hiển nhiên đã là các đống con hợp lệ, không cần phải vun đống**. Như mã nguồn dưới đây, nút không phải là lá cuối cùng chính là nút cha của nút cuối cùng trong mảng, chúng ta bắt đầu duyệt ngược từ nó và tiến hành vun đống:

```src
[file]{my_heap}-[class]{max_heap}-[func]{__init__}
```

## Phân tích độ phức tạp

Dưới đây, chúng ta sẽ thử suy luận độ phức tạp thời gian của phương pháp thiết lập đống thứ hai này:

- Giả sử cây nhị phân hoàn chỉnh có $n$ nút, khi đó số lượng nút lá là $(n + 1) / 2$ ，trong đó $/$ là phép chia lấy phần nguyên làm tròn xuống. Vì vậy số lượng nút cần vun đống là $n / 2$ 。
- Trong quá trình vun đống từ đỉnh xuống đáy, mỗi nút tối đa chỉ chìm xuống đến nút lá, do đó số lần lặp tối đa là chiều cao của cây nhị phân $\log n$ 。

Nhân hai đại lượng trên với nhau, ta thu được độ phức tạp thời gian của quá trình thiết lập đống là $O(n \log n)$ 。**Nhưng kết quả ước tính này không hoàn toàn chính xác, bởi vì chúng ta chưa tính đến đặc tính số lượng nút ở tầng dưới của cây nhị phân nhiều hơn rất nhiều so với các tầng trên**.

Tiếp theo chúng ta sẽ tiến hành tính toán một cách chuẩn xác hơn. Để giảm độ khó tính toán, giả sử cho một "cây nhị phân hoàn hảo" có $n$ nút và chiều cao $h$ ，giả thiết này hoàn toàn không làm ảnh hưởng đến tính đúng đắn của kết quả tính toán.

![Số lượng nút ở từng tầng của cây nhị phân hoàn hảo](build_heap.assets/heapify_operations_count.png)

Như hình trên, số lần lặp tối đa của thao tác "vun đống từ đỉnh xuống đáy" của một nút bằng khoảng cách từ nút đó đến nút lá, mà khoảng cách này chính là "chiều cao của nút". Do đó, chúng ta có thể tính tổng của tích "số lượng nút $\times$ chiều cao của nút" ở từng tầng, **từ đó thu được tổng số lần lặp vun đống của toàn bộ các nút**:

$$
T(h) = 2^0h + 2^1(h-1) + 2^2(h-2) + \dots + 2^{(h-1)}\times1
$$

Rút gọn biểu thức trên cần nhờ đến kiến thức dãy số ở trường trung học, trước tiên nhân $T(h)$ với $2$ ，ta được:

$$
\begin{aligned}
T(h) & = 2^0h + 2^1(h-1) + 2^2(h-2) + \dots + 2^{h-1}\times1 \newline
2 T(h) & = 2^1h + 2^2(h-1) + 2^3(h-2) + \dots + 2^{h}\times1 \newline
\end{aligned}
$$

Sử dụng phương pháp trừ dồn hai vế (sai phân), lấy phương thức dưới $2 T(h)$ trừ đi phương thức trên $T(h)$ ，ta có:

$$
2T(h) - T(h) = T(h) = -2^0h + 2^1 + 2^2 + \dots + 2^{h-1} + 2^h
$$

Quan sát biểu thức trên, nhận thấy $T(h)$ là một cấp số nhân, có thể áp dụng trực tiếp công thức tính tổng cấp số nhân, thu được độ phức tạp thời gian là:

$$
\begin{aligned}
T(h) & = 2 \frac{1 - 2^h}{1 - 2} - h \newline
& = 2^{h+1} - h - 2 \newline
& = O(2^h)
\end{aligned}
$$

Hơn nữa, số lượng nút của cây nhị phân hoàn hảo có chiều cao $h$ là $n = 2^{h+1} - 1$ ，dễ dàng suy ra độ phức tạp là $O(2^h) = O(n)$ 。Các bước suy luận trên chứng minh rằng, **việc nhập danh sách và thiết lập đống có độ phức tạp thời gian là $O(n)$ ，vô cùng hiệu quả**.
