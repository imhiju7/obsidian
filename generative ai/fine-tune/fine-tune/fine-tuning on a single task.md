![[Pasted image 20240701011611.png]]

bạn có thể tinh chỉnh một mô hình đã được huấn luyện trước để cải thiện hiệu suất chỉ trên nhiệm vụ mà bạn quan tâm. Ví dụ, tóm tắt bằng cách sử dụng một tập dữ liệu các ví dụ cho nhiệm vụ đó. Thú vị là, kết quả tốt có thể đạt được với tương đối ít ví dụ. Thường chỉ cần 500-1,000 ví dụ có thể mang lại hiệu suất tốt so với hàng tỷ đoạn văn bản mà mô hình đã thấy trong quá trình huấn luyện trước.

Tuy nhiên, có một mặt trái tiềm năng của việc tinh chỉnh trên một nhiệm vụ duy nhất. Quá trình này có thể dẫn đến hiện tượng gọi là "[[catastrophic forgetting]]" (quên thảm khốc).

Bạn có những lựa chọn nào để tránh quên thảm khốc?
- điều quan trọng là xác định liệu quên thảm khốc có thực sự ảnh hưởng đến trường hợp sử dụng của bạn hay không. Nếu tất cả những gì bạn cần là hiệu suất đáng tin cậy trên nhiệm vụ duy nhất mà bạn đã tinh chỉnh, thì có thể không phải là vấn đề khi mô hình không thể tổng quát hóa sang các nhiệm vụ khác.Nếu bạn muốn hoặc cần mô hình duy trì khả năng tổng quát hóa đa nhiệm vụ của mình, bạn có thể thực hiện tinh chỉnh trên nhiều nhiệm vụ cùng một lúc. Tinh chỉnh đa nhiệm vụ tốt có thể yêu cầu 50-100,000 ví dụ trên nhiều nhiệm vụ, và do đó sẽ yêu cầu nhiều dữ liệu và tính toán để huấn luyện.
- Lựa chọn thứ hai của chúng ta là thực hiện tinh chỉnh hiệu quả theo tham số ([[parameter efficient fine-tuning]], viết tắt là PEFT) thay vì tinh chỉnh toàn diện.
- 