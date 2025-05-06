Hãy nhớ, bạn muốn bắt đầu với một mô hình đã có hiệu suất tốt trên nhiệm vụ mà bạn quan tâm. Bạn sẽ làm việc để căn chỉnh một mô hình hướng dẫn và LLM.
- Đầu tiên, bạn sẽ gửi một prompt từ tập dữ liệu prompt của bạn. Trong trường hợp này, là "a dog is," đến mô hình LLM hướng dẫn, sau đó nó sẽ tạo ra một hoàn thành, trong trường hợp này là "a furry animal."
![[Pasted image 20240702165223.png]]
Tiếp theo, bạn gửi hoàn thành này và prompt gốc đến mô hình thưởng như một cặp prompt-hoàn thành. Mô hình thưởng đánh giá cặp dựa trên phản hồi của con người mà nó đã được huấn luyện, và trả về một giá trị thưởng. Một giá trị cao hơn, chẳng hạn như 0.24 như được hiển thị ở đây, đại diện cho một phản hồi được căn chỉnh tốt hơn.
![[Pasted image 20240702165521.png]]
Bạn sẽ sau đó gửi giá trị thưởng này cho cặp prompt-hoàn thành đến thuật toán học tăng cường để cập nhật các trọng số của LLM
![[Pasted image 20240702165621.png]]
và di chuyển nó hướng tới việc tạo ra các phản hồi được căn chỉnh tốt hơn, có giá trị thưởng cao hơn. Hãy gọi phiên bản trung gian này của mô hình là LLM cập nhật bằng RL.
![[Pasted image 20240702165729.png]]
Các bước này cùng nhau tạo thành một lần lặp của quá trình RLHF.
![[Pasted image 20240702165808.png]]
Các lần lặp này tiếp tục trong một số lượng epoch nhất định, giống như các loại tinh chỉnh khác. Ở đây, bạn có thể thấy rằng hoàn thành được tạo ra bởi LLM cập nhật bằng RL nhận được điểm thưởng cao hơn, cho thấy rằng các cập nhật về trọng số đã dẫn đến một hoàn thành được căn chỉnh tốt hơn. Nếu quá trình hoạt động tốt, bạn sẽ thấy điểm thưởng cải thiện sau mỗi lần lặp khi mô hình tạo ra văn bản ngày càng được căn chỉnh với sở thích của con người.
![[Pasted image 20240702165857.png]]
Bạn sẽ tiếp tục quá trình lặp này cho đến khi mô hình của bạn được căn chỉnh dựa trên một số tiêu chí đánh giá. Ví dụ, đạt đến một giá trị ngưỡng về sự hữu ích mà bạn đã xác định. Bạn cũng có thể định nghĩa một số bước tối đa, chẳng hạn như 20.000, làm tiêu chí dừng.
![[Pasted image 20240702165938.png]]
Tại thời điểm này, hãy gọi mô hình đã tinh chỉnh là LLM căn chỉnh với con người.

Một chi tiết mà chúng ta chưa thảo luận là bản chất chính xác của thuật toán [[reinforcement learing]]. Đây là thuật toán lấy đầu ra của mô hình thưởng và sử dụng nó để cập nhật các trọng số của mô hình LLM để điểm thưởng tăng theo thời gian.

Có nhiều thuật toán khác nhau mà bạn có thể sử dụng cho phần này của quá trình RLHF. Một lựa chọn phổ biến là tối ưu hóa chính sách tiệm cận ([[proximal policy optimization]]) hay PPO.