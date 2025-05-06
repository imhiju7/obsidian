![[Pasted image 20240702201213.png]]
Giả sử một số prompt được đưa ra. Đầu tiên, bạn tạo ra các phản hồi LLM cho các prompt, sau đó bạn tính cho các hoàn thành prompt sử dụng [[reward model]]. Ví dụ, hoàn thành prompt đầu tiên được hiển thị ở đây có thể nhận được phần thưởng là 1.87. Cái tiếp theo có thể nhận được phần thưởng là -1.24, và cứ tiếp tục. Bạn có một tập hợp các [[completion prompt]] và các phần thưởng tương ứng của chúng.

hàm giá trị ước tính phần thưởng tổng cộng kỳ vọng cho một trạng thái nhất định S.
![[Pasted image 20240702201532.png]]
Nói cách khác, khi LLM tạo ra mỗi token của một hoàn thành, bạn muốn ước tính phần thưởng tương lai tổng cộng dựa trên chuỗi token hiện tại. Bạn có thể nghĩ điều này như một cơ sở để đánh giá chất lượng của các hoàn thành so với các tiêu chí căn chỉnh của bạn.

Giả sử rằng ở bước này của hoàn thành, phần thưởng tương lai tổng cộng ước tính là 0.34. Với token tiếp theo được tạo ra, phần thưởng tương lai tổng cộng ước tính tăng lên 1.23. Mục tiêu là giảm thiểu tổn thất giá trị, đó là sự khác biệt giữa phần thưởng tương lai tổng cộng thực tế trong 
![[Pasted image 20240702201804.png]]
ví dụ này, 1.87, và sự xấp xỉ của nó với hàm giá trị, trong ví dụ này, 1.23. Tổn thất giá trị làm cho các ước tính về phần thưởng tương lai chính xác hơn. Hàm giá trị sau đó được sử dụng trong Ước lượng Lợi thế trong Giai đoạn 2. Điều này giống như khi bạn bắt đầu viết một đoạn văn, và bạn có một ý tưởng sơ bộ về hình thức cuối cùng của nó ngay cả trước khi bạn viết.