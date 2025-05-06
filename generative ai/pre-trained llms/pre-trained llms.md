Sau khi bạn đã xác định được trường hợp sử dụng và xác định cách mà LLM sẽ hoạt động trong ứng dụng của bạn, bước tiếp theo là chọn một mô hình để làm việc.Lựa chọn đầu tiên của bạn sẽ là hoặc làm việc với một mô hình hiện có hoặc huấn luyện mô hình của riêng bạn từ đầu.
- Mô hình chính xác mà bạn chọn sẽ phụ thuộc vào các chi tiết của nhiệm vụ bạn cần thực hiện.

LLMs encode một biểu diễn thống kê sâu về ngôn ngữ. Sự hiểu biết này được phát triển trong giai 
đoạn huấn luyện sơ bộ khi mô hình học từ lượng dữ liệu văn bản không có cấu trúc rất lớn

Trong bước học tự giám sát này, mô hình nắm bắt các mẫu và cấu trúc có trong ngôn ngữ. Những mẫu này sau đó cho phép mô hình hoàn thành mục tiêu huấn luyện của mình, điều này phụ thuộc vào kiến trúc của mô hình

Trong giai đoạn huấn luyện sơ bộ, các trọng số của mô hình được cập nhật để giảm thiểu sự mất mát của mục tiêu huấn luyện.

[[encoder]] ra một biểu diễn nhúng hoặc biểu diễn vector cho mỗi token.
![[Pasted image 20240629205701.png]]

- Lưu ý rằng, khi bạn lấy dữ liệu huấn luyện từ các trang web công cộng như Internet, bạn thường cần xử lý dữ liệu để tăng chất lượng, giải quyết thiên kiến và loại bỏ nội dung có hại khác.

# [[encoder-only]] 
được huấn luyện sơ bộ bằng cách sử dụng mô hình ngôn ngữ bị che giấu.
- Ở đây, các token trong chuỗi đầu vào bị che ngẫu nhiên, và mục tiêu huấn luyện là dự đoán các token bị che để tái tạo lại câu ban đầu. Đây cũng được gọi là mục tiêu khử nhiễu
![[Pasted image 20240629211712.png]]

- Các mô hình tự mã hóa xây dựng biểu diễn hai chiều của chuỗi đầu vào, nghĩa là mô hình có sự hiểu biết về toàn bộ ngữ cảnh của một token và không chỉ các từ đi trước.
- Các mô hình chỉ mã hóa lý tưởng cho các nhiệm vụ
	- phân tích cảm xúc
	- nhận dạng thực thể có tên
	- phân loại từ

# [[decoder-only]] 
được huấn luyện sơ bộ bằng cách sử dụng mô hình ngôn ngữ nhân quả
![[Pasted image 20240629224132.png]]
- mục tiêu huấn luyện là dự đoán token tiếp theo dựa trên chuỗi token trước đó. Dự đoán token tiếp theo đôi khi được các nhà nghiên cứu gọi là mô hình ngôn ngữ toàn bộ.
- Các mô hình tự hồi quy chỉ giải mã che chuỗi đầu vào và chỉ có thể nhìn thấy các token đầu vào dẫn đến token đang được xem xét. Mô hình không có kiến thức về kết thúc của câu. Mô hình sau đó lặp lại qua chuỗi đầu vào từng token một để dự đoán token tiếp theo.
- Bằng cách học cách dự đoán token tiếp theo từ số lượng ví dụ rất lớn, mô hình xây dựng lên một biểu diễn thống kê của ngôn ngữ. Các mô hình loại này sử dụng thành phần giải mã của kiến trúc gốc mà không có thành phần mã hóa.
- Các mô hình chỉ giải mã thường được sử dụng để tạo văn bản, mặc dù các mô hình chỉ giải mã lớn hơn thể hiện khả năng suy luận không có mẫu mạnh mẽ và có thể thực hiện tốt một loạt các nhiệm vụ.
# [[encoder-decoder]] 
huấn luyện sơ bộ bộ mã hóa bằng cách sử dụng tham nhũng chuỗi, che ngẫu nhiên các chuỗi token đầu vào.
![[Pasted image 20240629225325.png]]
Những chuỗi bị che sau đó được thay thế bằng một [[token Sentinel]] độc đáo, được hiển thị ở đây là x. Các token Sentinel là các token đặc biệt được thêm vào từ vựng, nhưng không tương ứng với bất kỳ từ nào thực tế từ văn bản đầu vào. Bộ giải mã sau đó có nhiệm vụ tái tạo các chuỗi token bị che tự hồi quy. Đầu ra là token Sentinel theo sau là các token được dự đoán.

Bạn có thể sử dụng các mô hình chuỗi tới chuỗi để dịch, tóm tắt và trả lời câu hỏi. Chúng thường hữu ích trong các trường hợp bạn có một tập văn bản làm cả đầu vào và đầu ra.

![[Pasted image 20240629225555.png]]\