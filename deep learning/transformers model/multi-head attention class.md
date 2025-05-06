Cơ chế **MultiHeadAttention** trong mô hình Transformer được thiết kế để xử lý thông tin từ nhiều góc độ khác nhau một cách đồng thời, giúp mô hình học được các biểu diễn đa dạng của dữ liệu.
![[Pasted image 20250318171749.png]]
### **1. Khởi tạo lớp (`__init__`)**:

- **Tham số**:
    - `d_model`: Kích thước vector đặc trưng đầu vào/đầu ra
    - `n_head`: Số lượng "heads" (đầu) trong cơ chế multi-head.
- **Các thành phần**:
    - **`self.w_q`, `self.w_k`, `self.w_v`**: Các lớp tuyến tính (Linear) để biến đổi Query (Q), Key (K), Value (V) thành các không gian con khác nhau.
    - **`self.w_concat`**: Lớp tuyến tính để gộp thông tin từ các heads sau khi tính toán.
    - **`self.attention`**: Lớp `ScaleDotProductAttention` thực hiện phép tính attention cơ bản (tích vô hướng có tỷ lệ).
### **2. Quá trình lan truyền (`forward`)**:

###### **Bước 1: Biến đổi Q, K, V bằng Linear Projection**
```python 
q, k, v = self.w_q(q), self.w_k(k), self.w_v(v)
```
- Mục đích: Chiếu Q, K, V vào các không gian con khác nhau để học các biểu diễn đa dạng. Mỗi head sẽ nhận một phần thông tin từ các không gian này.
###### **Bước 2: Chia tensor thành nhiều heads**
```python
q, k, v = self.split(q), self.split(k), self.split(v)
```
- **Ví dụ**: Nếu `d_model = 512` và `n_head = 8`, mỗi head sẽ xử lý một tensor có kích thước `64` (vì `512 / 8 = 64`).
- **Cách thực hiện**: Reshape tensor từ `[batch_size, length, d_model]` thành `[batch_size, n_head, length, d_tensor]` (với `d_tensor = d_model // n_head`).
###### **Bước 3: Tính toán Attention với `ScaleDotProductAttention`**
```python
out, attention = self.attention(q, k, v, mask=mask)
```
- **ScaleDotProductAttention**:
    - Tính độ tương đồng giữa Q và K bằng tích vô hướng.
    - Chia kết quả cho `sqrt(d_k)` để tránh giá trị quá lớn (giúp gradient ổn định hơn).
    - Áp dụng mask (nếu có) để che các phần tử không hợp lệ (ví dụ: padding hoặc từ ở tương lai trong decoder).
    - Dùng softmax để chuyển thành trọng số attention.
    - Nhân trọng số với V để lấy kết quả.
###### **Bước 4: Gộp các heads và chiếu qua lớp Linear**
```python
out = self.concat(out)
out = self.w_concat(out)
```
- **Gộp heads**: Kết hợp thông tin từ các heads thành tensor có kích thước ban đầu `[batch_size, length, d_model]`.
- **Chiếu qua Linear**: Biến đổi để tổng hợp thông tin từ tất cả heads.
```python
class MultiHeadAttention(nn.Module):

    def __init__(self, d_model, n_head):
        super(MultiHeadAttention, self).__init__()
        self.n_head = n_head
        self.attention = ScaleDotProductAttention()
        self.w_q = nn.Linear(d_model, d_model)
        self.w_k = nn.Linear(d_model, d_model)
        self.w_v = nn.Linear(d_model, d_model)
        self.w_concat = nn.Linear(d_model, d_model)

    def forward(self, q, k, v, mask=None):
        # 1. dot product with weight matrices
        q, k, v = self.w_q(q), self.w_k(k), self.w_v(v)

        # 2. split tensor by number of heads
        q, k, v = self.split(q), self.split(k), self.split(v)

        # 3. do scale dot product to compute similarity
        out, attention = self.attention(q, k, v, mask=mask)
        
        # 4. concat and pass to linear layer
        out = self.concat(out)
        out = self.w_concat(out)

        # 5. visualize attention map
        # TODO : we should implement visualization

        return out

    def split(self, tensor):
        """
        split tensor by number of head

        :param tensor: [batch_size, length, d_model]
        :return: [batch_size, head, length, d_tensor]
        """
        batch_size, length, d_model = tensor.size()

        d_tensor = d_model // self.n_head
        tensor = tensor.view(batch_size, length, self.n_head, d_tensor).transpose(1, 2)
        # it is similar with group convolution (split by number of heads)

        return tensor

    def concat(self, tensor):
        """
        inverse function of self.split(tensor : torch.Tensor)

        :param tensor: [batch_size, head, length, d_tensor]
        :return: [batch_size, length, d_model]
        """
        batch_size, head, length, d_tensor = tensor.size()
        d_model = head * d_tensor

        tensor = tensor.transpose(1, 2).contiguous().view(batch_size, length, d_model)
        return tensor
```

###### **Hàm `split` và `concat`**:

 **`split(tensor)`**:
- **Mục đích**: Chia tensor thành `n_head` phần để xử lý song song.
- **Ví dụ**: Tensor `[batch_size, length, 512]` → `[batch_size, 8, length, 64]`.
 **`concat(tensor)`**:
- **Mục đích**: Khôi phục tensor về kích thước ban đầu sau khi xử lý các heads.
- **Ví dụ**: Tensor `[batch_size, 8, length, 64]` → `[batch_size, length, 512]`.
###### **Ý nghĩa của MultiHeadAttention**:

- **Đa dạng hóa biểu diễn**: Mỗi head học cách tập trung vào các phần khác nhau của dữ liệu. Ví dụ:
    - Một head có thể tập trung vào quan hệ ngữ pháp.
    - Một head khác tập trung vào từ khóa chính.
- **Tăng hiệu suất**: Xử lý song song các heads giúp tận dụng tài nguyên tính toán.
- **Linh hoạt**: Các heads độc lập, cho phép mô hình học cả thông tin cục bộ và toàn cục.
###### **Ví dụ minh họa**:

- **Input**: Câu "She ate the pizza with mushrooms".
- **MultiHeadAttention hoạt động**
    - Head 1: Tập trung vào "ate" và "pizza" (động từ - danh từ).
    - Head 2: Tập trung vào "pizza" và "mushrooms" (danh từ - bổ nghĩa.
    - Head 3: Tập trung vào "She" và "ate" (chủ ngữ - động từ).
