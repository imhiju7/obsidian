- Transformer không sử dụng RNN/CNN (vốn có khả năng nắm bắt thứ tự tự nhiên), nên cần **mã hóa vị trí từng từ** trong chuỗi. Positional Encoding (PE) được **thêm vào Embedding** của từ, giúp mô hình hiểu được vị trí tương đối/ tuyệt đối của các từ.

![[Pasted image 20250318171011.png]]
```python
class PositionalEncoding(nn.Module):
    """
    compute sinusoid encoding.
    """
    def __init__(self, d_model, max_len, device):
        """
        constructor of sinusoid encoding class
        :param d_model: dimension of model
        :param max_len: max sequence length
        :param device: hardware device setting
        """
        super(PositionalEncoding, self).__init__()

        # same size with input matrix (for adding with input matrix)
        self.encoding = torch.zeros(max_len, d_model, device=device)
        self.encoding.requires_grad = False  # we don't need to compute gradient

        pos = torch.arange(0, max_len, device=device)
        pos = pos.float().unsqueeze(dim=1)
        # 1D => 2D unsqueeze to represent word's position

        _2i = torch.arange(0, d_model, step=2, device=device).float()
        # 'i' means index of d_model (e.g. embedding size = 50, 'i' = [0,50])
        # "step=2" means 'i' multiplied with two (same with 2 * i)

        self.encoding[:, 0::2] = torch.sin(pos / (10000 ** (_2i / d_model)))
        self.encoding[:, 1::2] = torch.cos(pos / (10000 ** (_2i / d_model)))
        # compute positional encoding to consider positional information of words

    def forward(self, x):
        # self.encoding
        # [max_len = 512, d_model = 512]

        batch_size, seq_len = x.size()
        # [batch_size = 128, seq_len = 30]

        return self.encoding[:seq_len, :]
        # [seq_len = 30, d_model = 512]
        # it will add with tok_emb : [128, 30, 512]
```

**3. Chi tiết từng phần:**

- **Tham số:**
    - `d_model`: Số chiều của Embedding vector (cùng kích thước với PE).
    - `max_len`: Độ dài tối đa của chuỗi mà PE có thể xử lý.
    - `device`: GPU/CPU để tính toán.
- **Ma trận PE:**
    - Khởi tạo ma trận `encoding` kích thước `[max_len, d_model]`, giá trị ban đầu bằng 0
    - Không tính gradient (`requires_grad=False`) vì PE là cố định, không học từ dữ liệu.
- **Công thức Sinusoid:**
    - **pos**: Vector vị trí từ 0 đến `max_len-1` (shape: `[max_len, 1]`).
    - **_2i**: Chỉ số chẵn từ 0 đến `d_model` (vd: [0, 2, 4,..., 510] nếu `d_model=512`).
    - **Tính PE**:
        - **Chỉ số chẵn**: $sin(pos / (10000^{2i/d_{model}})$  
        - **Chỉ số lẻ**: $cos(pos / (10000^{2i/d_{model}})$
**4. Ý nghĩa Toán học:**

- **Mục tiêu**: Tạo mã hóa duy nhất cho mỗi vị trí, đồng thời thể hiện quan hệ tương đối giữa các vị trí.
- **Hàm Sin/Cos**
    - Có tính **tuần hoàn**, giúp mô hình học được khoảng cách tương đối thông qua phép cộng vector.
    - **10000^(2i/d_model)**: Điều chỉnh tần số theo chiều `i`:
        - Chiều thấp (i nhỏ): Tần số cao → Thay đổi nhanh → Phân biệt vị trí gần.
        - Chiều cao (i lớn): Tần số thấp → Thay đổi chậm → Phân biệt vị trí xa.
**Ví dụ minh họa:**

- Giả sử `d_model = 4`, `max_len = 5`:
    
    - PE cho vị trí 0: `[sin(0/10000^0), cos(0/10000^0), sin(0/10000^(2/4)), cos(0/10000^(2/4))]`
    - PE cho vị trí 1: `[sin(1/10000^0), cos(1/10000^0), sin(1/10000^(2/4)), cos(1/10000^(2/4))]`
    - ... Mỗi vị trí có vector PE duy nhất.