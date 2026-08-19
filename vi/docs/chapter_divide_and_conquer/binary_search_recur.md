# Chiến lược tìm kiếm chia để trị

Chúng ta đã học rằng các thuật toán tìm kiếm được chia làm hai loại lớn:

- **Tìm kiếm vét cạn**: Thực hiện thông qua việc duyệt qua cấu trúc dữ liệu, có độ phức tạp thời gian là $O(n)$.
- **Tìm kiếm thích ứng**: Tận dụng hình thức tổ chức dữ liệu đặc thù hoặc thông tin tiên nghiệm, độ phức tạp thời gian có thể đạt tới $O(\log n)$ thậm chí là $O(1)$.

Trên thực tế, **các thuật toán tìm kiếm có độ phức tạp thời gian $O(\log n)$ thường được hiện thực dựa trên chiến lược chia để trị**, chẳng hạn như tìm kiếm nhị phân và cây.

- Mỗi bước của tìm kiếm nhị phân đều phân rã bài toán (tìm kiếm phần tử mục tiêu trong mảng) thành một bài toán con nhỏ hơn (tìm kiếm phần tử mục tiêu trong một nửa mảng), quá trình này diễn ra liên tục cho đến khi mảng rỗng hoặc tìm thấy phần tử mục tiêu thì dừng lại.
- Cây là đại diện tiêu biểu cho tư tưởng chia để trị. Trong các cấu trúc dữ liệu như cây tìm kiếm nhị phân, cây AVL, đống, v.v., độ phức tạp thời gian của các thao tác khác nhau đều là $O(\log n)$.

Chiến lược chia để trị của tìm kiếm nhị phân được thể hiện như sau:

- **Bài toán có thể phân rã**: Tìm kiếm nhị phân đệ quy chia bài toán ban đầu (tìm kiếm trong mảng) thành bài toán con (tìm kiếm trong một nửa mảng), điều này đạt được thông qua việc so sánh phần tử ở giữa với phần tử mục tiêu.
- **Các bài toán con mang tính độc lập**: Trong tìm kiếm nhị phân, mỗi vòng chỉ xử lý một bài toán con duy nhất, nó không chịu sự ảnh hưởng của các bài toán con khác.
- **Lời giải của bài toán con không cần hợp nhất**: Tìm kiếm nhị phân nhằm mục đích tìm ra một phần tử cụ thể, do đó không cần phải gộp lời giải của các bài toán con lại. Khi bài toán con được giải quyết thì bài toán ban đầu cũng đồng thời được giải quyết.

Chia để trị có thể nâng cao hiệu năng tìm kiếm, về bản chất là vì tìm kiếm vét cạn mỗi vòng chỉ loại trừ được một lựa chọn, **trong khi tìm kiếm chia để trị mỗi vòng có thể loại trừ được tới một nửa số lựa chọn**.

### Hiện thực tìm kiếm nhị phân dựa trên chia để trị

Trong các chương trước, tìm kiếm nhị phân được hiện thực dựa trên suy diễn lặp (iteration). Bây giờ chúng ta sẽ hiện thực nó dựa trên chia để trị (đệ quy).

!!! question

    Cho một mảng đã sắp xếp `nums` có độ dài $n$, trong đó tất cả các phần tử đều là duy nhất, hãy tìm kiếm phần tử `target`.

Xét từ góc độ chia để trị, chúng ta ký hiệu bài toán con ứng với khoảng tìm kiếm $[i, j]$ là $f(i, j)$.

Lấy bài toán ban đầu $f(0, n-1)$ làm điểm xuất phát, thực hiện tìm kiếm nhị phân qua các bước sau:

1. Tính toán trung điểm $m$ của khoảng tìm kiếm $[i, j]$, dựa vào đó để loại trừ một nửa khoảng tìm kiếm.
2. Đệ quy giải bài toán con có quy mô giảm đi một nửa, có thể là $f(i, m-1)$ hoặc $f(m+1, j)$.
3. Lặp lại bước `1.` và bước `2.`, cho đến khi tìm thấy `target` hoặc khoảng tìm kiếm trở nên rỗng thì trả về.

Hình dưới đây minh hoạ quá trình chia để trị khi tìm kiếm nhị phân phần tử số $6$ trong mảng.

![Quá trình chia để trị của tìm kiếm nhị phân](binary_search_recur.assets/binary_search_recur.png)

Trong mã nguồn hiện thực, chúng ta khai báo một hàm đệ quy `dfs()` để giải bài toán $f(i, j)$:

```src
[file]{binary_search_recur}-[class]{}-[func]{binary_search}
```
