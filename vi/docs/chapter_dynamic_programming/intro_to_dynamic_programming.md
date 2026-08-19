# Nhập môn quy hoạch động

<u>Quy hoạch động (dynamic programming)</u> là một mô thức thuật toán quan trọng, nó phân rã một bài toán thành một chuỗi các bài toán con nhỏ hơn, và thông qua việc lưu trữ lời giải của các bài toán con để tránh tính toán trùng lặp, từ đó nâng cao vượt bậc hiệu năng thời gian.

Trong phần này, chúng ta xuất phát từ một bài toán kinh điển, trước hết đưa ra cách giải bằng quay lui vét cạn, quan sát các bài toán con gối nhau (trùng lặp) bên trong nó, sau đó từng bước dẫn dắt tới cách giải quy hoạch động hiệu năng cao hơn.

!!! question "Leo cầu thang"

    Cho một chiếc cầu thang có tổng cộng $n$ bậc, mỗi bước bạn có thể bước $1$ bậc hoặc $2$ bậc, hỏi có bao nhiêu phương án để leo lên đến đỉnh cầu thang?

Như hình dưới đây, đối với cầu thang có $3$ bậc, có tổng cộng $3$ phương án để leo lên đỉnh.

![Số phương án leo lên bậc thứ 3](intro_to_dynamic_programming.assets/climbing_stairs_example.png)

Mục tiêu của bài toán này là tìm số phương án, **chúng ta có thể cân nhắc dùng quay lui để vét cạn tất cả các khả năng**. Cụ thể, hình dung việc leo cầu thang như một quá trình đưa ra lựa chọn qua nhiều vòng: xuất phát từ mặt đất, mỗi vòng chọn bước $1$ bậc hoặc $2$ bậc, mỗi khi lên tới đỉnh cầu thang thì tăng số phương án lên $1$ ，khi vượt quá đỉnh cầu thang thì cắt tỉa. Mã nguồn như sau:

```src
[file]{climbing_stairs_backtrack}-[class]{}-[func]{climbing_stairs_backtrack}
```

## Phương pháp 1: Tìm kiếm vét cạn

Thuật toán quay lui thông thường không phân rã bài toán một cách tường minh, mà coi việc giải bài toán là một chuỗi các bước ra quyết định, thông qua thử nghiệm và cắt tỉa để tìm kiếm tất cả các lời giải khả dĩ.

Chúng ta có thể thử phân tích bài toán này từ góc độ phân rã bài toán. Đặt số phương án để leo lên bậc thứ $i$ là $dp[i]$ ，khi đó $dp[i]$ chính là bài toán ban đầu, và các bài toán con của nó bao gồm:

$$
dp[i-1], dp[i-2], \dots, dp[2], dp[1]
$$

Do mỗi vòng chỉ có thể bước $1$ bậc hoặc $2$ bậc, vì vậy khi chúng ta đang đứng ở bậc thứ $i$ ，ở vòng trước đó ta chỉ có thể đứng ở bậc thứ $i - 1$ hoặc bậc thứ $i - 2$ 。Nói cách khác, chúng ta chỉ có thể bước lên bậc thứ $i$ từ bậc thứ $i - 1$ hoặc bậc thứ $i - 2$ 。

Từ đó có thể rút ra một kết luận quan trọng: **số phương án leo lên bậc thứ $i - 1$ cộng với số phương án leo lên bậc thứ $i - 2$ bằng đúng số phương án leo lên bậc thứ $i$** 。Công thức như sau:

$$
dp[i] = dp[i-1] + dp[i-2]
$$

Điều này có nghĩa là trong bài toán leo cầu thang, giữa các bài toán con tồn tại một quan hệ truy hồi (hệ thức truy hồi), **lời giải của bài toán ban đầu có thể được kiến tạo từ lời giải của các bài toán con**. Hình dưới đây minh hoạ quan hệ truy hồi này.

![Quan hệ truy hồi số phương án](intro_to_dynamic_programming.assets/climbing_stairs_state_transfer.png)

Chúng ta có thể dựa vào công thức truy hồi để đưa ra cách giải tìm kiếm vét cạn. Xuất phát từ $dp[n]$ ，**đệ quy chia nhỏ một bài toán lớn hơn thành tổng của hai bài toán nhỏ hơn**, cho đến khi chạm tới bài toán con nhỏ nhất $dp[1]$ và $dp[2]$ thì trả về. Trong đó, lời giải của bài toán con nhỏ nhất đã biết trước, tức $dp[1] = 1$ và $dp[2] = 2$ ，biểu thị leo lên bậc thứ $1$ và bậc thứ $2$ lần lượt có $1$ và $2$ phương án.

Quan sát mã nguồn dưới đây, nó cùng với mã nguồn quay lui chuẩn đều thuộc về tìm kiếm theo chiều sâu (DFS), nhưng ngắn gọn hơn nhiều:

```src
[file]{climbing_stairs_dfs}-[class]{}-[func]{climbing_stairs_dfs}
```

Hình dưới đây minh hoạ cây đệ quy do tìm kiếm vét cạn tạo thành. Đối với bài toán $dp[n]$ ，chiều sâu cây đệ quy của nó là $n$ ，độ phức tạp thời gian là $O(2^n)$ 。Bậc luỹ thừa là sự tăng trưởng bùng nổ, nếu chúng ta nhập vào một số $n$ tương đối lớn, chương trình sẽ rơi vào sự chờ đợi đằng đẵng.

![Cây đệ quy tương ứng bài toán leo cầu thang](intro_to_dynamic_programming.assets/climbing_stairs_dfs_tree.png)

Quan sát hình trên, **độ phức tạp thời gian bậc luỹ thừa là do các "bài toán con gối nhau" (overlapping subproblems) gây ra**. Ví dụ $dp[9]$ được phân rã thành $dp[8]$ và $dp[7]$ ，$dp[8]$ được phân rã thành $dp[7]$ và $dp[6]$ ，cả hai đều chứa bài toán con $dp[7]$ 。

Cứ thế tiếp tục, bên trong bài toán con lại chứa các bài toán con gối nhau nhỏ hơn, trùng lặp vô tận. Đại đa số tài nguyên tính toán đều bị lãng phí vào các bài toán con trùng lặp này.

## Phương pháp 2: Tìm kiếm có nhớ (Memoization)

Để nâng cao hiệu năng thuật toán, **chúng ta mong muốn toàn bộ các bài toán con gối nhau đều chỉ được tính toán đúng một lần**. Vì vậy, chúng ta khai báo một mảng `mem` để ghi lại lời giải của từng bài toán con, và trong quá trình tìm kiếm sẽ cắt tỉa các bài toán con gối nhau:

1. Khi lần đầu tiên tính toán $dp[i]$ ，chúng ta ghi nhận nó vào `mem[i]` để sử dụng sau này.
2. Khi lại cần tính toán $dp[i]$ ở lần tiếp theo, chúng ta có thể trực tiếp lấy kết quả từ `mem[i]` ，từ đó tránh được việc tính toán lặp lại bài toán con đó.

Mã nguồn như sau:

```src
[file]{climbing_stairs_dfs_mem}-[class]{}-[func]{climbing_stairs_dfs_mem}
```

Quan sát hình dưới đây, **sau khi áp dụng đệ quy có nhớ, tất cả các bài toán con gối nhau đều chỉ cần tính toán đúng một lần, độ phức tạp thời gian được tối ưu về $O(n)$** ，đây là một bước nhảy vọt khổng lồ.

![Cây đệ quy tương ứng của tìm kiếm có nhớ](intro_to_dynamic_programming.assets/climbing_stairs_dfs_memo_tree.png)

## Phương pháp 3: Quy hoạch động

**Tìm kiếm có nhớ là một phương pháp "từ đỉnh xuống đáy" (top-down)**: Chúng ta xuất phát từ bài toán ban đầu (nút gốc), đệ quy phân rã bài toán con lớn hơn thành các bài toán con nhỏ hơn, cho đến khi chạm tới bài toán con nhỏ nhất đã biết lời giải (nút lá). Sau đó, thông qua quay lui thu thập dần lời giải bài toán con qua từng tầng để kiến tạo nên lời giải của bài toán ban đầu.

Trái ngược với điều đó, **quy hoạch động là một phương pháp "từ đáy lên đỉnh" (bottom-up)**: Bắt đầu từ lời giải của bài toán con nhỏ nhất, suy diễn lặp để kiến tạo lời giải của các bài toán con lớn hơn, cho đến khi thu được lời giải của bài toán ban đầu.

Do quy hoạch động không chứa quá trình quay lui nên chỉ cần dùng vòng lặp để hiện thực, không cần dùng đệ quy. Trong mã nguồn dưới đây, chúng ta khởi tạo một mảng `dp` để lưu trữ lời giải của các bài toán con, nó đóng vai trò ghi nhận giống hệt mảng `mem` trong tìm kiếm có nhớ:

```src
[file]{climbing_stairs_dp}-[class]{}-[func]{climbing_stairs_dp}
```

Hình dưới đây mô phỏng quá trình thực thi của mã nguồn trên.

![Quá trình quy hoạch động của bài toán leo cầu thang](intro_to_dynamic_programming.assets/climbing_stairs_dp.png)

Cũng giống như thuật toán quay lui, quy hoạch động cũng sử dụng khái niệm "trạng thái" để biểu thị giai đoạn cụ thể của quá trình giải bài toán, mỗi trạng thái đều tương ứng với một bài toán con cùng lời giải tối ưu cục bộ tương ứng. Ví dụ, trạng thái của bài toán leo cầu thang được định nghĩa là bậc cầu thang hiện tại $i$ 。

Dựa trên nội dung ở trên, chúng ta có thể đúc kết các thuật ngữ thường dùng của quy hoạch động:

- Gọi mảng `dp` là <u>bảng dp (dp table)</u>, $dp[i]$ biểu thị lời giải của bài toán con tương ứng với trạng thái $i$ 。
- Gọi trạng thái tương ứng với bài toán con nhỏ nhất (bậc cầu thang thứ $1$ và thứ $2$) là <u>trạng thái ban đầu</u>.
- Gọi công thức truy hồi $dp[i] = dp[i-1] + dp[i-2]$ là <u>phương trình chuyển trạng thái</u>.

## Tối ưu hoá không gian

Bạn đọc tinh ý có thể đã nhận ra rằng, **do $dp[i]$ chỉ liên quan tới $dp[i-1]$ và $dp[i-2]$ ，vì vậy chúng ta hoàn toàn không cần dùng cả một mảng `dp` để lưu trữ lời giải của mọi bài toán con**, mà chỉ cần hai biến cuộn (rolling variables) tịnh tiến về phía trước là đủ. Mã nguồn như sau:

```src
[file]{climbing_stairs_dp}-[class]{}-[func]{climbing_stairs_dp_comp}
```

Quan sát mã nguồn trên, do đã loại bỏ không gian chiếm dụng của mảng `dp` nên độ phức tạp không gian giảm từ $O(n)$ xuống còn $O(1)$ 。

Trong các bài toán quy hoạch động, trạng thái hiện tại thường chỉ liên quan tới một số hữu hạn các trạng thái đứng trước nó, lúc này chúng ta có thể chỉ giữ lại những trạng thái cần thiết, thông qua "giảm chiều dữ liệu" để tiết kiệm bộ nhớ. **Kỹ thuật tối ưu hoá không gian này được gọi là "biến cuộn" hoặc "mảng cuộn" (rolling array)**.
