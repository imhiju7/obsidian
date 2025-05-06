- ReAct là một chiến lược [[chain of thought prompting]] với lập kế hoạch hành động.
![[Pasted image 20240705131206.png]]
Bài báo phát triển một loạt các ví dụ nhắc nhở phức tạp dựa trên các vấn đề từ Hot Pot QA, một tiêu chuẩn trả lời câu hỏi nhiều bước yêu cầu suy luận qua hai hoặc nhiều đoạn Wikipedia và fever, một tiêu chuẩn sử dụng các đoạn Wikipedia để xác minh sự thật.
![[Pasted image 20240705141006.png]]
ReAct sử dụng các ví dụ có cấu trúc để chỉ cho một mô hình ngôn ngữ lớn cách suy luận qua một vấn đề và xác định các hành động cần thực hiện để tiến gần hơn đến giải pháp. Các ví dụ nhắc nhở bắt đầu với một câu hỏi sẽ yêu cầu nhiều bước để trả lời.

Trong ví dụ về xuất bản báo chí, lời nhắc xác định rằng mô hình sẽ tìm kiếm cả hai tạp chí và xác định tạp chí nào được xuất bản trước. Để mô hình tương tác với một ứng dụng hoặc nguồn dữ liệu bên ngoài, nó phải xác định một hành động từ một danh sách định trước.
![[Pasted image 20240705131820.png]]
Trong trường hợp của khung ReAct, các tác giả đã tạo một API Python nhỏ để tương tác với Wikipedia. Ba hành động được phép là tìm kiếm, tìm kiếm một mục Wikipedia về một chủ đề cụ thể; tra cứu, tìm kiếm một chuỗi trên một trang Wikipedia; và kết thúc, mà mô hình thực hiện khi nó quyết định rằng nó đã xác định được câu trả lời.

![[Pasted image 20240705133546.png]]
- Trước tiên, nhiệm vụ được xác định, yêu cầu mô hình trả lời một câu hỏi bằng cách sử dụng cấu trúc nhắc nhở mà bạn vừa khám phá chi tiết. 
- Tiếp theo, các hướng dẫn đưa ra thêm chi tiết về suy nghĩ và sau đó xác định rằng bước hành động chỉ có thể là một trong ba loại. 
	- Đầu tiên là hành động tìm kiếm, tìm kiếm các mục Wikipedia liên quan đến thực thể được chỉ định. 
	- Thứ hai là hành động tra cứu, lấy câu tiếp theo chứa từ khóa được chỉ định. 
	- Hành động cuối cùng là kết thúc, trả lời và kết thúc nhiệm vụ. 
Điều quan trọng là phải xác định một tập hợp các hành động được phép khi sử dụng LLMs để lên kế hoạch cho các nhiệm vụ sẽ điều khiển các ứng dụng. LLMs rất sáng tạo và chúng có thể đề xuất thực hiện các bước không thực sự tương ứng với những gì ứng dụng có thể làm. Câu cuối cùng trong các hướng dẫn cho LLM biết rằng một số ví dụ sẽ được đưa vào tiếp theo trong văn bản nhắc nhở.
![[Pasted image 20240705135033.png]]
Lưu ý rằng tùy thuộc vào LLM mà bạn đang làm việc, bạn có thể cần bao gồm nhiều hơn một ví dụ và thực hiện suy luận trong tương lai. Tiếp theo, bạn sẽ gắn thêm các hướng dẫn vào đầu ví dụ và sau đó chèn câu hỏi mà bạn muốn trả lời vào cuối. Lời nhắc đầy đủ bây giờ bao gồm tất cả các phần riêng lẻ này và có thể được chuyển đến LLM để suy luận.
May mắn thay, các khung phát triển ứng dụng sử dụng các mô hình ngôn ngữ đang được phát triển tích cực. Một giải pháp đang được áp dụng rộng rãi được gọi là [[langchain]]. 