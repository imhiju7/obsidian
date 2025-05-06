là một kỹ thuật tập trung vào việc có một mô hình giáo viên lớn hơn huấn luyện một mô hình học sinh nhỏ hơn. Mô hình học sinh học cách bắt chước hành vi của mô hình giáo viên, hoặc chỉ trong lớp dự đoán cuối cùng hoặc cả trong các lớp ẩn của mô hình.

Bạn bắt đầu với LLM đã tinh chỉnh của mình làm mô hình giáo viên và tạo một LLM nhỏ hơn cho mô hình học sinh của mình.
![[Pasted image 20240704173312.png]]
Bạn cố định trọng số của mô hình giáo viên và sử dụng nó để tạo ra các phản hồi cho dữ liệu huấn luyện của bạn.
![[Pasted image 20240704173351.png]]
Đồng thời, bạn tạo ra các phản hồi cho dữ liệu huấn luyện bằng mô hình học sinh của mình.
Sự chưng cất kiến thức giữa mô hình giáo viên và học sinh được đạt được bằng cách tối thiểu hóa một hàm mất mát gọi là [[distilation loss]].
![[Pasted image 20240704173456.png]]
Để tính toán mất mát này, chưng cất sử dụng phân phối xác suất trên các token được tạo ra bởi lớp softmax của mô hình giáo viên.
Bây giờ, mô hình giáo viên đã được tinh chỉnh trên dữ liệu huấn luyện, vì vậy phân phối xác suất có thể sẽ khớp chặt chẽ với dữ liệu thực tế và sẽ không có nhiều biến thể trong các token. Đó là lý do tại sao chưng cất áp dụng một thủ thuật nhỏ là thêm một tham số [[temperature]] vào hàm softmax.
![[Pasted image 20240704173734.png]]
Với một tham số nhiệt độ lớn hơn một, phân phối xác suất trở nên rộng hơn và ít mạnh hơn. 
- Phân phối mềm này cung cấp cho bạn một tập hợp các token tương tự như các token thực tế. 
- Trong bối cảnh chưng cất, đầu ra của mô hình giáo viên thường được gọi là nhãn mềm và dự đoán của mô hình học sinh được gọi là dự đoán mềm.

Song song, bạn huấn luyện mô hình học sinh để tạo ra các dự đoán chính xác dựa trên dữ liệu huấn luyện thực tế của bạn. 
![[Pasted image 20240704174212.png]]
Ở đây, bạn không thay đổi cài đặt nhiệt độ và thay vào đó sử dụng hàm softmax tiêu chuẩn. Chưng cất gọi đầu ra của mô hình học sinh là các dự đoán cứng và nhãn cứng. 
Mất mát giữa hai điều này là mất mát học sinh. 
Các mất mát chưng cất và học sinh được kết hợp để cập nhật trọng số của mô hình học sinh thông qua [[backpropagation]].

Trên thực tế, chưng cất không hiệu quả bằng cho các mô hình sinh mã hóa. Nó thường hiệu quả hơn cho các mô hình chỉ mã hóa, chẳng hạn như Burt, có nhiều dư thừa trong đại diện.

Lưu ý rằng với chưng cất, bạn đang huấn luyện một mô hình thứ hai, nhỏ hơn để sử dụng trong suy luận. Bạn không giảm kích thước mô hình của LLM ban đầu theo bất kỳ cách nào.