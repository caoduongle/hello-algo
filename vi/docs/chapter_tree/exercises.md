# Bài tập

## Củng cố kiến thức

### Cây nhị phân hoàn chỉnh, đầy đủ và hoàn hảo

Hai mảng dưới đây biểu diễn cây nhị phân theo thứ tự duyệt theo tầng, `None` biểu thị vị trí ô trống:

- Cây A: `[1, 2, 3, 4, 5, 6]`
- Cây B: `[1, 2, 3, None, None, 6, 7]`

<!-- numbered-subquestions -->

1. Cây nào là cây nhị phân hoàn chỉnh?
2. Cây nào là cây nhị phân đầy đủ, tức là mỗi nút không phải lá đều có đúng hai nút con?
3. Trong hai cây có cây nào là cây nhị phân hoàn hảo không? Hãy giải thích lý do cho từng cây.

??? success "Đáp án tham khảo"

    1. Cây A là cây nhị phân hoàn chỉnh. Nó chỉ có tầng đáy cùng chưa được lấp đầy, và các nút được sắp xếp liên tục từ trái sang phải.
        Cây B không phải là cây nhị phân hoàn chỉnh, vì phía bên trái của tầng đáy cùng đã có vị trí trống, nhưng phía bên phải vẫn có nút.

    2. Cây B là cây nhị phân đầy đủ: nút 1 và nút 3 mỗi nút đều có đúng hai nút con, tất cả các nút còn lại đều là nút lá.
        Cây A không phải là cây nhị phân đầy đủ, vì nút 3 chỉ có một nút con trái là 6.

    3. Cả hai cây đều không phải là cây nhị phân hoàn hảo, vì tầng đáy cùng của cả hai cây đều chưa được lấp đầy hoàn toàn.

### Ba thứ tự duyệt trên cùng một cây

Lưu trữ mảng `[1, 2, 3, 4, 5, 6, 7]` theo thứ tự duyệt theo tầng vào một cây nhị phân hoàn chỉnh:

<!-- numbered-subquestions -->

1. Vẽ cây nhị phân này.
2. Viết các chuỗi duyệt tiền thứ tự, trung thứ tự và hậu thứ tự của nó.
3. Trong chuỗi trung thứ tự, hai đoạn chuỗi ở bên trái và bên phải của nút gốc 1 lần lượt tương ứng với phần nào của cây?

??? success "Đáp án tham khảo"

    1. Cây nhị phân này có dạng:

        ```text
              1
            /   \
           2     3
          / \   / \
         4   5 6   7
        ```

    2. Duyệt tiền thứ tự là `1, 2, 4, 5, 3, 6, 7`；
        Duyệt trung thứ tự là `4, 2, 5, 1, 6, 3, 7`；
        Duyệt hậu thứ tự là `4, 5, 2, 6, 7, 3, 1`。

    3. Đoạn `4, 2, 5` ở bên trái nút gốc 1 là chuỗi duyệt trung thứ tự của cây con trái;
        Đoạn `6, 3, 7` ở bên phải là chuỗi duyệt trung thứ tự của cây con phải.

### So sánh hai cây tìm kiếm nhị phân

Lần lượt chèn hai dãy số dưới đây từ trái sang phải vào cây tìm kiếm nhị phân rỗng:

- Dãy A: `[4, 2, 6, 1, 3, 5, 7]`
- Dãy B: `[1, 2, 3, 4, 5, 6, 7]`

<!-- numbered-subquestions -->

1. Lần lượt viết các nút đi qua khi tìm kiếm số 7 trong mỗi cây.
2. Nếu chiều cao được tính bằng số cạnh đi qua từ nút gốc đến nút lá xa nhất, thì chiều cao của hai cây lần lượt là bao nhiêu?
3. Dựa theo hai câu hỏi trước, bạn nghĩ hiệu năng tìm kiếm số 7 ở hai cây có giống nhau không? Hãy giải thích lý do kết hợp với hình dạng cây và đường đi tìm kiếm.

??? success "Đáp án tham khảo"

    1. Trong cây dựng từ Dãy A, đường đi tìm kiếm là `4 → 6 → 7`；
        Trong cây dựng từ Dãy B, đường đi tìm kiếm là `1 → 2 → 3 → 4 → 5 → 6 → 7`。

    2. Cây thứ nhất mọi tầng đều được lấp đầy, chiều cao là 2; cây thứ hai chỉ có nhánh con phải, chiều cao là 6.

    3. Hiệu năng tìm kiếm số 7 ở hai cây là khác nhau. Thứ tự chèn làm thay đổi hình dạng và chiều cao của cây tìm kiếm nhị phân. Khi tìm kiếm số 7, cây thứ nhất chỉ cần đi qua 3 nút,
        trong khi cây thứ hai phải lần lượt đi qua cả 7 nút; cây càng cao thì trong trường hợp xấu nhất số lượng nút cần so sánh dọc theo đường đi càng nhiều.

## Bài tập lập trình

### Chiều sâu tối đa của cây nhị phân

Cho nút gốc `root` của một cây nhị phân. Mỗi nút chứa một giá trị số nguyên cùng các tham chiếu trỏ đến các nút con trái và phải.

Gọi **số lượng nút** đi qua từ nút gốc đến nút lá xa nhất là chiều sâu tối đa của cây nhị phân. Hãy trả về chiều sâu tối đa của cây này; cây rỗng có chiều sâu tối đa là 0.
Hãy hoàn thành bằng phương pháp đệ quy.

??? tip "Gợi ý giải bài"

    1. Bài toán này tính độ sâu theo số lượng nút: khi chỉ có duy nhất một nút gốc, độ sâu tối đa là 1
    2. Cho hàm đệ quy trả về chiều sâu tối đa của cây con lấy nút hiện tại làm gốc
    3. Nút rỗng trả về 0, nút không rỗng trả về max(depth(left), depth(right)) + 1

[LeetCode](https://leetcode.com/problems/maximum-depth-of-binary-tree/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" } [Giải thích lời giải](https://leetcode.cn/problems/maximum-depth-of-binary-tree/solutions/2361697/104-er-cha-shu-de-zui-da-shen-du-hou-xu-txzrx/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }

### Duyệt cây nhị phân theo tầng

Cho nút gốc `root` của một cây nhị phân. Hãy sử dụng hàng đợi để truy cập toàn bộ các nút từ trên xuống dưới theo từng tầng một, trong cùng một tầng thì truy cập theo thứ tự từ trái sang phải.

Trả về một mảng hai chiều: mảng con thứ nhất lưu các giá trị nút ở tầng của nút gốc, mảng con thứ hai lưu các giá trị nút ở tầng tiếp theo, cứ thế tiếp tục.
Nếu cây nhị phân rỗng, trả về mảng rỗng.

??? tip "Gợi ý giải bài"

    1. Duyệt theo tầng yêu cầu các nút vào trước thì truy cập trước, do đó sử dụng hàng đợi
    2. Khi bắt đầu một vòng lặp, các nút trong hàng đợi vừa đúng thuộc về cùng một tầng
    3. Trước tiên ghi lại độ dài hàng đợi, sau đó lấy ra đúng ngần đó nút và đưa các nút con của chúng vào hàng đợi

[LeetCode](https://leetcode.com/problems/binary-tree-level-order-traversal/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" } [Giải thích lời giải](https://leetcode.cn/problems/binary-tree-level-order-traversal/solutions/2361604/102-er-cha-shu-de-ceng-xu-bian-li-yan-du-dyf7/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }

### Phần tử nhỏ thứ k trong cây tìm kiếm nhị phân

Một cây tìm kiếm nhị phân có tổng cộng `n` nút, giá trị các nút đôi một khác nhau.
Sau khi sắp xếp toàn bộ giá trị các nút từ nhỏ đến lớn, vị trí được đánh số bắt đầu từ 1.

Cho nút gốc `root` và số nguyên `k` thoả mãn `1 <= k <= n`，hãy trả về giá trị của nút xếp ở vị trí thứ `k`。
Hãy tìm kiếm kết quả trực tiếp trong quá trình duyệt trung thứ tự, không thu thập toàn bộ giá trị các nút trước.

??? tip "Gợi ý giải bài"

    1. Duyệt trung thứ tự cây tìm kiếm nhị phân sẽ truy cập các giá trị nút theo thứ tự từ nhỏ đến lớn
    2. Duyệt trung thứ tự lần lượt xử lý cây con trái, nút hiện tại và cây con phải; khi truy cập nút hiện tại thì tăng biến đếm lên 1
    3. Khi biến đếm lần đầu tiên bằng k, giá trị của nút hiện tại chính là đáp án, sau đó không cần tiếp tục duyệt nữa

[LeetCode](https://leetcode.com/problems/kth-smallest-element-in-a-bst/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" } [Giải thích lời giải](https://leetcode.cn/problems/kth-smallest-element-in-a-bst/solutions/2361685/230-er-cha-sou-suo-shu-zhong-di-k-xiao-d-n3he/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }
