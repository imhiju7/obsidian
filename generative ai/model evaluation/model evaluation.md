Trong học máy truyền thống, bạn có thể đánh giá mô hình hoạt động tốt như thế nào bằng cách xem xét hiệu suất của nó trên các tập dữ liệu huấn luyện và xác thực nơi đầu ra đã được biết trước. Bạn có thể tính toán các chỉ số đơn giản như độ chính xác, phản ánh tỷ lệ dự đoán đúng trong tất cả các dự đoán, vì các mô hình này là xác định.

Nhưng với các mô hình ngôn ngữ lớn, nơi đầu ra không xác định và đánh giá ngôn ngữ trở nên khó khăn hơn nhiều.

Hãy lấy ví dụ câu: Mike really loves drinking tea. Câu này khá giống với Mike adores sipping tea. 

Nhưng làm thế nào để bạn đo lường sự giống nhau? 
	- Hãy nhìn vào hai câu này: Mike does not drink coffee và Mike does drink coffee. 
Chỉ có một từ khác nhau giữa hai câu này.

Bây giờ, đối với con người chúng ta với bộ não hữu cơ, chúng ta có thể thấy những điểm giống và khác nhau. Nhưng khi bạn huấn luyện một mô hình trên hàng triệu câu, bạn cần một cách tự động, có cấu trúc để thực hiện các phép đo.

# ROUGE và BLEU
[[unigram]], [[bigram]], [[n-gram]].
![[Pasted image 20240701103242.png]]
- [[rouge]]
- [[bleu]]
- là hai chỉ số đánh giá được sử dụng rộng rãi cho các nhiệm vụ khác nhau.