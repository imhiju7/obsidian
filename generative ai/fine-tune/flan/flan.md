- fine-tuned language net là một tập hợp các chỉ dẫn cụ thể được sử dụng để điều chỉnh các mô hình khác nhau.
- FLAN-T5, phiên bản chỉ dẫn FLAN của mô hình nền tảng T5
- FLAN-T5 là một mô hình chỉ dẫn đa dụng tuyệt vời. Tổng cộng, nó đã được điều chỉnh trên 473 tập dữ liệu qua 146 danh mục nhiệm vụ. Các tập dữ liệu đó được chọn từ các mô hình và bài báo khác như được hiển thị ở đây.
- Nếu bạn quan tâm, bạn có thể truy cập bài báo gốc thông qua bài tập đọc sau video và xem xét kỹ hơn. Một ví dụ về tập dữ liệu gợi ý được sử dụng cho các nhiệm vụ tóm tắt trong FLAN-T5 là SAMSum. Nó là một phần của bộ sưu tập nhiệm vụ và tập dữ liệu muffin và được sử dụng để huấn luyện các mô hình ngôn ngữ để tóm tắt đối thoại. SAMSum là một tập dữ liệu với 16,000 cuộc trò chuyện giống như trên Messenger với các bản tóm tắt.

Sau đó, các chuyên gia ngôn ngữ đã tạo ra các bản tóm tắt ngắn gọn về những cuộc trò chuyện đó bao gồm các thông tin quan trọng và tên của những người trong cuộc trò chuyện. Đây là một mẫu gợi ý được thiết kế để hoạt động với tập dữ liệu tóm tắt đối thoại SAMSum. Mẫu này thực sự bao gồm nhiều chỉ dẫn khác nhau mà tất cả đều yêu cầu mô hình làm cùng một việc, tóm tắt một cuộc đối thoại

![[Pasted image 20240701084553.png]]

Ví dụ, tóm tắt ngắn gọn cuộc đối thoại đó. Bản tóm tắt của cuộc đối thoại này là gì? Chuyện gì đã xảy ra trong cuộc trò chuyện đó? 
Bao gồm các cách diễn đạt khác nhau của cùng một chỉ dẫn giúp mô hình tổng quát hóa và thực hiện tốt hơn. Giống như các mẫu gợi ý bạn đã thấy trước đó.

Bạn thấy rằng trong mỗi trường hợp, cuộc trò chuyện từ tập dữ liệu SAMSum được chèn vào mẫu bất cứ khi nào trường đối thoại xuất hiện. Bản tóm tắt được sử dụng làm nhãn. 
Sau khi áp dụng mẫu này cho từng hàng trong tập dữ liệu SAMSum, bạn có thể sử dụng nó để điều chỉnh nhiệm vụ tóm tắt đối thoại.

Trong thực tế, bạn sẽ đạt được kết quả tốt nhất bằng cách sử dụng dữ liệu nội bộ của công ty bạn. Ví dụ, các cuộc trò chuyện hỗ trợ từ ứng dụng hỗ trợ khách hàng của bạn. Điều này sẽ giúp mô hình học được các chi tiết cụ thể về cách công ty bạn thích tóm tắt các cuộc trò chuyện và điều gì là hữu ích nhất cho đồng nghiệp dịch vụ khách hàng của bạn.