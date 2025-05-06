- Pi Torch's Distributed Data-Parallel
- DDP sao chép mô hình của bạn lên mỗi [[gpu]] và gửi các lô dữ liệu đến từng GPU song song. 
- Mỗi bộ dữ liệu được xử lý song song và sau đó bước đồng bộ hóa kết hợp các kết quả từ mỗi GPU, từ đó cập nhật mô hình trên mỗi GPU, luôn giống hệt nhau trên tất cả các chip. 
- Cách triển khai này cho phép tính toán song song trên tất cả các GPU, dẫn đến quá trình huấn luyện nhanh hơn.
![[Pasted image 20240630085958.png]]
