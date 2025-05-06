Tinh chỉnh theo hướng dẫn, nơi tất cả các trọng số của mô hình được cập nhật, được gọi là tinh chỉnh toàn diện (full fine-tuning). Quá trình này tạo ra một phiên bản mới của mô hình với các trọng số được cập nhật.
Cần lưu ý rằng cũng như việc huấn luyện trước, tinh chỉnh toàn diện yêu cầu đủ bộ nhớ và ngân sách tính toán để lưu trữ và xử lý tất cả các gradient, tối ưu hóa và các thành phần khác đang được cập nhật trong quá trình huấn luyện.

![[Pasted image 20240701004021.png]]

- Dưới đây là một vài ví dụ yêu cầu để minh họa ý tưởng này. Hướng dẫn trong cả hai ví dụ là "phân loại đánh giá này" và kết quả mong muốn là một chuỗi văn bản bắt đầu bằng "tình cảm" (sentiment) tiếp theo là "tích cực" (positive) hoặc "tiêu cực" (negative). Tập dữ liệu bạn sử dụng để huấn luyện bao gồm nhiều cặp ví dụ yêu cầu-hoàn thành cho nhiệm vụ bạn quan tâm, mỗi cặp bao gồm một hướng dẫn.

- Ví dụ, nếu bạn muốn tinh chỉnh mô hình để cải thiện khả năng tóm tắt của nó, bạn sẽ xây dựng một tập dữ liệu các ví dụ bắt đầu bằng hướng dẫn "tóm tắt đoạn văn bản sau" hoặc một cụm từ tương tự. Và nếu bạn đang cải thiện khả năng dịch của mô hình, các ví dụ của bạn sẽ bao gồm các hướng dẫn như "dịch câu này". Những ví dụ yêu cầu-hoàn thành này cho phép mô hình học cách tạo ra các phản hồi tuân theo các hướng dẫn được đưa ra.

Vậy làm thế nào để bạn thực sự tiến hành tinh chỉnh theo hướng dẫn một LLM?
- Bước đầu tiên là chuẩn bị dữ liệu huấn luyện của bạn. Có rất nhiều tập dữ liệu có sẵn công khai đã được sử dụng để huấn luyện các thế hệ mô hình ngôn ngữ trước đó, mặc dù hầu hết chúng không được định dạng dưới dạng các hướng dẫn.
- May mắn thay, các nhà phát triển đã lắp ráp các thư viện mẫu yêu cầu có thể được sử dụng để biến các tập dữ liệu hiện có, ví dụ như tập dữ liệu lớn về đánh giá sản phẩm của Amazon, thành các tập dữ liệu yêu cầu hướng dẫn để tinh chỉnh. Thư viện mẫu yêu cầu bao gồm nhiều mẫu cho các nhiệm vụ khác nhau và các tập dữ liệu khác nhau.

Dưới đây là ba yêu cầu được thiết kế để sử dụng với tập dữ liệu đánh giá Amazon và có thể được sử dụng để tinh chỉnh các mô hình cho các nhiệm vụ phân loại, tạo văn bản và tóm tắt văn bản.

![[Pasted image 20240701004549.png]]

Bạn có thể thấy rằng trong mỗi trường hợp, bạn truyền đoạn đánh giá gốc, được gọi là review_body, vào mẫu, nơi nó được chèn vào văn bản bắt đầu bằng một hướng dẫn như "dự đoán xếp hạng liên quan", "tạo đánh giá sao", hoặc "đưa ra một câu ngắn mô tả đánh giá sản phẩm sau đây". Kết quả là một yêu cầu hiện chứa cả một hướng dẫn và ví dụ từ tập dữ liệu.

Khi bạn đã sẵn sàng tập dữ liệu hướng dẫn của mình, như với học có giám sát tiêu chuẩn, bạn chia tập dữ liệu thành các phần huấn luyện, xác thực và kiểm tra.
![[Pasted image 20240701005025.png]]

trong quá trình tinh chỉnh, bạn chọn các yêu cầu từ tập dữ liệu huấn luyện của mình và truyền chúng vào LLM, mô hình sau đó sẽ tạo ra các phản hồi. Tiếp theo, bạn so sánh phản hồi của LLM với phản hồi được chỉ định trong dữ liệu huấn luyện. 
![[Pasted image 20240701005246.png]]
Bạn có thể thấy ở đây mô hình không làm tốt, nó phân loại đánh giá là trung tính, điều này là một đánh giá hơi nhẹ. Đánh giá rõ ràng là rất tích cực. Hãy nhớ rằng đầu ra của một LLM là một phân phối xác suất trên các token.
![[Pasted image 20240701005347.png]]
Vì vậy, bạn có thể so sánh phân phối của phản hồi và của nhãn huấn luyện và sử dụng hàm cross-entropy tiêu chuẩn để tính toán mất mát giữa hai phân phối token này. Sau đó sử dụng mất mát đã tính toán để cập nhật các trọng số mô hình trong quá trình [[backpropagation]] chuẩn. Bạn sẽ làm điều này cho nhiều batch cặp yêu cầu-hoàn thành và qua nhiều epoch, cập nhật các trọng số để hiệu suất của mô hình trên nhiệm vụ được cải thiện. Như trong học có giám sát tiêu chuẩn, bạn có thể định nghĩa các bước đánh giá riêng biệt để đo lường hiệu suất LLM của bạn bằng cách sử dụng tập dữ liệu xác thực giữ lại.
![[Pasted image 20240701005623.png]]
Điều này sẽ cho bạn độ chính xác của quá trình xác thực, và sau khi bạn hoàn thành tinh chỉnh, bạn có thể thực hiện đánh giá hiệu suất cuối cùng bằng cách sử dụng tập dữ liệu kiểm tra giữ lại. Điều này sẽ cho bạn độ chính xác của quá trình kiểm tra.
![[Pasted image 20240701005645.png]]
Quá trình tinh chỉnh tạo ra một phiên bản mới của mô hình cơ bản, thường được gọi là mô hình hướng dẫn (instruct model) tốt hơn trong các nhiệm vụ bạn quan tâm. Tinh chỉnh với các hướng dẫn là cách phổ biến nhất để tinh chỉnh LLM hiện nay.

- [[fine-tuning on a single task]]