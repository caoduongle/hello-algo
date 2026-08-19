# Đánh giá hiệu năng thuật toán

Trong thiết kế thuật toán, chúng ta tuần tự hướng tới hai cấp độ mục tiêu sau:

1. **Tìm ra lời giải cho bài toán**: Thuật toán cần tìm được nghiệm đúng của bài toán một cách tin cậy trong phạm vi đầu vào quy định.
2. **Tìm kiếm lời giải tối ưu**: Một bài toán có thể tồn tại nhiều cách giải khác nhau, và chúng ta mong muốn tìm ra thuật toán có hiệu năng cao nhất có thể.

Nói cách khác, trên tiền đề giải quyết được bài toán, hiệu năng của thuật toán đã trở thành tiêu chí đánh giá chủ yếu để đo lường mức độ tối ưu của thuật toán. Tiêu chí này bao gồm hai chiều kích:

- **Hiệu năng thời gian**: Độ dài thời gian thực thi của thuật toán.
- **Hiệu năng không gian**: Dung lượng không gian bộ nhớ mà thuật toán chiếm dụng.

Tóm lại, **mục tiêu của chúng ta là thiết kế các cấu trúc dữ liệu và giải thuật "vừa nhanh vừa tiết kiệm"**. Việc đánh giá hiệu quả hiệu năng thuật toán đóng vai trò vô cùng cốt yếu, bởi chỉ khi làm được điều này, chúng ta mới có thể so sánh giữa các thuật toán với nhau, từ đó định hướng cho quá trình thiết kế và tối ưu hoá thuật toán.

Các phương pháp đánh giá hiệu năng chủ yếu chia làm hai loại: kiểm thử thực tế và ước lượng lý thuyết.

## Kiểm thử thực tế

Giả sử hiện tại chúng ta có thuật toán `A` và thuật toán `B`, cả hai đều giải quyết cùng một bài toán, và chúng ta cần so sánh hiệu năng giữa hai thuật toán này. Phương pháp trực tiếp nhất là dùng một chiếc máy tính, chạy cả hai thuật toán, đồng thời giám sát và ghi lại thời gian thực thi cũng như mức chiếm dụng bộ nhớ của chúng. Cách đánh giá này phản ánh đúng tình hình thực tế, nhưng lại tồn tại những hạn chế rất lớn.

Một mặt, **rất khó loại bỏ các yếu tố gây nhiễu từ môi trường kiểm thử**. Cấu hình phần cứng sẽ ảnh hưởng trực tiếp đến hiệu năng của thuật toán. Chẳng hạn, một thuật toán có mức độ song song hoá cao sẽ thích hợp hơn khi chạy trên CPU đa nhân; một thuật toán thực hiện nhiều thao tác bộ nhớ chuyên sâu sẽ thể hiện tốt hơn trên bộ nhớ RAM hiệu năng cao. Nghĩa là, kết quả kiểm thử của một thuật toán trên các dòng máy khác nhau có thể không đồng nhất. Điều này đồng nghĩa với việc chúng ta phải kiểm thử trên rất nhiều loại máy móc và thống kê hiệu năng trung bình, một việc làm hoàn toàn phi thực tế.

Mặt khác, **việc triển khai kiểm thử toàn diện tiêu tốn rất nhiều tài nguyên**. Khi lượng dữ liệu đầu vào thay đổi, thuật toán sẽ thể hiện các mức hiệu năng khác nhau. Ví dụ, khi lượng dữ liệu đầu vào nhỏ, thời gian thực thi của thuật toán `A` ngắn hơn thuật toán `B`; nhưng khi lượng dữ liệu đầu vào lớn, kết quả kiểm thử có thể hoàn toàn đảo ngược. Do đó, để đưa ra kết luận có sức thuyết phục, chúng ta cần phải kiểm thử với đủ mọi quy mô dữ liệu đầu vào, và điều này đòi hỏi một lượng tài nguyên tính toán khổng lồ.

## Ước lượng lý thuyết

Do phương pháp kiểm thử thực tế tồn tại nhiều hạn chế lớn, chúng ta có thể cân nhắc việc chỉ thông qua một số phép tính toán lý thuyết để đánh giá hiệu năng của thuật toán. Phương pháp ước lượng này được gọi là <u>phân tích độ phức tạp tiệm cận (asymptotic complexity analysis)</u>, gọi tắt là <u>phân tích độ phức tạp</u>.

Phân tích độ phức tạp có thể phản ánh mối quan hệ giữa tài nguyên thời gian và không gian cần thiết để thuật toán thực thi với quy mô dữ liệu đầu vào. **Nó mô tả xu hướng tăng trưởng của thời gian và không gian cần thiết để thuật toán thực thi khi quy mô dữ liệu đầu vào tăng lên**. Định nghĩa này có phần hơi trừu tượng, chúng ta có thể chia thành ba điểm mấu chốt để dễ hiểu hơn:

- "Tài nguyên thời gian và không gian" lần lượt tương ứng với <u>độ phức tạp thời gian (time complexity)</u> và <u>độ phức tạp không gian (space complexity)</u>.
- "Khi quy mô dữ liệu đầu vào tăng lên" biểu thị rằng độ phức tạp phản ánh mối quan hệ giữa hiệu năng thực thi của thuật toán và quy mô của dữ liệu đầu vào.
- "Xu hướng tăng trưởng của thời gian và không gian" thể hiện rằng phân tích độ phức tạp không tập trung vào giá trị cụ thể của thời gian chạy hay dung lượng bộ nhớ bị chiếm dụng, mà quan tâm đến "tốc độ" tăng trưởng của thời gian hoặc không gian đó diễn ra nhanh hay chậm.

**Phân tích độ phức tạp khắc phục trọn vẹn các nhược điểm của phương pháp kiểm thử thực tế**, thể hiện ở các khía cạnh sau:

- Không cần thực sự chạy mã nguồn, thân thiện hơn với môi trường và tiết kiệm năng lượng.
- Hoàn toàn độc lập với môi trường kiểm thử, kết quả phân tích có thể áp dụng cho mọi nền tảng thực thi.
- Có thể phản ánh hiệu năng thuật toán dưới các quy mô dữ liệu khác nhau, đặc biệt là hiệu năng khi xử lý lượng dữ liệu lớn.

!!! tip

    Nếu bạn vẫn còn cảm thấy băn khoăn về khái niệm độ phức tạp, xin đừng lo lắng, chúng ta sẽ tìm hiểu chi tiết trong các phần tiếp theo của chương này.

Phân tích độ phức tạp cung cấp cho chúng ta một "thước đo" chuẩn xác để đánh giá hiệu năng thuật toán, giúp chúng ta định lượng được tài nguyên thời gian và không gian cần thiết khi thực thi một thuật toán cụ thể, cũng như so sánh hiệu năng giữa các thuật toán với nhau.

Độ phức tạp là một khái niệm toán học, có thể khá trừu tượng đối với người mới bắt đầu và độ khó học tập tương đối cao. Đứng từ góc độ này, phân tích độ phức tạp có vẻ không phải là nội dung thích hợp nhất để giới thiệu đầu tiên. Tuy nhiên, khi thảo luận về đặc điểm của bất kỳ cấu trúc dữ liệu hay thuật toán nào, chúng ta khó lòng tránh khỏi việc phải phân tích tốc độ thực thi và mức độ sử dụng không gian bộ nhớ của chúng.

Tóm lại, trước khi đi sâu vào học cấu trúc dữ liệu và giải thuật, bạn **nên xây dựng cho mình những hiểu biết sơ bộ về phân tích độ phức tạp trước, để từ đó có thể tự mình hoàn thành việc phân tích độ phức tạp cho các thuật toán đơn giản**.
