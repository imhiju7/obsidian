Với prompt tuning, bạn thêm các [[tokens]] có thể huấn luyện vào [[prompt]] và để quá trình [[supervised learning]] xác định các giá trị tối ưu của chúng. Bộ token có thể huấn luyện này được gọi là soft prompt, và nó được thêm vào trước các [[vector embedding]] đại diện cho văn bản đầu vào của bạn.

![[Pasted image 20240701195302.png]]

Các vector soft prompt có cùng độ dài với các vector nhúng của các token ngôn ngữ. Việc bao gồm từ 20 đến 100 token ảo có thể đủ để đạt hiệu suất tốt. Các token đại diện cho ngôn ngữ tự nhiên là cứng vì chúng tương ứng với một vị trí cố định trong không gian vector nhúng.

Tuy nhiên, các soft prompt không phải là các từ cố định, rời rạc của ngôn ngữ tự nhiên. Thay vào đó, bạn có thể nghĩ về chúng như các token ảo có thể nhận bất kỳ giá trị nào trong không gian nhúng liên tục, đa chiều. Thông qua học có giám sát, mô hình học các giá trị cho các token ảo này để tối đa hóa hiệu suất cho một nhiệm vụ cụ thể.

với prompt tuning, các trọng số của mô hình ngôn ngữ lớn được giữ nguyên và mô hình không được cập nhật. Thay vào đó, các vector nhúng của soft prompt được cập nhật theo thời gian để tối ưu hóa phần hoàn thành của prompt.

![[Pasted image 20240701195904.png]]

Bạn có thể huấn luyện một bộ soft prompt khác nhau cho mỗi nhiệm vụ và sau đó dễ dàng hoán đổi chúng trong thời gian suy luận. Bạn có thể huấn luyện một bộ soft prompt cho một nhiệm vụ và một bộ khác cho nhiệm vụ khác. Để sử dụng chúng trong suy luận, bạn thêm các token đã học vào prompt đầu vào của mình. Để chuyển sang nhiệm vụ khác, bạn chỉ cần thay đổi soft prompt. Soft prompt rất nhỏ trên đĩa, vì vậy loại tinh chỉnh này cực kỳ hiệu quả và linh hoạt.

Vậy prompt tuning hoạt động tốt như thế nào? Trong bài báo gốc "Exploring the Method" của Brian Lester và các cộng tác viên tại Google, các tác giả đã so sánh prompt tuning với một số phương pháp khác cho nhiều kích thước mô hình.

![[Pasted image 20240701200231.png]]
Trong hình này từ bài báo, bạn có thể thấy kích thước mô hình trên trục X và điểm số SuperGLUE trên trục Y. Đây là tiêu chuẩn đánh giá bạn đã học trong tuần này, đánh giá hiệu suất mô hình trên một số nhiệm vụ ngôn ngữ khác nhau.

- Đường màu đỏ hiển thị điểm số cho các mô hình được tạo ra thông qua huấn luyện hoàn chỉnh trên một nhiệm vụ duy nhất. 
- Trong khi đường màu cam hiển thị điểm số cho các mô hình được tạo ra bằng cách huấn luyện nhiều nhiệm vụ. 
- Đường màu xanh lá cây hiển thị hiệu suất của prompt tuning
- Cuối cùng, đường màu xanh lam hiển thị điểm số chỉ cho prompt engineering.

prompt tuning không hiệu quả bằng huấn luyện hoàn chỉnh đối với các mô hình LLM nhỏ hơn. Tuy nhiên, khi kích thước mô hình tăng lên, hiệu suất của prompt tuning cũng tăng lên. Và khi các mô hình có khoảng 10 tỷ tham số, prompt tuning có thể hiệu quả như huấn luyện hoàn chỉnh và cung cấp một sự cải thiện đáng kể về hiệu suất so với prompt engineering đơn thuần.

Các token được huấn luyện không tương ứng với bất kỳ từ, từ ngữ hoặc cụm từ nào trong từ vựng của LLM. Tuy nhiên, một phân tích của các token gần nhất với vị trí soft prompt cho thấy chúng hình thành các cụm ngữ nghĩa chặt chẽ. Nói cách khác, các từ gần nhất với các token soft prompt có ý nghĩa tương tự. Các từ được xác định thường có ý nghĩa liên quan đến nhiệm vụ, cho thấy rằng các prompt đang học các biểu diễn giống từ.