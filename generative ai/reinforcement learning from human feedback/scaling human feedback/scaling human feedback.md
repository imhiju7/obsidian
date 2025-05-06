- Nỗ lực của con người để tạo ra mô hình phần thưởng được huấn luyện ban đầu là rất lớn. Tập dữ liệu được gắn nhãn dùng để huấn luyện mô hình phần thưởng thường đòi hỏi các nhóm lớn các người gắn nhãn, đôi khi lên đến hàng ngàn người để đánh giá nhiều lời nhắc khác nhau.
![[Pasted image 20240704132059.png]]
- Công việc này đòi hỏi rất nhiều thời gian và các tài nguyên khác, điều này có thể trở thành những yếu tố giới hạn quan trọng. Khi số lượng mô hình và các trường hợp sử dụng tăng lên, nỗ lực của con người trở thành một tài nguyên hạn chế.
- Các phương pháp để mở rộng phản hồi từ con người là một lĩnh vực nghiên cứu đang hoạt động. Một ý tưởng để vượt qua những hạn chế này là mở rộng thông qua sự tự giám sát của mô hình. Constitutional AI là một phương pháp tiếp cận để mở rộng sự giám sát.
![[Pasted image 20240704132120.png]]
Constitutional AI không chỉ hữu ích cho việc mở rộng phản hồi, mà nó còn có thể giúp giải quyết một số hậu quả không mong muốn của RLHF.
Ví dụ, tùy thuộc vào cách lời nhắc được cấu trúc, một mô hình đã được điều chỉnh có thể kết thúc bằng việc tiết lộ thông tin gây hại khi nó cố gắng cung cấp phản hồi hữu ích nhất có thể. Chẳng hạn, hãy tưởng tượng bạn yêu cầu mô hình cung cấp cho bạn hướng dẫn cách hack WiFi của hàng xóm. 
![[Pasted image 20240704132324.png]]
Vì mô hình này đã được điều chỉnh để ưu tiên tính hữu ích, nó thực sự sẽ cho bạn biết về một ứng dụng cho phép bạn làm điều này, mặc dù hoạt động này là bất hợp pháp.

Khi triển khai phương pháp Constitutional AI, bạn huấn luyện mô hình của mình trong hai giai đoạn riêng biệt.

# phase 1
![[Pasted image 20240704132747.png]]
- Bắt đầu bằng cách yêu cầu mô hình phản hồi các lời nhắc để cố gắng làm cho nó tạo ra các phản hồi có hại, quá trình này gọi là red teaming. 
- Sau đó, bạn yêu cầu mô hình tự phê bình các phản hồi có hại của mình theo các nguyên tắc hiến pháp và sửa đổi chúng để tuân thủ các quy tắc đó. 
- Khi hoàn tất, bạn sẽ tinh chỉnh mô hình bằng cách sử dụng các cặp lời nhắc red team và các phản hồi hiến pháp đã sửa đổi.

Trở lại với vấn đề hack WiFi. Như bạn đã thấy trước đó, mô hình này đưa ra một phản hồi có hại khi cố gắng tối đa hóa tính hữu ích của nó. Để giảm thiểu điều này, bạn bổ sung lời nhắc bằng phản hồi có hại và một tập hợp các hướng dẫn được xác định trước yêu cầu mô hình tự phê bình phản hồi của mình. Sử dụng các quy tắc được nêu trong Hiến pháp, mô hình phát hiện các vấn đề trong phản hồi của mình.
![[Pasted image 20240704133438.png]]
Trong trường hợp này, nó nhận thức đúng rằng việc hack vào WiFi của người khác là bất hợp pháp. Cuối cùng, bạn đặt tất cả các phần lại với nhau và yêu cầu mô hình viết một phản hồi mới loại bỏ tất cả nội dung có hại hoặc bất hợp pháp. Mô hình tạo ra một câu trả lời mới đưa các nguyên tắc hiến pháp vào thực tế và không bao gồm tham chiếu đến ứng dụng bất hợp pháp.

Lời nhắc red team ban đầu và phản hồi hiến pháp cuối cùng này sau đó có thể được sử dụng làm dữ liệu huấn luyện. 
![[Pasted image 20240704135111.png]]
Bạn sẽ xây dựng một tập dữ liệu của nhiều ví dụ như thế này để tạo ra một LLM đã được tinh chỉnh, học cách tạo ra các phản hồi hiến pháp.

# phase 2
Ở đây, bạn sử dụng mô hình đã được tinh chỉnh từ bước trước để tạo ra một tập hợp các phản hồi cho lời nhắc của bạn.
![[Pasted image 20240704144238.png]]
Sau đó, bạn yêu cầu mô hình cho biết phản hồi nào được ưa thích theo các nguyên tắc hiến pháp. Kết quả là một tập dữ liệu ưu tiên do mô hình tạo ra mà bạn có thể sử dụng để huấn luyện mô hình phần thưởng.