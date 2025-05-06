Độ lệch KL là một thước đo thống kê về sự khác biệt giữa hai phân phối xác suất. 
![[Pasted image 20240703015801.png]]

Trong PPO, mục tiêu là tìm một chính sách cải thiện cho một tác nhân bằng cách cập nhật các tham số của nó theo từng bước dựa trên các phần thưởng nhận được từ việc tương tác với môi trường. 
Tuy nhiên, cập nhật chính sách quá mạnh có thể dẫn đến việc học không ổn định hoặc thay đổi chính sách quá đáng kể. Để giải quyết điều này, PPO giới thiệu một ràng buộc giới hạn mức độ cập nhật chính sách. Ràng buộc này được thực thi bằng cách sử dụng KL-Divergence.

Để hiểu cách KL-Divergence hoạt động, hãy tưởng tượng chúng ta có hai phân phối xác suất: phân phối của LLM ban đầu và một phân phối mới được đề xuất của LLM được cập nhật bằng RL. KL-Divergence đo lường lượng thông tin trung bình thu được khi chúng ta sử dụng chính sách ban đầu để mã hóa các mẫu từ chính sách mới được đề xuất. 
Bằng cách giảm thiểu KL-Divergence giữa hai phân phối, PPO đảm bảo rằng chính sách được cập nhật ở gần chính sách ban đầu, ngăn chặn các thay đổi quá lớn có thể ảnh hưởng tiêu cực đến quá trình học.

Một thư viện mà bạn có thể sử dụng để huấn luyện các mô hình ngôn ngữ dạng transformer với học tăng cường, sử dụng các kỹ thuật như PPO, là TRL (Transformer Reinforcement Learning).