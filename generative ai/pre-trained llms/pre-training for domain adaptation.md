Nếu lĩnh vực mục tiêu của bạn sử dụng từ vựng và cấu trúc ngôn ngữ không được sử dụng phổ biến trong ngôn ngữ hàng ngày, bạn có thể cần thực hiện thích ứng theo miền để đạt được hiệu suất mô hình tốt.

Ví dụ, hãy tưởng tượng bạn là một nhà phát triển xây dựng một ứng dụng để giúp luật sư và trợ lý pháp lý tóm tắt các bản tóm tắt pháp lý. Văn bản pháp lý sử dụng các thuật ngữ rất cụ thể như "mens rea" trong ví dụ đầu tiên và "res judicata" trong ví dụ thứ hai. Những từ này hiếm khi được sử dụng ngoài thế giới pháp lý, điều đó có nghĩa là chúng không có khả năng xuất hiện rộng rãi trong văn bản huấn luyện của các LLM hiện có. Kết quả là, các mô hình có thể gặp khó khăn trong việc hiểu những thuật ngữ này hoặc sử dụng chúng đúng cách.

Một vấn đề khác là ngôn ngữ pháp lý đôi khi sử dụng các từ hàng ngày trong ngữ cảnh khác, như "consideration" trong ví dụ thứ ba. Từ này không liên quan gì đến sự tử tế, mà thay vào đó đề cập đến yếu tố chính của một hợp đồng làm cho thỏa thuận có hiệu lực. Vì lý do tương tự, bạn có thể gặp khó khăn nếu cố gắng sử dụng LLM hiện có trong một ứng dụng y tế.

![[Pasted image 20240630165946.png]]

Ngôn ngữ y tế chứa nhiều từ hiếm gặp để mô tả các tình trạng và thủ tục y tế. Và những từ này có thể không xuất hiện thường xuyên trong các tập dữ liệu huấn luyện bao gồm các trang web và sách. Một số lĩnh vực cũng sử dụng ngôn ngữ theo cách rất đặc thù. 

Ví dụ cuối cùng về ngôn ngữ y tế này có thể chỉ trông giống như một chuỗi ký tự ngẫu nhiên, nhưng thực sự là một cách viết tắt được bác sĩ sử dụng để viết đơn thuốc. Văn bản này có ý nghĩa rất rõ ràng đối với dược sĩ: "uống một viên thuốc bằng miệng bốn lần một ngày, sau bữa ăn và trước khi đi ngủ."

Vì các mô hình học từ vựng và hiểu ngôn ngữ thông qua nhiệm vụ tiền huấn luyện ban đầu, tiền huấn luyện mô hình của bạn từ đầu sẽ mang lại kết quả tốt hơn cho các lĩnh vực chuyên môn cao như luật, y học, tài chính hoặc khoa học.

[1] S. Wu _et al._, “BloombergGPT: A Large Language Model for Finance.” arXiv, Dec. 21, 2023.
Các nhà nghiên cứu của Bloomberg đã chọn kết hợp cả dữ liệu tài chính và dữ liệu văn bản chung để tiền huấn luyện một mô hình đạt được kết quả tốt nhất trên các tiêu chuẩn tài chính. Đồng thời duy trì hiệu suất cạnh tranh trên các tiêu chuẩn LLM chung.

Do đó, các nhà nghiên cứu đã chọn dữ liệu bao gồm 51% dữ liệu tài chính và 49% dữ liệu công cộng. Trong bài báo của họ, các nhà nghiên cứu của Bloomberg mô tả kiến trúc mô hình chi tiết hơn. Họ cũng thảo luận về cách họ bắt đầu với các luật mở rộng của Chinchilla để hướng dẫn và nơi họ phải thực hiện các sự cân nhắc.
![[Pasted image 20240630173913.png]]

![[Pasted image 20240630173800.png]]
Hai biểu đồ này so sánh một số LLM, bao gồm [[bloombergGPT]], với các luật mở rộng đã được thảo luận bởi các nhà nghiên cứu.

Ở bên trái, các đường chéo theo dõi kích thước mô hình tối ưu tính bằng tỷ tham số cho một loạt các ngân sách tính toán. 
Ở bên phải, các đường theo dõi kích thước tập dữ liệu huấn luyện tối ưu được tính bằng số token. 

Đường chấm hồng trên mỗi biểu đồ cho biết ngân sách tính toán mà nhóm Bloomberg có sẵn để huấn luyện mô hình mới của họ. Các vùng tô màu hồng tương ứng với các luật mở rộng tối ưu tính toán được xác định trong bài báo Chinchilla.

Về kích thước mô hình, bạn có thể thấy rằng [[bloombergGPT]] theo sát phương pháp tiếp cận Chinchilla cho ngân sách tính toán hiện có là 1,3 triệu giờ GPU, hoặc khoảng 230,000,000 [[petaflop]]. Mô hình chỉ cao hơn một chút so với vùng tô màu hồng, cho thấy số lượng tham số khá gần với mức tối ưu.

Tuy nhiên, số lượng [[tokens]] thực tế được sử dụng để tiền huấn luyện BloombergGPT là 569 tỷ, thấp hơn giá trị được khuyến nghị của Chinchilla cho ngân sách tính toán hiện có.

Tập dữ liệu huấn luyện nhỏ hơn mức tối ưu là do hạn chế về sẵn có của dữ liệu tài chính. Điều này cho thấy rằng các ràng buộc thực tế có thể buộc bạn phải thực hiện các sự cân nhắc khi tiền huấn luyện các mô hình của riêng mình.

Trong quá trình đào tạo BloombergGPT, các tác giả đã sử dụng Luật chia tỷ lệ Chinchilla để hướng dẫn số lượng tham số trong mô hình và khối lượng dữ liệu đào tạo, được đo bằng mã thông báo. Các khuyến nghị của Chinchilla được thể hiện bằng các dòng Chinchilla-1, Chinchilla-2 và Chinchilla-3 trong hình ảnh và chúng ta có thể thấy BloombergGPT cũng gần như vậy.

Dự án BloombergGPT là một minh họa điển hình về việc đào tạo trước một mô hình để tăng tính đặc hiệu của miền và những thách thức có thể buộc phải đánh đổi so với mô hình tối ưu tính toán và cấu hình đào tạo.