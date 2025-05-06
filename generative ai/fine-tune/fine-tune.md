- fine-tune là một quá trình thúc đẩy việc học chuyển giao để 'điều chỉnh' mô hình cho phù hợp với nhiệm vụ tiếp theo hoặc để giải quyết một vấn đề cụ thể. Khác với phương pháp [[few-shot learning]] và [[rag]], nó tạo ra một mô hình mới với các trọng số và độ lệch được cập nhật. Nó yêu cầu một tập hợp các ví dụ huấn luyện bao gồm một đầu vào duy nhất ([[prompt]]) và đầu ra liên quan của nó ([[completion]]).
	- Sử dụng các mô hình tinh chỉnh. Một doanh nghiệp muốn sử dụng các mô hình có khả năng kém hơn được tinh chỉnh (như mô hình nhúng) thay vì các mô hình hiệu suất cao, mang lại giải pháp nhanh chóng và tiết kiệm chi phí hơn.
	- Đang xem xét độ trễ. Độ trễ rất quan trọng đối với một trường hợp sử dụng cụ thể, do đó, không thể sử dụng lời nhắc quá dài hoặc số lượng ví dụ cần học từ mô hình không phù hợp với giới hạn độ dài lời nhắc.
	- Luôn cập nhật. Một doanh nghiệp có rất nhiều dữ liệu chất lượng cao và nhãn sự thật căn bản cũng như các tài nguyên cần thiết để duy trì dữ liệu này được cập nhật theo thời gian.

bạn đã thấy rằng một số mô hình có khả năng nhận diện hướng dẫn chứa trong một yêu cầu và thực hiện suy luận không có ví dụ ([[zero-shot inference]]) một cách chính xác, trong khi các mô hình nhỏ hơn có thể không thực hiện được nhiệm vụ
Bạn cũng đã thấy rằng việc bao gồm một hoặc nhiều ví dụ về những gì bạn muốn mô hình làm, được gọi là suy luận một lần ([[one-shot inference]]) hoặc vài lần ([[few-shot inference]]), có thể đủ để giúp mô hình nhận diện nhiệm vụ và tạo ra kết quả tốt.

Tuy nhiên, chiến lược này có một vài hạn chế. Đầu tiên, với các mô hình nhỏ hơn, nó không luôn luôn hiệu quả, ngay cả khi bao gồm năm hoặc sáu ví dụ. Thứ hai, bất kỳ ví dụ nào bạn bao gồm trong yêu cầu sẽ chiếm không gian quý giá trong cửa sổ ngữ cảnh, giảm lượng không gian bạn có để bao gồm các thông tin hữu ích khác. từ đó fine-tune là giải pháp hiệu quả được sinh ra

Khác với huấn luyện trước ([[pre-trained llms]]), nơi bạn huấn luyện LLM bằng cách sử dụng lượng lớn dữ liệu văn bản không cấu trúc thông qua học tự giám sát ([[self-supervised learning]]), tinh chỉnh là một quá trình học có giám sát ([[supervised learning]]) nơi bạn sử dụng một tập dữ liệu các ví dụ có gán nhãn để cập nhật trọng số của LLM. 
	Các ví dụ có gán nhãn là các cặp yêu cầu-hoàn thành, quá trình tinh chỉnh mở rộng việc huấn luyện của mô hình để cải thiện khả năng tạo ra kết quả tốt cho một nhiệm vụ cụ thể.

- tinh chỉnh theo hướng dẫn ([[instruction fine-tuning]]), đặc biệt hiệu quả trong việc cải thiện hiệu suất của mô hình trên nhiều nhiệm vụ khác nhau.

- [[fine-tuning on a single task]]
- [[multi-task instruction fine-tuning]]