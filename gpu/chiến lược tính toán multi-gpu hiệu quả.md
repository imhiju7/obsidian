- bạn sẽ cần sử dụng các chiến lược tính toán đa [[gpu]] khi mô hình của bạn trở nên quá lớn để vừa trên một [[gpu]] duy nhất.
- Sẽ hữu ích khi biết cách phân phối tính toán qua nhiều GPU ngay cả khi bạn đang làm việc với một mô hình nhỏ

Bước đầu tiên trong việc mở rộng huấn luyện mô hình là phân phối các bộ dữ liệu lớn qua nhiều GPU và xử lý các lô dữ liệu này song song. Một cách triển khai phổ biến của kỹ thuật sao chép mô hình này là Pi Torch's Distributed Data-Parallel, hay [[ddp]]. Lưu ý rằng DDP yêu cầu rằng trọng số mô hình của bạn và tất cả các tham số bổ sung, gradient, và trạng thái tối ưu hóa cần thiết cho việc huấn luyện, phải vừa trên một GPU.

Nếu mô hình của bạn quá lớn cho điều này, bạn nên tìm hiểu một kỹ thuật khác gọi là  phân mảnh mô hình. Một cách triển khai phổ biến của phân mảnh mô hình là PyTorch's Fully Sharded Data Parallel, hay [[fsdp]]

Hãy xem xét cách [[fsdp]] hoạt động so với [[ddp]] được đo bằng [[teraflop]]s mỗi GPU. Các thử nghiệm này được thực hiện bằng cách sử dụng tối đa 512 GPU NVIDIA V100, mỗi GPU có 80 gigabyte bộ nhớ. Bạn có thể thấy các số hiệu suất khác nhau của FSDP, phân mảnh đầy đủ trong màu xanh lam, phân mảnh đa chiều trong màu cam và sao chép đầy đủ trong màu xanh lá cây. 
[1] Y. Zhao _et al._, “PyTorch FSDP: Experiences on Scaling Fully Sharded Data Parallel.” arXiv, Sep. 12, 2023. doi: [10.48550/arXiv.2304.11277](https://doi.org/10.48550/arXiv.2304.11277).

![[Pasted image 20240630101541.png]]
Để tham khảo, hiệu suất của DDP được hiển thị bằng màu đỏ. Đối với các mô hình đầu tiên với 611 triệu tham số và 2,28 tỷ tham số, hiệu suất của FSDP và DDP là tương tự. 
Bây giờ, nếu bạn chọn một kích thước mô hình lớn hơn 2,28 tỷ, chẳng hạn như T5 với 11,3 tỷ tham số, DDP sẽ gặp lỗi hết bộ nhớ. FSDP mặt khác có thể dễ dàng xử lý các mô hình kích thước này và đạt được số teraflop cao hơn nhiều khi giảm độ chính xác của mô hình xuống 16-bit. Hình thứ hai cho thấy sự giảm 7% trong teraflop mỗi GPU khi tăng số lượng GPU từ 8 đến 512 cho mô hình T5 11 tỷ, được vẽ ở đây bằng cách sử dụng kích thước batch là 16 màu cam và kích thước batch là 8 màu xanh lam.
- Khi mô hình tăng kích thước và được phân phối qua nhiều GPU hơn, sự gia tăng khối lượng liên lạc giữa các chip bắt đầu ảnh hưởng đến hiệu suất, làm chậm quá trình tính toán.

![[Pasted image 20240630102838.png]]
