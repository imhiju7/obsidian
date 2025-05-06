*Học tăng cường là một loại [[machine learning]] trong đó một tác nhân học cách đưa ra các quyết định liên quan đến một mục tiêu cụ thể bằng cách thực hiện các hành động trong một môi trường, với mục tiêu tối đa hóa một khái niệm nào đó về phần thưởng tích lũy.*
- RLHF sử dụng [[reinforcement learning]], viết tắt là RL, để fine-tune LLM với dữ liệu phản hồi của con người, kết quả là một mô hình phù hợp hơn với sở thích của con người. Bạn có thể sử dụng RLHF để đảm bảo rằng mô hình của bạn tạo ra các đầu ra tối ưu về mức độ hữu ích và liên quan đến gợi ý đầu vào.
![[Pasted image 20240702103225.png]]
Quan trọng nhất, RLHF có thể giúp giảm thiểu khả năng gây hại. Bạn có thể huấn luyện mô hình của mình đưa ra các cảnh báo thừa nhận giới hạn của chúng và tránh ngôn ngữ và chủ đề độc hại.

Một ứng dụng tiềm năng thú vị của RLHF là cá nhân hóa LLMs, nơi các mô hình học sở thích của từng người dùng thông qua quá trình phản hồi liên tục. Điều này có thể dẫn đến các công nghệ mới thú vị như kế hoạch học tập cá nhân hóa hoặc trợ lý AI cá nhân hóa.

Trong khung này, tác nhân liên tục học hỏi từ kinh nghiệm của mình bằng cách thực hiện các hành động, quan sát các thay đổi kết quả trong môi trường, và nhận phần thưởng hoặc hình phạt, dựa trên kết quả của các hành động của nó.
![[Pasted image 20240702104117.png]]
Bằng cách lặp đi lặp lại quá trình này, tác nhân dần dần tinh chỉnh chiến lược hoặc chính sách của mình để đưa ra các quyết định tốt hơn và tăng cơ hội thành công.

Một ví dụ hữu ích để minh họa những ý tưởng này là huấn luyện một mô hình chơi Tic-Tac-Toe.
- Trong ví dụ này, tác nhân là một mô hình hoặc chính sách hành động như một người chơi Tic-Tac-Toe. 
- Mục tiêu của nó là thắng trò chơi.
- Môi trường là bảng trò chơi ba ô vuông, và trạng thái tại bất kỳ thời điểm nào là cấu hình hiện tại của bảng. 
- Không gian hành động bao gồm tất cả các vị trí mà người chơi có thể chọn dựa trên trạng thái bảng hiện tại. 
- Tác nhân đưa ra các quyết định bằng cách theo dõi một chiến lược được gọi là chính sách RL.
![[Pasted image 20240702104857.png]]
Mục tiêu của học tăng cường là để tác nhân học chính sách tối ưu cho một môi trường nhất định, tối đa hóa phần thưởng của nó.

Ban đầu, tác nhân thực hiện một hành động ngẫu nhiên dẫn đến một trạng thái mới. Từ trạng thái này, tác nhân tiến hành khám phá các trạng thái tiếp theo thông qua các hành động khác. Chuỗi các hành động và các trạng thái tương ứng tạo thành một lượt chơi, thường được gọi là một rollout.

Khi tác nhân tích lũy kinh nghiệm, nó dần dần khám phá ra các hành động mang lại phần thưởng lâu dài cao nhất, cuối cùng dẫn đến thành công trong trò chơi.

Bây giờ, hãy xem cách ví dụ Tic-Tac-Toe có thể được mở rộng đến trường hợp fine-tuning các mô hình ngôn ngữ lớn với RLHF
- Trong trường hợp này, chính sách của tác nhân hướng dẫn các hành động là LLM, và mục tiêu của nó là tạo ra văn bản được coi là phù hợp với sở thích của con người. Điều này có thể có nghĩa là văn bản, ví dụ, hữu ích, chính xác và không độc hại. 
- Môi trường là cửa sổ ngữ cảnh của mô hình, không gian trong đó văn bản có thể được nhập thông qua một gợi ý. 
- Trạng thái mà mô hình xem xét trước khi thực hiện một hành động là ngữ cảnh hiện tại. Điều đó có nghĩa là bất kỳ văn bản nào hiện có trong cửa sổ ngữ cảnh.
- Hành động ở đây là hành động tạo văn bản. Điều này có thể là một từ đơn, một câu, hoặc một văn bản dài hơn, tùy thuộc vào nhiệm vụ do người dùng chỉ định. 
- Không gian hành động là từ vựng token, nghĩa là tất cả các token có thể mà mô hình có thể chọn để tạo ra phần hoàn thành. 
- Cách LLM quyết định tạo ra token tiếp theo trong một chuỗi phụ thuộc vào đại diện thống kê của ngôn ngữ mà nó học được trong quá trình huấn luyện. Tại bất kỳ thời điểm nào, hành động mà mô hình sẽ thực hiện, tức là token nào nó sẽ chọn tiếp theo, phụ thuộc vào văn bản gợi ý trong ngữ cảnh và phân phối xác suất trên không gian từ vựng. 
- Phần thưởng được gán dựa trên mức độ phù hợp của các phần hoàn thành với sở thích của con người. 
![[Pasted image 20240702110914.png]]
- [[obtaining feedback from humans]]
Do sự biến đổi trong phản hồi của con người đối với ngôn ngữ, việc xác định phần thưởng phức tạp hơn so với ví dụ Tic-Tac-Toe. Một cách bạn có thể làm điều này là có một người đánh giá tất cả các phần hoàn thành của mô hình dựa trên một số tiêu chí phù hợp, chẳng hạn như xác định xem văn bản được tạo ra là độc hại hay không độc hại. Phản hồi này có thể được biểu diễn dưới dạng một giá trị vô hướng, hoặc là số không hoặc một.
![[Pasted image 20240702111657.png]]
Như một giải pháp thực tế và có thể mở rộng, bạn có thể sử dụng một mô hình bổ sung, được gọi là [[reward model]], để phân loại các đầu ra của LLM và đánh giá mức độ phù hợp với sở thích của con người.
- Bạn sẽ bắt đầu với một số lượng nhỏ các ví dụ của con người để huấn luyện mô hình thứ cấp theo các phương pháp học có giám sát truyền thống.
- Sau khi được huấn luyện, bạn sẽ sử dụng mô hình phần thưởng để đánh giá đầu ra của LLM và gán giá trị phần thưởng, giá trị này sau đó sẽ được sử dụng để cập nhật trọng số của LLM và huấn luyện một phiên bản mới phù hợp với con người. 
- Chính xác cách trọng số được cập nhật khi các phần hoàn thành của mô hình được đánh giá phụ thuộc vào thuật toán được sử dụng để tối ưu hóa chính sách.

lưu ý rằng trong bối cảnh [[llms]], chuỗi hành động và trạng thái được gọi là một rollout, thay vì thuật ngữ playout được sử dụng trong học tăng cường cổ điển.