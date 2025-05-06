- mục tiêu của lượng tử hóa là giảm bộ nhớ cần để lưu trữ và huấn luyện mô hình bằng cách giảm độ chính xác của các trọng số mô hình. 
- lượng tử hóa chiếu các số thực 32-bit ban đầu vào các không gian độ chính xác thấp hơn, sử dụng các hệ số tỷ lệ được tính toán dựa trên phạm vi của các số thực 32-bit ban đầu. 
- các framework và thư viện học sâu hiện đại hỗ trợ huấn luyện nhận thức lượng tử hóa, học các hệ số tỷ lệ lượng tử hóa trong quá trình huấn luyện.

Ý tưởng chính ở đây là bạn giảm bộ nhớ cần để lưu trữ các trọng số của mô hình bằng cách giảm độ chính xác từ số thực 32-bit xuống số thực 16-bit, hoặc số nguyên 8-bit. 
- Các kiểu dữ liệu tương ứng được sử dụng trong các thư viện và frameworks học sâu là FP32 cho độ chính xác 32-bit, FP16 hoặc Bfloat16 cho độ chính xác 16-bit, và int8 cho số nguyên 8-bit.
- Phạm vi các số bạn có thể biểu diễn với FP32 từ khoảng $-3*e^{38}$ đến $3*e^{38}$.
![[Pasted image 20240630072704.png]]
Lượng tử hóa chiếu các số thực 32-bit ban đầu vào không gian độ chính xác thấp hơn, sử dụng các hệ số tỷ lệ được tính toán dựa trên phạm vi của các số thực 32-bit ban đầu.
- Các số thực được lưu trữ dưới dạng một chuỗi các bit 0 và 1. 
- 32 bit để lưu trữ số ở độ chính xác đầy đủ với FP32 gồm một bit cho dấu, nơi số 0 chỉ ra số dương và số 1 chỉ ra số âm. 
- Sau đó, tám bit cho số mũ của số, và 23 bit biểu diễn phần lẻ của số. Phần lẻ còn được gọi là mantissa hoặc significant. Nó biểu diễn các bit chính xác của số.

Nếu bạn chuyển đổi giá trị số thực 32-bit trở lại giá trị thập phân, bạn sẽ nhận thấy một chút mất mát độ chính xác.

Bây giờ, hãy xem điều gì xảy ra nếu bạn chiếu biểu diễn FP32 của Pi vào không gian độ chính xác thấp hơn FP16, 16-bit.
![[Pasted image 20240630073215.png]]
- 16 bit bao gồm một bit cho dấu, như bạn đã thấy với FP32, nhưng bây giờ FP16 chỉ gán năm bit để biểu diễn số mũ và 10 bit để biểu diễn phần lẻ. 
- Do đó, phạm vi các số bạn có thể biểu diễn với FP16 nhỏ hơn rất nhiều, từ -65.504 đến +65.504. 
- Giá trị FP32 ban đầu được chiếu thành 3.140625 trong không gian 16-bit. 
- Lưu ý rằng bạn mất một chút độ chính xác với phép chiếu này.

BFLOAT16 hoặc BF16 là một dạng lai giữa độ chính xác bán phần FP16 và độ chính xác đầy đủ FP32. BF16 đáng kể giúp ổn định việc huấn luyện và được hỗ trợ bởi các GPU mới hơn như Nvidia A100. BFLOAT16 thường được mô tả như một số thực 32-bit bị cắt ngắn, vì nó nắm bắt đầy đủ phạm vi động của số thực 32-bit nhưng chỉ sử dụng 16-bit.

BFLOAT16 sử dụng đủ tám bit để biểu diễn số mũ, nhưng cắt ngắn phần lẻ xuống chỉ còn bảy bit.

![[Pasted image 20240630073643.png]]
