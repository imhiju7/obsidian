## what is prompt engineering?
- Prompt engineering là quá trình thiết kế và tối ưu hóa đầu vào văn bản (lời nhắc) để đưa ra phản hồi (hoàn thành) nhất quán và chất lượng cho một mục tiêu và mô hình ứng dụng nhất định. Chúng ta có thể coi đây là một quá trình gồm 2 bước:
	- Thiết kế lời nhắc ban đầu cho một mô hình và mục tiêu nhất định
	- Tinh chỉnh lời nhắc lặp đi lặp lại để cải thiện chất lượng phản hồi
- Đây nhất thiết phải là một quá trình thử và sai, đòi hỏi trực giác và nỗ lực của người dùng để có được kết quả tối ưu.
	- [[tokenization]] = cách mô hình "nhìn thấy" lời nhắc
	- [[foundation model]] = mô hình nền tảng "xử lý" lời nhắc như thế nào
	- [[instruction tuned llms]]= làm thế nào mô hình bây giờ có thể thấy "nhiệm vụ"
## why do we need Prompt Engineering?
- Phản ứng của mô hình là ngẫu nhiên. Cùng một lời nhắc có thể sẽ tạo ra các phản hồi khác nhau với các kiểu máy hoặc phiên bản kiểu máy khác nhau. Và nó thậm chí có thể tạo ra những kết quả khác nhau với cùng một mô hình ở những thời điểm khác nhau. Kỹ thuật kỹ thuật nhanh chóng có thể giúp chúng tôi giảm thiểu những biến thể này bằng cách cung cấp các rào chắn tốt hơn.
- Các mô hình có thể tạo ra các phản hồi. Các mô hình được đào tạo trước với các bộ dữ liệu lớn nhưng hữu hạn, nghĩa là chúng thiếu kiến ​​thức về các khái niệm bên ngoài phạm vi đào tạo đó. Kết quả là, họ có thể đưa ra những thông tin hoàn chỉnh không chính xác, tưởng tượng hoặc mâu thuẫn trực tiếp với những sự thật đã biết. Các kỹ thuật kỹ thuật nhanh chóng giúp người dùng xác định và giảm thiểu những hành vi bịa đặt như vậy, chẳng hạn như bằng cách yêu cầu AI trích dẫn hoặc lý luận.
- Khả năng của mô hình sẽ khác nhau. Các mẫu hoặc thế hệ mẫu mới hơn sẽ có khả năng phong phú hơn nhưng cũng mang lại những đặc điểm riêng biệt và sự cân bằng về chi phí và độ phức tạp. Kỹ thuật nhanh chóng có thể giúp chúng tôi phát triển các phương pháp thực hành và quy trình công việc tốt nhất giúp loại bỏ những khác biệt và thích ứng với các yêu cầu cụ thể của mô hình theo những cách liền mạch, có thể mở rộng.
# prompt construction

## basic prompt
- Lời nhắc cơ bản: nội dung nhập văn bản được gửi đến mô hình mà không có ngữ cảnh nào khác.
	- khi chúng tôi gửi một vài từ đầu tiên của quốc ca Hoa Kỳ tới API hoàn thành OpenAI, nó sẽ ngay lập tức hoàn thành phản hồi với một vài dòng tiếp theo, minh họa hành vi dự đoán cơ bản.
![[Pasted image 20240619111112.png]]
## complex prompt
Lời nhắc phức tạp dưới dạng tập hợp các tin nhắn với:
- Các cặp đầu vào/đầu ra phản ánh phản hồi đầu vào và trợ lý của người dùng
```javascript
response = openai.chat.completions.create(
    model="gpt-3.5-turbo",
    messages=[
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": "Who won the world series in 2020?"},
        {"role": "assistant", "content": "The Los Angeles Dodgers won the World Series in 2020."},
        {"role": "user", "content": "Where was it played?"}
    ]
)
```
# instruction prompt
![[Pasted image 20240619111249.png]]
# Prompt Templates
- Mẫu lời nhắc là một công thức được xác định trước cho lời nhắc, có thể được lưu trữ và sử dụng lại khi cần, nhằm mang lại trải nghiệm người dùng nhất quán hơn trên quy mô lớn. Ở dạng đơn giản nhất, nó chỉ đơn giản là một tập hợp các ví dụ nhắc nhở như ví dụ này từ OpenAI cung cấp cả thành phần nhắc nhở tương tác (thông báo của người dùng và hệ thống) và định dạng yêu cầu dựa trên API - để hỗ trợ tái sử dụng.
# Prompt Cues
![[Pasted image 20240619112047.png]]