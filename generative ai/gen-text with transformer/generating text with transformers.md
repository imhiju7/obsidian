1. [[tokenization]]: Câu đầu vào được token hóa bằng cùng một tokenizer đã được sử dụng để huấn luyện mạng.
2. **Xử lý qua [[encoder]]**: Các token được đưa vào [[encoder]], qua [[embedding class]], và các [[multi-head attention class]]. Kết quả là một biểu diễn sâu về cấu trúc và ý nghĩa của chuỗi đầu vào.
3. **Xử lý qua [[decoder]]**: Biểu diễn này được đưa vào giữa [[decoder]] để ảnh hưởng đến cơ chế [[self-attention]] của nó. Một [[tokens]] bắt đầu chuỗi được thêm vào đầu vào của [[decoder]] để kích hoạt việc dự đoán [[tokens]] tiếp theo.
4. **Dự đoán [[tokens]]**: Đầu ra của các [[self-attention class]] trong [[decoder]] được đưa qua một [[feed-forward network]] và [[softmax class]] cuối cùng để dự đoán [[ai/nlp/Learn/Learning/tokens]]. Quá trình này lặp lại cho đến khi mô hình dự đoán token kết thúc chuỗi.
5. **Chuyển đổi token thành từ**: Các token được giải mã thành từ, ví dụ "I love machine learning".
Kiến trúc [[transformers model]] bao gồm [[encoder]]và [[decoder]]. [[encoder]] chuyển chuỗi đầu vào thành biểu diễn sâu, còn [[decoder]] sử dụng biểu diễn này để tạo các token mới. Các biến thể của mô hình bao gồm:
- **[[encoder-only]]**: Sử dụng cho các tác vụ phân loại như phân tích cảm xúc. Ví dụ: [[bert]].
- **[[encoder-decoder]]**: Dùng cho các tác vụ dịch thuật và tạo văn bản. Ví dụ: [[bart]], [[t5]].
- **[[decoder-only]]**: Phổ biến cho các tác vụ tổng quát hóa văn bản. Ví dụ: [[gpt]], [[bloombergGPT]], [[jurassic]], [[llama]].