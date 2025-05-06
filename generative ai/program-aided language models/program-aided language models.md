- mô hình thực tế không thực hiện bất kỳ phép toán nào ở đây. Nó chỉ đơn giản cố gắng dự đoán các token có khả năng nhất để hoàn thành lời nhắc.
- Bạn có thể khắc phục hạn chế này bằng cách cho phép mô hình của bạn tương tác với các ứng dụng bên ngoài tốt về toán học, như một trình thông dịch Python. Một khung thú vị để tăng cường LLM theo cách này được gọi là program-aided language models, hay PAL viết tắt.
![[Pasted image 20240705013444.png]]
Chiến lược đằng sau PAL là để LLM tạo ra các hoàn thành mà các bước suy luận đi kèm với mã máy tính. Mã này sau đó được truyền cho một trình thông dịch để thực hiện các phép toán cần thiết để giải quyết vấn đề. Bạn chỉ định định dạng đầu ra cho mô hình bằng cách bao gồm các ví dụ cho suy luận một hoặc vài lần trong lời nhắc.

Làm việc với câu chuyện về Roger mua bóng tennis như một ví dụ một lần.
![[Pasted image 20240705015156.png]]
Đây là một ví dụ chain of thought. 
- Bạn có thể thấy các bước suy luận được viết ra bằng lời trên các dòng được đánh dấu màu xanh lam. 
- Điều khác biệt so với các lời nhắc bạn đã thấy trước đó là sự bao gồm các dòng mã Python được hiển thị bằng màu hồng. Những dòng này dịch bất kỳ bước suy luận nào liên quan đến các phép toán thành mã. Các biến được khai báo dựa trên văn bản trong mỗi bước suy luận.
- Giá trị của chúng được gán trực tiếp, như trong dòng mã đầu tiên ở đây, hoặc dưới dạng các phép toán sử dụng các số có trong văn bản suy luận như bạn thấy trong dòng Python thứ hai. 
- Mô hình cũng có thể làm việc với các biến nó tạo ra trong các bước khác, như bạn thấy trong dòng thứ ba. 
- Lưu ý rằng văn bản của mỗi bước suy luận bắt đầu bằng dấu thăng, để dòng này có thể được bỏ qua dưới dạng nhận xét bởi trình thông dịch Python.

Bây giờ bạn biết cách cấu trúc các ví dụ sẽ yêu cầu LLM viết các script Python dựa trên các bước suy luận của nó, hãy xem lại cách khung PAL cho phép một LLM tương tác với một trình thông dịch bên ngoài.
Để chuẩn bị cho suy luận với PAL, bạn sẽ định dạng lời nhắc của mình để chứa một hoặc nhiều ví dụ. Mỗi ví dụ nên chứa một câu hỏi theo sau là các bước suy luận trong các dòng mã Python giải quyết vấn đề.
Tiếp theo, bạn sẽ thêm câu hỏi mới mà bạn muốn trả lời vào mẫu lời nhắc. Lời nhắc định dạng PAL kết quả của bạn bây giờ chứa cả ví dụ và vấn đề cần giải quyết.
Tiếp theo, bạn sẽ truyền lời nhắc kết hợp này cho LLM của bạn, mô hình này sau đó tạo ra một hoàn thành dưới dạng một script Python sau khi đã học cách định dạng đầu ra dựa trên ví dụ trong lời nhắc.
Bây giờ bạn có thể chuyển script cho một trình thông dịch Python, bạn sẽ sử dụng để chạy mã và tạo ra một câu trả lời.
![[Pasted image 20240705020745.png]]
Bộ điều phối được hiển thị ở đây dưới dạng hộp màu vàng là một thành phần kỹ thuật có thể quản lý luồng thông tin và việc khởi tạo các cuộc gọi đến các nguồn dữ liệu bên ngoài hoặc ứng dụng.
![[Pasted image 20240705020930.png]]
Nó cũng có thể quyết định các hành động cần thực hiện dựa trên thông tin chứa trong đầu ra của LLM. Hãy nhớ rằng, LLM là động cơ suy luận của ứng dụng của bạn. Cuối cùng, nó tạo ra kế hoạch mà bộ điều phối sẽ diễn giải và thực thi.

Trong PAL chỉ có một hành động cần được thực hiện, đó là thực thi mã [[python]]. LLM thực sự không cần phải quyết định chạy mã, nó chỉ cần viết script mà bộ điều phối sau đó chuyển cho trình thông dịch bên ngoài để chạy.