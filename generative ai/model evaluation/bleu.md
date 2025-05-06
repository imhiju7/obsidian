- BLEU hay Bilingual Evaluation Understudy là một thuật toán được thiết kế để đánh giá chất lượng của văn bản dịch máy, cũng bằng cách so sánh nó với các bản dịch do con người tạo ra.
- Điểm số này được tính toán bằng cách sử dụng độ chính xác trung bình trên nhiều kích thước n-gram.

Điểm BLEU định lượng chất lượng của một bản dịch bằng cách kiểm tra xem có bao nhiêu n-gram trong bản dịch do máy tạo ra khớp với những n-gram trong bản dịch tham chiếu. Để tính toán điểm số này, bạn lấy độ chính xác trung bình trên một loạt các kích thước n-gram khác nhau. Nếu bạn tính toán điều này bằng tay, bạn sẽ thực hiện nhiều phép tính và sau đó lấy trung bình tất cả các kết quả để tìm điểm BLEU.

![[Pasted image 20240701105528.png]]

Tính toán điểm BLEU rất dễ dàng với các thư viện được viết sẵn từ các nhà cung cấp như Hugging Face và tôi đã làm điều đó cho từng câu ứng viên của chúng ta. Câu ứng viên đầu tiên là: "I am very happy that I am drinking a cup of tea." Điểm BLEU là 0.495. Khi chúng ta càng gần và gần hơn với câu gốc, điểm số sẽ càng gần và gần hơn với một.