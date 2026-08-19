# Tóm tắt

### Điểm mấu chốt cần nhớ

- Mảng và danh sách liên kết là hai cấu trúc dữ liệu cơ bản, lần lượt đại diện cho hai phương thức lưu trữ dữ liệu trong bộ nhớ máy tính: lưu trữ trong không gian liên tục và lưu trữ trong không gian phân tán. Đặc điểm của cả hai mang tính bổ trợ lẫn nhau.
- Mảng hỗ trợ truy cập ngẫu nhiên, chiếm ít bộ nhớ hơn; nhưng thao tác chèn và xoá phần tử kém hiệu quả, và độ dài là cố định sau khi khởi tạo.
- Danh sách liên kết hiện thực việc chèn và xoá nút hiệu quả thông qua việc thay đổi tham chiếu (con trỏ), đồng thời có thể điều chỉnh độ dài một cách linh hoạt; nhưng thao tác truy cập nút kém hiệu quả và chiếm nhiều bộ nhớ hơn. Các loại danh sách liên kết phổ biến bao gồm danh sách liên kết đơn, danh sách liên kết vòng và danh sách liên kết đôi.
- Danh sách là một tập hợp các phần tử có thứ tự hỗ trợ các thao tác thêm, xoá, tra cứu, sửa đổi, thường được hiện thực dựa trên mảng động. Nó giữ lại các ưu thế của mảng, đồng thời có thể linh hoạt điều chỉnh độ dài.
- Sự ra đời của danh sách đã nâng cao đáng kể tính thực tiễn của mảng, nhưng có thể gây lãng phí một phần không gian bộ nhớ.
- Khi chương trình chạy, dữ liệu chủ yếu được lưu trữ trong bộ nhớ RAM. Mảng mang lại hiệu năng không gian bộ nhớ cao hơn, trong khi danh sách liên kết lại linh hoạt hơn trong việc sử dụng bộ nhớ.
- Bộ nhớ đệm Cache cung cấp khả năng truy cập dữ liệu nhanh chóng cho CPU thông qua các cơ chế nạp dữ liệu như dòng đệm (cache line), cơ chế nạp trước (prefetching), cùng tính cục bộ không gian và tính cục bộ thời gian, giúp cải thiện đáng kể hiệu suất thực thi của chương trình.
- Do mảng có tỷ lệ trúng bộ nhớ đệm cao hơn, nên thông thường nó vận hành hiệu quả hơn danh sách liên kết. Khi lựa chọn cấu trúc dữ liệu, nên đưa ra quyết định phù hợp dựa trên nhu cầu và ngữ cảnh cụ thể.

### Hỏi & Đáp (Q & A)

**Q**: Mảng được lưu trữ trên stack và lưu trữ trên heap có ảnh hưởng đến hiệu năng thời gian và không gian không?

Cả mảng lưu trữ trên stack và heap đều nằm trong các ô nhớ liên tục, nên hiệu năng thao tác dữ liệu về cơ bản là như nhau. Tuy nhiên, stack và heap có những đặc điểm riêng biệt dẫn đến các điểm khác biệt sau:

1. Hiệu năng cấp phát và giải phóng: Stack là một vùng nhớ tương đối nhỏ, việc cấp phát do trình biên dịch tự động thực hiện; trong khi heap có dung lượng lớn hơn nhiều, có thể cấp phát động trong mã nguồn và dễ bị phân mảnh hơn. Do đó, các thao tác cấp phát và giải phóng trên heap thường chậm hơn so với trên stack.
2. Giới hạn kích thước: Dung lượng bộ nhớ stack tương đối nhỏ, kích thước heap nói chung chỉ bị giới hạn bởi bộ nhớ khả dụng của hệ thống. Do đó heap thích hợp hơn để lưu trữ các mảng có kích thước lớn.
3. Độ linh hoạt: Kích thước của mảng trên stack cần phải được xác định tại thời điểm biên dịch, trong khi kích thước mảng trên heap có thể xác định linh hoạt tại thời điểm thực thi (runtime).

**Q**: Tại sao mảng yêu cầu các phần tử phải có cùng kiểu dữ liệu, trong khi danh sách liên kết lại không bắt buộc điều này?

Danh sách liên kết được tạo thành từ các nút, các nút liên kết với nhau thông qua tham chiếu (con trỏ), mỗi nút có thể lưu trữ các kiểu dữ liệu khác nhau như `int`, `double`, `string`, `object`, v.v.

Ngược lại, các phần tử trong mảng bắt buộc phải có cùng kiểu dữ liệu, có như vậy mới có thể tính toán độ lệch để truy cập vị trí của phần tử tương ứng. Ví dụ, nếu mảng chứa đồng thời cả kiểu `int` và `long`, một phần tử đơn lẻ lần lượt chiếm 4 byte và 8 byte, khi đó không thể dùng công thức sau để tính toán độ lệch địa chỉ được nữa, vì trong mảng có chứa hai loại "kích thước phần tử":

```shell
# Địa chỉ bộ nhớ phần tử = Địa chỉ bộ nhớ mảng (địa chỉ phần tử đầu tiên) + Kích thước phần tử * Chỉ số phần tử
```

**Q**: Sau khi xoá nút `P`, có nhất thiết phải gán `P.next` bằng `None` không?

Không cần sửa `P.next` cũng được. Đứng từ góc độ của danh sách liên kết này, việc duyệt từ nút đầu đến nút cuối đã không còn gặp `P` nữa. Điều này đồng nghĩa với việc nút `P` đã bị xoá khỏi danh sách liên kết, lúc này nút `P` trỏ tới đâu cũng không gây ảnh hưởng gì tới danh sách liên kết này.

Đứng từ góc độ cấu trúc dữ liệu và giải thuật (làm bài tập), việc không ngắt kết nối không thành vấn đề, chỉ cần đảm bảo logic của chương trình là chính xác. Đứng từ góc độ hiện thực thư viện chuẩn, việc ngắt kết nối sẽ an toàn hơn và logic rõ ràng hơn. Nếu không ngắt kết nối, giả sử nút bị xoá không được bộ thu dọn rác thu hồi đúng cách, nó có thể ảnh hưởng đến việc thu hồi bộ nhớ của các nút đứng sau.

**Q**: Trong danh sách liên kết, độ phức tạp thời gian của thao tác chèn và xoá là $O(1)$. Nhưng trước khi thêm/xoá đều cần $O(n)$ thời gian để tìm phần tử, tại sao độ phức tạp thời gian không phải là $O(n)$?

Nếu là tìm kiếm phần tử trước rồi mới xoá phần tử, độ phức tạp thời gian quả thực là $O(n)$. Tuy nhiên, ưu thế chèn và xoá $O(1)$ của danh sách liên kết có thể được thể hiện trong các ứng dụng khác. Chẳng hạn, hàng đợi hai đầu (deque) rất thích hợp để hiện thực bằng danh sách liên kết, chúng ta duy trì các biến con trỏ luôn trỏ vào nút đầu và nút cuối, mỗi thao tác chèn và xoá ở hai đầu đều đạt $O(1)$.

**Q**: Trong hình "Định nghĩa và phương thức lưu trữ của danh sách liên kết", con trỏ nút màu xanh lam nhạt có chiếm một ô địa chỉ bộ nhớ không? Hay là chiếm một nửa cùng với giá trị của nút?

Sơ đồ đó chỉ mang tính biểu diễn định tính, việc định lượng cụ thể cần căn cứ vào tình huống thực tế:

- Giá trị của nút thuộc các kiểu dữ liệu khác nhau sẽ chiếm dung lượng khác nhau, ví dụ như `int`, `long`, `double` và các đối tượng thực thể.
- Kích thước không gian bộ nhớ mà biến con trỏ chiếm dụng phụ thuộc vào hệ điều hành và môi trường biên dịch sử dụng, phần lớn là 8 byte (trên hệ 64-bit) hoặc 4 byte (trên hệ 32-bit).

**Q**: Thao tác thêm phần tử vào cuối danh sách có luôn luôn đạt $O(1)$ trong mọi thời điểm không?

Nếu khi thêm phần tử mà kích thước vượt quá sức chứa của danh sách, cần phải mở rộng dung lượng danh sách trước rồi mới thêm vào. Hệ thống sẽ xin cấp phát một vùng nhớ mới và chuyển toàn bộ phần tử của danh sách cũ sang đó, lúc này độ phức tạp thời gian sẽ là $O(n)$.

**Q**: "Sự ra đời của danh sách đã nâng cao đáng kể tính thực tiễn của mảng, nhưng có thể gây lãng phí một phần không gian bộ nhớ", sự lãng phí không gian ở đây có phải là bộ nhớ do các biến bổ sung như dung lượng, độ dài, hệ số mở rộng chiếm dụng không?

Sự lãng phí không gian ở đây chủ yếu bao gồm hai khía cạnh: một mặt, danh sách luôn thiết lập một dung lượng ban đầu nhất định mà chúng ta chưa chắc đã dùng hết; mặt khác, để tránh việc phải mở rộng dung lượng quá thường xuyên, mỗi lần mở rộng dung lượng thường sẽ nhân với một hệ số, ví dụ như $\times 1.5$ hoặc $\times 2$. Như vậy sẽ xuất hiện nhiều vị trí trống mà thông thường chúng ta không thể lấp đầy hoàn toàn.

**Q**: Trong Python, sau khi khởi tạo `n = [1, 2, 3]`, địa chỉ của 3 phần tử này nằm liên tiếp nhau, nhưng khi khởi tạo `m = [2, 1, 3]` lại thấy id của từng phần tử không liên tiếp mà lần lượt trùng với id trong `n`. Địa chỉ của các phần tử này không liên tục, vậy `m` có còn là mảng không?

Giả sử thay các phần tử trong danh sách bằng các nút danh sách liên kết `n = [n1, n2, n3, n4, n5]`, thông thường 5 đối tượng nút này cũng nằm phân tán ở khắp nơi trong bộ nhớ. Tuy nhiên, cho trước một chỉ số danh sách, chúng ta vẫn có thể lấy được địa chỉ bộ nhớ của nút trong thời gian $O(1)$, từ đó truy cập đến nút tương ứng. Điều này là do thứ được lưu trong mảng là tham chiếu đến các nút, chứ không phải bản thân các đối tượng nút.

Khác với nhiều ngôn ngữ khác, các số nguyên trong Python cũng được đóng gói thành đối tượng; thứ được lưu trữ trong danh sách không phải là bản thân con số, mà là tham chiếu trỏ đến con số đó. Do đó, chúng ta sẽ thấy cùng một con số ở hai mảng khác nhau lại có chung một `id`, và địa chỉ bộ nhớ của các con số này không nhất thiết phải nằm liên tiếp nhau.

**Q**: Trong C++ STL đã có `std::list` hiện thực danh sách liên kết đôi, nhưng dường như một số sách thuật toán không hay dùng trực tiếp nó, có phải vì nó có hạn chế gì không?

Một mặt, chúng ta thường ưa chuộng sử dụng mảng để hiện thực thuật toán hơn và chỉ dùng danh sách liên kết khi thực sự cần thiết, chủ yếu vì hai lý do:

- Chi phí không gian: Do mỗi phần tử cần thêm hai con trỏ (một trỏ đến phần tử trước, một trỏ đến phần tử sau), nên `std::list` thường tốn nhiều bộ nhớ hơn so với `std::vector`.
- Không thân thiện với bộ nhớ đệm Cache: Do dữ liệu không được lưu trữ liên tục, nên `std::list` có tỷ lệ tận dụng bộ nhớ đệm thấp hơn. Trong điều kiện thông thường, hiệu năng của `std::vector` sẽ tốt hơn.

Mặt khác, các tình huống bắt buộc phải dùng danh sách liên kết chủ yếu là cây nhị phân và đồ thị. Ngăn xếp và hàng đợi thường sử dụng `stack` và `queue` do ngôn ngữ lập trình cung cấp sẵn thay vì dùng danh sách liên kết.

**Q**: Thao tác `res = [[0]] * n` tạo ra một danh sách hai chiều, trong đó mỗi `[0]` có độc lập với nhau không?

Không hề độc lập. Trong danh sách hai chiều này, tất cả các `[0]` thực chất đều là tham chiếu trỏ đến cùng một đối tượng danh sách duy nhất. Nếu chúng ta sửa đổi một phần tử bên trong, tất cả các hàng còn lại đều sẽ thay đổi theo.

Nếu muốn mỗi `[0]` trong danh sách hai chiều đều độc lập với nhau, có thể sử dụng `res = [[0] for _ in range(n)]`. Nguyên lý của cách này là khởi tạo ra $n$ đối tượng danh sách `[0]` hoàn toàn riêng biệt.

**Q**: Thao tác `res = [0] * n` tạo ra một danh sách, trong đó mỗi số nguyên 0 có độc lập với nhau không?

Trong danh sách này, tất cả các số nguyên 0 đều tham chiếu đến cùng một đối tượng. Điều này là do Python áp dụng cơ chế vùng đệm (cache pool) cho các số nguyên nhỏ (thường từ -5 đến 256) nhằm tối đa hoá việc tái sử dụng đối tượng và nâng cao hiệu năng.

Mặc dù chúng cùng trỏ đến một đối tượng, nhưng chúng ta vẫn có thể sửa đổi độc lập từng phần tử trong danh sách, bởi vì số nguyên trong Python là "đối tượng bất biến" (immutable object). Khi chúng ta gán giá trị mới cho một phần tử, thực chất là chuyển phần tử đó sang tham chiếu đến một đối tượng số khác, chứ không phải thay đổi đối tượng ban đầu.

Tuy nhiên, khi phần tử của danh sách là "đối tượng khả biến" (mutable object, ví dụ như danh sách con, từ điển hoặc thể hiện của lớp, v.v.), việc thay đổi phần tử sẽ trực tiếp làm thay đổi bản thân đối tượng đó, và toàn bộ các phần tử đang tham chiếu đến đối tượng đó sẽ cùng biến đổi theo.
