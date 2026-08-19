---
comments: true
icon: material/rocket-launch-outline
---

# Lời mở đầu

Vài năm trước, tôi đã chia sẻ loạt bài giải cho bộ đề "Kiếm chỉ Offer" (*Sword for Offer*) trên LeetCode và nhận được rất nhiều sự khích lệ cũng như ủng hộ từ độc giả. Trong quá trình giao lưu với các bạn độc giả, câu hỏi tôi thường gặp nhất là "làm thế nào để nhập môn thuật toán?". Dần dần, tôi nảy sinh niềm hứng thú sâu sắc với câu hỏi này.

Lao đầu vào luyện đề dường như là phương pháp phổ biến nhất: đơn giản, trực diện và hiệu quả. Tuy nhiên, việc luyện đề giống như chơi trò "Dò mìn" (*Minesweeper*): người có khả năng tự học tốt có thể thuận lợi gỡ từng quả mìn, còn người thiếu nền tảng rất dễ bị nổ cho tơi tả và dần chùn bước trước những thất bại. Đọc hết giáo trình cũng là một cách tiếp cận quen thuộc, nhưng đối với những ai đang chuẩn bị tìm việc, luận văn tốt nghiệp, nộp CV, chuẩn bị cho các bài thi viết và phỏng vấn đã tiêu tốn phần lớn sức lực, việc "gặm nhấm" những cuốn sách dày cộm thường trở thành một thử thách đầy gian nan.

Nếu bạn cũng đang gặp phải những băn khoăn tương tự, thật may mắn khi cuốn sách này đã "tìm" đến bạn. Cuốn sách này chính là câu trả lời của tôi cho câu hỏi đó — dù có thể chưa phải là lời giải tối ưu, nhưng ít nhất cũng là một nỗ lực đầy tâm huyết. Dù cuốn sách không thể giúp bạn trực tiếp nhận ngay được Offer việc làm, nhưng nó sẽ dẫn lối bạn khám phá "bản đồ tri thức" của cấu trúc dữ liệu và giải thuật, giúp bạn nhận biết hình dạng, kích thước cũng như vị trí phân bố của từng loại "mìn", đồng thời trang bị cho bạn các "phương pháp gỡ mìn" khác nhau. Khi đã nắm vững những kỹ năng này, tôi tin rằng bạn có thể tự tin hơn khi luyện đề và đọc các tài liệu chuyên ngành, từng bước xây dựng nên một hệ thống kiến thức hoàn chỉnh cho riêng mình.

Tôi rất tâm đắc với câu nói của Giáo sư Feynman: *"Knowledge isn't free. You have to pay attention."* (Tri thức không miễn phí. Bạn phải trả bằng sự chú ý). Theo nghĩa đó, cuốn sách này không hoàn toàn "miễn phí". Để không phụ "sự chú ý" quý giá mà bạn dành cho cuốn sách, tôi sẽ dốc hết sức mình, dành trọn "sự chú ý" lớn nhất để hoàn thành tác phẩm này.

Tôi tự biết học vấn và tài năng của mình còn nông cạn. Dù nội dung sách đã được trau chuốt qua một thời gian, chắc chắn vẫn không tránh khỏi nhiều thiếu sót. Tôi rất mong nhận được những lời phê bình, chỉ giáo quý báu từ các thầy cô và bạn đọc.

![Hello Thuật toán](../assets/covers/chapter_hello_algo.jpg){ class="cover-image" }

<div style="text-align: center;">
    <h2 style="margin-top: 0.8em; margin-bottom: 0.8em;">Hello, Thuật toán!</h2>
</div>

Sự xuất hiện của máy tính đã mang lại những biến đổi to lớn cho thế giới. Nhờ vào năng lực tính toán tốc độ cao và khả năng lập trình vượt trội, máy tính đã trở thành phương tiện lý tưởng để thực thi thuật toán và xử lý dữ liệu. Dù là đồ hoạ sống động trong trò chơi điện tử, các quyết định thông minh trong xe tự hành, hay những ván cờ tuyệt đỉnh của AlphaGo, những màn tương tác tự nhiên của ChatGPT, tất cả các ứng dụng này đều là những màn trình diễn kỳ diệu của thuật toán trên máy tính.

Trên thực tế, trước khi máy tính ra đời, thuật toán và cấu trúc dữ liệu đã luôn hiện diện ở mọi ngóc ngách của thế giới. Các thuật toán thời kỳ đầu tương đối đơn giản, chẳng hạn như phương pháp đếm hay các bước chế tác công cụ thời cổ đại. Cùng với sự tiến bộ của văn minh nhân loại, các thuật toán dần trở nên tinh vi và phức tạp hơn. Từ tay nghề khéo léo tuyệt luân của người thợ thủ công, đến các sản phẩm công nghiệp giải phóng sức lao động, cho tới những quy luật khoa học vận hành vũ trụ — đằng sau hầu như mọi điều bình dị hay kỳ vĩ đều ẩn chứa tư tưởng thuật toán tinh tế.

Tương tự như vậy, cấu trúc dữ liệu cũng hiện diện ở khắp mọi nơi: từ mạng xã hội rộng lớn cho đến mạng lưới tàu điện ngầm thu nhỏ, nhiều hệ thống đều có thể được mô hình hoá dưới dạng "đồ thị"; từ một quốc gia cho đến một gia đình nhỏ, các hình thức tổ chức chủ yếu của xã hội đều mang đặc trưng của "cây"; quần áo mùa đông giống như "ngăn xếp", món mặc vào đầu tiên sẽ là món cởi ra sau cùng; ống đựng quả cầu lông lại tựa như "hàng đợi", cho vào ở một đầu và lấy ra ở đầu kia; còn cuốn từ điển hệt như một "bảng băm", cho phép tra cứu nhanh từ mục cần tìm.

Cuốn sách này hướng tới mục tiêu thông qua các hình động minh hoạ trực quan, dễ hiểu cùng các đoạn mã ví dụ có thể chạy được, giúp độc giả nắm bắt được các khái niệm cốt lõi của thuật toán và cấu trúc dữ liệu, đồng thời có thể tự tay hiện thực hoá chúng bằng lập trình. Trên nền tảng đó, cuốn sách nỗ lực hé mở sự hiện diện sống động của thuật toán trong thế giới phức tạp và tôn vinh vẻ đẹp của thuật toán. Hy vọng cuốn sách này sẽ mang lại nhiều điều bổ ích cho bạn!
