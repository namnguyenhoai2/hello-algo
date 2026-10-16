# Cách sử dụng cuốn sách này

!!! tip

    Để có trải nghiệm đọc tốt nhất, bạn nên đọc kỹ phần này.

## Quy ước về phong cách viết

- Các phần có `*` sau tiêu đề là phần tùy chọn và có phần khó hơn. Nếu không có nhiều thời gian, bạn có thể bỏ qua trong lần đọc đầu tiên.
- Các thuật ngữ kỹ thuật được in đậm (trong bản in và bản PDF) hoặc gạch chân (trong bản web), chẳng hạn như <u>mảng</u>. Bạn nên ghi nhớ chúng, vì chúng sẽ giúp ích khi đọc các tài liệu kỹ thuật.
- Nội dung quan trọng và các câu tóm tắt sẽ được **in đậm**, vì vậy bạn nên đặc biệt chú ý đến những phần này.
- Các từ và cụm từ có ý nghĩa cụ thể sẽ được đặt trong “dấu ngoặc kép” để tránh mơ hồ.
- Khi thuật ngữ khác nhau giữa các ngôn ngữ lập trình, cuốn sách này sử dụng quy ước của Python; chẳng hạn, sách dùng `None` để biểu thị “null”.
- Cuốn sách này nới lỏng một phần các quy ước thông thường về phong cách comment của ngôn ngữ lập trình để có bố cục cô đọng hơn. Comment chủ yếu được chia thành ba loại: comment tiêu đề, comment nội dung và comment nhiều dòng.

=== "Python"

    ```python title=""
    """Comment tiêu đề, dùng để gắn nhãn cho các hàm, class, test case, v.v."""

    # Comment nội dung, dùng để giải thích chi tiết về code

    """
    Comment nhiều dòng
    """
    ```

=== "C++"

    ```cpp title=""
    /* Comment tiêu đề, dùng để gắn nhãn cho các hàm, class, test case, v.v. */

    // Comment nội dung, dùng để giải thích chi tiết về code

    /**
     * Comment nhiều dòng
     */
    ```

=== "Java"

    ```java title=""
    /* Comment tiêu đề, dùng để gắn nhãn cho các hàm, class, test case, v.v. */

    // Comment nội dung, dùng để giải thích chi tiết về code

    /**
     * Comment nhiều dòng
     */
    ```

=== "C#"

    ```csharp title=""
    /* Comment tiêu đề, dùng để gắn nhãn cho các hàm, class, test case, v.v. */

    // Comment nội dung, dùng để giải thích chi tiết về code

    /**
     * Comment nhiều dòng
     */
    ```

=== "Go"

    ```go title=""
    /* Comment tiêu đề, dùng để gắn nhãn cho các hàm, class, test case, v.v. */

    // Comment nội dung, dùng để giải thích chi tiết về code

    /**
     * Comment nhiều dòng
     */
    ```

=== "Swift"

    ```swift title=""
    /* Comment tiêu đề, dùng để gắn nhãn cho các hàm, class, test case, v.v. */

    // Comment nội dung, dùng để giải thích chi tiết về code

    /**
     * Comment nhiều dòng
     */
    ```

=== "JS"

    ```javascript title=""
    /* Comment tiêu đề, dùng để gắn nhãn cho các hàm, class, test case, v.v. */

    // Comment nội dung, dùng để giải thích chi tiết về code

    /**
     * Comment nhiều dòng
     */
    ```

=== "TS"

    ```typescript title=""
    /* Comment tiêu đề, dùng để gắn nhãn cho các hàm, class, test case, v.v. */

    // Comment nội dung, dùng để giải thích chi tiết về code

    /**
     * Comment nhiều dòng
     */
    ```

=== "Dart"

    ```dart title=""
    /* Comment tiêu đề, dùng để gắn nhãn cho các hàm, class, test case, v.v. */

    // Comment nội dung, dùng để giải thích chi tiết về code

    /**
     * Comment nhiều dòng
     */
    ```

=== "Rust"

    ```rust title=""
    /* Comment tiêu đề, dùng để gắn nhãn cho các hàm, class, test case, v.v. */

    // Comment nội dung, dùng để giải thích chi tiết về code

    // Comment nhiều dòng
    // 
    ```

=== "C"

    ```c title=""
    /* Comment tiêu đề, dùng để gắn nhãn cho các hàm, class, test case, v.v. */

    // Comment nội dung, dùng để giải thích chi tiết về code

    /**
     * Comment nhiều dòng
     */
    ```

=== "Kotlin"

    ```kotlin title=""
    /* Comment tiêu đề, dùng để gắn nhãn cho các hàm, class, test case, v.v. */

    // Comment nội dung, dùng để giải thích chi tiết về code

    /**
     * Comment nhiều dòng
     */
    ```

=== "Ruby"

    ```ruby title=""
    ### Comment tiêu đề, dùng để gắn nhãn cho các hàm, class, test case, v.v. ###

    # Comment nội dung, dùng để giải thích chi tiết về code

    # Comment nhiều dòng
    # 
    ```

## Học hiệu quả với hình minh họa động

So với văn bản thuần túy, video và hình ảnh có mật độ thông tin cao hơn cùng cấu trúc rõ ràng hơn, nên dễ hiểu hơn. Trong cuốn sách này, **các khái niệm quan trọng và chủ đề khó chủ yếu được trình bày thông qua hình minh họa động**, còn văn bản đóng vai trò giải thích và bổ sung.

Nếu trong khi đọc cuốn sách này, bạn bắt gặp một hình minh họa động như hình dưới đây, **hãy xem hình minh họa là nội dung chính và văn bản là phần bổ trợ**, đồng thời kết hợp cả hai để hiểu nội dung.

![Ví dụ về hình minh họa động](../index.assets/animation.gif)

## Hiểu sâu hơn thông qua thực hành code

Code đi kèm cuốn sách này được lưu trữ trong [kho lưu trữ GitHub](https://github.com/krahets/hello-algo). Như hình dưới đây cho thấy, **source code đi kèm các test case và có thể chạy chỉ bằng một cú nhấp chuột**.

Nếu có thời gian, **bạn nên tự gõ code**. Nếu thời gian học hạn chế, ít nhất hãy đọc kỹ và chạy toàn bộ code.

So với việc chỉ đọc code, tự viết code thường mang lại nhiều lợi ích hơn. **Học thật sự diễn ra qua thực hành**.

![Ví dụ chạy code](../index.assets/running_code.gif)

Để chạy được code, về cơ bản cần thực hiện ba bước chuẩn bị.

**Bước 1: Cài đặt môi trường lập trình cục bộ**. Hãy làm theo [hướng dẫn](https://www.hello-algo.com/chapter_appendix/installation/) trong phần phụ lục. Nếu đã cài đặt rồi, bạn có thể bỏ qua bước này.

**Bước 2: Clone hoặc tải xuống repository chứa code**. Truy cập [kho lưu trữ GitHub](https://github.com/krahets/hello-algo). Nếu đã cài đặt [Git](https://git-scm.com/downloads), bạn có thể clone repository này bằng lệnh sau:

```shell
git clone https://github.com/krahets/hello-algo.git
```

Ngoài ra, bạn có thể nhấp vào nút “Download ZIP” như hình dưới đây để tải trực tiếp kho lưu trữ dưới dạng tệp ZIP, sau đó giải nén tại máy.

![Clone repository và tải code](suggestions.assets/download_code.png)

**Bước 3: Chạy source code**. Như hình dưới đây cho thấy, đối với các khối code có tên tệp ở phía trên, chúng ta có thể tìm thấy các tệp source code tương ứng trong thư mục `codes` của repository. Các tệp source code có thể chạy chỉ bằng một cú nhấp chuột, giúp bạn tiết kiệm thời gian debug không cần thiết và tập trung vào việc học nội dung.

![Các khối code và tệp source code tương ứng](suggestions.assets/code_md_to_repo.png)

Ngoài việc chạy code cục bộ, **phiên bản web còn hỗ trợ thực thi Python code trực quan** (được triển khai dựa trên [pythontutor](https://pythontutor.com/)). Như hình dưới đây cho thấy, bạn có thể nhấp vào “Visual Run” bên dưới khối code để mở rộng khung hiển thị và quan sát quá trình thực thi của algorithm code; bạn cũng có thể nhấp vào “Full Screen View” để có trải nghiệm xem tốt hơn.

![Chạy Python code trực quan](suggestions.assets/pythontutor_example.png)

## Cùng nhau tiến bộ qua câu hỏi và thảo luận

Khi đọc cuốn sách này, đừng bỏ qua những điểm mà bạn vẫn chưa hiểu đầy đủ. **Bạn cứ thoải mái đặt câu hỏi trong phần bình luận**, tôi và các bạn của mình sẽ cố gắng hết sức để trả lời, thường là trong vòng hai ngày.

Như hình dưới đây cho thấy, phiên bản web có phần bình luận ở cuối mỗi chương. Tôi khuyến khích bạn chú ý theo dõi các cuộc thảo luận ở đó. Một mặt, bạn có thể tìm hiểu những vấn đề mà người khác gặp phải, từ đó bổ sung những điểm còn thiếu trong hiểu biết của mình và thúc đẩy suy nghĩ sâu hơn. Mặt khác, tôi hy vọng bạn sẽ sẵn lòng trả lời câu hỏi của những độc giả khác, chia sẻ hiểu biết của mình và giúp đỡ người khác tiến bộ.

![Ví dụ về phần bình luận](../index.assets/comment.gif)

## Lộ trình học algorithm

Nhìn chung, chúng ta có thể chia quá trình học cấu trúc dữ liệu và algorithm thành ba giai đoạn.

1. **Giai đoạn 1: Nhập môn algorithm**. Chúng ta cần làm quen với đặc điểm và cách sử dụng của nhiều cấu trúc dữ liệu khác nhau, đồng thời học các nguyên lý, quy trình, công dụng và hiệu suất của những algorithm khác nhau.
2. **Giai đoạn 2: Luyện tập các bài toán algorithm**. Bạn nên bắt đầu với những bài toán phổ biến và giải ít nhất 100 bài trước, để làm quen với các dạng câu hỏi algorithm phổ biến. Khi mới bắt đầu luyện tập, việc “quên kiến thức” có thể khiến bạn cảm thấy khó khăn, nhưng hãy yên tâm, điều này hoàn toàn bình thường. Chúng ta có thể ôn lại các bài toán theo “đường cong lãng quên Ebbinghaus”; sau 3-5 vòng lặp lại, kiến thức thường sẽ được ghi nhớ vững chắc. Để xem danh sách bài toán và kế hoạch luyện tập được đề xuất, hãy tham khảo [kho lưu trữ GitHub](https://github.com/krahets/LeetCode-Book).
3. **Giai đoạn 3: Xây dựng hệ thống kiến thức**. Về việc học, chúng ta có thể đọc các bài viết trong chuyên mục algorithm, các framework giải bài và giáo trình algorithm để không ngừng làm phong phú hệ thống kiến thức. Về việc luyện tập, chúng ta có thể thử các chiến lược giải bài nâng cao, chẳng hạn như phân loại theo chủ đề, một bài nhiều cách giải, một cách giải cho nhiều bài, v.v. Bạn có thể tìm thấy những chia sẻ liên quan đến việc giải bài trong nhiều cộng đồng khác nhau.

Như minh họa trong hình dưới đây, nội dung của cuốn sách này chủ yếu bao quát “Giai đoạn 1”, nhằm giúp bạn thực hiện việc học ở Giai đoạn 2 và Giai đoạn 3 hiệu quả hơn.

![Lộ trình học thuật toán](suggestions.assets/learning_route.png)