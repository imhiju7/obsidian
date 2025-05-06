[1] A. Vaswani _et al._, “Attention Is All You Need.” arXiv, Aug. 01, 2023.
- Được mở rộng quy mô một cách hiệu quả để dùng [[gpu]] đa lõi. Xử lí song song dữ liệu đầu vào. sử dụng nguồn data huấn luyện lớn hơn
- Quan trọng, nó có thể học cách chú ý tới ý nghĩa của các từ mà nó đang xử lý
# cấu trúc của model transformers
- Kiến trúc transformer chia thành hai phần: [[encoder]] và [[decoder]]. Trước khi đưa văn bản vào mô hình, cần phải [[tokenization]] tức là chuyển đổi các từ thành số. 
			![[Pasted image 20250318165912.png]]
- Sau đó, các số này được chuyển đến [[embedding class]], nơi mỗi [[tokens]] được biểu diễn dưới dạng vector trong không gian nhiều chiều. 
- Tiếp theo, các vector này được cộng với [[positional encoding]] và chuyển đến [[self-attention class]], nơi mô hình phân tích mối quan hệ giữa các [[tokens]] trong chuỗi đầu vào.
- [[self-attention weights]] học được trong quá trình đào tạo phản ánh tầm quan trọng của mỗi từ trong chuỗi đầu vào đối với các từ khác. transformer có nhiều đầu attention ([[multi-head attention class]]) để học các khía cạnh khác nhau của ngôn ngữ. 
- Cuối cùng, các trọng số attention được áp dụng cho dữ liệu đầu vào và kết quả được xử lý [[neural network fully-connected]] để tạo ra vector logits, được chuyển qua [[softmax class]] để tạo ra xác suất cho mỗi từ trong từ điển.