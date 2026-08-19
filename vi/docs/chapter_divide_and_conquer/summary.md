# Tóm tắt

### Điểm mấu chốt cần nhớ

- Chia để trị là một chiến lược thiết kế thuật toán phổ biến, bao gồm hai giai đoạn: chia (phân chia) và trị (hợp nhất), thường được hiện thực dựa trên đệ quy.
- Các tiêu chí để nhận biết một bài toán chia để trị bao gồm: bài toán có thể phân rã hay không, các bài toán con có độc lập hay không, và lời giải của các bài toán con có thể hợp nhất được hay không.
- Sắp xếp trộn là ứng dụng tiêu biểu của chiến lược chia để trị, nó đệ quy chia đôi mảng thành hai mảng con có độ dài bằng nhau cho đến khi chỉ còn lại một phần tử thì bắt đầu gộp từng tầng lại, từ đó hoàn thành việc sắp xếp.
- Đưa vào chiến lược chia để trị thường giúp nâng cao hiệu năng thuật toán. Một mặt, chiến lược chia để trị làm giảm số lượng thao tác; mặt khác, sau khi chia để trị rất có lợi cho việc tối ưu hoá tính toán song song của hệ thống.
- Chia để trị vừa có thể giải quyết nhiều bài toán thuật toán, vừa được ứng dụng rộng rãi trong thiết kế thuật toán và cấu trúc dữ liệu, có thể bắt gặp bóng dáng của nó ở khắp mọi nơi.
- So với tìm kiếm vét cạn, tìm kiếm thích ứng có hiệu năng cao hơn. Các thuật toán tìm kiếm có độ phức tạp thời gian $O(\log n)$ thường được hiện thực dựa trên chiến lược chia để trị.
- Tìm kiếm nhị phân là một ứng dụng tiêu biểu khác của chia để trị, nó không chứa bước hợp nhất lời giải của các bài toán con. Chúng ta có thể hiện thực tìm kiếm nhị phân thông qua chia để trị bằng đệ quy.
- Trong bài toán dựng cây nhị phân, việc dựng cây (bài toán ban đầu) có thể chia thành dựng cây con trái và cây con phải (các bài toán con), điều này có thể thực hiện thông qua việc phân chia các khoảng chỉ số trong duyệt tiền thứ tự và duyệt trung thứ tự.
- Trong bài toán tháp Hà Nội, một bài toán có quy mô $n$ có thể chia thành hai bài toán con quy mô $n-1$ và một bài toán con quy mô $1$ 。Sau khi giải quyết ba bài toán con này theo đúng thứ tự, bài toán ban đầu cũng theo đó mà được giải quyết xong.
