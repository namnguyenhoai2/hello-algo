# Bài tập

## Ôn tập khái niệm

### Cây nhị phân hoàn chỉnh, đầy đủ và hoàn hảo

Hai mảng sau biểu diễn các cây nhị phân theo thứ tự theo từng mức, trong đó `None` đánh dấu một vị trí trống:

- Cây A: `[1, 2, 3, 4, 5, 6]`
- Cây B: `[1, 2, 3, None, None, 6, 7]`

<!-- numbered-subquestions -->

1. Cây nào là cây nhị phân hoàn chỉnh?
2. Cây nào là cây nhị phân đầy đủ, nghĩa là mọi nút không phải nút lá đều có hai nút con?
3. Có cây nào là cây nhị phân hoàn hảo không? Giải thích lý do đối với từng cây.

??? success "Đáp án"

    1. Cây A là cây nhị phân hoàn chỉnh. Chỉ mức thấp nhất của cây chưa đầy đủ, và các nút ở mức đó nằm ở các vị trí liên tiếp từ trái sang phải.
        Cây B không hoàn chỉnh vì có các vị trí trống ở bên trái của mức thấp nhất trong khi các nút vẫn xuất hiện ở bên phải.

    2. Cây B là cây nhị phân đầy đủ: các nút 1 và 3 mỗi nút có hai nút con, còn tất cả các nút khác đều là nút lá.
        Cây A không đầy đủ vì nút 3 chỉ có một nút con, là nút con bên trái 6.

    3. Không cây nào là cây nhị phân hoàn hảo vì mức thấp nhất của mỗi cây chưa được lấp đầy hoàn toàn.

### Ba thứ tự duyệt trên cùng một cây

Lưu mảng `[1, 2, 3, 4, 5, 6, 7]` theo thứ tự theo từng mức trong một cây nhị phân hoàn chỉnh.

<!-- numbered-subquestions -->

1. Vẽ cây.
2. Viết các chuỗi duyệt preorder, inorder và postorder của cây.
3. Trong chuỗi inorder, các phần nào của cây tương ứng với các chuỗi con ở bên trái và bên phải của nút gốc 1?

??? success "Đáp án"

    1. Cây là:

        ```text
              1
            /   \
           2     3
          / \   / \
         4   5 6   7
        ```

    2. Duyệt preorder là `1, 2, 4, 5, 3, 6, 7`;
        duyệt inorder là `4, 2, 5, 1, 6, 3, 7`;
        duyệt postorder là `4, 5, 2, 6, 7, 3, 1`.

    3. Chuỗi `4, 2, 5` ở bên trái nút gốc 1 là phép duyệt inorder của cây con bên trái;
        chuỗi `6, 3, 7` ở bên phải nút đó là phép duyệt inorder của cây con bên phải.

### So sánh hai cây tìm kiếm nhị phân

Chèn từng chuỗi sau, từ trái sang phải, vào một cây tìm kiếm nhị phân rỗng:

- Chuỗi A: `[4, 2, 6, 1, 3, 5, 7]`
- Chuỗi B: `[1, 2, 3, 4, 5, 6, 7]`

<!-- numbered-subquestions -->

1. Với mỗi cây, hãy viết các nút được truy cập khi tìm kiếm 7.
2. Nếu chiều cao được đo bằng số cạnh từ nút gốc đến nút lá xa nhất, chiều cao của mỗi cây là bao nhiêu?
3. Dựa trên hai câu hỏi đầu, việc tìm kiếm 7 có hiệu quả như nhau trong hai cây không? Giải thích dựa trên hình dạng của cây và các đường đi khi tìm kiếm.

??? success "Đáp án"

    1. Trong cây được tạo từ Chuỗi A, đường đi khi tìm kiếm là `4 → 6 → 7`.
        Trong cây được tạo từ Chuỗi B, đường đi khi tìm kiếm là `1 → 2 → 3 → 4 → 5 → 6 → 7`.

    2. Mọi mức của cây thứ nhất đều đầy đủ, và chiều cao của cây là 2. Cây thứ hai chỉ có các nút con bên phải, và chiều cao của cây là 6.

    3. Việc tìm kiếm 7 không có hiệu quả như nhau trong hai cây. Thứ tự chèn làm thay đổi hình dạng và chiều cao của cây tìm kiếm nhị phân. Phép tìm kiếm chỉ truy cập 3 nút trong cây thứ nhất
        nhưng truy cập cả 7 nút trong cây thứ hai. Cây càng cao thì trong trường hợp xấu nhất, càng có nhiều nút có thể cần được so sánh dọc theo một đường đi.

## Bài tập lập trình

### Độ sâu lớn nhất của cây nhị phân

Bạn được cung cấp nút gốc `root` của một cây nhị phân. Mỗi nút chứa một giá trị nguyên và các tham chiếu đến nút con bên trái và bên phải.

Độ sâu lớn nhất là **số nút** trên đường đi từ nút gốc đến nút lá xa nhất. Hãy trả về độ sâu lớn nhất của cây; độ sâu lớn nhất của một cây rỗng là 0.
Sử dụng đệ quy.

??? tip "Gợi ý"

    1. Trong bài tập này, độ sâu được đo bằng số nút, vì vậy một cây chỉ chứa nút gốc có độ sâu lớn nhất là 1
    2. Cho hàm đệ quy trả về độ sâu lớn nhất của cây con có gốc là nút hiện tại
    3. Trả về 0 đối với một nút rỗng; với một nút không rỗng, trả về max(depth(left), depth(right)) + 1

[LeetCode](https://leetcode.com/problems/maximum-depth-of-binary-tree/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }

### Duyệt cây nhị phân theo từng mức

Cho nút gốc `root` của một cây nhị phân, hãy sử dụng queue để truy cập tất cả các nút theo từng mức, từ trên xuống dưới và từ trái sang phải trong mỗi mức.

Trả về một mảng hai chiều: mảng con thứ nhất lưu các giá trị ở mức của nút gốc, mảng con thứ hai lưu các giá trị ở mức tiếp theo, v.v.
Nếu cây rỗng, hãy trả về một mảng rỗng.

??? tip "Gợi ý"

    1. Phép duyệt theo thứ tự theo từng mức truy cập các nút được đưa vào queue sớm hơn trước, vì vậy hãy sử dụng queue
    2. Khi bắt đầu mỗi lượt, tất cả các nút hiện có trong queue đều thuộc cùng một mức
    3. Trước tiên, ghi lại độ dài của queue, sau đó xóa chính xác số nút đó và đưa các nút con của chúng vào queue

[LeetCode](https://leetcode.com/problems/binary-tree-level-order-traversal/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }

### Phần tử nhỏ thứ k trong cây tìm kiếm nhị phân

Một cây tìm kiếm nhị phân chứa `n` nút có các giá trị phân biệt.
Nếu tất cả giá trị của các nút được sắp xếp từ nhỏ đến lớn, vị trí của chúng được đánh số bắt đầu từ 1.

Cho nút gốc `root` và một số nguyên `k` thỏa mãn `1 <= k <= n`, hãy trả về giá trị ở vị trí `k`.
Tìm trực tiếp đáp án trong khi duyệt inorder thay vì thu thập trước tất cả giá trị của các nút.

??? tip "Gợi ý"

    1. Phép duyệt inorder của cây tìm kiếm nhị phân truy cập các giá trị của nút từ nhỏ đến lớn
    2. Phép duyệt inorder xử lý cây con bên trái, nút hiện tại rồi đến cây con bên phải; tăng bộ đếm khi truy cập nút hiện tại
    3. Khi bộ đếm lần đầu tiên bằng k, giá trị của nút hiện tại là đáp án, vì vậy không cần duyệt thêm

[LeetCode](https://leetcode.com/problems/kth-smallest-element-in-a-bst/){ .rounded-button .exercise-button target="_blank" rel="noopener noreferrer" }