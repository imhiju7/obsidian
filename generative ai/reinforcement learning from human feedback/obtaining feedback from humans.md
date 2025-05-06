- khi bắt đầu với một mô hình hướng dẫn đã được tinh chỉnh trên nhiều nhiệm vụ và có một số khả năng chung. Bạn sẽ sử dụng LLM này cùng với một tập dữ liệu prompt để tạo ra một số phản hồi khác nhau cho mỗi prompt. Tập dữ liệu prompt bao gồm nhiều prompt, mỗi prompt sẽ được xử lý bởi LLM để tạo ra một tập hợp các hoàn thành.
- Bước tiếp theo là thu thập phản hồi từ những người gán nhãn trên các hoàn thành do LLM tạo ra. Đây là phần phản hồi của con người trong học tăng cường với phản hồi của con người. 
	- Trước tiên, bạn phải quyết định tiêu chí mà bạn muốn con người đánh giá các hoàn thành. Điều này có thể là bất kỳ vấn đề nào đã được thảo luận như sự hữu ích hay độ độc hại. 
	- Sau khi đã quyết định, bạn sẽ yêu cầu những người gán nhãn đánh giá từng hoàn thành trong tập dữ liệu dựa trên tiêu chí đó.

Trong trường hợp này, prompt là "nhà của tôi quá nóng". Bạn gửi prompt này cho LLM, sau đó nó tạo ra ba hoàn thành khác nhau. Nhiệm vụ của những người gán nhãn là xếp hạng ba hoàn thành theo mức độ hữu ích từ hữu ích nhất đến ít hữu ích nhất.
![[Pasted image 20240702133926.png]]
- Ở đây, người gán nhãn có thể quyết định rằng hoàn thành thứ hai là hữu ích nhất. Nó đưa ra cho người dùng một giải pháp thực tế để làm mát nhà và xếp hạng hoàn thành này đầu tiên. 
- Cả hoàn thành thứ nhất và thứ ba đều không hữu ích lắm, nhưng có lẽ người gán nhãn sẽ quyết định rằng hoàn thành thứ ba là tệ nhất vì mô hình chủ động phản đối ý kiến của người dùng. Vì vậy, người gán nhãn xếp hạng hoàn thành đầu tiên thứ hai và hoàn thành cuối cùng thứ ba.
Quá trình này sau đó được lặp lại cho nhiều tập hợp hoàn thành prompt, xây dựng lên một tập dữ liệu có thể được sử dụng để huấn luyện mô hình thưởng sẽ thực hiện công việc này thay cho con người. 

Các tập hợp hoàn thành prompt thường được giao cho nhiều người gán nhãn để thiết lập sự đồng thuận và giảm thiểu tác động của những người gán nhãn kém trong nhóm. Như người gán nhãn thứ ba ở đây, người có phản hồi không đồng ý với những người khác và có thể cho thấy rằng họ đã hiểu sai hướng dẫn.
![[Pasted image 20240702134233.png]]
Đây thực sự là một điểm quan trọng. Sự rõ ràng của hướng dẫn của bạn có thể tạo ra sự khác biệt lớn về chất lượng phản hồi của con người mà bạn nhận được. 
Những người gán nhãn thường được chọn từ các mẫu của dân số đại diện cho suy nghĩ đa dạng và toàn cầu.

Dưới đây là một ví dụ về tập hợp hướng dẫn được viết cho những người gán nhãn. Đây sẽ được trình bày cho người gán nhãn đọc trước khi bắt đầu nhiệm vụ và luôn có sẵn để họ tham khảo trong quá trình làm việc qua tập dữ liệu.
![[Pasted image 20240702134542.png]]
- Hướng dẫn bắt đầu với nhiệm vụ tổng thể mà người gán nhãn cần thực hiện. Trong trường hợp này, là chọn hoàn thành tốt nhất cho prompt. 
- Hướng dẫn tiếp tục với các chi tiết bổ sung để hướng dẫn người gán nhãn cách hoàn thành nhiệm vụ. 
	- Nhìn chung, bạn càng làm rõ chi tiết hướng dẫn này, khả năng cao là những người gán nhãn sẽ hiểu nhiệm vụ mà họ phải thực hiện và hoàn thành nó chính xác như bạn mong muốn. 
	- Ví dụ, trong mục hướng dẫn thứ hai, những người gán nhãn được yêu cầu đưa ra quyết định dựa trên nhận thức của họ về tính đúng đắn và thông tin của phản hồi. Họ được yêu cầu có thể sử dụng Internet để kiểm tra thực tế và tìm kiếm thông tin khác.
- Họ cũng nhận được hướng dẫn rõ ràng về những gì cần làm nếu họ phát hiện ra một sự ràng buộc, nghĩa là một cặp hoàn thành mà họ cho rằng đúng và thông tin như nhau. Những người gán nhãn được cho phép xếp hạng hai hoàn thành như nhau, nhưng họ nên làm điều này một cách tiết kiệm.
- Một hướng dẫn cuối cùng đáng lưu ý ở đây là làm gì trong trường hợp có câu trả lời vô nghĩa, gây nhầm lẫn hoặc không liên quan. Trong trường hợp này, người gán nhãn nên chọn F thay vì xếp hạng, để các câu trả lời chất lượng kém có thể được loại bỏ dễ dàng.
- Việc cung cấp một tập hợp hướng dẫn chi tiết như thế này làm tăng khả năng các phản hồi sẽ có chất lượng cao và các cá nhân sẽ thực hiện nhiệm vụ theo cách tương tự nhau. Điều này có thể giúp đảm bảo rằng tập hợp các hoàn thành được gán nhãn sẽ đại diện cho quan điểm đồng thuận.

Khi những người gán nhãn của bạn đã hoàn thành việc đánh giá các tập hợp hoàn thành prompt, bạn sẽ có tất cả dữ liệu cần thiết để huấn luyện mô hình thưởng. Mô hình này sẽ được sử dụng thay cho con người để phân loại các hoàn thành mô hình trong quá trình tinh chỉnh học tăng cường.

Trước khi bắt đầu huấn luyện mô hình thưởng, tuy nhiên, bạn cần chuyển đổi dữ liệu xếp hạng thành so sánh cặp đôi của các hoàn thành. Nói cách khác, tất cả các cặp đôi hoàn thành có thể có từ các lựa chọn có sẵn cho một prompt nên được phân loại là 0 hoặc 1 điểm.
![[Pasted image 20240702135141.png]]
Trong ví dụ được hiển thị ở đây, có ba hoàn thành cho một prompt, và xếp hạng được gán bởi những người gán nhãn là 2, 1, 3 như đã chỉ ra, nơi 1 là xếp hạng cao nhất tương ứng với phản hồi được ưa thích nhất. 
Với ba hoàn thành khác nhau, có ba cặp đôi có thể: tím-vàng, tím-xanh lá và vàng-xanh lá. Tùy thuộc vào số lượng N của các hoàn thành thay thế cho mỗi prompt, bạn sẽ có N chọn hai tổ hợp. Đối với mỗi cặp, bạn sẽ gán một điểm thưởng là 1 cho phản hồi được ưa thích và một điểm thưởng là 0 cho phản hồi ít được ưa thích hơn. 
Sau đó, bạn sẽ sắp xếp lại các prompt sao cho lựa chọn được ưa thích xuất hiện trước. Đây là một bước quan trọng vì mô hình thưởng mong đợi hoàn thành được ưa thích, được gọi là Yj, xuất hiện trước. 
Sau khi hoàn thành việc cấu trúc lại dữ liệu này, các phản hồi của con người sẽ ở định dạng chính xác để huấn luyện mô hình thưởng. Lưu ý rằng trong khi phản hồi kiểu like-dislike thường dễ thu thập hơn so với phản hồi xếp hạng, phản hồi xếp hạng cung cấp cho bạn nhiều dữ liệu hoàn thành prompt hơn để huấn luyện mô hình thưởng của bạn. 
Như bạn có thể thấy, ở đây bạn nhận được ba cặp hoàn thành prompt từ mỗi phản hồi xếp hạng của con người.