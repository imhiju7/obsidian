- PyTorch's Fully Sharded Data Parallel
- FSDP được thúc đẩy bởi một bài báo do các nhà nghiên cứu tại Microsoft công bố năm 2019, đề xuất một kỹ thuật gọi là ZeRO. [1] S. Rajbhandari, J. Rasley, O. Ruwase, and Y. He, “ZeRO: Memory Optimizations Toward Training Trillion Parameter Models.” arXiv, May 13, 2020. 
- ZeRO viết tắt của Zero Redundancy Optimizer và mục tiêu của ZeRO là tối ưu hóa bộ nhớ bằng cách phân phối hoặc phân mảnh các trạng thái mô hình qua các GPU với ZeRO data overlap. Điều này cho phép bạn mở rộng việc huấn luyện mô hình qua các GPU khi mô hình của bạn không vừa trong bộ nhớ của một chip duy nhất.
![[Pasted image 20240630092140.png]]
- yêu cầu bộ nhớ lớn nhất là cho các trạng thái của optimizer, chiếm không gian gấp đôi so với trọng số, tiếp theo là chính các trọng số và các gradient. 
	- Hãy biểu diễn các tham số như hộp màu xanh, các gradient màu vàng và trạng thái optimizer màu xanh lá cây. 
	![[Pasted image 20240630092443.png]]
	- Lượng bộ nhớ sử dụng ở [[ddp]]
Một hạn chế của chiến lược sao chép mô hình mà tôi đã chỉ ra trước đây là bạn cần giữ một bản sao đầy đủ của mô hình trên mỗi GPU, dẫn đến tiêu thụ bộ nhớ dư thừa. Bạn đang lưu trữ cùng một số trên mọi GPU.

ZeRO, loại bỏ sự dư thừa này bằng cách phân phối hoặc phân mảnh các tham số mô hình, gradient, và trạng thái optimizer qua các GPU thay vì sao chép chúng. Đồng thời, chi phí liên lạc để đồng bộ hóa các trạng thái mô hình gần bằng với ADP đã thảo luận trước đây

![[Pasted image 20240630092823.png]]

ZeRO cung cấp ba giai đoạn tối ưu hóa
- Stage 1 chỉ phân mảnh các trạng thái optimizer qua các GPU, điều này có thể giảm dấu chân bộ nhớ của bạn đến bốn lần.
		![[Pasted image 20240630093850.png]]
- Stage 2 cũng phân mảnh các gradient qua các chip. Khi áp dụng cùng với Stage 1, điều này có thể giảm dấu chân bộ nhớ của bạn đến tám lần.
		![[Pasted image 20240630093955.png]]
- Stage 3 phân mảnh tất cả các thành phần bao gồm cả các tham số mô hình qua các GPU. Khi áp dụng cùng với các Giai đoạn 1 và 2, việc giảm bộ nhớ là tuyến tính với số lượng GPU.
		![[Pasted image 20240630094232.png]]

![[Pasted image 20240630094807.png]]
Với chiến lược này, bạn có thể làm việc với các mô hình quá lớn để vừa trên một chip duy nhất.
- Trái ngược với GDP, nơi mỗi GPU có tất cả các trạng thái mô hình cần thiết để xử lý mỗi lô dữ liệu có sẵn tại chỗ, FSDP yêu cầu bạn thu thập dữ liệu này từ tất cả các GPU trước khi thực hiện bước tiến và lùi. 
- Mỗi CPU yêu cầu dữ liệu từ các GPU khác theo yêu cầu để chuyển đổi dữ liệu phân mảnh thành dữ liệu không phân mảnh trong thời gian thực hiện phép toán. 
- Sau phép toán, bạn giải phóng dữ liệu không phân mảnh không địa phương trở lại các GPU khác dưới dạng dữ liệu phân mảnh ban đầu. Bạn cũng có thể chọn giữ lại dữ liệu này cho các phép toán tương lai trong bước lùi ví dụ. Lưu ý rằng điều này yêu cầu nhiều RAM GPU hơn một lần nữa, đây là quyết định đánh đổi điển hình giữa hiệu suất và sử dụng bộ nhớ.
Trong bước cuối cùng sau bước lùi, FSDP đồng bộ hóa các gradient qua các GPU theo cách giống như DDP. 
- việc phân mảnh mô hình như đã mô tả với FSDP cho phép bạn giảm mức sử dụng bộ nhớ GPU tổng thể.
- bạn có thể chỉ định rằng FSDP chuyển phần tính toán huấn luyện sang CPU để giảm thêm mức sử dụng bộ nhớ GPU của bạn.
# hệ số phân mảnh
- Để quản lý sự đánh đổi giữa hiệu suất và sử dụng bộ nhớ, bạn có thể cấu hình mức độ phân mảnh bằng cách sử dụng hệ số phân mảnh của FSDP.
- Hệ số phân mảnh là một về cơ bản loại bỏ việc phân mảnh và sao chép mô hình đầy đủ tương tự như DDP. 
- Nếu bạn đặt hệ số phân mảnh tối đa cho số lượng GPU có sẵn, bạn bật chế độ phân mảnh đầy đủ. Điều này có sự tiết kiệm bộ nhớ nhiều nhất, nhưng tăng khối lượng liên lạc giữa các GPU. Bất kỳ hệ số phân mảnh nào ở giữa đều cho phép phân mảnh đa chiều.
![[Pasted image 20240630101146.png]]





