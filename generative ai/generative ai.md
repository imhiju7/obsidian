- [[artificial intelligence]]
- [[machine learning]] là một nhánh của [[artificial intelligence]] cho phép máy móc học từ các dữ liệu hiện có và cải thiện hơn với data đó để đưa ra quyết định hoặc dự đoán.
- [[deep learning]] là một kĩ thuật học máy. Trong đó, mạng neuron được dùng để xử lý dữ liệu và tạo ra quyết định.
- generative ai: Tạo content, ảnh, video,... từ việc đưa prompt và dữ liệu hiện có.
- [[generative ai project lifecycle]]
# Introduction
- [[llms]]
- [[rnns]]
- [[prompt engineering]]
## task type
- SEQ_CLS
- SEQ_2_SEQ_LM
- CAUSAL_LM
- TOKEN_CLS
- QUESTION_ANS
- FEATURE_EXTRACTION.
# model
- [[foundation model]] vs [[llms]]
- [[open source model llms]] vs [[proprietary model]]
- [[embedding model]] vs [[image generation model]] vs  [[text and code generation model]]
- [[transformers model]]
- [[generating text with transformers]]
- [[service ai]] vs [[model ai]]
# generative ai
- [[tokenization]]
- generative configuration: mỗi mô hình đều cung cấp một tập hợp các tham số cấu hình có thể ảnh hưởng đến đầu ra của mô hình trong quá trình suy luận.
	- [[max new tokens]]
	- [[random sampling]]
	- [[top k]]
	- [[top p]]
	- [[temperature]]
- [[pre-trained llms]] & [[pre-training for domain adaptation]]
- [[model evaluation]]
- [[benchmarks]] - [[lora]] - [[soft prompt]]
- [[reinforcement learning from human feedback]]
- [[fine-tuning with reforcement learning]]
- [[proximal policy optimization]]
- [[reward hacking]]
- [[program-aided language models]]
- [[langchain]]
## [[scaling laws and compute-optimal model]]
## prompt engineering
- sau khi lời nhắc được mã hóa, chức năng chính của [[foundation model]] là dự đoán mã thông báo theo trình tự đó. Vì LLM được đào tạo trên các tập dữ liệu văn bản khổng lồ nên họ hiểu rõ về mối quan hệ thống kê giữa các mã thông báo và có thể đưa ra dự đoán đó một cách tự tin. 
	- Lưu ý rằng họ không hiểu nghĩa của các từ trong lời nhắc hoặc mã thông báo; họ chỉ nhìn thấy một mẫu mà họ có thể "hoàn thành" với dự đoán tiếp theo của mình. Họ có thể tiếp tục dự đoán trình tự cho đến khi bị chấm dứt bởi sự can thiệp của người dùng hoặc một số điều kiện được thiết lập trước.
- [[instruction tuned llms]]
- [[predicting output tokens]]
- selection process, probability distribution
	- Mã thông báo đầu ra được mô hình chọn theo xác suất xảy ra sau chuỗi văn bản hiện tại. Điều này là do mô hình dự đoán phân bổ xác suất trên tất cả các 'mã thông báo tiếp theo' có thể có, được tính toán dựa trên quá trình đào tạo của nó. 
	- Tuy nhiên, không phải lúc nào token có xác suất cao nhất cũng được chọn từ phân phối kết quả. Mức độ ngẫu nhiên được thêm vào lựa chọn này, theo cách mà mô hình hoạt động theo kiểu không xác định 
	- Chúng ta không nhận được cùng một đầu ra cho cùng một đầu vào. Mức độ ngẫu nhiên này được thêm vào để mô phỏng quá trình tư duy sáng tạo và nó có thể được điều chỉnh bằng cách sử dụng tham số mô hình gọi là [[temperature]].
- [[encoder-decoder]] vs [[decoder-only]]
	- Hãy tưởng tượng người quản lý của bạn giao cho bạn nhiệm vụ viết một bài kiểm tra cho học sinh. Bạn có hai đồng nghiệp; một người giám sát việc tạo nội dung và người kia giám sát việc xem xét chúng. 
	- Người sáng tạo nội dung giống như một mô hình duy nhất của [[decoder]], họ có thể xem chủ đề và xem những gì bạn đã viết và sau đó anh ta có thể viết một khóa học dựa trên đó. Họ rất giỏi viết nội dung hấp dẫn và giàu thông tin, nhưng lại không giỏi hiểu chủ đề và mục tiêu học tập. Một số ví dụ về mô hình Bộ giải mã là các mô hình dòng [[gpt]], chẳng hạn như gpt-3. 
	- Người đánh giá giống như một mô hình chỉ dành cho [[encoder]], họ xem khóa học được viết và các câu trả lời, nhận thấy mối quan hệ giữa chúng và hiểu ngữ cảnh, nhưng họ không giỏi tạo ra nội dung. Một ví dụ về mô hình chỉ dành cho Bộ mã hóa sẽ là [[bert]]. 
	- Hãy tưởng tượng rằng chúng ta có thể có ai đó có thể tạo và xem lại bài kiểm tra, đây là mô hình [[encoder-decoder]]. Một số ví dụ sẽ là BART và T5.
	- Một mô hình như LLaMA có sẵn để sử dụng, đòi hỏi sức mạnh tính toán để chạy mô hình.
### Primary Content
- Trong các ví dụ trên, lời nhắc vẫn khá mở, cho phép LLM quyết định phần nào của tập dữ liệu được đào tạo trước có liên quan. Với mẫu thiết kế nội dung chính, văn bản đầu vào được chia thành hai phần:
	- một hướng dẫn (hành động)
	- nội dung có liên quan (có ảnh hưởng đến hành động)
![[Pasted image 20240619111516.png]]
Phân đoạn nội dung chính có thể được sử dụng theo nhiều cách khác nhau để hướng dẫn hiệu quả hơn
- **Examples** - thay vì yêu cầu mô hình phải làm gì với một hướng dẫn rõ ràng, hãy đưa cho nó các ví dụ về những việc cần làm và để nó suy ra mẫu.
- **Cues** - làm theo hướng dẫn kèm theo một "dấu hiệu" báo hiệu việc hoàn thành, hướng dẫn mô hình hướng tới các phản hồi phù hợp hơn.
- **Templates** - đây là những 'công thức' có thể lặp lại cho lời nhắc có phần giữ chỗ (biến) có thể được tùy chỉnh bằng dữ liệu cho các trường hợp sử dụng cụ thể.
![[Pasted image 20240619112010.png]]
- use case: [[sumarize dialogue]]
## improving llms results
- **[[prompt engineering with context]]**
- **[[rag]]**
- **[[fine-tune]]d model**
- **[[trained model]]**
![[Pasted image 20240618094052.png]]
# computational challenges of training llms
- Một trong những vấn đề phổ biến nhất mà bạn gặp phải khi cố gắng huấn luyện các mô hình ngôn ngữ lớn (LLM) là hết bộ nhớ
- hầu hết các LLM rất lớn và cần rất nhiều bộ nhớ để lưu trữ và huấn luyện tất cả các tham số của chúng
- Một tham số đơn lẻ thường được biểu diễn bởi một số thực 32-bit, đó là cách máy tính biểu diễn các số thực. Một số thực 32-bit chiếm bốn byte bộ nhớ. Vì vậy, để lưu trữ một tỷ tham số, bạn sẽ cần bốn byte nhân với một tỷ tham số, tức là bốn gigabyte RAM GPU ở độ chính xác 32-bit.
- Nếu bạn muốn huấn luyện mô hình, bạn sẽ phải dự trù thêm các thành phần khác sử dụng bộ nhớ GPU trong quá trình huấn luyện. Bao gồm hai trạng thái của Adam optimizer, gradients, activations, và các biến tạm thời cần thiết bởi các hàm của bạn. Điều này có thể dễ dàng dẫn đến việc sử dụng thêm 20 byte bộ nhớ mỗi tham số của mô hình.
- Một kỹ thuật mà bạn có thể sử dụng để giảm bộ nhớ là lượng tử hóa ([[quantization]])
- [[chiến lược tính toán multi-gpu hiệu quả]]
- [[data parallelism]]
# aligning models with human values
Đến nay, bạn có thể đã thấy nhiều tiêu đề về các mô hình ngôn ngữ lớn cư xử không đúng mực. Các vấn đề bao gồm 
- mô hình sử dụng ngôn ngữ độc hại trong các câu trả lời
- phản hồi bằng giọng điệu hung hăng
- cung cấp thông tin chi tiết về các chủ đề nguy hiểm.
Những vấn đề này tồn tại vì các mô hình lớn được huấn luyện trên lượng lớn dữ liệu văn bản từ Internet, nơi ngôn ngữ như vậy xuất hiện thường xuyên.
# model optimizations for deployment
- Một trong những cách chính để cải thiện hiệu suất ứng dụng là giảm kích thước của LLM. Điều này có thể cho phép tải mô hình nhanh hơn, giảm độ trễ suy luận. Tuy nhiên, thách thức là giảm kích thước của mô hình trong khi vẫn duy trì hiệu suất mô hình.
- [[distilation]]
- [[quantization]]
- [[model pruning]]
# using the llm in applications
Một vấn đề là kiến thức nội bộ mà mô hình nắm giữ bị cắt đứt vào thời điểm huấn luyện ban đầu. Ví dụ, nếu bạn hỏi một mô hình được huấn luyện vào đầu năm 2022 ai là Thủ tướng Anh, có thể nó sẽ trả lời là Boris Johnson. Kiến thức này đã lỗi thời. Mô hình không biết rằng Johnson rời khỏi chức vụ vào cuối năm 2022 vì sự kiện đó xảy ra sau khi nó được huấn luyện.
![[Pasted image 20240704180843.png]]
Các mô hình cũng có thể gặp khó khăn với toán học phức tạp. Nếu bạn yêu cầu một mô hình hành động như một máy tính, nó có thể trả lời sai, tùy thuộc vào độ phức tạp của bài toán. 
![[Pasted image 20240704180859.png]]
Ví dụ, bạn yêu cầu mô hình thực hiện một phép chia. Mô hình trả về một số gần đúng với đáp án đúng, nhưng không chính xác. LLMs không thực hiện các phép toán thực sự. Chúng chỉ cố gắng dự đoán token tốt nhất tiếp theo dựa trên việc huấn luyện, và kết quả là, chúng có thể dễ dàng sai.

Cuối cùng, một trong những vấn đề nổi tiếng nhất của LLMs là xu hướng tạo ra văn bản ngay cả khi chúng không biết câu trả lời cho một vấn đề.
![[Pasted image 20240704181313.png]]
Điều này thường được gọi là "hallucination" (ảo giác), và ở đây bạn có thể thấy mô hình rõ ràng bịa ra một mô tả về một cây không tồn tại, cây Martian Dunetree. Mặc dù chưa có bằng chứng thuyết phục về sự sống trên sao Hỏa, mô hình vẫn vui vẻ nói khác đi.

Ứng dụng của bạn phải quản lý việc chuyển đầu vào của người dùng đến mô hình ngôn ngữ lớn và trả lại các phản hồi. Điều này thường được thực hiện thông qua một số loại thư viện điều phối.
![[Pasted image 20240704181439.png]]
Lớp này có thể cho phép một số công nghệ mạnh mẽ mở rộng và tăng cường hiệu suất của LLM tại thời gian chạy. Bằng cách cung cấp quyền truy cập vào các nguồn dữ liệu bên ngoài hoặc kết nối với các API hiện có của các ứng dụng khác.
![[Pasted image 20240704181557.png]]
# interacting with external applications
- kết nối LLM với các ứng dụng bên ngoài cho phép mô hình tương tác với thế giới rộng lớn hơn, mở rộng tiện ích của chúng vượt ra ngoài các tác vụ ngôn ngữ.
![[Pasted image 20240705002845.png]]
- Điều quan trọng cần lưu ý là các lời nhắc và hoàn thành là trọng tâm của các quy trình làm việc này. Các hành động mà ứng dụng sẽ thực hiện để đáp ứng các yêu cầu của người dùng sẽ được xác định bởi LLM, là động cơ lý luận của ứng dụng.
- mô hình cần có khả năng tạo ra một tập hợp các hướng dẫn để ứng dụng biết phải thực hiện những hành động gì. Những hướng dẫn này cần dễ hiểu và tương ứng với các hành động được phép.
![[Pasted image 20240705004707.png]]
[[completion]] cần được định dạng theo cách mà ứng dụng rộng hơn có thể hiểu. Điều này có thể đơn giản như một cấu trúc câu cụ thể hoặc phức tạp như viết một kịch bản trong Python hoặc tạo một lệnh SQL.
Cuối cùng, mô hình có thể cần thu thập thông tin cho phép nó xác thực một hành động. Ví dụ, trong cuộc trò chuyện của ShopBot, ứng dụng cần xác minh địa chỉ email mà khách hàng đã sử dụng để đặt hàng ban đầu. Bất kỳ thông tin nào cần thiết để xác thực cần được lấy từ người dùng và chứa trong hoàn thành để có thể được chuyển qua ứng dụng.
# helping llms reason and plan with chain-of-thought
- việc suy luận phức tạp có thể là một thách thức đối với LLM, đặc biệt là đối với các vấn đề liên quan đến nhiều bước hoặc toán học. Những vấn đề này tồn tại ngay cả trong các mô hình lớn cho thấy hiệu suất tốt ở nhiều nhiệm vụ khác. Đây là một ví dụ mà một LLM gặp khó khăn trong việc hoàn thành nhiệm vụ.
- Lời nhắc của bạn bao gồm một vấn đề ví dụ tương tự, kèm theo giải pháp, để giúp mô hình hiểu nhiệm vụ thông qua suy luận một lần.
- Một chiến lược đã cho thấy một số thành công là yêu cầu mô hình suy nghĩ giống như con người hơn, bằng cách chia nhỏ vấn đề thành các bước.
- Yêu cầu mô hình bắt chước hành vi này được gọi là [[chain of thought prompting]]. Nó hoạt động bằng cách bao gồm một loạt các bước suy luận trung gian vào bất kỳ ví dụ nào mà bạn sử dụng để [[one-shot inference]] hoặc [[few-shot inference]].
- Chain of thought prompting là một kỹ thuật mạnh mẽ cải thiện khả năng của mô hình của bạn để suy luận qua các vấn đề. Trong khi điều này có thể cải thiện đáng kể hiệu suất của mô hình của bạn, các kỹ năng toán học hạn chế của các LLM vẫn có thể gây ra vấn đề nếu nhiệm vụ của bạn yêu cầu các phép tính chính xác, như tổng hợp doanh số bán hàng trên một trang thương mại điện tử, tính toán thuế, hoặc áp dụng giảm giá.
# combining reasoning and action
- Hầu hết các ứng dụng sẽ yêu cầu LLM quản lý các quy trình công việc phức tạp hơn, có thể bao gồm tương tác với nhiều nguồn dữ liệu và ứng dụng bên ngoài. Trong video này, bạn sẽ khám phá một khung làm việc gọi là [[react]], có thể giúp LLM lên kế hoạch và thực hiện các quy trình công việc này.
# llm application architectures
Bạn sẽ cần một số thành phần chính để tạo ra các giải pháp từ đầu đến cuối cho các ứng dụng của mình, bắt đầu với lớp cơ sở hạ tầng. 
![[Pasted image 20240705164933.png]]
- Lớp này cung cấp khả năng tính toán, lưu trữ và mạng để phục vụ các LLM của bạn, cũng như để lưu trữ các thành phần của ứng dụng. Bạn có thể sử dụng cơ sở hạ tầng tại chỗ của mình hoặc có thể được cung cấp qua các dịch vụ đám mây theo yêu cầu và thanh toán theo sử dụng.
- Tiếp theo, bạn sẽ bao gồm các mô hình ngôn ngữ lớn mà bạn muốn sử dụng trong ứng dụng của mình. Các mô hình này có thể bao gồm các mô hình nền tảng, cũng như các mô hình bạn đã điều chỉnh cho nhiệm vụ cụ thể của mình. Các mô hình được triển khai trên cơ sở hạ tầng phù hợp với nhu cầu suy luận của bạn, xem xét liệu bạn có cần tương tác theo thời gian thực hoặc gần thời gian thực với mô hình.
- Bạn cũng có thể cần lấy thông tin từ các nguồn bên ngoài, chẳng hạn như những nguồn được thảo luận trong phần tạo ra thông tin bổ sung bằng cách tìm kiếm.
- Ứng dụng của bạn sẽ trả lại các phần [[completion]] từ mô hình ngôn ngữ lớn cho người dùng hoặc ứng dụng tiêu thụ. Tùy thuộc vào trường hợp sử dụng của bạn, bạn có thể cần thực hiện cơ chế để ghi lại và lưu trữ các đầu ra. Ví dụ, bạn có thể xây dựng khả năng lưu trữ các phần hoàn thành của người dùng trong một phiên để tăng cường kích thước cửa sổ ngữ cảnh cố định của LLM.
- Bạn cũng có thể thu thập phản hồi từ người dùng có thể hữu ích cho việc điều chỉnh thêm, căn chỉnh hoặc đánh giá khi ứng dụng của bạn trưởng thành.
- Tiếp theo, bạn có thể cần sử dụng các công cụ và khung làm việc bổ sung cho các mô hình ngôn ngữ lớn giúp bạn dễ dàng triển khai một số kỹ thuật. Ví dụ, bạn có thể sử dụng các thư viện tích hợp của LangChain để triển khai các kỹ thuật như PAL, ReAct hoặc nhắc nhở chuỗi suy nghĩ. Bạn cũng có thể sử dụng các trung tâm mô hình cho phép bạn quản lý và chia sẻ các mô hình trung tâm để sử dụng trong các ứng dụng.
- Trong lớp cuối cùng, bạn thường có một loại giao diện người dùng nào đó mà ứng dụng sẽ được tiêu thụ qua, chẳng hạn như một trang web hoặc một API REST. Lớp này cũng là nơi bạn sẽ bao gồm các thành phần bảo mật cần thiết để tương tác với ứng dụng của bạn.
	- Ở mức độ cao, ngăn xếp kiến trúc này đại diện cho các thành phần khác nhau cần xem xét là một phần của các ứng dụng AI sinh ra. Người dùng của bạn, dù là người dùng cuối hoặc các hệ thống khác truy cập ứng dụng của bạn thông qua các API của nó, sẽ tương tác với toàn bộ ngăn xếp này.