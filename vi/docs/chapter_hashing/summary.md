# Tóm tắt

### Điểm mấu chốt cần nhớ

- Nhập `key` ，bảng băm có thể tra cứu ra `value` tương ứng trong thời gian $O(1)$ ，hiệu năng cực kỳ cao.
- Các thao tác bảng băm phổ biến bao gồm tra cứu, thêm cặp khoá - giá trị, xoá cặp khoá - giá trị và duyệt bảng băm.
- Hàm băm ánh xạ `key` thành chỉ số mảng, từ đó truy cập vào ngăn tương ứng và lấy ra `value` 。
- Hai `key` khác nhau có thể thu được cùng một chỉ số mảng sau khi đi qua hàm băm, dẫn đến sai lệch kết quả tra cứu, hiện tượng này được gọi là đụng độ băm.
- Sức chứa của bảng băm càng lớn thì xác suất đụng độ băm càng thấp. Do đó có thể giảm thiểu đụng độ băm thông qua việc mở rộng dung lượng bảng băm. Tương tự như mở rộng mảng, thao tác mở rộng bảng băm có chi phí rất lớn.
- Hệ số tải được định nghĩa là số lượng phần tử trong bảng băm chia cho số lượng ngăn, phản ánh mức độ nghiêm trọng của đụng độ băm và thường được dùng làm điều kiện kích hoạt mở rộng bảng băm.
- Phương pháp nối chuỗi biến đổi từng phần tử đơn lẻ thành danh sách liên kết, lưu trữ toàn bộ các phần tử xảy ra đụng độ vào trong cùng một danh sách liên kết. Tuy nhiên nếu danh sách liên kết quá dài sẽ làm giảm hiệu năng tra cứu, có thể cải thiện bằng cách chuyển đổi danh sách liên kết thành cây đỏ-đen.
- Phương pháp địa chỉ mở xử lý đụng độ băm thông qua việc dò tìm nhiều lần. Dò tuyến tính sử dụng bước nhảy cố định, có nhược điểm là không thể trực tiếp xoá phần tử và dễ phát sinh hiện tượng tụ cụm. Băm kép sử dụng nhiều hàm băm để dò tìm, ít bị tụ cụm hơn so với dò tuyến tính nhưng lại làm tăng khối lượng tính toán.
- Các ngôn ngữ lập trình áp dụng những cách hiện thực bảng băm khác nhau. Ví dụ `HashMap` trong Java sử dụng nối chuỗi, còn `dict` trong Python sử dụng địa chỉ mở.
- Trong bảng băm, chúng ta mong muốn thuật toán băm có tính xác định, hiệu năng cao và phân bố đồng đều. Trong mật mã học, thuật toán băm còn cần có tính kháng va chạm và hiệu ứng thác đổ.
- Thuật toán băm thường sử dụng số nguyên tố lớn làm số chia (modulus) để tối đa hoá sự phân bố đồng đều của giá trị băm và giảm thiểu đụng độ băm.
- Các thuật toán băm phổ biến bao gồm MD5, SHA-1, SHA-2 và SHA-3. MD5 thường dùng để kiểm tra tính toàn vẹn của tệp tin, còn dòng SHA-2 thường dùng trong các ứng dụng bảo mật và giao thức mạng.
- Ngôn ngữ lập trình thường cung cấp thuật toán băm tích hợp sẵn cho các kiểu dữ liệu để tính toán chỉ số ngăn trong bảng băm. Thông thường chỉ có các đối tượng bất biến mới có thể băm được.

### Hỏi & Đáp (Q & A)

**Q**：Độ phức tạp thời gian của bảng băm trong trường hợp nào sẽ là $O(n)$ ？

Khi đụng độ băm diễn ra nghiêm trọng, độ phức tạp thời gian của bảng băm sẽ thoái hoá về $O(n)$ 。Khi hàm băm được thiết kế tốt, sức chứa được thiết lập hợp lý và các xung đột phân bố tương đối đồng đều thì độ phức tạp thời gian là $O(1)$ 。Khi sử dụng bảng băm tích hợp sẵn trong các ngôn ngữ lập trình, thông thường chúng ta coi độ phức tạp thời gian là $O(1)$ 。

**Q**：Tại sao không sử dụng hàm băm $f(x) = x$ ？Như vậy sẽ không có đụng độ băm nào cả.

Dưới hàm băm $f(x) = x$ ，mỗi phần tử tương ứng với một chỉ số ngăn duy nhất, điều này tương đương với mảng. Tuy nhiên, không gian đầu vào thường lớn hơn rất nhiều so với không gian đầu ra (độ dài mảng), do đó bước cuối cùng của hàm băm bắt buộc phải lấy dư với độ dài mảng. Nói cách khác, mục tiêu của bảng băm là ánh xạ một không gian trạng thái lớn vào một không gian nhỏ hơn và cung cấp hiệu năng tra cứu $O(1)$ 。

**Q**：Tầng dưới của bảng băm được hiện thực bằng mảng, danh sách liên kết, cây nhị phân, nhưng tại sao hiệu năng của nó lại có thể cao hơn chúng?

Thứ nhất, hiệu năng thời gian của bảng băm tăng lên nhưng hiệu năng không gian lại giảm đi. Bảng băm luôn có một phần dung lượng bộ nhớ đáng kể không được sử dụng hết.

Thứ hai, nó chỉ nâng cao hiệu năng thời gian trong các tình huống sử dụng cụ thể. Nếu một tính năng có thể thực hiện bằng mảng hoặc danh sách liên kết với cùng độ phức tạp thời gian, thì thông thường nó sẽ nhanh hơn so với bảng băm, bởi vì việc tính toán hàm băm tốn thêm chi phí (hệ số hằng số trong độ phức tạp thời gian lớn hơn).

Cuối cùng, độ phức tạp thời gian của bảng băm có nguy cơ bị thoái hoá. Ví dụ trong phương pháp nối chuỗi, khi thực hiện thao tác tìm kiếm trong danh sách liên kết hoặc cây đỏ-đen, nó vẫn tiềm ẩn rủi ro thoái hoá về thời gian $O(n)$ 。

**Q**：Phương pháp băm kép có gặp phải nhược điểm không thể trực tiếp xoá phần tử không? Không gian được đánh dấu đã xoá có thể tái sử dụng không?

Băm kép là một dạng của địa chỉ mở, và mọi phương pháp địa chỉ mở đều có nhược điểm là không thể trực tiếp xoá phần tử mà phải thông qua cơ chế xoá trễ (đánh dấu xoá). Không gian được đánh dấu đã xoá hoàn toàn có thể được tái sử dụng: khi chèn phần tử mới vào bảng băm và hàm băm tìm đến vị trí đã được đánh dấu xoá, vị trí đó có thể được phần tử mới sử dụng ngay. Làm như vậy vừa giữ nguyên chuỗi dò tìm của bảng băm, vừa đảm bảo tỷ lệ tận dụng không gian bộ nhớ.

**Q**：Tại sao trong dò tuyến tính, khi tìm kiếm phần tử lại xuất hiện đụng độ băm?

Khi tìm kiếm, chương trình dùng hàm băm để tìm đến ngăn và cặp khoá - giá trị tương ứng, nếu phát hiện `key` không khớp thì chứng tỏ đã có đụng độ băm xảy ra tại vị trí đó. Do đó, phương pháp dò tuyến tính sẽ dựa theo bước nhảy định sẵn để lần lượt tìm kiếm tiếp xuống phía dưới cho đến khi tìm thấy đúng cặp khoá - giá trị hoặc xác định không tìm thấy mới thoát ra.

**Q**：Tại sao mở rộng dung lượng bảng băm lại có thể làm giảm đụng độ băm?

Bước cuối cùng của hàm băm thường là lấy dư với độ dài mảng $n$ để kết quả đầu ra nằm trong phạm vi chỉ số của mảng. Sau khi mở rộng dung lượng, độ dài mảng $n$ thay đổi, khiến cho chỉ số tương ứng với `key` cũng có thể thay đổi theo. Nhiều `key` ban đầu rơi vào cùng một ngăn thì sau khi mở rộng dung lượng có thể sẽ được phân bổ vào các ngăn khác nhau, từ đó giúp giảm thiểu đụng độ băm.

**Q**：Nếu muốn lưu trữ và truy cập hiệu năng cao, tại sao không dùng trực tiếp mảng cho nhanh?

Khi `key` của dữ liệu là các số nguyên liên tiếp trong phạm vi nhỏ, dùng trực tiếp mảng là lựa chọn đơn giản và hiệu quả nhất. Nhưng khi `key` thuộc các kiểu dữ liệu khác (chẳng hạn như chuỗi ký tự), chúng ta cần phải nhờ đến hàm băm để ánh xạ `key` thành chỉ số mảng, rồi lưu trữ phần tử thông qua mảng các ngăn, và cấu trúc như vậy chính là bảng băm.
