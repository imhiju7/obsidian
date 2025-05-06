- Là việc chúng ta đưa ra thuật toán cho một bộ dữ liệu đã có câu trả lời chính xác. Sau đó thuật toán sẽ xử lý nhiều câu trả lời chính xác cho mẫu dữ liệu mới.

![[Pasted image 20240522223238.png]]
- Trục tung thể hiện giá nhà
- Trục hoành thể hiện diện tích căn nhà
- Làm sao để biết với diện tích là 750 thì giá nhà bao nhiêu? Liệu có thể sử dụng học máy 
![[Pasted image 20240523000601.png]]

- Để dự đoán thì có một cách có thể làm đó là vẽ một đường thẳng tuyến tính qua các bộ dữ liệu
- Sau đó tìm y dựa trên đường tuyến tính và x có sẵn
![[Pasted image 20240523001049.png]]
- Cách tốt hơn là vẽ một đường với y = biểu thức bậc hai, sẽ tốt hơn với bộ dữ liệu này. 

Supervised learning là việc chúng ta đưa ra thuật toán cho một bộ dữ liệu đã có câu trả lời chính xác. Sau đó thuật toán sẽ xử lý nhiều câu trả lời chính xác cho mẫu dữ liệu mới. Đây được gọi là bài toán hồi qui [[regression]]
- Chúng ta đang dự đoán giá trị đầu ra liên tục, cụ thể là giá nhà.

Tiếp theo là bài toán dự đoán ung thư vú
![[Pasted image 20240523002324.png]]
- Trục x là thể hiện kích cỡ của khối u
- Trục y thể hiện có bị ung thư vú hay không, 1 là có, 0 là 0
![[Pasted image 20240523002701.png]]

Dùng các thuật toán học máy để dự đoán với kích thước của khối u hiện tại thì bệnh nhân có bị ung thư vú hay không. Đây là bài toán phân loại [[Classification]]. Bài toán này có thể có nhiều giá trị đầu ra.
![[Pasted image 20240523003148.png]]

Ví dụ như dataset có nhiều thuộc tính, ở đây có thêm thuộc tính là tuổi.
![[Pasted image 20240523003345.png]]

Bài toán machine learning không chỉ có 1 đặc trưng hay vài đặc trưng. Mà còn có nhiều đặc trưng hơn thế. Làm sao để xử lý chúng ? Chúng ta có thể sử dụng [[support vector machine]] để sử dụng  mẹo toán học cho phép xử lý hàng vạn đặc trưng

# Algorithm
## linear regression
- [[univariate linear regression]]