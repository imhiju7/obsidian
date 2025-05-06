- hack phần thưởng, trong đó tác nhân học cách gian lận hệ thống bằng cách ưu tiên các hành động tối đa hóa phần thưởng nhận được ngay cả khi các hành động đó không liên kết tốt với mục tiêu ban đầu.
- Trong ngữ cảnh của LLM, hack phần thưởng có thể biểu hiện dưới dạng việc thêm các từ hoặc cụm từ vào các hoàn thành dẫn đến điểm số cao cho số liệu được liên kết.

Nhưng điều đó làm giảm chất lượng tổng thể của ngôn ngữ.
Ví dụ: giả sử bạn đang sử dụng RHF để giải độc và hướng dẫn mô hình. Bạn đã đào tạo một mô hình phần thưởng có thể thực hiện phân tích cảm xúc và phân loại các hoàn thành mô hình là độc hại hoặc không độc hại.

Bạn chọn một lời nhắc từ dữ liệu đào tạo sản phẩm này, và chuyển nó cho hướng dẫn LLM tạo ra một [[completion]].
![[Pasted image 20240703013453.png]]
[[completion]] "rác rưởi hoàn toàn" có thể được dự đoán sẽ nhận được điểm độc hại cao.

Hoàn thành này được xử lý bởi mô hình thưởng về độ độc hại, tạo ra một điểm số và điểm này được chuyển cho thuật toán PPO, sử dụng nó để cập nhật các trọng số của mô hình. Khi bạn lặp lại, RHF sẽ cập nhật LLM để tạo ra các phản hồi ít độc hại hơn.
![[Pasted image 20240703014041.png]]
Tuy nhiên, khi chính sách cố gắng tối ưu hóa phần thưởng, nó có thể lệch quá nhiều so với mô hình ngôn ngữ ban đầu.
Trong ví dụ này, mô hình đã bắt đầu tạo ra các hoàn thành mà nó đã học sẽ dẫn đến điểm độc hại rất thấp bằng cách bao gồm các cụm từ như "tuyệt vời nhất", "không thể tin được nhất". Ngôn ngữ này nghe rất cường điệu.

Mô hình cũng có thể bắt đầu tạo ra văn bản vô nghĩa, không đúng ngữ pháp chỉ để tối đa hóa phần thưởng. Những đầu ra như vậy chắc chắn không hữu ích.
![[Pasted image 20240703014327.png]]

# avoid reward hacking
Để ngăn chặn hacking phần thưởng, bạn có thể sử dụng LLM hướng dẫn ban đầu làm tham chiếu hiệu suất. Hãy gọi nó là mô hình tham chiếu. Trọng số của mô hình tham chiếu được cố định và không được cập nhật trong các lần lặp lại của RHF. Bằng cách này, bạn luôn duy trì một mô hình tham chiếu để so sánh.
![[Pasted image 20240703014620.png]]

Trong quá trình đào tạo, mỗi gợi ý được truyền qua cả hai mô hình, tạo ra một hoàn thành từ LLM tham chiếu và mô hình LLM được cập nhật trung gian. Tại điểm này, bạn có thể so sánh hai hoàn thành và tính toán một giá trị gọi là độ lệch [[rlhf kullback-leibler divergence]]
![[Pasted image 20240703014654.png]]
- Bạn có thể sử dụng nó để so sánh các hoàn thành của hai mô hình và xác định mức độ mô hình được cập nhật đã lệch bao nhiêu so với tham chiếu.
- Độ lệch KL được tính toán cho mỗi token tạo ra trên toàn bộ từ vựng của LLM. Điều này có thể dễ dàng là hàng chục hoặc hàng trăm nghìn token. Tuy nhiên, sử dụng hàm softmax, bạn giảm số lượng xác suất xuống ít hơn nhiều so với kích thước từ vựng đầy đủ. Hãy nhớ rằng đây vẫn là một quá trình tương đối tốn kém về tính toán. Bạn sẽ hầu như luôn có lợi từ việc sử dụng GPU.

Sau khi tính toán độ lệch KL giữa hai mô hình, bạn thêm nó như một thuật ngữ vào tính toán phần thưởng. Điều này sẽ phạt mô hình RL được cập nhật nếu nó lệch quá xa so với LLM tham chiếu và tạo ra các hoàn thành quá khác biệt. 
![[Pasted image 20240703015002.png]]
Lưu ý rằng bạn bây giờ cần hai bản sao đầy đủ của LLM để tính toán độ lệch KL, LLM tham chiếu cố định và LLM được cập nhật bằng PPO.

Bằng cách này, bạn có thể kết hợp RHF với [[parameter efficient fine-tuning]]. 
![[Pasted image 20240703015159.png]]
Trong trường hợp này, bạn chỉ cập nhật các trọng số của p-Tuned adapter, không phải các trọng số đầy đủ của LLM. Điều này có nghĩa là bạn có thể tái sử dụng cùng một LLM cơ bản cho cả mô hình tham chiếu và mô hình PPO, mà bạn cập nhật với các trọng số đã được đào tạo của p-Tuned. Điều này giảm bớt khối lượng bộ nhớ trong quá trình đào tạo khoảng một nửa.

# evaluate
Sau khi bạn hoàn thành việc điều chỉnh RHF của mô hình, bạn sẽ muốn đánh giá hiệu suất của mô hình. Bạn có thể sử dụng bộ dữ liệu tóm tắt để định lượng việc giảm độ độc hại

ví dụ như bộ dữ liệu đối thoại mà bạn đã thấy trước đó trong khóa học. Số bạn sẽ sử dụng ở đây là điểm số độ độc hại, đây là xác suất của lớp tiêu cực, trong trường hợp này là phản hồi độc hại hoặc thù hận trung bình trên các hoàn thành. Nếu RHF đã giảm thành công độ độc hại của LLM, điểm số này sẽ giảm xuống.
![[Pasted image 20240703015504.png]]
Đầu tiên, bạn sẽ tạo một điểm số độ độc hại cơ bản cho LLM hướng dẫn ban đầu bằng cách đánh giá các hoàn thành của nó trên bộ dữ liệu tóm tắt với một mô hình thưởng có thể đánh giá ngôn ngữ độc hại. 
Sau đó, bạn sẽ đánh giá mô hình mới được điều chỉnh theo con người trên cùng một bộ dữ liệu và so sánh các điểm số. Trong ví dụ này, điểm số độ độc hại đã thực sự giảm sau RHF, cho thấy một mô hình ít độc hại hơn và tốt hơn.
