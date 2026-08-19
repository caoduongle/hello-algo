# Bộ nhớ trong và bộ nhớ đệm *

Trong hai phần đầu của chương này, chúng ta đã tìm hiểu về mảng và danh sách liên kết, hai cấu trúc dữ liệu nền tảng và quan trọng, lần lượt đại diện cho hai cấu trúc vật lý: "lưu trữ liên tục" và "lưu trữ phân tán".

Trên thực tế, **cấu trúc vật lý quyết định phần lớn hiệu quả sử dụng bộ nhớ trong (RAM) và bộ nhớ đệm (Cache) của chương trình**, từ đó ảnh hưởng sâu sắc đến hiệu năng tổng thể của chương trình thuật toán.

## Các thiết bị lưu trữ của máy tính

Trong máy tính bao gồm ba loại thiết bị lưu trữ chính: <u>ổ đĩa cứng (hard disk)</u>, <u>bộ nhớ trong (random-access memory, RAM)</u>, và <u>bộ nhớ đệm (cache memory)</u>. Bảng dưới đây thể hiện vai trò và đặc điểm hiệu năng khác nhau của chúng trong hệ thống máy tính.

<p align="center"> Bảng <id> &nbsp; Các thiết bị lưu trữ của máy tính </p>

|                | Ổ đĩa cứng                               | Bộ nhớ trong (RAM)                     | Bộ nhớ đệm (Cache)                                |
| -------------- | ---------------------------------------- | -------------------------------------- | ------------------------------------------------- |
| Mục đích       | Lưu trữ dữ liệu lâu dài, bao gồm hệ điều hành, chương trình, tệp tin, v.v. | Lưu trữ tạm thời các chương trình đang chạy và dữ liệu đang được xử lý | Lưu trữ dữ liệu và lệnh thường xuyên truy cập, giảm số lần CPU phải truy cập vào RAM |
| Tính khả biến (mất dữ liệu khi mất điện) | Không bị mất dữ liệu khi mất điện | Dữ liệu sẽ mất khi mất điện | Dữ liệu sẽ mất khi mất điện |
| Dung lượng     | Lớn, cấp độ TB                           | Nhỏ hơn, cấp độ GB                     | Rất nhỏ, cấp độ MB                                |
| Tốc độ         | Chậm, vài trăm đến vài nghìn MB/s        | Nhanh, vài chục GB/s                   | Cực nhanh, vài chục đến vài trăm GB/s             |
| Giá thành      | Rất rẻ                                   | Khá đắt                                | Cực kỳ đắt, được tích hợp sẵn cùng gói CPU        |

Chúng ta có thể hình dung hệ thống lưu trữ của máy tính như cấu trúc kim tự tháp trong hình dưới đây. Thiết bị lưu trữ càng gần đỉnh kim tự tháp thì tốc độ càng nhanh, dung lượng càng nhỏ và chi phí càng cao. Thiết kế đa tầng này không phải là ngẫu nhiên, mà là kết quả sau quá trình cân nhắc kỹ lưỡng của các nhà khoa học và kỹ sư máy tính:

- **Ổ đĩa cứng khó có thể bị RAM thay thế hoàn toàn**. Trước hết, dữ liệu trong RAM sẽ bị mất khi mất điện, do đó nó không thích hợp để lưu trữ dữ liệu lâu dài; thứ hai, giá thành của RAM đắt gấp hàng chục lần so với ổ đĩa cứng, khiến nó khó phổ cập rộng rãi với dung lượng cực lớn trên thị trường tiêu dùng.
- **Bộ nhớ đệm khó có thể đồng thời đạt được cả dung lượng lớn lẫn tốc độ cao**. Khi dung lượng các tầng đệm L1, L2, L3 tăng lên, kích thước vật lý của chúng sẽ phình to ra và khoảng cách vật lý đến nhân CPU sẽ xa hơn, dẫn đến thời gian truyền dữ liệu tăng lên và độ trễ truy cập phần tử cao hơn. Với công nghệ hiện tại, cấu trúc bộ nhớ đệm đa tầng là điểm cân bằng tối ưu giữa dung lượng, tốc độ và giá thành.

![Hệ thống lưu trữ máy tính](ram_and_cache.assets/storage_pyramid.png)

!!! tip

    Cấu trúc phân tầng lưu trữ của máy tính thể hiện sự cân bằng tinh tế giữa tốc độ, dung lượng và giá thành. Trên thực tế, sự đánh đổi này phổ biến ở mọi lĩnh vực công nghiệp, đòi hỏi chúng ta phải tìm ra điểm cân bằng tối ưu giữa các ưu thế và hạn chế khác nhau.

Tóm lại, **ổ đĩa cứng dùng để lưu trữ lâu dài lượng lớn dữ liệu, RAM dùng để lưu trữ tạm thời dữ liệu đang được xử lý khi chương trình vận hành, còn bộ nhớ đệm Cache dùng để lưu trữ dữ liệu và các lệnh thường xuyên được truy cập**, nhằm nâng cao hiệu năng thực thi của chương trình. Cả ba phối hợp chặt chẽ với nhau để đảm bảo hệ thống máy tính vận hành hiệu quả nhất.

Như minh hoạ trong hình dưới đây, khi chương trình chạy, dữ liệu sẽ được đọc từ ổ đĩa cứng vào trong RAM để cung cấp cho CPU tính toán. Bộ nhớ đệm Cache có thể coi như một phần của CPU, **nó nạp dữ liệu một cách thông minh từ RAM**, mang lại khả năng đọc dữ liệu tốc độ cực cao cho CPU, nhờ đó nâng cao đáng kể hiệu suất thực thi của chương trình và giảm thiểu sự phụ thuộc vào bộ nhớ RAM vốn có tốc độ chậm hơn.

![Luồng lưu chuyển dữ liệu giữa ổ cứng, RAM và bộ nhớ đệm Cache](ram_and_cache.assets/computer_storage_devices.png)

## Hiệu năng bộ nhớ của cấu trúc dữ liệu

Xét về khía cạnh tận dụng không gian bộ nhớ, mảng và danh sách liên kết đều có những ưu điểm và hạn chế riêng:

Một mặt, **bộ nhớ là tài nguyên có hạn và cùng một vùng nhớ không thể được chia sẻ đồng thời bởi nhiều chương trình**, do đó chúng ta mong muốn cấu trúc dữ liệu có thể tận dụng không gian một cách hiệu quả nhất có thể. Các phần tử mảng được sắp xếp san sát nhau, không cần tốn thêm không gian để lưu trữ tham chiếu (con trỏ) giữa các nút như danh sách liên kết, vì vậy hiệu quả không gian cao hơn. Tuy nhiên, mảng đòi hỏi phải cấp phát một khối không gian bộ nhớ liên tục đủ lớn ngay từ đầu, điều này có thể dẫn đến lãng phí bộ nhớ, và việc mở rộng dung lượng mảng cũng đòi hỏi thêm chi phí thời gian và không gian. Ngược lại, danh sách liên kết cấp phát và thu hồi bộ nhớ động theo từng đơn vị "nút", mang lại độ linh hoạt cao hơn nhiều.

Mặt khác, trong quá trình chương trình vận hành, **việc liên tục xin cấp phát và giải phóng bộ nhớ sẽ khiến mức độ phân mảnh của bộ nhớ trống ngày càng tăng cao**, từ đó làm giảm hiệu quả tận dụng bộ nhớ. Nhờ phương thức lưu trữ liên tục, mảng tương đối ít gây phân mảnh bộ nhớ hơn. Trái lại, các phần tử của danh sách liên kết được lưu trữ phân tán, qua các thao tác chèn và xoá thường xuyên sẽ rất dễ gây ra hiện tượng phân mảnh bộ nhớ.

## Hiệu năng bộ nhớ đệm của cấu trúc dữ liệu

Mặc dù bộ nhớ đệm Cache có dung lượng nhỏ hơn rất nhiều so với RAM, nhưng tốc độ của nó lại nhanh hơn RAM rất nhiều và đóng vai trò mang tính quyết định đối với tốc độ thực thi của chương trình. Do dung lượng bộ nhớ đệm có hạn và chỉ có thể lưu một phần nhỏ dữ liệu thường xuyên truy cập, nên khi CPU cố gắng truy cập dữ liệu không có sẵn trong bộ nhớ đệm, hiện tượng <u>trượt bộ nhớ đệm (cache miss)</u> sẽ xảy ra, lúc này CPU buộc phải nạp dữ liệu cần thiết từ bộ nhớ RAM có tốc độ chậm hơn.

Rõ ràng, **số lần "trượt bộ nhớ đệm" càng ít thì hiệu suất đọc ghi dữ liệu của CPU càng cao**, và hiệu năng chương trình càng tốt. Chúng ta gọi tỷ lệ dữ liệu mà CPU lấy thành công từ bộ nhớ đệm là <u>tỷ lệ trúng bộ nhớ đệm (cache hit rate)</u>, chỉ số này thường được dùng để đo lường hiệu năng của bộ nhớ đệm.

Để đạt được hiệu năng cao nhất có thể, bộ nhớ đệm sẽ áp dụng các cơ chế nạp dữ liệu sau:

- **Đường truyền dòng đệm (Cache line)**: Bộ nhớ đệm không lưu trữ và nạp dữ liệu theo từng byte đơn lẻ, mà lấy dòng đệm (cache line) làm đơn vị nạp. So với truyền tải từng byte riêng lẻ, hình thức truyền theo dòng đệm có hiệu năng cao hơn nhiều.
- **Cơ chế nạp trước (Prefetching)**: Bộ xử lý sẽ cố gắng dự đoán quy luật truy cập dữ liệu (chẳng hạn truy cập tuần tự, nhảy cách quãng với bước cố định, v.v.) và dựa theo quy luật đó để nạp trước dữ liệu vào bộ nhớ đệm, qua đó nâng cao tỷ lệ trúng.
- **Tính cục bộ không gian (Spatial locality)**: Nếu một mẩu dữ liệu được truy cập, thì các dữ liệu nằm gần nó cũng rất có khả năng sẽ được truy cập trong thời gian ngắn sắp tới. Vì vậy khi nạp một dữ liệu nào đó, bộ nhớ đệm cũng sẽ đồng thời nạp luôn các dữ liệu lân cận để nâng cao tỷ lệ trúng.
- **Tính cục bộ thời gian (Temporal locality)**: Nếu một mẩu dữ liệu được truy cập, thì rất có khả năng nó sẽ được truy cập lại nhiều lần trong tương lai gần. Bộ nhớ đệm tận dụng nguyên lý này bằng cách giữ lại dữ liệu vừa truy cập gần đây nhất để tăng tỷ lệ trúng.

Trên thực tế, **mảng và danh sách liên kết có hiệu quả tận dụng bộ nhớ đệm hoàn toàn khác nhau**, thể hiện chủ yếu ở các khía cạnh sau:

- **Dung lượng chiếm dụng**: Phần tử danh sách liên kết chiếm nhiều dung lượng hơn phần tử mảng, dẫn đến lượng dữ liệu hữu ích chứa được trong bộ nhớ đệm ít hơn.
- **Dòng đệm (Cache line)**: Dữ liệu của danh sách liên kết nằm phân tán khắp nơi trong bộ nhớ, trong khi bộ nhớ đệm lại nạp "theo từng dòng", do đó tỷ lệ nạp phải dữ liệu không dùng đến sẽ cao hơn.
- **Cơ chế nạp trước**: Quy luật truy cập dữ liệu của mảng có "tính dự đoán" cao hơn nhiều so với danh sách liên kết, giúp hệ thống dễ dàng đoán đúng dữ liệu sắp được nạp tiếp theo.
- **Tính cục bộ không gian**: Mảng được lưu trữ trong một khoảng không gian bộ nhớ tập trung liên tục, do đó dữ liệu nằm cạnh dữ liệu vừa được nạp sẽ có khả năng rất cao sắp được truy cập tới.

Nhìn chung, **mảng có tỷ lệ trúng bộ nhớ đệm cao hơn, vì vậy hiệu năng thao tác của nó thường vượt trội hơn so với danh sách liên kết**. Điều này lý giải tại sao khi giải các bài toán thuật toán, các cấu trúc dữ liệu hiện thực dựa trên mảng thường được ưa chuộng hơn.

Cần lưu ý rằng, **hiệu năng bộ nhớ đệm cao không đồng nghĩa với việc mảng sẽ vượt trội hơn danh sách liên kết trong mọi trường hợp**. Trong ứng dụng thực tế, việc lựa chọn cấu trúc dữ liệu nào nên căn cứ vào nhu cầu cụ thể. Ví dụ, cả mảng và danh sách liên kết đều có thể hiện thực cấu trúc dữ liệu "ngăn xếp" (sẽ tìm hiểu chi tiết ở chương sau), nhưng chúng phù hợp với các ngữ cảnh khác nhau:

- Khi làm các bài tập thuật toán, chúng ta thường có xu hướng chọn ngăn xếp hiện thực bằng mảng vì nó mang lại hiệu năng thao tác cao hơn và khả năng truy cập ngẫu nhiên, cái giá phải trả chỉ là cần phân bổ sẵn một lượng bộ nhớ nhất định cho mảng.
- Nếu lượng dữ liệu cực lớn, tính biến động rất cao, khó ước lượng trước kích thước tối đa của ngăn xếp, thì ngăn xếp hiện thực bằng danh sách liên kết sẽ thích hợp hơn. Danh sách liên kết có thể lưu trữ lượng lớn dữ liệu phân tán ở các vùng nhớ khác nhau và tránh được chi phí phát sinh khi phải mở rộng dung lượng mảng.
