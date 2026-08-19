# Thuật toán sắp xếp

<u>Thuật toán sắp xếp (sorting algorithm)</u> được dùng để sắp xếp một tập hợp dữ liệu theo một thứ tự nhất định. Thuật toán sắp xếp có ứng dụng rất rộng rãi, bởi vì dữ liệu có thứ tự thường có thể được tìm kiếm, phân tích và xử lý với hiệu năng cao hơn nhiều.

Như hình dưới đây, kiểu dữ liệu trong thuật toán sắp xếp có thể là số nguyên, số thực, ký tự hoặc chuỗi ký tự, v.v. Quy tắc so sánh khi sắp xếp có thể thiết lập tuỳ theo nhu cầu, chẳng hạn như độ lớn của số, thứ tự mã ASCII của ký tự hoặc quy tắc tuỳ biến.

![Ví dụ về kiểu dữ liệu và quy tắc sắp xếp](sorting_algorithm.assets/sorting_examples.png)

## Các tiêu chí đánh giá

**Hiệu năng thực thi**: Chúng ta mong muốn độ phức tạp thời gian của thuật toán sắp xếp càng thấp càng tốt, và tổng số lượng thao tác càng ít càng tốt (hệ số hằng số trong độ phức tạp thời gian nhỏ đi). Đối với lượng dữ liệu lớn, hiệu năng thực thi trở nên đặc biệt quan trọng.

**Tính tại chỗ**: Đúng như tên gọi, <u>sắp xếp tại chỗ (in-place sort)</u> thực hiện sắp xếp bằng cách thao tác trực tiếp trên mảng ban đầu mà không cần nhờ đến mảng phụ trợ, nhờ đó tiết kiệm bộ nhớ. Thông thường, sắp xếp tại chỗ có số lượng thao tác di chuyển dữ liệu ít hơn và tốc độ chạy cũng nhanh hơn.

**Tính ổn định**: <u>Sắp xếp ổn định (stable sort)</u> sau khi hoàn thành sắp xếp, thứ tự tương đối của các phần tử có giá trị bằng nhau trong mảng không bị thay đổi.

Sắp xếp ổn định là điều kiện bắt buộc trong các tình huống sắp xếp nhiều cấp độ (multi-level sorting). Giả sử chúng ta có một bảng lưu thông tin sinh viên, trong đó cột 1 và cột 2 lần lượt là tên và tuổi. Trong tình huống này, <u>sắp xếp không ổn định (unstable sort)</u> có thể khiến tính có thứ tự của dữ liệu đầu vào bị mất đi:

```shell
# Dữ liệu đầu vào đã được sắp xếp theo tên
# (name, age)
  ('A', 19)
  ('B', 18)
  ('C', 21)
  ('D', 19)
  ('E', 23)

# Giả sử dùng thuật toán sắp xếp không ổn định để sắp xếp danh sách theo tuổi,
# trong kết quả vị trí tương đối giữa ('D', 19) và ('A', 19) bị thay đổi,
# tính chất dữ liệu đầu vào đã sắp xếp theo tên bị mất đi
  ('B', 18)
  ('D', 19)
  ('A', 19)
  ('C', 21)
  ('E', 23)
```

**Tính thích ứng**: <u>Sắp xếp thích ứng (adaptive sort)</u> có khả năng tận dụng thông tin thứ tự đã có sẵn của dữ liệu đầu vào để giảm thiểu khối lượng tính toán, đạt được hiệu năng thời gian tốt hơn. Độ phức tạp thời gian tốt nhất của các thuật toán sắp xếp thích ứng thường vượt trội hơn so với độ phức tạp thời gian trung bình.

**Có dựa trên so sánh hay không**: <u>Sắp xếp dựa trên so sánh (comparison sort)</u> dựa vào các toán tử so sánh ($<$, $=$, $>$) để xác định thứ tự tương đối giữa các phần tử, từ đó sắp xếp toàn bộ mảng; chặn dưới của độ phức tạp thời gian trong trường hợp xấu nhất của nó là $\Omega(n \log n)$. Trong khi đó <u>sắp xếp không dựa trên so sánh (non-comparison sort)</u> không sử dụng các toán tử so sánh, độ phức tạp thời gian có thể đạt tới $O(n)$, nhưng tính tổng quát của nó tương đối hạn chế.

## Thuật toán sắp xếp lý tưởng

**Chạy nhanh, tại chỗ, ổn định, thích ứng và tính tổng quát cao**. Rõ ràng, cho đến nay vẫn chưa tìm thấy bất kỳ thuật toán sắp xếp nào hội tụ đầy đủ tất cả các đặc tính nêu trên. Do đó, khi lựa chọn thuật toán sắp xếp, chúng ta cần phải căn cứ vào đặc điểm dữ liệu cụ thể và yêu cầu của bài toán để đưa ra quyết định.

Tiếp theo, chúng ta sẽ cùng nhau tìm hiểu các thuật toán sắp xếp khác nhau, và phân tích ưu nhược điểm của từng thuật toán dựa trên các tiêu chí đánh giá ở trên.
