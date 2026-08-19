# Hướng dẫn sử dụng sách

!!! tip

    Để có được trải nghiệm đọc tốt nhất, bạn nên đọc kỹ toàn bộ nội dung phần này.

## Quy ước phong cách trình bày

- Các mục có đánh dấu `*` sau tiêu đề là phần đọc thêm và tương đối nâng cao. Nếu thời gian có hạn, bạn có thể tạm bỏ qua ở lần đọc đầu tiên.
- Các thuật ngữ chuyên môn sẽ được in đậm (ở bản in và bản PDF) hoặc gạch chân (ở bản web), ví dụ như <u>mảng (array)</u>. Bạn nên ghi nhớ chúng để tiện tra cứu tài liệu chuyên ngành.
- Các nội dung trọng tâm và câu kết luận sẽ được **in đậm**, bạn nên dành sự lưu tâm đặc biệt cho những nội dung này.
- Các từ ngữ mang hàm ý cụ thể hoặc đặc thù sẽ được đặt trong "dấu ngoặc kép" để tránh gây hiểu nhầm.
- Khi gặp những khái niệm có sự khác biệt giữa các ngôn ngữ lập trình, cuốn sách này thống nhất lấy Python làm chuẩn; ví dụ sử dụng `None` để biểu thị "rỗng".
- Cuốn sách này lược bớt một phần quy chuẩn chú thích của từng ngôn ngữ lập trình nhằm tối ưu không gian trình bày gọn gàng hơn. Chú thích trong sách chủ yếu chia làm ba loại: chú thích tiêu đề, chú thích nội dung và chú thích nhiều dòng.

=== "Python"

    ```python title=""
    """Chú thích tiêu đề, dùng để đánh dấu hàm, lớp, trường hợp kiểm thử, v.v."""
    
    # Chú thích nội dung, dùng để giải thích chi tiết mã nguồn
    
    """
    Chú thích
    nhiều dòng
    """
    ```

=== "C++"

    ```cpp title=""
    /* Chú thích tiêu đề, dùng để đánh dấu hàm, lớp, trường hợp kiểm thử, v.v. */
    
    // Chú thích nội dung, dùng để giải thích chi tiết mã nguồn
    
    /**
     * Chú thích
     * nhiều dòng
     */
    ```

=== "Java"

    ```java title=""
    /* Chú thích tiêu đề, dùng để đánh dấu hàm, lớp, trường hợp kiểm thử, v.v. */
    
    // Chú thích nội dung, dùng để giải thích chi tiết mã nguồn
    
    /**
     * Chú thích
     * nhiều dòng
     */
    ```

=== "C#"

    ```csharp title=""
    /* Chú thích tiêu đề, dùng để đánh dấu hàm, lớp, trường hợp kiểm thử, v.v. */
    
    // Chú thích nội dung, dùng để giải thích chi tiết mã nguồn
    
    /**
     * Chú thích
     * nhiều dòng
     */
    ```

=== "Go"

    ```go title=""
    /* Chú thích tiêu đề, dùng để đánh dấu hàm, lớp, trường hợp kiểm thử, v.v. */
    
    // Chú thích nội dung, dùng để giải thích chi tiết mã nguồn
    
    /**
     * Chú thích
     * nhiều dòng
     */
    ```

=== "Swift"

    ```swift title=""
    /* Chú thích tiêu đề, dùng để đánh dấu hàm, lớp, trường hợp kiểm thử, v.v. */
    
    // Chú thích nội dung, dùng để giải thích chi tiết mã nguồn
    
    /**
     * Chú thích
     * nhiều dòng
     */
    ```

=== "JS"

    ```javascript title=""
    /* Chú thích tiêu đề, dùng để đánh dấu hàm, lớp, trường hợp kiểm thử, v.v. */
    
    // Chú thích nội dung, dùng để giải thích chi tiết mã nguồn
    
    /**
     * Chú thích
     * nhiều dòng
     */
    ```

=== "TS"

    ```typescript title=""
    /* Chú thích tiêu đề, dùng để đánh dấu hàm, lớp, trường hợp kiểm thử, v.v. */
    
    // Chú thích nội dung, dùng để giải thích chi tiết mã nguồn
    
    /**
     * Chú thích
     * nhiều dòng
     */
    ```

=== "Dart"

    ```dart title=""
    /* Chú thích tiêu đề, dùng để đánh dấu hàm, lớp, trường hợp kiểm thử, v.v. */
    
    // Chú thích nội dung, dùng để giải thích chi tiết mã nguồn
    
    /**
     * Chú thích
     * nhiều dòng
     */
    ```

=== "Rust"

    ```rust title=""
    /* Chú thích tiêu đề, dùng để đánh dấu hàm, lớp, trường hợp kiểm thử, v.v. */

    // Chú thích nội dung, dùng để giải thích chi tiết mã nguồn
    
    // Chú thích
    // nhiều dòng
    ```

=== "C"

    ```c title=""
    /* Chú thích tiêu đề, dùng để đánh dấu hàm, lớp, trường hợp kiểm thử, v.v. */
    
    // Chú thích nội dung, dùng để giải thích chi tiết mã nguồn
    
    /**
     * Chú thích
     * nhiều dòng
     */
    ```

=== "Kotlin"

    ```kotlin title=""
    /* Chú thích tiêu đề, dùng để đánh dấu hàm, lớp, trường hợp kiểm thử, v.v. */
    
    // Chú thích nội dung, dùng để giải thích chi tiết mã nguồn
    
    /**
     * Chú thích
     * nhiều dòng
     */
    ```

=== "Ruby"

    ```ruby title=""
    ### Chú thích tiêu đề, dùng để đánh dấu hàm, lớp, trường hợp kiểm thử, v.v. ###

    # Chú thích nội dung, dùng để giải thích chi tiết mã nguồn
    
    # Chú thích
    # nhiều dòng
    ```

## Học tập hiệu quả qua hình động minh hoạ

So với văn bản thuần tuý, video và hình ảnh có mật độ thông tin cao hơn và tính cấu trúc rõ ràng hơn, giúp người đọc dễ tiếp thu hơn. Trong cuốn sách này, **các kiến thức trọng tâm và phức tạp sẽ chủ yếu được truyền tải thông qua hình động minh hoạ**, còn câu chữ đóng vai trò giải thích và bổ trợ.

Khi đọc sách, nếu bắt gặp phần nội dung có hình động minh hoạ như dưới đây, **hãy lấy hình ảnh làm chủ đạo, văn bản làm phần bổ trợ**, kết hợp cả hai để nắm bắt trọn vẹn nội dung.

![Ví dụ hình động minh hoạ](../index.assets/animation.gif)

## Đào sâu hiểu biết qua thực hành mã nguồn

Mã nguồn đi kèm cuốn sách được lưu trữ trên [kho lưu trữ GitHub](https://github.com/krahets/hello-algo). Như minh hoạ dưới đây, **mã nguồn có kèm sẵn các bộ dữ liệu kiểm thử và có thể chạy chỉ bằng một cú nhấp chuột**.

Nếu điều kiện thời gian cho phép, **bạn nên tự tay gõ lại mã nguồn một lần**. Nếu thời gian học tập có hạn, xin hãy đọc kỹ và chạy thử toàn bộ mã nguồn ít nhất một lần.

So với việc chỉ đọc mã, quá trình tự tay viết mã luôn mang lại nhiều bài học bổ ích hơn. **Tự tay thực hành mới là cách học thực thụ**.

![Ví dụ chạy mã nguồn](../index.assets/running_code.gif)

Các bước chuẩn bị trước khi chạy mã nguồn bao gồm 3 bước chính:

**Bước 1: Cài đặt môi trường lập trình cục bộ**. Vui lòng làm theo [hướng dẫn cài đặt](https://www.hello-algo.com/chapter_appendix/installation/) trong phần phụ lục; nếu đã cài đặt rồi, bạn có thể bỏ qua bước này.

**Bước 2: Nhân bản (clone) hoặc tải về kho lưu trữ mã nguồn**. Truy cập [kho lưu trữ GitHub](https://github.com/krahets/hello-algo). Nếu đã cài đặt [Git](https://git-scm.com/downloads), bạn có thể nhân bản kho mã nguồn bằng lệnh sau:

```shell
git clone https://github.com/krahets/hello-algo.git
```

Ngoài ra, bạn cũng có thể bấm vào nút "Download ZIP" ở vị trí như trong hình dưới đây để tải về tệp nén của kho mã nguồn, sau đó giải nén trên máy cục bộ.

![Nhân bản kho lưu trữ và tải mã nguồn](suggestions.assets/download_code.png)

**Bước 3: Chạy mã nguồn**. Như minh hoạ dưới đây, đối với các khối mã có tên tệp ở trên đầu, chúng ta có thể tìm thấy tệp mã nguồn tương ứng trong thư mục `codes` của kho lưu trữ. Tệp mã nguồn có thể chạy được ngay chỉ với một cú nhấp chuột, giúp bạn tiết kiệm thời gian gỡ lỗi không cần thiết để tập trung vào nội dung học tập.

![Khối mã và tệp mã nguồn tương ứng](suggestions.assets/code_md_to_repo.png)

Bên cạnh việc chạy mã cục bộ, **bản web còn hỗ trợ chạy trực quan hoá mã nguồn Python** (được phát triển dựa trên [pythontutor](https://pythontutor.com/)). Như minh hoạ dưới đây, bạn có thể nhấn "Chạy trực quan" bên dưới khối mã để mở rộng giao diện, quan sát từng bước thực thi của thuật toán; hoặc nhấn "Xem toàn màn hình" để có trải nghiệm xem tốt hơn.

![Chạy trực quan hoá mã nguồn Python](suggestions.assets/pythontutor_example.png)

## Cùng nhau tiến bộ qua trao đổi và thảo luận

Khi đọc cuốn sách này, xin đừng vội vàng bỏ qua những điểm kiến thức mà bạn chưa hoàn toàn thấu suốt. **Rất hoan nghênh bạn đặt câu hỏi trong phần bình luận**, tôi và các bạn đồng hành sẽ nỗ lực giải đáp cho bạn, thông thường trong vòng hai ngày.

Như minh hoạ dưới đây, ở cuối mỗi chương của bản web đều có phần bình luận. Mong bạn dành nhiều sự quan tâm cho khu vực này. Một mặt, bạn có thể theo dõi những khúc mắc của người khác để bổ khuyết lỗ hổng kiến thức của bản thân và gợi mở tư duy sâu hơn. Mặt khác, rất hy vọng bạn sẵn lòng giải đáp câu hỏi của các bạn đọc khác, chia sẻ góc nhìn của mình và giúp đỡ mọi người cùng tiến bộ.

![Ví dụ về phần bình luận](../index.assets/comment.gif)

## Lộ trình học thuật toán

Nhìn một cách tổng thể, chúng ta có thể chia quá trình học cấu trúc dữ liệu và giải thuật thành 3 giai đoạn:

1. **Giai đoạn 1: Nhập môn thuật toán**. Chúng ta cần làm quen với các đặc điểm và cách dùng của từng cấu trúc dữ liệu, đồng thời học hỏi nguyên lý hoạt động, quy trình, phạm vi ứng dụng và hiệu năng của các thuật toán khác nhau.
2. **Giai đoạn 2: Luyện giải bài tập thuật toán**. Khuyến khích bạn bắt đầu từ các bài toán phổ biến, tích luỹ ít nhất 100 bài trước để quen thuộc với các dạng bài thuật toán chủ đạo. Khi mới bắt đầu luyện đề, hiện tượng "quên kiến thức" có thể là một thử thách, nhưng xin hãy yên tâm, đây là điều hết sức bình thường. Chúng ta có thể ôn tập các bài toán theo "đường cong lãng quên Ebbinghaus" (Ebbinghaus forgetting curve), thông thường sau 3 đến 5 vòng lặp lại, kiến thức sẽ được ghi nhớ sâu sắc. Danh sách đề bài và kế hoạch luyện tập gợi ý được trình bày trong [kho lưu trữ GitHub này](https://github.com/krahets/LeetCode-Book).
3. **Giai đoạn 3: Xây dựng hệ thống kiến thức**. Về mặt học tập lý thuyết, chúng ta có thể đọc thêm các chuyên mục chuyên sâu về thuật toán, các khung giải bài và giáo trình thuật toán nâng cao để không ngừng làm phong phú hệ thống tri thức. Về mặt luyện đề, có thể áp dụng các chiến lược nâng cao như phân loại theo chuyên đề, một bài nhiều cách giải, một cách giải cho nhiều bài toán, v.v., những kinh nghiệm luyện đề này có thể dễ dàng tìm thấy trong nhiều cộng đồng.

Như minh hoạ dưới đây, nội dung của cuốn sách này chủ yếu bao quát "Giai đoạn 1", nhằm tạo nền tảng vững chắc giúp bạn bước vào Giai đoạn 2 và Giai đoạn 3 một cách hiệu quả hơn.

![Lộ trình học thuật toán](suggestions.assets/learning_route.png)
