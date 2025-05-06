![[Pasted image 20240702210859.png]]
- Trước tiên, tập trung vào biểu thức quan trọng nhất và bỏ qua phần còn lại lúc này. 
	![[Pasted image 20240702211453.png]]
- $\Pi$ của $A_{t}$ cho $S_{t}$ trong ngữ cảnh của một LLM, là xác suất của token tiếp theo $A_{t}$ dựa trên prompt hiện tại $S_{t}$. Hành động $A_{t}$ là token tiếp theo, và trạng thái $S_{t}$ là prompt đã hoàn thành cho đến token t.
	![[Pasted image 20240702212037.png]]
- Mẫu số là xác suất của token tiếp theo với phiên bản ban đầu của LLM được đóng băng. Tử số là xác suất của token tiếp theo, thông qua LLM cập nhật, mà chúng ta có thể thay đổi để nhận được phần thưởng tốt hơn. 
- $Â_{t}$ được gọi là đại lượng lợi thế ước lượng của một lựa chọn hành động cụ thể. Đại lượng lợi thế ước lượng mức độ tốt hơn hay tệ hơn của hành động hiện tại so với tất cả các hành động có thể tại trạng thái dữ liệu.
- Chúng tôi xem xét các phần thưởng tương lai kỳ vọng của một hoàn thành sau khi có token mới, và chúng tôi ước lượng mức độ lợi thế của hoàn thành này so với phần còn lại. Có một công thức đệ quy để ước lượng đại lượng này dựa trên hàm giá trị mà chúng ta đã thảo luận trước đó. Ở đây, chúng ta tập trung vào sự hiểu biết trực quan. Đây là một biểu diễn hình ảnh của những gì tôi vừa mô tả.
	![[Pasted image 20240702212304.png]]
- Bạn có một prompt S, và bạn có các con đường khác nhau để hoàn thành nó, được minh họa bằng các con đường khác nhau trên hình vẽ. Đại lượng lợi thế cho bạn biết mức độ tốt hơn hay tệ hơn của token hiện tại$A_{t}$ so với tất cả các token có thể.
- Trong hình ảnh này, con đường trên cùng đi lên là hoàn thành tốt hơn, nhận được phần thưởng cao hơn. Con đường dưới cùng đi xuống là hoàn thành tệ hơn.
- tại sao việc tối đa hóa đại lượng này lại dẫn đến phần thưởng cao hơn? Hãy xem xét trường hợp lợi thế là dương cho token được đề xuất. Lợi thế dương có nghĩa là token được đề xuất tốt hơn trung bình. Do đó, tăng xác suất của token hiện tại có vẻ như là một chiến lược tốt dẫn đến phần thưởng cao hơn. Điều này chuyển thành việc tối đa hóa biểu thức mà chúng ta có ở đây. Nếu token được đề xuất tệ hơn trung bình, lợi thế sẽ âm. 
- Một lần nữa, tối đa hóa biểu thức sẽ giảm xác suất token, đó là chiến lược đúng. Vì vậy, kết luận tổng thể là tối đa hóa biểu thức này dẫn đến một LLM được căn chỉnh tốt hơn.

- Trực tiếp tối đa hóa biểu thức sẽ dẫn đến các vấn đề vì các tính toán của chúng ta đáng tin cậy dưới giả định rằng các ước lượng lợi thế của chúng ta là chính xác. Các ước lượng lợi thế chỉ chính xác khi các chính sách cũ và mới gần nhau.
![[Pasted image 20240702213839.png]]
- điều gì xảy ra ở đây là bạn chọn cái nhỏ hơn trong hai thuật ngữ
- Chú ý rằng biểu thức thứ hai này định nghĩa một vùng, nơi hai chính sách gần nhau. Những thuật ngữ bổ sung này là các lan can bảo vệ, và chỉ đơn giản định nghĩa một vùng tiệm cận LLM, nơi các ước lượng của chúng ta có lỗi nhỏ. Đây được gọi là vùng tin cậy. Những thuật ngữ bổ sung này đảm bảo rằng chúng ta không rời khỏi vùng tin cậy.