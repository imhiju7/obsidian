- ROUGE hay Recall-Oriented Understudy for Gisting Evaluation chủ yếu được sử dụng để đánh giá chất lượng của các bản tóm tắt tự động bằng cách so sánh chúng với các bản tóm tắt do con người tạo ra.

# rouge - 1
- hãy xem xét một câu tham chiếu do con người tạo ra: It is cold outside và một đầu ra được tạo ra: It is very cold outside. Bạn có thể thực hiện các phép tính chỉ số đơn giản tương tự như các nhiệm vụ học máy khác bằng cách sử dụng recall, precision và F1.
![[Pasted image 20240701103332.png]]
- Chỉ số recall đo lường số lượng từ hoặc unigram trùng khớp giữa tham chiếu và đầu ra được tạo ra chia cho số lượng từ hoặc unigram trong tham chiếu. Trong trường hợp này, nó đạt điểm hoàn hảo là một vì tất cả các từ được tạo ra khớp với các từ trong tham chiếu.
- precision đo lường số lượng unigram trùng khớp chia cho kích thước của đầu ra.
- điểm F1 là trung bình điều hòa của cả hai giá trị này.
![[Pasted image 20240701103556.png]]
# rouge - 2
- Bạn có thể nhận được điểm cao hơn một chút bằng cách xem xét các bigram hoặc các cặp từ cùng một lúc từ câu tham chiếu và câu được tạo ra. Bằng cách làm việc với các cặp từ, bạn đang thừa nhận một cách rất đơn giản thứ tự của các từ trong câu. Bằng cách sử dụng các bigram, bạn có thể tính toán một chỉ số ROUGE-2
![[Pasted image 20240701103855.png]]
- Bây giờ, bạn có thể tính toán recall, precision và F1 score sử dụng các bigram trùng khớp thay vì các từ riêng lẻ. Bạn sẽ nhận thấy rằng điểm số thấp hơn so với điểm số ROUGE-1. Với các câu dài hơn, cơ hội các bigram không khớp càng lớn, và điểm số có thể còn thấp hơn.
# rouge - L
Thay vì tiếp tục với các số ROUGE lớn hơn đến các n-gram ba hoặc bốn, hãy lấy một cách tiếp cận khác. Thay vào đó, bạn sẽ tìm kiếm chuỗi con chung dài nhất có mặt trong cả đầu ra được tạo ra và đầu ra tham chiếu. Trong trường hợp này, chuỗi con trùng khớp dài nhất là, it is và cold outside, mỗi cái có độ dài là hai.
![[Pasted image 20240701104150.png]]
Bạn có thể sử dụng giá trị LCS để tính toán recall, precision và F1 score, trong đó tử số trong cả phép tính recall và precision là độ dài của chuỗi con chung dài nhất, trong trường hợp này là hai. Tập hợp, ba số lượng này được gọi là điểm ROUGE-L.

một vấn đề cụ thể với các điểm ROUGE đơn giản là có thể một phần hoàn thành kém lại dẫn đến điểm số tốt. Lấy ví dụ, đầu ra được tạo ra này: cold, cold, cold, cold. Vì đầu ra được tạo ra này chứa một trong các từ từ câu tham chiếu, nó sẽ đạt điểm cao, mặc dù cùng một từ được lặp lại nhiều lần. 
	 - Điểm precision ROUGE-1 sẽ hoàn hảo. 
	 - Một cách bạn có thể khắc phục vấn đề này là sử dụng một hàm clipping để giới hạn số lượng unigram trùng khớp với số lượng tối đa của unigram đó trong tham chiếu. 
	 - Trong trường hợp này, có một sự xuất hiện của từ cold trong tham chiếu và do đó một precision sửa đổi với một clip trên các unigram trùng khớp dẫn đến một điểm số giảm mạnh.
![[Pasted image 20240701104715.png]]

Tuy nhiên, bạn vẫn sẽ gặp khó khăn nếu các từ được tạo ra đều có mặt, nhưng chỉ theo một thứ tự khác. Ví dụ, với câu được tạo ra này: outside cold it is. Câu này sẽ đạt điểm hoàn hảo ngay cả trên precision đã sửa đổi với hàm clipping vì tất cả các từ trong đầu ra được tạo ra đều có mặt trong tham chiếu.
![[Pasted image 20240701104938.png]]
