# scaling laws
- mục tiêu trong quá trình tiền huấn luyện là tối đa hóa hiệu suất của mô hình đối với mục tiêu học tập của nó, đó là giảm thiểu mất mát khi dự đoán các token.
- Hai tùy chọn bạn có để đạt được hiệu suất tốt hơn là 
	- tăng kích thước của tập dữ liệu mà bạn huấn luyện mô hình của mình 
	- tăng số lượng tham số trong mô hình của bạn.
- một vấn đề khác cần xem xét là ngân sách tính toán của bạn bao gồm các yếu tố như số lượng GPU bạn có và thời gian bạn có sẵn để huấn luyện mô hình.
[1] T. B. Brown _et al._, “Language Models are Few-Shot Learners.” arXiv, Jul. 22, 2020. 
![[Pasted image 20240630141003.png]]
Biểu đồ này làm rõ rằng một lượng lớn tính toán là cần thiết để huấn luyện các mô hình lớn nhất. 
Bạn có thể thấy rằng các mô hình lớn hơn cần nhiều tài nguyên tính toán hơn để huấn luyện và thường cũng yêu cầu nhiều dữ liệu hơn để đạt được hiệu suất tốt.

![[Pasted image 20240630142817.png]]
- Trục y là mất mát thử nghiệm, mà bạn có thể xem như một proxy cho hiệu suất mô hình, nơi các giá trị nhỏ hơn là tốt hơn.
- Trục x là ngân sách tính toán bằng đơn vị petaFLOP mỗi giây mỗi ngày.

các số lớn hơn có thể đạt được bằng cách sử dụng nhiều sức mạnh tính toán hơn hoặc huấn luyện trong thời gian dài hơn hoặc cả hai. Mỗi dòng xanh mỏng ở đây cho thấy sự mất mát của mô hình trong suốt một lần huấn luyện. Nhìn vào nơi mà sự mất mát bắt đầu giảm chậm hơn cho mỗi lần huấn luyện, tiết lộ một mối quan hệ rõ ràng giữa ngân sách tính toán và hiệu suất mô hình.

Điều này có thể được ước lượng bằng một mối quan hệ lũy thừa, được hiển thị bởi đường màu hồng này. Mối quan hệ lũy thừa là một mối quan hệ toán học giữa hai biến, nơi một biến tỷ lệ thuận với biến kia được nâng lên một số mũ nào đó.

![[Pasted image 20240630145029.png]]
Nếu bạn giữ ngân sách tính toán cố định, hai đòn bẩy bạn có để cải thiện hiệu suất mô hình là kích thước của tập dữ liệu huấn luyện và số lượng tham số trong mô hình của bạn.

![[Pasted image 20240630145239.png]]

Ở đây, ngân sách tính toán và kích thước mô hình được giữ cố định và kích thước của tập dữ liệu huấn luyện được thay đổi. Biểu đồ cho thấy khi khối lượng dữ liệu huấn luyện tăng lên, hiệu suất của mô hình tiếp tục cải thiện.

![[Pasted image 20240630145634.png]]
Trong biểu đồ thứ hai, ngân sách tính toán và kích thước tập dữ liệu huấn luyện được giữ cố định. Các mô hình với số lượng tham số khác nhau được huấn luyện. Khi mô hình tăng kích thước, mất mát thử nghiệm giảm xuống cho thấy hiệu suất tốt hơn.
# Compute-Optimal Large Language Models
[1] J. Hoffmann _et al._, “Training Compute-Optimal Large Language Models.” arXiv, Mar. 29, 2022.
Bài báo Chinchilla gợi ý rằng nhiều mô hình ngôn ngữ lớn với hàng trăm tỷ tham số như GPT-3 có thể thực sự bị quá tải tham số, có nghĩa là chúng có nhiều tham số hơn mức cần thiết để đạt được hiểu biết tốt về ngôn ngữ và được huấn luyện chưa đủ để chúng sẽ có lợi từ việc thấy nhiều dữ liệu huấn luyện hơn.
![[Pasted image 20240630150947.png]]

Các tác giả giả thuyết rằng các mô hình nhỏ hơn có thể đạt được hiệu suất tương đương với các mô hình lớn hơn nhiều nếu chúng được huấn luyện trên các tập dữ liệu lớn hơn.

![[Pasted image 20240630163409.png]]

Một kết luận quan trọng từ bài báo Chinchilla là kích thước tập dữ liệu huấn luyện tối ưu cho một mô hình nhất định là khoảng 20 lần lớn hơn số lượng tham số trong mô hình. Chinchilla được xác định là mô hình tối ưu về tính toán.
- Đối với một mô hình có 70 tỷ tham số, tập dữ liệu huấn luyện lý tưởng chứa 1,4 nghìn tỷ token hoặc gấp 20 lần số lượng tham số. 
- Ba mô hình cuối cùng trong bảng được huấn luyện trên các tập dữ liệu nhỏ hơn so với kích thước tối ưu Chinchilla. Những mô hình này có thể thực sự bị huấn luyện chưa đủ. 
- Ngược lại, LLaMA được huấn luyện trên tập dữ liệu có kích thước 1,4 nghìn tỷ token, gần với số lượng được khuyến nghị bởi Chinchilla.
bạn có thể kỳ vọng sẽ thấy sự lệch khỏi xu hướng lớn hơn là tốt hơn trong vài năm qua khi nhiều nhóm hoặc nhà phát triển như bạn bắt đầu tối ưu hóa thiết kế mô hình của mình.