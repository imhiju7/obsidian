Lớp này triển khai cơ chế **Scaled Dot-Product Attention** - trái tim của Transformer, dùng để tính toán sự tập trung (attention) giữa các từ trong câu. Nó xác định mức độ liên quan giữa các từ (qua Query, Key, Value) và tổng hợp thông tin.
![[Pasted image 20250318172441.png]]
### **Thành phần chính**

1. **Khởi tạo (`__init__`)**:
    - `nn.Softmax(dim=-1)`: Áp dụng hàm softmax theo chiều cuối cùng của tensor để chuẩn hóa điểm attention thành phân phối xác suất [0, 1].
2. **Phương thức `forward`**:  
    Nhận đầu vào gồm:
    - `q` (Query): Biểu diễn từ cần tập trung (thường từ decoder).
    - `k` (Key), `v` (Value): Biểu diễn các từ để so sánh với Query (thường từ encoder).
    - `mask`: Che các vị trí không liên quan (ví dụ: token pad hoặc token tương lai trong decoder).
### **Code**

```python
class ScaleDotProductAttention(nn.Module):
    """
    compute scale dot product attention
    Query : given sentence that we focused on (decoder)
    Key : every sentence to check relationship with Qeury(encoder)
    Value : every sentence same with Key (encoder)
    """

    def __init__(self):
        super(ScaleDotProductAttention, self).__init__()
        self.softmax = nn.Softmax(dim=-1)

    def forward(self, q, k, v, mask=None, e=1e-12):
        # input is 4 dimension tensor
        # [batch_size, head, length, d_tensor]
        batch_size, head, length, d_tensor = k.size()

        # 1. dot product Query with Key^T to compute similarity
        k_t = k.transpose(2, 3)  # transpose
        score = (q @ k_t) / math.sqrt(d_tensor)  # scaled dot product

        # 2. apply masking (opt)
        if mask is not None:
            score = score.masked_fill(mask == 0, -10000)

        # 3. pass them softmax to make [0, 1] range
        score = self.softmax(score)

        # 4. multiply with Value
        v = score @ v

        return v, score
```

### **4 Bước tính toán**

1. **Tính điểm Similarity (Độ tương đồng)**:
    - **Transpose Key**: `k_t = k.transpose(2, 3)` để chuyển vị chiều `length` và `d_tensor`.
    - **Dot Product**: `q @ k_t` tính tích vô hướng giữa Query và Key.
    - **Scaling**: Chia cho `sqrt(d_tensor)` để tránh giá trị quá lớn (khi chiều `d_tensor` lớn), giúp ổn định gradient.
2. **Áp dụng Mask (Tùy chọn)**:
    - Nếu `mask` được cung cấp, thay thế các vị trí `mask == 0` bằng `-10000`. Sau softmax, những vị trí này có xác suất ~0, giúp bỏ qua các từ không liên quan (ví dụ: padding hoặc từ tương lai trong decoder)
3. **Chuẩn hóa bằng Softmax**:
    - Áp dụng softmax để biến điểm số thành phân phối xác suất, thể hiện mức độ tập trung vào các từ.
4. **Nhân với Value**:
    - Kết hợp Value với trọng số từ softmax: `v = score @ v` → Kết quả cuối cùng là tổng có trọng số của Value.
### **Ví dụ minh họa**

Giả sử đầu vào là câu "Tôi đi học":
- **Query**: Từ "học" (cần tập trung).
- **Key/Value**: Các từ "Tôi", "đi", "học".
- **Score**: Xác định "học" liên quan đến "đi" và "Tôi" thế nào.
- **Output**: Biểu diễn mới của "học" sau khi tổng hợp thông tin từ cả câu.