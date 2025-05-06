PPO là một thuật toán khá phức tạp, và bạn không cần phải quen thuộc với tất cả các chi tiết để có thể sử dụng nó. Tuy nhiên, nó có thể là một thuật toán khó triển khai và hiểu rõ hơn về cách hoạt động của nó có thể giúp bạn khắc phục sự cố nếu gặp vấn đề khi triển khai.
![[Pasted image 20240702170259.png]]
PPO tối ưu hóa một chính sách, trong trường hợp này là LLM, để được căn chỉnh hơn với sở thích của con người. Qua nhiều lần lặp, PPO thực hiện các cập nhật nhỏ cho LLM. Các cập nhật này nhỏ và trong một vùng giới hạn, kết quả là một LLM cập nhật gần với phiên bản trước đó, do đó có tên là Proximal Policy Optimization. Giữ các thay đổi trong vùng nhỏ này dẫn đến việc học ổn định hơn. Mục tiêu là cập nhật chính sách sao cho điểm thưởng được tối đa hóa.

Bạn bắt đầu PPO với LLM hướng dẫn ban đầu của mình, sau đó ở mức cao, mỗi chu kỳ của PPO đi qua hai giai đoạn.
- Trong Giai đoạn I, LLM được sử dụng để thực hiện một số thí nghiệm, hoàn thành các prompt đã cho. Những thí nghiệm này cho phép bạn cập nhật LLM dựa trên [[reward model]] trong Giai đoạn II.
	- Nhớ rằng [[reward model]] nắm bắt các sở thích của con người. Ví dụ, phần thưởng có thể xác định mức độ hữu ích, vô hại và trung thực của các phản hồi. Phần thưởng kỳ vọng của một hoàn thành là một đại lượng quan trọng được sử dụng trong mục tiêu PPO. Chúng tôi ước tính đại lượng này thông qua một đầu riêng biệt của LLM gọi là [[value function]].
		![[Pasted image 20240702201012.png]]

Hãy cùng xem xét kỹ hơn [[value function]] và [[value loss]]

Trong Giai đoạn 2, bạn thực hiện các cập nhật nhỏ cho mô hình và đánh giá tác động của những cập nhật này đối với mục tiêu căn chỉnh của mô hình. Các cập nhật trọng số của mô hình được hướng dẫn bởi các [[completion prompt]], tổn thất và phần thưởng
- Các cập nhật trọng số của mô hình được hướng dẫn bởi các [[completion prompt]], tổn thất và phần thưởng. PPO cũng đảm bảo giữ các cập nhật mô hình trong một vùng nhỏ nhất định gọi là vùng tin cậy. Đây là nơi khía cạnh tiệm cận của PPO xuất hiện. Lý tưởng nhất, chuỗi các cập nhật nhỏ này sẽ di chuyển mô hình hướng tới các phần thưởng cao hơn.
- mục tiêu là tìm một chính sách có phần thưởng kỳ vọng cao. Nói cách khác, bạn đang cố gắng thực hiện các cập nhật cho trọng số của LLM để các hoàn thành được căn chỉnh tốt hơn với sở thích của con người và do đó nhận được phần thưởng cao hơn.
- [[policy loss]] là mục tiêu chính mà thuật toán PPO cố gắng tối ưu hóa trong quá trình huấn luyện.

Tóm lại, tối ưu hóa mục tiêu chính sách PPO dẫn đến một LLM tốt hơn mà không vượt quá vùng đáng tin cậy.

Bạn cũng có [[entropy loss]]. Trong khi tổn thất chính sách di chuyển mô hình hướng tới mục tiêu căn chỉnh, entropy cho phép mô hình duy trì tính sáng tạo.

Tập hợp tất cả các thành phần lại như một tổng trọng số, chúng ta có mục tiêu PPO của mình, cập nhật mô hình hướng tới sở thích của con người một cách ổn định.
![[Pasted image 20240702220310.png]]
Các hệ số C1 và C2 là các siêu tham số. Mục tiêu PPO cập nhật trọng số của mô hình thông qua [[backpropagation]] qua một số bước. Một khi các trọng số của mô hình được cập nhật, PPO bắt đầu một chu kỳ mới. Cho lần lặp tiếp theo, LLM được thay thế bằng LLM cập nhật, và một chu kỳ PPO mới bắt đầu. Sau nhiều lần lặp, bạn đạt được LLM căn chỉnh với con người.