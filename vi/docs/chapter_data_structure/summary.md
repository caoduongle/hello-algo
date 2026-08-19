# Tóm tắt

### Điểm mấu chốt cần nhớ

- Cấu trúc dữ liệu có thể được phân loại từ hai góc độ: cấu trúc logic và cấu trúc vật lý. Cấu trúc logic mô tả mối quan hệ logic giữa các phần tử dữ liệu, trong khi cấu trúc vật lý mô tả phương thức lưu trữ dữ liệu trong bộ nhớ máy tính.
- Các cấu trúc logic phổ biến bao gồm tuyến tính, dạng cây và dạng mạng, v.v. Thông thường chúng ta chia cấu trúc dữ liệu thành hai loại: tuyến tính (mảng, danh sách liên kết, ngăn xếp, hàng đợi) và phi tuyến tính (cây, đồ thị, đống - heap) dựa trên cấu trúc logic. Việc hiện thực hoá bảng băm có thể bao gồm đồng thời cả cấu trúc dữ liệu tuyến tính và phi tuyến tính.
- Khi chương trình chạy, dữ liệu được lưu trữ trong bộ nhớ máy tính. Mỗi không gian bộ nhớ đều sở hữu một địa chỉ bộ nhớ tương ứng, và chương trình truy cập dữ liệu thông qua các địa chỉ bộ nhớ này.
- Cấu trúc vật lý chủ yếu chia thành lưu trữ không gian liên tục (mảng) và lưu trữ không gian phân tán (danh sách liên kết). Mọi cấu trúc dữ liệu đều được xây dựng từ mảng, danh sách liên kết hoặc sự kết hợp của cả hai.
- Các kiểu dữ liệu cơ bản trong máy tính bao gồm số nguyên `byte`, `short`, `int`, `long` ，số thực dấu phẩy động `float`, `double` ，ký tự `char` và Boolean `bool` 。Phạm vi giá trị của chúng phụ thuộc vào dung lượng bộ nhớ chiếm dụng và phương thức biểu diễn.
- Mã dấu-độ lớn (nguyên mã), mã bù một (phản mã) và mã bù hai (bổ mã) là ba phương pháp mã hoá số trong máy tính, chúng có thể chuyển đổi qua lại lẫn nhau. Bit cao nhất của mã dấu-độ lớn là bit dấu, các bit còn lại biểu thị giá trị của số đó.
- Số nguyên được lưu trữ trong máy tính dưới dạng mã bù hai. Dưới biểu diễn mã bù hai, máy tính có thể xử lý phép cộng giữa số dương và số âm như nhau, không cần thiết kế mạch phần cứng chuyên dụng cho phép trừ, và không tồn tại sự nhập nhằng giữa số không âm và không dương.
- Mã hoá của số thực dấu phẩy động gồm 1 bit dấu, 8 bit mũ và 23 bit định trị (phân số). Nhờ có bit mũ, phạm vi giá trị của số thực dấu phẩy động lớn hơn rất nhiều so với số nguyên, nhưng phải đánh đổi bằng sự suy giảm độ chính xác.
- Mã ASCII là bảng mã ký tự tiếng Anh xuất hiện sớm nhất, có độ dài 1 byte, thu thập 128 ký tự. Bảng mã GBK là bảng mã chữ Hán thông dụng, thu thập hơn hai vạn chữ Hán. Unicode hướng tới việc cung cấp một chuẩn bảng mã ký tự hoàn chỉnh, thu thập chữ viết của mọi ngôn ngữ trên thế giới, qua đó giải quyết triệt để vấn đề vỡ chữ do bất đồng phương pháp mã hoá.
- UTF-8 là phương pháp mã hoá Unicode phổ biến nhất, có tính tương thích cực kỳ cao. Nó là một phương pháp mã hoá độ dài khả biến, có tính mở rộng tốt và nâng cao hiệu quả sử dụng không gian lưu trữ. UTF-16 và UTF-32 là các phương pháp mã hoá độ dài cố định. Khi mã hoá chữ Hán, UTF-16 chiếm ít không gian hơn UTF-8. Các ngôn ngữ lập trình như Java và C# mặc định sử dụng mã hoá UTF-16.

### Hỏi & Đáp (Q & A)

**Q**：Tại sao bảng băm lại đồng thời chứa cả cấu trúc dữ liệu tuyến tính và phi tuyến tính?

Tầng bên dưới của bảng băm là mảng; để giải quyết đụng độ băm, chúng ta có thể sử dụng phương pháp "nối chuỗi" (sẽ được giới thiệu trong chương "Đụng độ băm"): mỗi ngăn (bucket) trong mảng trỏ đến một danh sách liên kết, và khi độ dài của danh sách liên kết vượt quá một ngưỡng nhất định thì nó có thể được chuyển đổi thành cây (thường là cây đỏ-đen).

Đứng từ góc độ lưu trữ, nền tảng của bảng băm là mảng, trong đó mỗi vị trí ô/ngăn có thể chứa một giá trị, một danh sách liên kết hoặc một cái cây. Do đó, bảng băm có thể đồng thời chứa cả cấu trúc dữ liệu tuyến tính (mảng, danh sách liên kết) và cấu trúc dữ liệu phi tuyến tính (cây).

**Q**：Độ dài của kiểu `char` có phải luôn là 1 byte không?

Độ dài của kiểu `char` do phương pháp mã hoá mà ngôn ngữ lập trình sử dụng quyết định. Ví dụ: Java, JavaScript, TypeScript, C# đều áp dụng mã hoá UTF-16 (để lưu điểm mã Unicode), do đó độ dài của kiểu `char` là 2 byte.

**Q**：Việc gọi cấu trúc dữ liệu xây dựng dựa trên mảng là "cấu trúc dữ liệu tĩnh" có gây hiểu nhầm không? Ngăn xếp cũng có thể thực hiện thao tác đẩy vào (push) và lấy ra (pop), các thao tác này đều mang tính "động".

Ngăn xếp quả thực có thể thực hiện các thao tác dữ liệu mang tính động, nhưng bản thân cấu trúc dữ liệu vẫn là "tĩnh" (độ dài không thể thay đổi). Mặc dù cấu trúc dữ liệu dựa trên mảng có thể thêm hoặc xoá phần tử một cách linh hoạt, nhưng dung lượng sức chứa của chúng là cố định. Nếu lượng dữ liệu vượt quá kích thước được cấp phát trước, hệ thống cần phải tạo ra một mảng mới lớn hơn và sao chép toàn bộ nội dung của mảng cũ sang mảng mới.

**Q**：Khi khởi tạo ngăn xếp (hàng đợi), ta không chỉ định kích thước của nó, tại sao chúng lại là "cấu trúc dữ liệu tĩnh"?

Trong các ngôn ngữ lập trình bậc cao, chúng ta không cần phải tự tay chỉ định dung lượng ban đầu của ngăn xếp (hàng đợi), công việc này được lớp xử lý tự động ở bên trong. Ví dụ dung lượng ban đầu của `ArrayList` trong Java thường là 10. Ngoài ra, thao tác mở rộng dung lượng cũng được hiện thực hoá hoàn toàn tự động. Chi tiết xin xem trong chương "Danh sách" tiếp theo.

**Q**：Phương pháp chuyển từ mã dấu-độ lớn sang mã bù hai là "đảo bit rồi cộng 1", vậy chuyển từ mã bù hai sang mã dấu-độ lớn đáng lẽ phải là phép toán ngược "trừ 1 rồi đảo bit", nhưng tại sao chuyển từ mã bù hai sang mã dấu-độ lớn cũng có thể thực hiện thông qua "đảo bit rồi cộng 1"?

Đó là vì sự chuyển đổi qua lại giữa mã dấu-độ lớn và mã bù hai thực chất là quá trình tính toán "phần bù" (complement). Trước tiên chúng ta hãy cùng xem định nghĩa về phần bù: giả sử $a + b = c$ ，khi đó ta gọi $a$ là phần bù của $b$ đối với $c$ ，và ngược lại $b$ cũng là phần bù của $a$ đối với $c$ 。

Cho một số nhị phân có độ dài $n = 4$ bit là $0010$ ，nếu coi số này là mã dấu-độ lớn (không xét bit dấu), thì mã bù hai của nó được tạo ra thông qua thao tác "đảo bit rồi cộng 1":

$$
0010 \rightarrow 1101 \rightarrow 1110
$$

Chúng ta sẽ nhận thấy tổng của mã dấu-độ lớn và mã bù hai là $0010 + 1110 = 10000$ ，nghĩa là mã bù hai $1110$ chính là "phần bù" của mã dấu-độ lớn $0010$ đối với $10000$ 。**Điều này đồng nghĩa với việc thao tác "đảo bit rồi cộng 1" ở trên thực chất là quá trình tính toán phần bù đối với $10000$**。

Vậy "phần bù" của mã bù hai $1110$ đối với $10000$ là bao nhiêu? Chúng ta vẫn có thể dùng "đảo bit rồi cộng 1" để tìm ra nó:

$$
1110 \rightarrow 0001 \rightarrow 0010
$$

Nói cách khác, mã dấu-độ lớn và mã bù hai là "phần bù" của nhau đối với $10000$ ，do đó "chuyển mã dấu-độ lớn sang mã bù hai" và "chuyển mã bù hai sang mã dấu-độ lớn" có thể thực hiện bằng cùng một chuỗi thao tác (đảo bit rồi cộng 1).

Dĩ nhiên, chúng ta cũng có thể dùng phép toán ngược để tìm mã dấu-độ lớn của mã bù hai $1110$ ，tức là "trừ 1 rồi đảo bit":

$$
1110 \rightarrow 1101 \rightarrow 0010
$$

Tóm lại, cả hai phép toán "đảo bit rồi cộng 1" và "trừ 1 rồi đảo bit" đều là đang tính toán phần bù đối với $10000$ ，và chúng hoàn toàn tương đương nhau.

Về bản chất, thao tác "đảo bit" thực chất là tìm phần bù đối với $1111$ （bởi vì luôn có `Mã dấu-độ lớn + Mã bù một = 1111`）；và khi cộng thêm 1 vào mã bù một thì thu được mã bù hai, chính là phần bù đối với $10000$ 。

Ví dụ trên lấy $n = 4$ ，và nguyên lý này có thể mở rộng ra cho các số nhị phân có số bit tuỳ ý.
