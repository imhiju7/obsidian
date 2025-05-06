PEFT là một tập hợp các kỹ thuật giữ nguyên các trọng số của LLM gốc và chỉ huấn luyện một số ít các lớp adapter và tham số cụ thể cho nhiệm vụ. PEFT cho thấy sự bền vững hơn đối với quên thảm khốc vì hầu hết các trọng số đã được huấn luyện trước không bị thay đổi.

Với PEFT, hầu hết nếu không phải tất cả các trọng số của LLM được giữ nguyên. Kết quả là, số lượng tham số được huấn luyện nhỏ hơn nhiều so với số lượng tham số trong LLM gốc. Trong một số trường hợp, chỉ khoảng 15-20% trọng số của LLM gốc. Điều này làm cho yêu cầu bộ nhớ cho việc huấn luyện trở nên dễ quản lý hơn nhiều.

Thực tế, PEFT thường có thể được thực hiện trên một GPU duy nhất. Và vì LLM gốc chỉ được thay đổi một chút hoặc không thay đổi, PEFT ít bị vấn đề [[catastrophic forgetting]] hơn so với việc [[instruction fine-tuning]].

Việc tinh chỉnh hoàn chỉnh dẫn đến một phiên bản mới của mô hình cho mỗi nhiệm vụ bạn huấn luyện. Mỗi phiên bản này có cùng kích thước với mô hình gốc, vì vậy nó có thể tạo ra một vấn đề lưu trữ tốn kém nếu bạn tinh chỉnh cho nhiều nhiệm vụ.
![[Pasted image 20240701115257.png]]
Với tinh chỉnh hiệu quả tham số, bạn chỉ huấn luyện một số ít trọng số, dẫn đến tổng thể nhỏ hơn nhiều, chỉ còn ở mức megabyte tùy thuộc vào nhiệm vụ. Các tham số mới được kết hợp với trọng số LLM gốc để suy luận. 
Các trọng số PEFT được huấn luyện cho mỗi nhiệm vụ và có thể dễ dàng thay thế cho suy luận, cho phép thích nghi hiệu quả của mô hình gốc với nhiều nhiệm vụ.

![[Pasted image 20240701115439.png]]

# selected method
Các phương pháp chọn lọc là những phương pháp chỉ tinh chỉnh một tập hợp nhỏ các tham số của LLM gốc. 
- Có nhiều cách tiếp cận khác nhau mà bạn có thể áp dụng để xác định các tham số bạn muốn cập nhật. 
- Bạn có thể chọn huấn luyện chỉ một số thành phần nhất định của mô hình hoặc các lớp cụ thể, hoặc thậm chí các loại tham số riêng lẻ. 
Các nhà nghiên cứu đã tìm thấy rằng hiệu suất của các phương pháp này là hỗn hợp và có những sự đánh đổi đáng kể giữa hiệu quả tham số và hiệu quả tính toán.
# reparameterization method
Các phương pháp tái tham số hóa cũng làm việc với các tham số LLM gốc, nhưng giảm số lượng tham số cần huấn luyện bằng cách tạo ra các biến đổi hạng thấp mới của trọng số mạng gốc.
- [[lora]]
- [[soft prompt]]
# additive method
các phương pháp bổ sung thực hiện tinh chỉnh bằng cách giữ nguyên tất cả trọng số của LLM gốc và giới thiệu các thành phần có thể huấn luyện mới. Ở đây có hai cách tiếp cận chính.
- Các phương pháp adapter thêm các lớp có thể huấn luyện mới vào kiến trúc của mô hình, thường nằm bên trong các thành phần [[encoder]] hoặc [[decoder]] sau các [[attention class]] hoặc [[feed-forward]].
- Các phương pháp [[soft prompt]] , mặt khác, giữ nguyên kiến trúc mô hình và tập trung vào việc thao tác đầu vào để đạt hiệu suất tốt hơn. Điều này có thể được thực hiện bằng cách thêm các tham số có thể huấn luyện vào các [[embeddings prompt]] hoặc giữ nguyên đầu vào và huấn luyện lại các [[embedding weight]].