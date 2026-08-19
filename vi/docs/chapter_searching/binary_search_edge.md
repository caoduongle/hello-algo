# Biên tìm kiếm nhị phân

## Tìm kiếm biên trái

!!! question

    Cho một mảng đã sắp xếp `nums` có độ dài $n$, trong đó có thể chứa các phần tử trùng lặp. Hãy trả về chỉ số của phần tử `target` ngoài cùng bên trái trong mảng. Nếu mảng không chứa phần tử này, trả về $-1$.

Nhớ lại phương pháp tìm kiếm điểm chèn bằng tìm kiếm nhị phân, sau khi tìm kiếm kết thúc $i$ sẽ trỏ tới `target` ngoài cùng bên trái, **do đó việc tìm kiếm điểm chèn về bản chất chính là tìm kiếm chỉ số của `target` ngoài cùng bên trái**.

Cân nhắc hiện thực tìm kiếm biên trái thông qua hàm tìm điểm chèn. Xin lưu ý rằng trong mảng có thể không chứa `target`, tình huống này có thể dẫn tới hai kết quả sau:

- Chỉ số điểm chèn $i$ vượt quá giới hạn mảng.
- Phần tử `nums[i]` không bằng `target`.

Khi gặp phải hai tình huống trên, chúng ta chỉ cần trực tiếp trả về $-1$ là được. Mã nguồn như sau:

```src
[file]{binary_search_edge}-[class]{}-[func]{binary_search_left_edge}
```

## Tìm kiếm biên phải

Vậy làm thế nào để tìm kiếm `target` ngoài cùng bên phải? Cách tiếp cận trực tiếp nhất là sửa đổi mã nguồn, thay thế thao tác thu hẹp con trỏ trong trường hợp `nums[m] == target`. Mã nguồn phần này được lược bỏ, bạn đọc quan tâm có thể tự mình hiện thực.

Dưới đây chúng tôi giới thiệu hai phương pháp khéo léo hơn.

### Tái sử dụng hàm tìm kiếm biên trái

Trên thực tế, chúng ta có thể tận dụng hàm tìm kiếm phần tử ngoài cùng bên trái để tìm kiếm phần tử ngoài cùng bên phải, phương pháp cụ thể là: **chuyển đổi việc tìm kiếm `target` ngoài cùng bên phải thành việc tìm kiếm `target + 1` ngoài cùng bên trái**.

Như minh hoạ trong hình dưới đây, sau khi tìm kiếm xong, con trỏ $i$ trỏ tới `target + 1` ngoài cùng bên trái (nếu có tồn tại), còn $j$ trỏ tới `target` ngoài cùng bên phải, **do đó chỉ cần trả về $j$ là xong**.

![Chuyển đổi tìm kiếm biên phải thành tìm kiếm biên trái](binary_search_edge.assets/binary_search_right_edge_by_left_edge.png)

Xin lưu ý rằng điểm chèn trả về là $i$, vì vậy cần phải trừ đi $1$ để thu được $j$:

```src
[file]{binary_search_edge}-[class]{}-[func]{binary_search_right_edge}
```

### Chuyển đổi thành bài toán tìm kiếm phần tử

Chúng ta biết rằng khi mảng không chứa `target`, cuối cùng $i$ và $j$ sẽ lần lượt trỏ tới phần tử đầu tiên lớn hơn `target` và phần tử tận cùng bên phải nhỏ hơn `target`.

Do đó, như minh hoạ trong hình dưới đây, chúng ta có thể dựng nên một phần tử không tồn tại trong mảng để phục vụ cho việc tìm kiếm biên trái và biên phải:

- Tìm `target` ngoài cùng bên trái: Có thể chuyển đổi thành việc tìm kiếm `target - 0.5`, và trả về con trỏ $i$.
- Tìm `target` ngoài cùng bên phải: Có thể chuyển đổi thành việc tìm kiếm `target + 0.5`, và trả về con trỏ $j$.

![Chuyển đổi tìm kiếm biên thành tìm kiếm phần tử](binary_search_edge.assets/binary_search_edge_by_element.png)

Mã nguồn phần này được lược bỏ, hai điểm sau đây rất đáng lưu ý:

- Mảng đã cho không chứa số thập phân, điều này đồng nghĩa với việc chúng ta không cần bận tâm đến việc xử lý trường hợp bằng nhau.
- Vì phương pháp này đưa thêm số thập phân vào, nên cần phải đổi biến `target` trong hàm thành kiểu số thực dấu phẩy động (Python không cần thay đổi).
