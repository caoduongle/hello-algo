# Đụng độ băm

Ở phần trước đã đề cập, **thông thường không gian đầu vào của hàm băm lớn hơn rất nhiều so với không gian đầu ra**, vì vậy về mặt lý thuyết đụng độ băm là điều không thể tránh khỏi. Ví dụ: không gian đầu vào là toàn thể các số nguyên, không gian đầu ra là kích thước sức chứa của mảng, thì chắc chắn sẽ có nhiều số nguyên cùng ánh xạ vào một chỉ số ngăn duy nhất.

Đụng độ băm sẽ dẫn đến kết quả tra cứu bị sai lệch, ảnh hưởng nghiêm trọng đến tính khả dụng của bảng băm. Để giải quyết vấn đề này, mỗi khi gặp đụng độ băm, chúng ta có thể mở rộng dung lượng bảng băm cho đến khi đụng độ biến mất. Cách tiếp cận này tuy đơn giản, trực tiếp và hiệu quả nhưng hiệu năng quá thấp, vì việc mở rộng bảng băm đòi hỏi phải di chuyển lượng lớn dữ liệu và tính toán lại toàn bộ giá trị băm. Để nâng cao hiệu năng, chúng ta có thể áp dụng các chiến lược sau:

1. Cải tiến cấu trúc dữ liệu của bảng băm, **giúp bảng băm vẫn có thể vận hành bình thường ngay cả khi xuất hiện đụng độ băm**.
2. Chỉ thực hiện thao tác mở rộng dung lượng khi thực sự cần thiết, tức là khi đụng độ băm diễn ra tương đối nghiêm trọng.

Các phương pháp cải tiến cấu trúc bảng băm chủ yếu bao gồm "nối chuỗi" (separate chaining) và "địa chỉ mở" (open addressing).

## Nối chuỗi (Separate Chaining)

Trong bảng băm nguyên bản, mỗi ngăn chỉ có thể lưu trữ một cặp khoá - giá trị. <u>Nối chuỗi (separate chaining)</u> chuyển đổi từng phần tử đơn lẻ thành một danh sách liên kết, coi mỗi cặp khoá - giá trị là một nút trong danh sách liên kết, và gom toàn bộ các cặp khoá - giá trị xảy ra đụng độ vào lưu trữ trong cùng một danh sách liên kết. Hình dưới đây minh hoạ một ví dụ về bảng băm nối chuỗi.

![Bảng băm nối chuỗi](hash_collision.assets/hash_table_chaining.png)

Phương thức thao tác trên bảng băm hiện thực bằng phương pháp nối chuỗi có những thay đổi sau:

- **Tra cứu phần tử**: Nhập `key`, thông qua hàm băm để lấy chỉ số ngăn, từ đó truy cập vào nút đầu của danh sách liên kết, sau đó duyệt danh sách liên kết và so sánh `key` để tìm kiếm cặp khoá - giá trị mục tiêu.
- **Thêm phần tử**: Đầu tiên dùng hàm băm để truy cập nút đầu của danh sách liên kết, sau đó thêm nút mới (cặp khoá - giá trị) vào trong danh sách liên kết.
- **Xoá phần tử**: Dựa vào kết quả của hàm băm để truy cập đầu danh sách liên kết, sau đó duyệt danh sách liên kết để tìm nút mục tiêu và xoá nút đó đi.

Phương pháp nối chuỗi tồn tại một số hạn chế sau:

- **Tăng không gian chiếm dụng**: Danh sách liên kết chứa các con trỏ nút, tiêu tốn nhiều không gian bộ nhớ hơn so với mảng.
- **Giảm hiệu năng tra cứu**: Do cần phải duyệt tuyến tính qua danh sách liên kết để tìm phần tử tương ứng.

Đoạn mã dưới đây cung cấp một hiện thực đơn giản của bảng băm nối chuỗi, cần lưu ý hai điểm:

- Sử dụng danh sách (mảng động) thay cho danh sách liên kết để đơn giản hoá mã nguồn. Trong thiết lập này, bảng băm (mảng) chứa nhiều ngăn, mỗi ngăn là một danh sách.
- Hiện thực dưới đây bao gồm cả phương thức mở rộng dung lượng bảng băm. Khi hệ số tải vượt quá $\frac{2}{3}$, chúng ta sẽ mở rộng dung lượng bảng băm lên gấp $2$ lần kích thước ban đầu.

```src
[file]{hash_map_chaining}-[class]{hash_map_chaining}-[func]{}
```

Cần lưu ý rằng khi danh sách liên kết quá dài, hiệu năng tra cứu $O(n)$ sẽ rất kém. **Lúc này có thể chuyển đổi danh sách liên kết thành "cây AVL" hoặc "cây đỏ-đen"**, từ đó tối ưu hoá độ phức tạp thời gian của thao tác tra cứu xuống còn $O(\log n)$.

## Địa chỉ mở (Open Addressing)

<u>Địa chỉ mở (open addressing)</u> không đưa thêm các cấu trúc dữ liệu bổ sung, mà xử lý đụng độ băm thông qua việc "dò tìm nhiều lần" (multiple probing). Các phương thức dò tìm chủ yếu bao gồm dò tuyến tính, dò bậc hai và băm kép.

Dưới đây lấy dò tuyến tính làm ví dụ để giới thiệu cơ chế hoạt động của bảng băm địa chỉ mở.

### Dò tuyến tính (Linear Probing)

Dò tuyến tính áp dụng tìm kiếm tuyến tính với bước nhảy cố định để dò tìm vị trí trống, phương thức thao tác của nó có đôi chút khác biệt so với bảng băm thông thường:

- **Chèn phần tử**: Tính toán chỉ số ngăn qua hàm băm, nếu phát hiện trong ngăn đã có phần tử, thì từ vị trí đụng độ sẽ duyệt tuyến tính về phía sau (bước nhảy thường là $1$ ) cho đến khi tìm thấy ngăn trống và chèn phần tử vào đó.
- **Tìm kiếm phần tử**: Nếu phát hiện đụng độ băm, sử dụng cùng bước nhảy đó để duyệt tuyến tính về phía sau cho đến khi tìm thấy phần tử khớp và trả về `value`; nếu gặp ngăn trống thì chứng tỏ phần tử mục tiêu không tồn tại trong bảng băm, trả về `None`.

Hình dưới đây minh hoạ sự phân bố các cặp khoá - giá trị trong bảng băm địa chỉ mở (dò tuyến tính). Theo hàm băm này, các `key` có hai chữ số cuối giống nhau đều sẽ được ánh xạ vào cùng một ngăn. Thông qua dò tuyến tính, chúng lần lượt được lưu trữ tại ngăn đó và các ngăn liền kề phía sau.

![Phân bố cặp khoá - giá trị trong bảng băm địa chỉ mở (dò tuyến tính)](hash_collision.assets/hash_table_linear_probing.png)

Tuy nhiên, **dò tuyến tính rất dễ phát sinh "hiện tượng tụ cụm" (clustering)**. Cụ thể, chuỗi các vị trí bị chiếm dụng liên tiếp trong mảng càng dài thì khả năng xảy ra đụng độ băm tại các vị trí liên tiếp này càng cao, từ đó càng thúc đẩy cụm đó phình to hơn, tạo thành một vòng xoáy luẩn quẩn, cuối cùng dẫn đến sự suy giảm hiệu năng của mọi thao tác thêm, xoá, sửa, tra cứu.

Cần lưu ý rằng, **chúng ta không thể trực tiếp xoá phần tử trong bảng băm địa chỉ mở**. Điều này là do việc xoá phần tử sẽ tạo ra một ngăn trống `None` trong mảng, mà khi tra cứu phần tử, thao tác dò tuyến tính gặp ngăn trống sẽ lập tức dừng lại và trả về kết quả, khiến cho các phần tử nằm phía sau ngăn trống đó hoàn toàn không thể truy cập được nữa, và chương trình có thể phán đoán sai rằng các phần tử đó không tồn tại, như minh hoạ trong hình dưới đây.

![Vấn đề tra cứu do xoá phần tử trong địa chỉ mở](hash_collision.assets/hash_table_open_addressing_deletion.png)

Để giải quyết vấn đề này, chúng ta có thể áp dụng cơ chế <u>xoá trễ (lazy deletion)</u>: không trực tiếp xoá bỏ phần tử khỏi bảng băm, **mà sử dụng một hằng số `TOMBSTONE` (bia mộ) để đánh dấu ngăn đó**. Dưới cơ chế này, cả `None` và `TOMBSTONE` đều đại diện cho ngăn trống và đều có thể đặt cặp khoá - giá trị mới vào. Điểm khác biệt là khi dò tuyến tính gặp `TOMBSTONE`, nó sẽ tiếp tục duyệt tiếp về phía sau vì có thể vẫn còn các cặp khoá - giá trị nằm bên dưới.

Tuy nhiên, **xoá trễ có thể đẩy nhanh tốc độ thoái hoá hiệu năng của bảng băm**. Điều này là do mỗi thao tác xoá đều tạo ra một dấu mốc xoá, khi số lượng `TOMBSTONE` tăng lên, thời gian tìm kiếm cũng sẽ tăng theo do thao tác dò tuyến tính có thể phải nhảy qua rất nhiều `TOMBSTONE` mới tìm thấy phần tử mục tiêu.

Vì vậy, có thể cân nhắc ghi lại chỉ số của `TOMBSTONE` đầu tiên bắt gặp trong quá trình dò tuyến tính, và hoán đổi vị trí của phần tử mục tiêu tìm thấy với `TOMBSTONE` đó. Lợi ích của việc này là sau mỗi lần tra cứu hoặc thêm phần tử, phần tử sẽ được dịch chuyển về ngăn gần với vị trí lý tưởng (điểm bắt đầu dò) hơn, qua đó tối ưu hoá hiệu năng tra cứu.

Mã nguồn dưới đây hiện thực một bảng băm địa chỉ mở (dò tuyến tính) tích hợp cơ chế xoá trễ. Để tận dụng không gian bảng băm một cách triệt để hơn, chúng ta coi bảng băm như một "mảng vòng", khi vượt quá cuối mảng sẽ quay lại đầu mảng để tiếp tục duyệt.

```src
[file]{hash_map_open_addressing}-[class]{hash_map_open_addressing}-[func]{}
```

### Dò bậc hai (Quadratic Probing)

Dò bậc hai tương tự như dò tuyến tính, đều là các chiến lược phổ biến của địa chỉ mở. Khi xảy ra đụng độ, dò bậc hai không đơn thuần nhảy qua một số bước cố định, mà nhảy qua số bước bằng "bình phương số lần dò", tức là $1, 4, 9, \dots$ bước.

Dò bậc hai sở hữu những ưu thế chính sau:

- Dò bậc hai giảm thiểu hiệu ứng tụ cụm của dò tuyến tính nhờ việc nhảy cách quãng theo khoảng cách bình phương.
- Dò bậc hai nhảy qua khoảng cách lớn hơn để tìm vị trí trống, giúp dữ liệu được phân bố đồng đều hơn.

Tuy nhiên, dò bậc hai không hoàn hảo:

- Vẫn tồn tại hiện tượng tụ cụm thứ cấp, nghĩa là một số vị trí vẫn dễ bị chiếm dụng hơn các vị trí khác.
- Do bước nhảy tăng theo hàm bậc hai, dò bậc hai có thể không duyệt qua được toàn bộ các ngăn trong bảng băm, đồng nghĩa với việc ngay cả khi trong bảng băm vẫn còn ngăn trống, dò bậc hai cũng có thể không tiếp cận được ngăn trống đó.

### Băm kép (Double Hashing)

Đúng như tên gọi, phương pháp băm kép sử dụng nhiều hàm băm $f_1(x)$, $f_2(x)$, $f_3(x)$, $\dots$ để tiến hành dò tìm:

- **Chèn phần tử**: Nếu hàm băm $f_1(x)$ xảy ra đụng độ, sẽ thử tiếp $f_2(x)$, cứ tiếp tục như vậy cho đến khi tìm được vị trí trống rồi mới chèn phần tử vào.
- **Tìm kiếm phần tử**: Thực hiện tìm kiếm theo đúng thứ tự các hàm băm đó cho đến khi tìm thấy phần tử mục tiêu thì trả về; nếu gặp vị trí trống hoặc đã thử hết toàn bộ hàm băm mà không thấy thì chứng tỏ phần tử không tồn tại trong bảng băm, trả về `None`.

So với dò tuyến tính, phương pháp băm kép khó phát sinh tụ cụm hơn, nhưng việc sử dụng nhiều hàm băm sẽ kéo theo chi phí tính toán bổ sung.

!!! tip

    Xin lưu ý rằng tất cả các bảng băm địa chỉ mở (dò tuyến tính, dò bậc hai và băm kép) đều gặp phải vấn đề "không thể trực tiếp xoá phần tử".

## Sự lựa chọn của các ngôn ngữ lập trình

Các ngôn ngữ lập trình áp dụng những chiến lược hiện thực bảng băm khác nhau, dưới đây là một số ví dụ:

- **Python** áp dụng địa chỉ mở: Từ điển `dict` sử dụng dãy số giả ngẫu nhiên để dò tìm vị trí.
- **Java** áp dụng nối chuỗi: Kể từ JDK 1.8, khi độ dài mảng bên trong `HashMap` đạt 64 và độ dài danh sách liên kết đạt 8, danh sách liên kết sẽ được tự động chuyển đổi thành cây đỏ-đen để nâng cao hiệu năng tìm kiếm.
- **Go** áp dụng nối chuỗi: Go quy định mỗi ngăn lưu tối đa 8 cặp khoá - giá trị, nếu vượt quá sức chứa thì sẽ nối thêm một ngăn tràn (overflow bucket); khi có quá nhiều ngăn tràn, hệ thống sẽ thực hiện một thao tác mở rộng dung lượng đẳng tích đặc biệt để đảm bảo hiệu năng.
