- Mô hình ngôn ngữ lớn đã được huấn luyện qua hàng ngàn tỉ từ qua hàng tuần, hàng tháng với lượng tính toán lớn
- [[prompt]] là lời nhắc đến model llm thực hiện những việc bạn muốn làm
- [[context]] là bộ nhớ có sẵn cho prompt, nó chứa khoảng vài nghìn từ
- Đầu ra của model gọi là [[completion]]
- Hành động sử dụng model để suy ra văn bản gọi là [[inference]]
# different types of llms
- **Nhận dạng âm thanh và giọng nói**. Với mục đích này, các mô hình kiểu Whisper là một lựa chọn tuyệt vời vì chúng có mục đích chung và nhằm mục đích nhận dạng giọng nói. Nó được đào tạo về âm thanh đa dạng và có thể thực hiện nhận dạng giọng nói đa ngôn ngữ. Tìm hiểu thêm về các mô hình kiểu [[whisper]] tại đây.
- **Tạo hình ảnh**. Để tạo hình ảnh, [[dall-e]] và [[midjourney]] là hai lựa chọn được nhiều người biết đến. [[dall-e]] được cung cấp bởi Azure OpenAI.
- **Tạo văn bản**. Hầu hết các mô hình đều được đào tạo về cách tạo văn bản và bạn có rất nhiều lựa chọn từ GPT-3.5 đến GPT-4. Chúng có nhiều mức giá khác nhau trong đó GPT-4 là đắt nhất. Bạn nên xem xét sân chơi Azure OpenAI để đánh giá mô hình nào phù hợp nhất với nhu cầu của bạn về khả năng và chi phí.
- **Đa phương thức**. Nếu bạn đang tìm cách xử lý nhiều loại dữ liệu ở đầu vào và đầu ra, bạn có thể muốn xem xét các mô hình như [[gpt-4 turbo]] with Vision hoặc [[gpt-4o]] - phiên bản mới nhất của mô hình OpenAI - có khả năng kết hợp xử lý ngôn ngữ tự nhiên đến sự hiểu biết trực quan, cho phép tương tác thông qua các giao diện đa phương thức.
# use case
- Được sử dụng để tóm gọn văn bản dựa vào prompt
- Tạo code thông qua prompt
- Truy xuất thông tin thông qua tài liệu sẵn có
- Tăng cường dữ liệu vào llm để nó có thể tương tác tốt hơn với prompt đã cung cấp
...