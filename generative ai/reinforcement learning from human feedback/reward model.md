Mô hình thưởng sẽ hiệu quả thay thế cho người gán nhãn và tự động chọn hoàn thành được ưa thích trong quá trình RLHF. Mô hình thưởng này thường cũng là một mô hình ngôn ngữ.

![[Pasted image 20240702155159.png]]
Đối với một prompt X cụ thể, mô hình thưởng học cách ưu tiên hoàn thành được con người ưa thích y_j, trong khi giảm thiểu log sigmoid của sự khác biệt giữa các điểm thưởng, r_j - r_k.

Sau khi mô hình đã được huấn luyện trên các cặp prompt-hoàn thành được xếp hạng của con người, bạn có thể sử dụng mô hình thưởng như một bộ phân loại nhị phân để cung cấp một tập hợp các logits cho các lớp tích cực và tiêu cực. Logits là các đầu ra chưa được chuẩn hóa của mô hình trước khi áp dụng bất kỳ hàm kích hoạt nào.
![[Pasted image 20240702155507.png]]
Giả sử bạn muốn làm sạch độc tính cho LLM của mình, và mô hình thưởng cần phải xác định xem hoàn thành có chứa ngôn từ thù địch hay không. Trong trường hợp này, hai lớp sẽ là không thù địch, lớp tích cực mà bạn cuối cùng muốn tối ưu hóa và thù địch, lớp tiêu cực mà bạn muốn tránh. Giá trị lớn nhất của lớp tích cực là giá trị thưởng mà bạn sử dụng trong LLHF. Để nhắc bạn, nếu bạn áp dụng hàm Softmax lên logits, bạn sẽ nhận được các xác suất. Ví dụ ở đây cho thấy một phần thưởng tốt cho hoàn thành không độc hại và ví dụ thứ hai cho thấy một phần thưởng xấu được đưa ra cho hoàn thành độc hại.
- [[reward hacking]]