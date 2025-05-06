# AI Algorithm

# AI Learning
## Model deep learning
Mô hình học sâu (Deep Learning) là một nhánh của trí tuệ nhân tạo (AI) và học máy (Machine Learning), dựa trên việc xây dựng các mạng nơ-ron nhân tạo nhiều tầng để học và trích xuất các đặc trưng phức tạp từ dữ liệu. Mô hình học sâu có khả năng tự học từ dữ liệu lớn mà không cần phải được lập trình cụ thể để nhận diện các đặc trưng đó.
### Các thành phần chính của mô hình học sâu
1. **Mạng nơ-ron nhân tạo (Artificial Neural Networks - ANN)**: Cấu trúc cơ bản của một mô hình học sâu bao gồm các nơ-ron kết nối với nhau theo các tầng (layers). Tầng đầu vào (input layer), các tầng ẩn (hidden layers), và tầng đầu ra (output layer).
2. **Tầng ẩn nhiều lớp (Deep Layered Architecture)**: Học sâu liên quan đến việc sử dụng nhiều lớp ẩn để trích xuất các đặc trưng phức tạp, khác với học máy truyền thống chỉ có một hoặc ít tầng ẩn.
3. **Hàm kích hoạt (Activation Function)**: Các hàm này quyết định đầu ra của một nơ-ron dựa trên các trọng số (weights) và độ chệch (bias). Một số hàm phổ biến bao gồm ReLU, Sigmoid, và Tanh.
4. **Lan truyền ngược (Backpropagation)**: Phương pháp điều chỉnh trọng số của mạng dựa trên sai số dự đoán so với giá trị thực tế, thông qua thuật toán tối ưu như gradient descent.
5. **Dữ liệu lớn (Big Data)**: Mô hình học sâu thường yêu cầu lượng dữ liệu lớn để học hiệu quả và giảm thiểu vấn đề quá khớp (overfitting).
### Một số loại mô hình học sâu phổ biến:
### Mạng nơ-ron tích chập (Convolutional Neural Network - CNN)
là một loại mô hình học sâu được thiết kế đặc biệt cho việc xử lý và phân tích dữ liệu dưới dạng lưới, như hình ảnh và video. CNN đã trở thành công cụ quan trọng trong lĩnh vực thị giác máy tính, xử lý hình ảnh, và nhận dạng đối tượng.
#### Cấu trúc cơ bản của CNN:
Mạng CNN có cấu trúc bao gồm các tầng khác nhau để học và trích xuất các đặc trưng từ hình ảnh. Các tầng phổ biến trong CNN gồm:
1. **Tầng tích chập (Convolutional Layer)**:
    - Tầng này sử dụng các bộ lọc (filter/kernel) nhỏ để quét qua hình ảnh đầu vào.
    - Mỗi bộ lọc sẽ phát hiện các đặc trưng cụ thể như đường viền, góc cạnh, hoặc các hình dạng nhỏ trong ảnh.
    - Quá trình tích chập giúp mô hình tập trung vào những khu vực quan trọng của hình ảnh mà không cần xử lý toàn bộ dữ liệu một cách trực tiếp.
2. **Tầng kích hoạt (Activation Layer)**:
    - Sau khi thực hiện tích chập, các giá trị sẽ được đưa qua một hàm kích hoạt, phổ biến nhất là **ReLU (Rectified Linear Unit)**, để giữ lại các giá trị dương và loại bỏ các giá trị âm.
    - Điều này giúp mạng trở nên phi tuyến tính, tăng khả năng học tập các đặc trưng phức tạp.
3. **Tầng gộp (Pooling Layer)**:
    - Tầng này giảm kích thước không gian của dữ liệu đầu ra từ tầng tích chập, thường được gọi là **down-sampling**.
    - Có hai loại gộp chính: **Max pooling** (chọn giá trị lớn nhất trong mỗi vùng) và **Average pooling** (tính trung bình giá trị trong mỗi vùng).
    - Tầng gộp giúp giảm số lượng tham số và tính toán, ngăn chặn việc quá khớp (overfitting).
4. **Tầng phẳng (Flattening Layer)**:
    - Sau các tầng tích chập và gộp, dữ liệu sẽ được làm phẳng thành một mảng dài để có thể đưa vào mạng nơ-ron fully connected.
5. **Tầng fully connected (Fully Connected Layer - FC)**:
    - Tầng này kết nối tất cả các nơ-ron trong lớp hiện tại với các nơ-ron trong lớp tiếp theo.
    - Mục tiêu là học các mối quan hệ phức tạp giữa các đặc trưng đã được trích xuất từ các tầng trước đó.
    - Tầng cuối cùng thường là một lớp softmax để tạo ra các xác suất phân loại.
#### Quá trình hoạt động của CNN:
- **Input**: Dữ liệu đầu vào thường là một hình ảnh được biểu diễn dưới dạng ma trận điểm ảnh (pixels).
- **Feature Extraction**: Tầng tích chập và tầng gộp sẽ thực hiện trích xuất các đặc trưng quan trọng từ hình ảnh, giảm kích thước nhưng vẫn giữ lại thông tin quan trọng.
- **Classification**: Tầng fully connected sẽ thực hiện phân loại dựa trên các đặc trưng đã được trích xuất.
#### Ví dụ ứng dụng của CNN:
1. **Nhận dạng hình ảnh**: CNN đã tạo ra đột phá trong các bài toán nhận dạng hình ảnh, chẳng hạn như phân loại ảnh (ImageNet).
2. **Phát hiện đối tượng**: Mạng CNN có thể được sử dụng để phát hiện các đối tượng trong ảnh và đánh dấu vị trí của chúng (Object Detection).
3. **Xử lý văn bản**: Dù CNN chủ yếu được sử dụng trong xử lý hình ảnh, nhưng nó cũng có thể áp dụng để trích xuất đặc trưng từ văn bản trong một số ứng dụng như phân loại văn bản hoặc phân tích cảm xúc.
CNN hoạt động tốt nhờ khả năng tự động học các đặc trưng mà không cần con người chỉ định, giúp giảm thiểu lượng tiền xử lý dữ liệu so với các phương pháp truyền thống.
### Mạng nơ-ron hồi quy (Recurrent Neural Networks - RNN)
**Mạng nơ-ron hồi quy (Recurrent Neural Networks - RNN)** là một loại mạng nơ-ron chuyên xử lý dữ liệu có tính tuần tự, chẳng hạn như chuỗi thời gian, văn bản, hoặc âm thanh. Khác với các mạng nơ-ron truyền thống, RNN có khả năng lưu trữ thông tin từ các bước trước trong chuỗi và sử dụng thông tin đó để dự đoán hoặc đưa ra các quyết định cho các bước sau.
#### Cấu trúc cơ bản của RNN:

- **Các nơ-ron hồi quy** trong RNN có một đặc điểm khác biệt so với các mạng truyền thống, đó là mỗi nơ-ron không chỉ nhận đầu vào từ tầng trước mà còn nhận đầu vào từ chính nó ở thời điểm trước đó.
- RNN có một **trạng thái ẩn (hidden state)** giúp ghi nhớ thông tin từ các bước trước trong chuỗi. Tại mỗi bước, trạng thái ẩn được cập nhật dựa trên đầu vào hiện tại và trạng thái ẩn của bước trước.
#### Công thức hoạt động:
- **Đầu vào (input)** tại thời điểm $t$: $x_{t}$
- **Trạng thái ẩn (hidden state)** tại thời điểm $t$: $x_{t}$, được tính dựa trên trạng thái ẩn trước đó $h_{t-1}$​ và đầu vào hiện tại $x_{t}$
    Công thức toán học cho trạng thái ẩn là:
     $$h_t=f(W_{hx}⋅x_t+W_{hh}⋅h_{t−1}+b_h)h_t$$
    Trong đó:
    - $W_{hx},W_{hh}$ là các ma trận trọng số.
    - $b_{h}$​ là độ chệch.
    - $f$ là hàm kích hoạt (thường là tanh hoặc ReLU).
- **Đầu ra (output)** tại thời điểm $t$: $y_{t}$​, được tính dựa trên trạng thái ẩn hiện tại hth_tht​.
    Công thức toán học cho đầu ra là:
    $$y_t=g(W_{hy}⋅h_t+b_y)y_t$$
    Trong đó:
    - $W_{hy}$ là ma trận trọng số kết nối trạng thái ẩn với đầu ra.
    - $b_y$​ là độ chệch cho đầu ra.
    - $g$ là hàm kích hoạt hoặc hàm softmax nếu sử dụng cho phân loại.
#### Hạn chế của RNN thông thường:
1. **Vấn đề về mờ dần hoặc bùng nổ gradient (vanishing/exploding gradients)**: Khi chuỗi dữ liệu quá dài, RNN gặp khó khăn trong việc học thông tin từ các bước trước xa do gradient giảm dần hoặc tăng đột ngột qua nhiều tầng
2. **Khó nhớ thông tin dài hạn**: Do thông tin từ các bước trước được lưu giữ và truyền qua trạng thái ẩn, RNN thông thường gặp khó khăn khi cần lưu giữ thông tin dài hạn trong chuỗi.
#### Các biến thể của RNN:
Để giải quyết những hạn chế của RNN thông thường, hai biến thể phổ biến đã được phát triển:
1. **LSTM (Long Short-Term Memory)**:
    - LSTM được thiết kế để khắc phục vấn đề về vanishing gradient bằng cách sử dụng các cơ chế **cổng (gates)** để kiểm soát thông tin nào nên được lưu giữ, thông tin nào nên được quên và thông tin nào nên được sử dụng trong tính toán đầu ra.
    - LSTM có 3 loại cổng: **Forget Gate** (quyết định thông tin nào sẽ bị quên), **Input Gate** (quyết định thông tin nào được thêm vào trạng thái), và **Output Gate** (quyết định thông tin nào sẽ được xuất ra).
2. **GRU (Gated Recurrent Unit)**:
    - GRU là một biến thể đơn giản hơn của LSTM nhưng vẫn giải quyết được vấn đề mờ dần gradient. Nó chỉ sử dụng hai cổng: **Update Gate** và **Reset Gate**.
    - GRU có cấu trúc nhẹ hơn so với LSTM nhưng mang lại hiệu suất tương đương trong nhiều trường hợp.
#### Ứng dụng của RNN:
RNN và các biến thể của nó được sử dụng rộng rãi trong các ứng dụng cần xử lý dữ liệu tuần tự, như:
- **Xử lý ngôn ngữ tự nhiên (NLP)**: Dịch máy, phân tích cảm xúc, tạo văn bản tự động.
- **Nhận dạng giọng nói**: RNN có khả năng nhận diện các chuỗi âm thanh và chuyển đổi chúng thành văn bản.
- **Dự đoán chuỗi thời gian**: Phân tích và dự đoán các dữ liệu tuần tự như giá cổ phiếu, dữ liệu thời tiết.
- **Phân loại video**: RNN có thể sử dụng để phân loại và hiểu nội dung của một đoạn video dựa trên chuỗi các khung hình.
#### Minh họa hoạt động của RNN:
- **Input Sequence**: x1,x2,…,xTx_1, x_2, \dots, x_Tx1​,x2​,…,xT​ (Chuỗi đầu vào).
- **Hidden States**: h1,h2,…,hTh_1, h_2, \dots, h_Th1​,h2​,…,hT​ (Trạng thái ẩn tại mỗi bước).
- **Output Sequence**: y1,y2,…,yTy_1, y_2, \dots, y_Ty1​,y2​,…,yT​ (Chuỗi đầu ra).
RNN sẽ cập nhật trạng thái ẩn dựa trên thông tin từ cả chuỗi đầu vào hiện tại và trạng thái ẩn của bước trước, giúp mô hình lưu giữ và sử dụng thông tin theo thời gian.
### Mạng nơ-ron truy hồi (Transformer) 
là một mô hình học sâu tiên tiến, được phát triển để giải quyết các vấn đề liên quan đến chuỗi dữ liệu tuần tự, đặc biệt trong các tác vụ xử lý ngôn ngữ tự nhiên (NLP) như dịch máy, tóm tắt văn bản, và sinh văn bản. Transformer đã thay thế các mạng hồi quy (RNN) và LSTM trong nhiều ứng dụng nhờ khả năng xử lý hiệu quả và nhanh chóng hơn trên các chuỗi dữ liệu dài, mà không gặp phải những hạn chế của RNN như vấn đề về mờ dần gradient.
#### Cấu trúc chính của Transformer:
Mô hình Transformer bao gồm hai phần chính: **bộ mã hóa (encoder)** và **bộ giải mã (decoder)**. Mỗi bộ mã hóa và giải mã bao gồm nhiều lớp (layers) kết hợp các cơ chế chính là **cơ chế tự chú ý (self-attention)** và **mạng truyền dẫn đầy đủ (fully connected feed-forward network)**.
#### 1. **Cơ chế Tự Chú ý (Self-Attention Mechanism)**
- **Attention** là thành phần cốt lõi của Transformer, giúp mô hình tập trung vào các phần quan trọng của chuỗi đầu vào khi tạo ra đầu ra.
- Thay vì chỉ dựa vào thông tin từ một bước trước đó như trong RNN, mô hình Transformer sử dụng cơ chế tự chú ý để tính toán sự liên quan giữa tất cả các từ trong câu (hoặc các phần tử trong chuỗi) một cách song song.
- Tại mỗi bước, mô hình tạo ra các ma trận **Q (Query)**, **K (Key)**, và **V (Value)**. Mô hình sẽ tính toán một trọng số chú ý bằng cách lấy tích vô hướng của các giá trị Query và Key, sau đó nhân với ma trận Value để xác định thông tin quan trọng.
Công thức chính cho self-attention:
$$Attention(Q,K,V)=softmax(\frac{QK^{t}}{\sqrt{d_{k}}}V)$$
Trong đó:
- Q, K, và V là các ma trận khác nhau của dữ liệu đầu vào.
- $d_k$ là kích thước của vector K.
- Hàm **softmax** được sử dụng để chuẩn hóa các trọng số chú ý.
#### 2. **Multi-Head Attention (Chú ý đa đầu)**
- Để tăng cường khả năng học nhiều loại thông tin khác nhau, Transformer sử dụng nhiều **đầu chú ý (attention heads)**. Mỗi đầu chú ý học một phần khác nhau của chuỗi đầu vào, sau đó kết hợp các kết quả lại với nhau để cải thiện khả năng hiểu ngữ cảnh.
- Điều này cho phép mô hình có thể "nhìn" vào nhiều khía cạnh của câu cùng một lúc.
#### 3. **Mạng truyền dẫn đầy đủ (Fully Connected Feed-Forward Network)**
- Sau khi xử lý qua cơ chế chú ý, dữ liệu được truyền qua một mạng truyền dẫn đầy đủ với một số lớp ẩn (hidden layers) để học thêm các đặc trưng.
- Hàm kích hoạt thường được sử dụng là **ReLU**.
#### 4. **Normalization (Chuẩn hóa) và Residual Connections**
- Mỗi lớp trong bộ mã hóa và giải mã có một lớp **chuẩn hóa (Layer Normalization)** giúp ổn định việc huấn luyện mô hình.
- **Residual connections** (kết nối tắt) được thêm vào để giảm thiểu việc mất mát thông tin trong quá trình truyền từ lớp này sang lớp khác, đảm bảo rằng thông tin không bị mất đi qua nhiều tầng xử lý.
#### 5. **Bộ Mã hóa (Encoder)**
- Bộ mã hóa gồm nhiều lớp giống hệt nhau, mỗi lớp gồm hai thành phần chính: cơ chế chú ý đa đầu (multi-head self-attention) và mạng truyền dẫn đầy đủ.
- Bộ mã hóa nhận đầu vào là toàn bộ chuỗi, tính toán các liên hệ giữa các phần tử trong chuỗi thông qua cơ chế tự chú ý, và xuất ra một biểu diễn ngữ nghĩa cho từng phần tử.

#### 6. **Bộ Giải mã (Decoder)**
- Bộ giải mã có cấu trúc tương tự như bộ mã hóa nhưng có thêm một cơ chế chú ý vào chuỗi đầu ra trước đó (self-attention), cùng với chú ý vào đầu ra của bộ mã hóa (encoder-decoder attention).
- Bộ giải mã dùng các thông tin từ chuỗi đầu vào (thông qua bộ mã hóa) và từ các từ đã sinh ra trước đó để tạo ra từ tiếp theo trong chuỗi đầu ra.
#### 7. **Embedding (Mã hóa vị trí)**
- Transformer không sử dụng các chuỗi tuần tự như RNN, vì vậy nó cần một cách để biểu diễn vị trí của các phần tử trong chuỗi. **Vị trí embedding (positional encoding)** được thêm vào để mô hình có thể biết được vị trí của từng từ trong câu.
#### Ưu điểm của Transformer:
1. **Xử lý song song**: Khác với RNN phải xử lý từng bước một, Transformer xử lý toàn bộ chuỗi dữ liệu cùng lúc, giúp giảm thời gian tính toán và cải thiện hiệu suất.
2. **Tốt hơn với các chuỗi dài**: Transformer không gặp vấn đề về gradient bị mờ dần hay bùng nổ như RNN/LSTM, giúp mô hình có thể học tốt hơn với chuỗi dài.
3. **Khả năng học ngữ cảnh toàn cục**: Nhờ vào cơ chế chú ý, Transformer có thể học được ngữ cảnh trên toàn bộ chuỗi, thay vì chỉ giới hạn ở thông tin gần nhất như RNN.
#### Ứng dụng của Transformer:
1. **Xử lý ngôn ngữ tự nhiên (NLP)**: Transformer đã tạo ra đột phá trong các tác vụ NLP như dịch máy, tóm tắt văn bản, và phân loại văn bản. Mô hình nổi bật nhất là **GPT (Generative Pretrained Transformer)** và **BERT (Bidirectional Encoder Representations from Transformers)**.
2. **Dịch máy (Machine Translation)**: Mô hình dịch máy dựa trên Transformer như **Google Translate** đã đạt độ chính xác cao hơn so với các mô hình trước đây.
3. **Xử lý hình ảnh**: Các biến thể của Transformer, chẳng hạn như **Vision Transformer (ViT)**, đã bắt đầu được sử dụng trong xử lý hình ảnh, phân loại ảnh và các bài toán thị giác máy tính khác.
4. **Phát hiện đối tượng (Object Detection)**: Mô hình Transformer đã được áp dụng thành công trong các tác vụ phát hiện đối tượng và phân đoạn hình ảnh.
## LLM
Mô hình ngôn ngữ lớn (Large Language Model - LLM) là một loại mô hình máy học được huấn luyện trên một lượng lớn dữ liệu ngôn ngữ tự nhiên để thực hiện các tác vụ xử lý ngôn ngữ tự nhiên (NLP). Mô hình này thường được huấn luyện bằng cách sử dụng các mạng nơ-ron sâu, như transformer, giúp nó có khả năng học các mẫu ngôn ngữ từ hàng tỷ từ và câu.
Các đặc điểm chính của mô hình ngôn ngữ lớn bao gồm:
1. **Khả năng dự đoán từ/câu tiếp theo**: Mô hình có thể dự đoán từ hoặc câu tiếp theo dựa trên ngữ cảnh của câu hiện tại.
2. **Hiểu và tạo văn bản**: Mô hình có thể hiểu và tạo ra văn bản tự nhiên, từ đó thực hiện nhiều tác vụ như trả lời câu hỏi, dịch thuật, tạo văn bản tự động, và nhiều ứng dụng khác.
3. **Huấn luyện trên lượng dữ liệu khổng lồ**: Mô hình được huấn luyện với lượng dữ liệu rất lớn từ nhiều nguồn khác nhau, từ đó có thể nắm bắt được nhiều kiến thức và mẫu ngôn ngữ đa dạng.
4. **Sử dụng các kiến trúc mạng nơ-ron sâu**: Transformer là một trong những kiến trúc chính được sử dụng trong việc xây dựng các mô hình này. Các mô hình tiêu biểu bao gồm GPT (Generative Pretrained Transformer), BERT (Bidirectional Encoder Representations from Transformers), và T5.
## Sinh Video
### StableVideo 
Là một dự án nghiên cứu sử dụng mô hình khuếch tán (diffusion model) để chỉnh sửa video dựa trên các prompt văn bản. Dự án này dựa trên nền tảng của Stable Diffusion, một mô hình tạo hình ảnh nổi tiếng, và được mở rộng để tạo video. Mô hình này hoạt động bằng cách chọn các khung hình chính từ video và áp dụng chỉnh sửa dựa trên văn bản. Sau đó, thông tin từ các khung hình chính này được lan truyền sang các khung hình liền kề, đảm bảo sự nhất quán về hình ảnh và hình dạng trong toàn bộ video.
StableVideo cũng sử dụng kỹ thuật "inter-frame propagation" để duy trì sự đồng nhất về ngoại hình của các đối tượng qua các khung hình, giúp video giữ được sự liên tục về hình học và chuyển động. Công nghệ này đặc biệt hữu ích trong các ứng dụng như thay đổi thuộc tính đối tượng, áp dụng phong cách nghệ thuật mới, hoặc thậm chí thay thế nền mà vẫn đảm bảo tính nhất quán về không gian và thời gian​
###  Sora
Sora là một mô hình AI tiên tiến của OpenAI, được thiết kế để tạo ra video từ văn bản. Dưới đây là một số chi tiết về cách Sora hoạt động và ứng dụng của nó:
#### Cách Sora Hoạt Động
1. **Kỹ Thuật Khuếch Tán**: Sora sử dụng kỹ thuật khuếch tán để biến đổi video từ trạng thái nhiễu thành hình ảnh rõ ràng. Quá trình này diễn ra qua nhiều bước, mỗi bước làm giảm dần nhiễu và cải thiện chất lượng hình ảnh.
2. **Mô Hình Học Sâu**: Sora được huấn luyện trên một lượng lớn dữ liệu video và văn bản, giúp nó hiểu và tạo ra các video phù hợp với mô tả văn bản.
3. **Tạo Video**: Khi nhận được một đoạn văn bản, Sora sẽ phân tích và chuyển đổi thông tin này thành các khung hình video liên tiếp, tạo ra một video hoàn chỉnh.
#### Ứng Dụng Của Sora
1. **Sáng Tạo Nội Dung**: Sora có thể được sử dụng để tạo ra các video sáng tạo cho quảng cáo, phim ảnh, và các dự án nghệ thuật.
2. **Giáo Dục**: Mô hình này có thể tạo ra các video giáo dục dựa trên nội dung văn bản, giúp học sinh và sinh viên dễ dàng tiếp thu kiến thức.
3. **Giải Trí**: Sora có thể tạo ra các video giải trí dựa trên các câu chuyện hoặc kịch bản do người dùng cung cấp.
### Runway Gen-3
là một công cụ mạnh mẽ trong việc tạo video từ văn bản. Nó sử dụng các mô hình học sâu tiên tiến để tạo ra các video với chất lượng chuyển động cao. Runway Gen-3 có thể tạo ra các video chân thực và sáng tạo, phù hợp cho nhiều ứng dụng từ quảng cáo đến nghệ thuật.
### Dream Machine
Dream machine của Luma Labs là một mô hình tiên tiến khác, có khả năng tạo ra các video dài hơn và hiểu chuyển động tốt hơn. Dream Machine sử dụng các kỹ thuật học sâu để phân tích và tạo ra các khung hình video liên tiếp, giúp tạo ra các video mượt mà và chân thực.
### Pika Labs
**Pika Labs** cung cấp các công cụ tạo video AI với nhiều phong cách và nội dung khác nhau. Đây là một lựa chọn tốt nếu bạn muốn thử nghiệm với các video ngắn và đa dạng. Pika Labs tập trung vào việc tạo ra các video ngắn nhưng chất lượng cao, phù hợp cho các nền tảng mạng xã hội.
## Sinh Voice
### Tacotron 2
- **Phát triển bởi**: Google
- **Cơ chế hoạt động**: Tacotron 2 sử dụng mạng nơ-ron hồi quy để chuyển đổi văn bản thành phổ mel-spectrogram, sau đó sử dụng WaveNet để chuyển đổi phổ này thành sóng âm thanh.
- **Ưu điểm**: Tạo ra giọng nói tự nhiên và mượt mà, có thể điều chỉnh ngữ điệu và tốc độ nói.
- **Ứng dụng**: Được sử dụng trong các dịch vụ TTS của Google như Google Assistant.
### WaveNet
- **Phát triển bởi**: DeepMind (Google)
- **Cơ chế hoạt động**: WaveNet mô phỏng sóng âm thanh bằng cách sử dụng mạng nơ-ron tích chập (convolutional neural network).
- **Ưu điểm**: Tạo ra giọng nói chất lượng cao với độ chân thực cao, có thể mô phỏng nhiều giọng nói và ngữ điệu khác nhau.
- **Ứng dụng**: Được sử dụng trong các dịch vụ TTS của Google và các ứng dụng khác
### FastSpeech
- **Phát triển bởi**: Microsoft
- **Cơ chế hoạt động**: FastSpeech sử dụng kiến trúc transformer để cải thiện tốc độ và chất lượng của quá trình tổng hợp giọng nói.
- **Ưu điểm**: Tốc độ tổng hợp nhanh hơn so với các mô hình truyền thống, chất lượng giọng nói cao.
- **Ứng dụng**: Được sử dụng trong các dịch vụ TTS của Microsoft như Azure Cognitive Services.
### SpeechT5
- **Phát triển bởi**: Microsoft
- **Cơ chế hoạt động**: SpeechT5 sử dụng kiến trúc transformer để hỗ trợ nhiều ngôn ngữ và giọng nói khác nhau.
- **Ưu điểm**: Đa ngôn ngữ, có thể tùy chỉnh giọng nói và ngữ điệu.
- **Ứng dụng**: Được sử dụng trong các dịch vụ TTS của Microsoft.
### Bark
- **Phát triển bởi**: Suno
- **Cơ chế hoạt động**: Bark sử dụng mạng nơ-ron để tạo ra giọng nói tự nhiên và có thể tùy chỉnh.
- **Ưu điểm**: Giọng nói tự nhiên, có thể điều chỉnh ngữ điệu và tốc độ nói.
- **Ứng dụng**: Được sử dụng trong các ứng dụng TTS của Suno.
### HiFi-GAN
- **Phát triển bởi**: NVIDIA
- **Cơ chế hoạt động**: HiFi-GAN sử dụng mạng nơ-ron tích chập để tạo ra giọng nói chất lượng cao với tốc độ nhanh.
- **Ưu điểm**: Chất lượng giọng nói cao, tốc độ tổng hợp nhanh.
- **Ứng dụng**: Được sử dụng trong các dịch vụ TTS của NVIDIA.
## Speech to text
### DeepSpeech
- **Phát triển bởi**: Mozilla
- **Cơ chế hoạt động**: DeepSpeech sử dụng mạng nơ-ron hồi quy sâu (RNN) để chuyển đổi giọng nói thành văn bản.
- **Ưu điểm**: Mã nguồn mở, dễ dàng tùy chỉnh và tích hợp vào các ứng dụng khác.
- **Ứng dụng**: Được sử dụng trong nhiều ứng dụng nhận diện giọng nói và trợ lý ảo.
### Wav2Vec 2.0
- **Phát triển bởi**: Facebook AI Research (FAIR)
- **Cơ chế hoạt động**: Wav2Vec 2.0 sử dụng mạng nơ-ron transformer để học các đặc trưng từ sóng âm thanh và chuyển đổi chúng thành văn bản.
- **Ưu điểm**: Hiệu suất cao, có thể hoạt động tốt với dữ liệu ít được gán nhãn.
- **Ứng dụng**: Được sử dụng trong các hệ thống nhận diện giọng nói và dịch vụ chuyển đổi giọng nói thành văn bản.
### Jasper
- **Phát triển bởi**: NVIDIA
- **Cơ chế hoạt động**: Jasper sử dụng mạng nơ-ron tích chập (CNN) để xử lý và chuyển đổi giọng nói thành văn bản.
- **Ưu điểm**: Tốc độ xử lý nhanh, độ chính xác cao.
- **Ứng dụng**: Được sử dụng trong các ứng dụng nhận diện giọng nói thời gian thực.
### Conformer
- **Phát triển bởi**: Google
- **Cơ chế hoạt động**: Conformer kết hợp giữa mạng nơ-ron tích chập và mạng nơ-ron hồi quy để cải thiện độ chính xác và tốc độ của quá trình chuyển đổi giọng nói thành văn bản.
- **Ưu điểm**: Hiệu suất cao, khả năng xử lý tốt với các ngữ cảnh phức tạp.
- **Ứng dụng**: Được sử dụng trong các dịch vụ nhận diện giọng nói của Google.
## Image
### DALL-E
- **Phát triển bởi**: OpenAI
- **Cơ chế hoạt động**: DALL-E sử dụng kiến trúc transformer để tạo ra hình ảnh từ mô tả văn bản. Nó có khả năng tạo ra các hình ảnh phức tạp và sáng tạo từ các mô tả chi tiết.
- **Ưu điểm**: Khả năng tạo ra hình ảnh độc đáo và sáng tạo, hỗ trợ nhiều phong cách hình ảnh khác nhau.
- **Ứng dụng**: Được sử dụng trong các dự án nghệ thuật, thiết kế sản phẩm, và các ứng dụng sáng tạo khác.
### Stable Diffusion
- **Phát triển bởi**: Stability AI
- **Cơ chế hoạt động**: Stable Diffusion sử dụng mô hình khuếch tán để tạo ra hình ảnh từ văn bản. Nó hoạt động bằng cách dần dần loại bỏ nhiễu từ một hình ảnh ngẫu nhiên để tạo ra hình ảnh cuối cùng.
- **Ưu điểm**: Tạo ra hình ảnh chất lượng cao, có thể tùy chỉnh phong cách và chi tiết.
- **Ứng dụng**: Được sử dụng trong nghệ thuật kỹ thuật số, thiết kế đồ họa, và các ứng dụng sáng tạo khác.
### MidJourney
- **Phát triển bởi**: MidJourney
- **Cơ chế hoạt động**: MidJourney sử dụng các kỹ thuật học sâu để tạo ra hình ảnh từ văn bản. Nó tập trung vào việc tạo ra các hình ảnh nghệ thuật và sáng tạo.
- **Ưu điểm**: Hình ảnh nghệ thuật, phong cách đa dạng.
- **Ứng dụng**: Được sử dụng trong nghệ thuật kỹ thuật số, thiết kế đồ họa, và các dự án sáng tạo khác
## Học tập
1. **ClassPoint AI**:
    - **Chức năng chính**: Tạo câu hỏi trắc nghiệm từ các slide PowerPoint.
    - **Cách hoạt động**: ClassPoint AI phân tích nội dung của slide và tự động tạo ra các câu hỏi trắc nghiệm phù hợp. Giáo viên có thể điều chỉnh loại câu hỏi và mức độ khó để phù hợp với mục tiêu giảng dạy.
    - **Ưu điểm**: Tiết kiệm thời gian cho giáo viên, hỗ trợ nhiều ngôn ngữ, và giúp tạo ra các bài kiểm tra đa dạng và phong phú.
2. **Gradescope**:
    - **Chức năng chính**: Tự động chấm điểm và phản hồi cho các bài kiểm tra.
    - **Cách hoạt động**: Gradescope sử dụng AI để nhận diện và chấm điểm các bài kiểm tra viết tay hoặc đánh máy. Nó cũng có khả năng phát hiện đạo văn và cung cấp phản hồi chi tiết cho học sinh.
    - **Ưu điểm**: Giảm tải công việc chấm bài cho giáo viên, đảm bảo tính chính xác và công bằng trong chấm điểm, và cung cấp phản hồi nhanh chóng cho học sinh.
3. **Magic School AI**:
    - **Chức năng chính**: Hỗ trợ lập kế hoạch bài học và tạo kế hoạch đánh giá trắc nghiệm.
    - **Cách hoạt động**: Magic School AI phân tích mục tiêu giảng dạy và nội dung bài học để tạo ra các kế hoạch bài giảng và bài kiểm tra phù hợp. Nó cũng cung cấp các công cụ giảng dạy khác như tạo bài tập và tài liệu học tập.
    - **Ưu điểm**: Giúp giáo viên tiết kiệm thời gian trong việc lập kế hoạch giảng dạy, nâng cao hiệu quả giảng dạy và đảm bảo các bài học được thiết kế một cách khoa học và hợp lý
    ### **Cognii**
- **Mô tả**: Cognii là một hệ thống hỗ trợ học tập cá nhân hóa bằng trợ lý ảo AI. Điểm nổi bật của Cognii là khả năng phản hồi tức thì với câu trả lời được cá nhân hóa dựa trên các câu hỏi và mục tiêu học tập của từng học viên.
- **Tính năng chính**:
    - **Trợ lý ảo AI**: Tương tác theo thời gian thực với người học, đưa ra các gợi ý, giải thích, và phản hồi tức thì.
    - **Cá nhân hóa lộ trình học**: Phân tích khả năng của từng học viên và đề xuất các bài học phù hợp để nâng cao năng lực.
    - **Đánh giá tự động**: Cognii tự động chấm điểm và đưa ra phản hồi cho các câu trả lời, giúp tiết kiệm thời gian và nâng cao hiệu quả học tập.
- **Ưu điểm**: Hỗ trợ phản hồi cá nhân hóa, giúp người học nắm bắt kiến thức một cách hiệu quả; hỗ trợ giáo viên trong việc đánh giá và phản hồi tức thì cho học viên.
- **Ứng dụng**: Phù hợp với các môi trường học tập trực tuyến, đặc biệt là trong giáo dục đại học và đào tạo nghề nghiệp.

### **Learning 360**
- **Mô tả**: Learning 360 là một nền tảng học tập toàn diện kết hợp AI nhằm cung cấp một hệ sinh thái học tập cá nhân hóa cho người dùng. Nền tảng này phân tích hành vi học tập và tiến trình của từng học viên để điều chỉnh nội dung và phương pháp giảng dạy.
- **Tính năng chính**:
    - **Phân tích hành vi học tập**: Thu thập dữ liệu từ các hoạt động học tập, từ đó phân tích và điều chỉnh lộ trình học.
    - **Đề xuất nội dung học tập thông minh**: Dựa trên tiến trình và hành vi của học viên, hệ thống tự động đưa ra các đề xuất nội dung học tập phù hợp.
    - **Theo dõi tiến độ**: Giúp người học và giáo viên dễ dàng theo dõi sự tiến bộ và thành tích học tập, đồng thời điều chỉnh chiến lược học tập khi cần.
- **Ưu điểm**: Phân tích hành vi chi tiết, giúp tối ưu hóa nội dung học tập phù hợp với từng cá nhân; dễ dàng tích hợp với các hệ thống LMS (Learning Management System) hiện có.
- **Ứng dụng**: Phù hợp cho các tổ chức giáo dục, đặc biệt là các tổ chức lớn muốn cá nhân hóa chương trình đào tạo của họ.

### **CogniSpark AI**
- **Mô tả**: CogniSpark AI là một nền tảng cá nhân hóa học tập sử dụng AI nhằm nâng cao sự tương tác giữa giáo viên và học sinh, tạo điều kiện để đánh giá và cải thiện năng lực của người học.
- **Tính năng chính**:
    - **Trợ lý học tập thông minh**: Cung cấp thông tin và hướng dẫn cho người học, giúp giải đáp thắc mắc và nâng cao sự tự tin trong học tập.
    - **Phân tích tiến trình học tập**: Theo dõi tiến độ học tập và đưa ra các biện pháp cải thiện cho học viên dựa trên dữ liệu học tập.
    - **Đo lường và đánh giá tiến bộ**: Hỗ trợ giáo viên trong việc theo dõi sự tiến bộ của từng học sinh và xác định các khía cạnh cần cải thiện.
- **Ưu điểm**: Cải thiện khả năng tương tác giữa giáo viên và học viên; giúp giáo viên hiểu rõ nhu cầu học tập của học viên và điều chỉnh phương pháp giảng dạy phù hợp.
- **Ứng dụng**: Được sử dụng rộng rãi trong các trường học và trung tâm đào tạo để cá nhân hóa học tập và đánh giá kết quả học tập.

### **Zavvy**
- **Mô tả**: Zavvy là một hệ thống quản lý học tập cá nhân hóa, tích hợp các tính năng AI để điều chỉnh nội dung học tập và trải nghiệm của người học, đảm bảo mỗi người có một lộ trình học tập hiệu quả.
- **Tính năng chính**:
    - **Điều chỉnh nội dung theo nhu cầu cá nhân**: Zavvy đề xuất và điều chỉnh nội dung học tập dựa trên sở thích và tiến độ của người học.
    - **Theo dõi và đánh giá sự phát triển**: Cung cấp các báo cáo tiến độ, từ đó giúp người học hiểu rõ về mức độ tiến bộ và các lĩnh vực cần cải thiện.
    - **Tăng cường trải nghiệm học tập**: Zavvy mang lại trải nghiệm học tập cá nhân hóa, hỗ trợ người học qua các phương pháp học mới và nâng cao sự tự tin.
- **Ưu điểm**: Nâng cao trải nghiệm học tập, dễ sử dụng, và phù hợp với các môi trường học tập hiện đại; giúp người học đạt được mục tiêu cá nhân một cách hiệu quả.
- **Ứng dụng**: Thích hợp cho các tổ chức giáo dục và doanh nghiệp muốn triển khai các chương trình đào tạo cá nhân hóa cho nhân viên hoặc học viên.
# MetaHeuristic Algorithm

## 2.1
### Hãy trình bày về thuật toán tham lam
Thuật toán tham lam (greedy algorithm) là một kỹ thuật giải quyết vấn đề bằng cách chọn lựa phương án tốt nhất ngay tại thời điểm hiện tại mà không quan tâm đến hệ quả dài hạn. Điều này có nghĩa là thuật toán tham lam đưa ra các quyết định cục bộ tối ưu để hướng đến một lời giải tổng thể có thể là tối ưu toàn cục hoặc gần tối ưu.

#### Đặc điểm của thuật toán tham lam:

1. **Tính chất lựa chọn tham lam**: Tại mỗi bước, thuật toán sẽ chọn phương án tốt nhất (lớn nhất, nhỏ nhất, nhanh nhất, v.v.) mà không cần xem xét toàn bộ bài toán. Quyết định ở mỗi bước được đưa ra dựa trên lợi ích hiện tại mà không cần quay lại điều chỉnh.
    
2. **Nguyên lý tối ưu con**: Bài toán có thể được chia thành các bài toán con độc lập, và lời giải của từng bài toán con phải có tính chất tối ưu thì lời giải tổng thể cũng sẽ tối ưu. Nếu bài toán có tính chất này thì thuật toán tham lam thường sẽ tìm được lời giải tối ưu.
    

#### Quy trình giải quyết bài toán bằng thuật toán tham lam:

1. **Bước 1**: Khởi tạo từ điểm bắt đầu.
2. **Bước 2**: Tại mỗi bước, chọn lựa phương án tốt nhất hiện có dựa trên tiêu chí tham lam.
3. **Bước 3**: Lặp lại quá trình cho đến khi đạt được lời giải.

#### Điều kiện áp dụng:

- Thuật toán tham lam không phải lúc nào cũng đưa ra lời giải tối ưu cho tất cả các bài toán. Nó chỉ phù hợp với những bài toán có **cấu trúc bài toán con tối ưu** và **tính chất lựa chọn tham lam**.
- Một số bài toán không có lời giải tối ưu nếu dùng phương pháp tham lam, nhưng vẫn có thể áp dụng thuật toán này để tìm lời giải gần đúng (xấp xỉ).
### Thuật toán tham lam giải bài toán TSP:

Thuật toán tham lam đưa ra một giải pháp xấp xỉ cho bài toán TSP bằng cách áp dụng nguyên tắc "chọn con đường ngắn nhất" tại mỗi bước, mặc dù nó không đảm bảo tìm được lời giải tối ưu.
#### Ý tưởng chính:

1. Bắt đầu từ một thành phố bất kỳ (gọi là thành phố xuất phát).
2. Tại mỗi bước, từ thành phố hiện tại, chọn thành phố gần nhất (chưa được thăm) để đi tiếp.
3. Lặp lại cho đến khi tất cả các thành phố đã được thăm.
4. Cuối cùng, quay trở lại thành phố xuất phát để hoàn thành chu trình.
#### Quy trình cụ thể:

1. **Khởi tạo**: Chọn một thành phố xuất phát (có thể chọn ngẫu nhiên hoặc dựa trên một quy tắc nhất định).
2. **Lặp qua các thành phố**:
    - Từ thành phố hiện tại, tìm thành phố gần nhất chưa được thăm và đi đến đó.
    - Đánh dấu thành phố đó đã được thăm.
    - Lặp lại quá trình cho đến khi tất cả các thành phố đã được thăm.
3. **Quay lại thành phố xuất phát**: Sau khi thăm hết các thành phố, quay trở lại thành phố xuất phát để hoàn thành chu trình.
### Yêu cầu là sử dụng thuật toán tham lam (Greedy Travelling Salesman - GTS2) để tìm hành trình tối ưu.

![[Pasted image 20240928132621.png]]
#### Đề bài đã cho các giá trị:

- p=4p = 4p=4: Thành phố xuất phát là 4.
- v1=1, v2=3, v3=4, v4=6: Đây là thứ tự các thành phố cần thăm.
Chúng ta sẽ thực hiện giải thuật theo các bước sau:
#### Bước 1: Khởi tạo tại thành phố 4

Từ thành phố 4, ta cần chọn thành phố có chi phí nhỏ nhất. Lựa chọn gần nhất từ thành phố 4 là:

- Thành phố 1 với chi phí 13
- Thành phố 2 với chi phí 18
- Thành phố 3 với chi phí 11
- Thành phố 5 với chi phí 19
- Thành phố 6 với chi phí 19

**Chọn thành phố 3** (chi phí 11 là nhỏ nhất).

#### Bước 2: Từ thành phố 3, tiếp tục chọn thành phố gần nhất chưa thăm:

- Thành phố 1 với chi phí 21
- Thành phố 2 với chi phí 22
- Thành phố 5 với chi phí 18
- Thành phố 6 với chi phí 19
**Chọn thành phố 5** (chi phí 18 là nhỏ nhất).
#### Bước 3: Từ thành phố 5, chọn thành phố tiếp theo chưa thăm:

- Thành phố 1 với chi phí 14
- Thành phố 2 với chi phí 15
- Thành phố 6 với chi phí 8
**Chọn thành phố 6** (chi phí 8 là nhỏ nhất).
#### Bước 4: Từ thành phố 6, chọn thành phố chưa thăm:

- Thành phố 1 với chi phí 19
- Thành phố 2 với chi phí 20

**Chọn thành phố 1** (chi phí 19 là nhỏ nhất).

#### Bước 5: Từ thành phố 1, chọn thành phố cuối cùng (thành phố 2):

- Chỉ còn lại thành phố 2 với chi phí 16.

**Chọn thành phố 2** (chi phí 16).

#### Bước cuối: Quay trở lại thành phố xuất phát (thành phố 4):

- Từ thành phố 2 quay về thành phố 4 với chi phí 10.

#### Lộ trình:

4 → 3 → 5 → 6 → 1 → 2 → 4

#### Tổng chi phí:

11+18+8+19+16+10=82

Như vậy, hành trình tốt nhất theo thuật toán tham lam là: **4 → 3 → 5 → 6 → 1 → 2 → 4**, với tổng chi phí là **82**.

Đối với các bài toán dạng thiết kế thì ưu tiên về lời giải
Đối với các bài toán dạng thực thi thì ưu tiên thời gian tính
## 2.2
### Trình bày thuật toán tham lam Welsh - Powell giải bài toán tô màu đồ thị
#### Bài toán tô màu đồ thị:

- Cho một đồ thị vô hướng G=(V,E)G = (V, E)G=(V,E) với tập các đỉnh VVV và tập các cạnh EEE.
- Mục tiêu: Tô màu các đỉnh của đồ thị sao cho không có hai đỉnh kề nhau (nối bởi một cạnh) có cùng màu, đồng thời sử dụng số màu ít nhất có thể.

#### Thuật toán Welsh - Powell:

1. **Sắp xếp đỉnh**: Sắp xếp các đỉnh của đồ thị theo bậc (số cạnh nối với đỉnh đó) giảm dần. Đỉnh có bậc lớn nhất sẽ được xem xét trước.
    
2. **Tô màu tham lam**:
    
    - Duyệt qua các đỉnh đã được sắp xếp.
    - Đối với mỗi đỉnh, gán cho nó màu nhỏ nhất có thể mà không bị trùng với màu của các đỉnh kề với nó (nếu có).
    - Tiếp tục tô màu các đỉnh khác cho đến khi tất cả các đỉnh đều được tô.
3. **Kết thúc**: Sau khi tất cả các đỉnh đều được tô màu, ta có một cách tô màu đồ thị với số màu sử dụng ít nhất theo thuật toán.
    

#### Cấu trúc thuật toán:
Giả sử đồ thị có nnn đỉnh và mmm cạnh, các bước thực hiện thuật toán có thể được mô tả như sau:
1. **Sắp xếp các đỉnh theo bậc giảm dần**:
    - Tính bậc của từng đỉnh và sắp xếp các đỉnh từ cao đến thấp theo bậc.
2. **Gán màu cho các đỉnh**:
    - Khởi tạo mảng màu color[], trong đó color[i]=−1 nghĩa là đỉnh i chưa được tô màu.
    - Duyệt qua từng đỉnh trong danh sách đã sắp xếp:
        - Đối với mỗi đỉnh, tìm các màu đã sử dụng bởi các đỉnh kề với nó (nếu có).
        - Chọn màu nhỏ nhất chưa được sử dụng để tô cho đỉnh đó.
3. **Trả về kết quả**: Sau khi hoàn tất, mỗi đỉnh sẽ được gán một màu.
### Tô màu đồ thị
Để tô màu đồ thị trong hình đã tải lên, ta sẽ áp dụng thuật toán Welsh-Powell đã mô tả trước đó. Thuật toán này thực hiện các bước chính sau:

1. **Xác định bậc của các đỉnh**: Đếm số cạnh nối với mỗi đỉnh để xác định bậc của nó.
2. **Sắp xếp các đỉnh theo bậc giảm dần**: Đỉnh có bậc lớn nhất sẽ được xử lý trước.
#### Bước 1: Tính bậc của các đỉnh
Dựa vào hình, ta có các đỉnh và các cạnh tương ứng:
- **Đỉnh H**: Kết nối với A, G, K, I, J → Bậc = 5
- **Đỉnh K**: Kết nối với D, J, I, H → Bậc = 4
- **Đỉnh I**: Kết nối với A, H, J, K → Bậc = 4
- **Đỉnh J**: Kết nối với K, I, H → Bậc = 3
- **Đỉnh G**: Kết nối với H → Bậc = 1
- **Đỉnh F**: Kết nối với E → Bậc = 1
- **Đỉnh E**: Kết nối với F → Bậc = 1
- **Đỉnh A**: Kết nối với H, I → Bậc = 2
- **Đỉnh B**: Kết nối với D → Bậc = 1
- **Đỉnh D**: Kết nối với C, B, K → Bậc = 3
- **Đỉnh C**: Kết nối với D → Bậc = 1
#### Bước 2: Sắp xếp các đỉnh theo bậc giảm dần:
Danh sách sắp xếp theo bậc giảm dần là: H (5), I (4), K (4), D (3), J (3), A (2), G (1), F (1), E (1), B (1), C (1).
#### Bước 3: Tô màu các đỉnh
Dựa vào thứ tự các đỉnh đã sắp xếp, chúng ta tô màu như sau:
- **H**: Màu 1
- **I**: Màu 2 (vì I kề với H đã được tô màu 1)
- **K**: Màu 3 (kề với I và H)
- **D**: Màu 1 (kề với K nên không được màu 3)
- **J**: Màu 1 (kề với K và I đã có màu 2 và 3)
- **A**: Màu 1 (kề với I, nhưng vẫn có thể dùng màu 1)
- **G**: Màu 2 (kề với H, không được màu 1)
- **F**: Màu 1 (kề với E)
- **E**: Màu 2 (kề với F)
- **B**: Màu 2 (kề với D, đã có màu 1)
- **C**: Màu 2 (kề với D)
#### Kết quả cuối cùng:
- H: Màu 1
- I: Màu 2
- K: Màu 3
- D: Màu 1
- J: Màu 1
- A: Màu 1
- G: Màu 2
- F: Màu 1
- E: Màu 2
- B: Màu 2
- C: Màu 2
## 2.3
### Bước 1: Phân tích các yêu cầu
- Có 12 quyển sách thuộc 4 loại khác nhau:
    - Truyện cười: A, C, D, G.
    - Âm nhạc: B, H, K.
    - Lịch sử: E, J, L.
    - Khoa học: F, I.
- Ràng buộc:
    1. Các quyển sách cùng loại không được để chung một kệ.
    2. Sách **A** không được để chung với sách khoa học (F, I).
    3. Sách **L** không được để chung với sách âm nhạc (B, H, K).
### Bước 2: Xây dựng mô hình bài toán
Ta có thể biểu diễn các quyển sách như các đỉnh trong đồ thị, và nối cạnh giữa hai đỉnh nếu chúng không thể đặt cùng một kệ.
#### Đồ thị:
- Các sách cùng loại phải khác kệ → Nối cạnh giữa các sách cùng loại.
- Sách A không được chung kệ với F và I → Nối cạnh A với F và I.
- Sách L không được chung kệ với B, H, K → Nối cạnh L với B, H, K.
#### Đồ thị các cạnh:
- A: C, D, G, F, I.
- C: A, D, G.
- D: A, C, G.
- G: A, C, D.
- B: H, K, L.
- H: B, K, L.
- K: B, H, L.
- E: J, L.
- J: E, L.
- L: E, J, B, H, K.
- F: A, I.
- I: A, F.
### Bước 3: Áp dụng thuật toán tô màu đồ thị
Bài toán này trở thành bài toán tô màu đồ thị, trong đó mỗi kệ là một màu và số lượng màu (số kệ) phải tối ưu. Ta sẽ tô màu các đỉnh sao cho các đỉnh có cạnh nối không được tô cùng màu.
1. Đỉnh A cần một màu (kệ) khác với C, D, G, F, I.
2. Tương tự cho các đỉnh khác dựa trên đồ thị.
Ta có thể sử dụng thuật toán tô màu Greedy để giải quyết, hoặc thử với từng màu cho đến khi tìm được cách sắp xếp sử dụng số màu (kệ) ít nhất.
### Kết quả
Sau khi áp dụng thuật toán, số kệ tối thiểu sẽ là 5.
- Kệ 1: A, B, E, F.
- Kệ 2: C, H, I.
- Kệ 3: D, J.
- Kệ 4: G, K.
- Kệ 5: L.
## 2.10 
### 1. **Thuật toán Heuristic**

Thuật toán heuristic là những phương pháp nhằm tìm kiếm lời giải tốt cho một bài toán trong một khoảng thời gian hữu hạn. Các thuật toán này dựa trên các quy tắc hoặc "kinh nghiệm" để rút ngắn thời gian tìm kiếm, giúp đạt được giải pháp hợp lý nhanh chóng mà không cần phải kiểm tra mọi khả năng.

- **Đặc điểm**:
    
    - **Nhanh chóng**: Heuristic thường đưa ra lời giải nhanh hơn so với các phương pháp tối ưu hóa toàn cục.
    - **Không đảm bảo tối ưu toàn cục**: Do ưu tiên tốc độ, các thuật toán heuristic thường chỉ đạt được giải pháp tốt (nhưng không phải lúc nào cũng tối ưu) cho bài toán.
    - **Phụ thuộc vào bài toán**: Mỗi bài toán cần một heuristic khác nhau, thường phải xây dựng các quy tắc và "mẹo" dựa trên cấu trúc cụ thể của bài toán.
- **Ví dụ**: Một số heuristic phổ biến gồm:
    
    - **Greedy Algorithm**: Lựa chọn phương án tốt nhất tại mỗi bước với hy vọng rằng cách tiếp cận này sẽ dẫn đến giải pháp tốt nhất.
    - **Nearest Neighbor Heuristic** trong bài toán người đi du lịch (Traveling Salesman Problem - TSP).

### 2. **Thuật toán Metaheuristic**

Thuật toán metaheuristic là một lớp các thuật toán cao hơn được thiết kế để tối ưu hóa cho một tập rộng các bài toán. Các thuật toán này không bị ràng buộc vào cấu trúc cụ thể của từng bài toán mà có thể được áp dụng một cách linh hoạt cho nhiều loại bài toán tối ưu hóa khác nhau.

- **Đặc điểm**:
    
    - **Linh hoạt**: Metaheuristic có thể áp dụng cho nhiều bài toán khác nhau mà không cần điều chỉnh quá nhiều.
    - **Khả năng tìm kiếm toàn cục**: Các thuật toán này thường có cơ chế giúp tránh rơi vào bẫy tối ưu cục bộ và có thể tiến tới lời giải tối ưu toàn cục.
    - **Thường dùng trong tối ưu hóa phức tạp**: Được áp dụng trong các bài toán tối ưu hóa lớn, khó giải quyết bằng các phương pháp thông thường.
- **Ví dụ**: Một số thuật toán metaheuristic nổi tiếng gồm:
    
    - **Genetic Algorithm (GA)**: Mô phỏng quá trình chọn lọc tự nhiên và lai tạo để tìm ra lời giải tối ưu.
    - **Simulated Annealing (SA)**: Sử dụng ý tưởng làm lạnh kim loại để khám phá không gian tìm kiếm.
    - **Particle Swarm Optimization (PSO)**: Mô phỏng hành vi của đàn chim để tối ưu hóa hàm số.
    - **Ant Colony Optimization (ACO)**: Mô phỏng cách tìm kiếm thức ăn của loài kiến.

### Sự khác biệt chính giữa Heuristic và Metaheuristic

| Đặc điểm            | Heuristic                               | Metaheuristic                              |
| ------------------- | --------------------------------------- | ------------------------------------------ |
| **Tốc độ**          | Thường nhanh hơn                        | Có thể chậm hơn tùy thuộc vào thuật toán   |
| **Đảm bảo tối ưu**  | Không, có thể chỉ đạt lời giải gần đúng | Có khả năng tìm được tối ưu toàn cục       |
| **Phạm vi áp dụng** | Thường đặc thù cho từng bài toán        | Áp dụng rộng rãi, nhiều bài toán khác nhau |

Heuristic thường phù hợp với các bài toán có quy mô nhỏ hoặc trung bình, nơi việc tìm kiếm giải pháp chính xác không phải là mục tiêu chính. Trong khi đó, metaheuristic lại thường được sử dụng trong các bài toán có quy mô lớn và phức tạp, nơi mà thời gian và tài nguyên tính toán là một yếu tố cần cân nhắc.
## 2.11
### **1. Ưu điểm của thuật toán Heuristic**:

- **Tốc độ**: Thuật toán heuristic thường nhanh hơn đáng kể so với các thuật toán tìm lời giải chính xác vì chúng không cần duyệt hết tất cả các khả năng mà chỉ dựa vào các quy tắc gần đúng.
- **Đơn giản và dễ triển khai**: Heuristic thường dễ dàng xây dựng và triển khai hơn vì chúng không đòi hỏi tính toán phức tạp.
- **Tiêu thụ ít tài nguyên**: Chúng sử dụng ít bộ nhớ và thời gian tính toán hơn các thuật toán chính xác, điều này làm cho chúng phù hợp với các bài toán lớn hoặc khi thời gian tính toán là yếu tố quan trọng.
- **Ứng dụng thực tế**: Heuristic có thể giải quyết được các bài toán thực tế phức tạp và có tính ngẫu nhiên, ví dụ như các bài toán tối ưu hóa trong kỹ thuật và khoa học máy tính.

### **2. Khuyết điểm của thuật toán Heuristic**:

- **Không đảm bảo tìm được lời giải tối ưu**: Do không duyệt qua toàn bộ không gian tìm kiếm, thuật toán heuristic chỉ cung cấp lời giải gần đúng, không chắc chắn sẽ tìm được lời giải tốt nhất.
- **Phụ thuộc vào từng bài toán**: Mỗi heuristic cần được tùy chỉnh cho từng bài toán cụ thể, điều này làm cho chúng không linh hoạt khi áp dụng vào các bài toán khác nhau.
- **Cạm bẫy tối ưu cục bộ**: Heuristic có thể dễ bị rơi vào bẫy tối ưu cục bộ, dẫn đến việc dừng lại ở các lời giải không phải là tốt nhất.

### **3. Ưu điểm của các thuật toán tìm lời giải chính xác**:

- **Đảm bảo tìm được lời giải tối ưu**: Các thuật toán như quy hoạch động, quay lui, nhánh cận có thể tìm được lời giải tối ưu chính xác cho bài toán.
- **Áp dụng được cho nhiều loại bài toán**: Các thuật toán chính xác thường được áp dụng rộng rãi cho các bài toán có cấu trúc phức tạp và yêu cầu lời giải chính xác, không phụ thuộc vào tính đặc thù của bài toán.
- **Không bị ảnh hưởng bởi tối ưu cục bộ**: Do khám phá toàn bộ không gian tìm kiếm, các thuật toán này không bị mắc kẹt tại các điểm tối ưu cục bộ.

### **4. Khuyết điểm của các thuật toán tìm lời giải chính xác**:

- **Thời gian tính toán cao**: Các thuật toán tìm lời giải chính xác thường tốn kém về mặt thời gian, đặc biệt là đối với các bài toán có không gian tìm kiếm lớn (ví dụ, bài toán NP-complete).
- **Sử dụng nhiều tài nguyên**: Các thuật toán chính xác thường yêu cầu nhiều bộ nhớ và tài nguyên tính toán, làm cho chúng không phù hợp cho các bài toán lớn.
- **Khó triển khai cho các bài toán thực tế**: Trong nhiều trường hợp, các thuật toán này quá phức tạp và khó áp dụng cho các bài toán thực tế hoặc môi trường động, nơi mà các giải pháp gần đúng chấp nhận được.

### **So sánh tổng quan**:

||**Thuật toán Heuristic**|**Thuật toán Chính Xác (Quy hoạch động, Quay lui, Nhánh cận)**|
|---|---|---|
|**Tốc độ**|Nhanh, ít tính toán phức tạp|Chậm, tốn nhiều tài nguyên tính toán|
|**Lời giải**|Gần đúng, không đảm bảo tối ưu toàn cục|Chính xác, đảm bảo tối ưu toàn cục|
|**Khả năng tổng quát**|Phải tùy chỉnh cho từng bài toán|Áp dụng được cho nhiều bài toán khác nhau|
|**Bẫy tối ưu cục bộ**|Có thể bị mắc kẹt|Không bị ảnh hưởng|
|**Phù hợp với thực tế**|Thường phù hợp với các bài toán thực tế có ràng buộc|Thường khó triển khai hơn cho các bài toán thực tế phức tạp |

Tùy thuộc vào yêu cầu về độ chính xác và thời gian xử lý, việc lựa chọn
## 2.12 
**Thuật toán tìm kiếm cục bộ (Local Search Algorithm)** là một dạng thuật toán heuristic được sử dụng rộng rãi trong các bài toán tối ưu hóa, đặc biệt khi không gian tìm kiếm quá lớn khiến các thuật toán chính xác trở nên không khả thi. Tìm kiếm cục bộ không khám phá toàn bộ không gian lời giải mà chỉ tìm cách cải thiện giải pháp hiện tại bằng cách thay đổi một phần nhỏ của nó.
### **Nguyên lý của thuật toán tìm kiếm cục bộ**:

- Thuật toán bắt đầu với một lời giải khả thi ban đầu.
- Sau đó, thuật toán liên tục tìm kiếm trong "láng giềng" (neighborhood) của lời giải hiện tại để tìm ra một lời giải tốt hơn.
- Quá trình này tiếp tục cho đến khi không có lời giải nào tốt hơn trong vùng lân cận hoặc một điều kiện dừng khác được đáp ứng.

### **Quá trình hoạt động**:

1. **Lựa chọn giải pháp khởi đầu**: Thuật toán bắt đầu với một lời giải khả thi ban đầu (có thể được chọn ngẫu nhiên hoặc thông qua một phương pháp khác).
2. **Khám phá lân cận**: Tại mỗi bước, thuật toán sẽ xem xét các giải pháp trong vùng lân cận của giải pháp hiện tại. Vùng lân cận này có thể được định nghĩa bởi một số thao tác nhỏ như thay đổi vị trí của một phần tử, hoán đổi hai phần tử, hoặc thực hiện các thay đổi nhỏ khác trong lời giải.
3. **Cập nhật lời giải**: Nếu tìm thấy một lời giải tốt hơn trong lân cận, thuật toán sẽ cập nhật và sử dụng giải pháp này làm lời giải hiện tại. Nếu không tìm thấy giải pháp tốt hơn, thuật toán dừng lại.
4. **Điều kiện dừng**: Thuật toán sẽ dừng khi một trong các điều kiện sau được thỏa mãn:
    - Đạt đến một số lần lặp nhất định.
    - Không còn lời giải nào tốt hơn trong lân cận.
    - Đạt được chất lượng lời giải mong muốn.
## 2.13
#### a. 
Thuật toán di truyền (Genetic Algorithm - GA) là một phương pháp tối ưu hóa dựa trên nguyên lý tiến hóa tự nhiên. Nó sử dụng các khái niệm như chọn lọc tự nhiên, lai ghép và đột biến để tìm kiếm giải pháp cho các bài toán phức tạp. Dưới đây là các bước cơ bản của thuật toán di truyền:

1. **Khởi tạo quần thể (Population Initialization)**:
    
    - Tạo một quần thể ban đầu gồm nhiều cá thể (individuals), mỗi cá thể đại diện cho một giải pháp tiềm năng cho bài toán.
2. **Đánh giá (Evaluation)**:
    
    - Tính toán độ thích nghi (fitness) của mỗi cá thể trong quần thể. Độ thích nghi thể hiện mức độ tốt của cá thể trong việc giải quyết bài toán.
3. **Chọn lọc (Selection)**:
    
    - Chọn các cá thể dựa trên độ thích nghi của chúng. Những cá thể có độ thích nghi cao hơn có khả năng được chọn nhiều hơn để truyền lại gen cho thế hệ tiếp theo.
4. **Lai ghép (Crossover)**:
    
    - Kết hợp các gen của hai cá thể cha mẹ để tạo ra cá thể con. Quá trình này giúp khai thác thông tin tốt từ các cá thể khác nhau.
5. **Đột biến (Mutation)**:
    
    - Thực hiện một số thay đổi ngẫu nhiên trên cá thể con để tạo ra sự đa dạng trong quần thể. Điều này giúp tránh rơi vào các cực trị địa phương.
6. **Thay thế (Replacement)**:
    
    - Thay thế quần thể cũ bằng quần thể mới được tạo ra từ quá trình lai ghép và đột biến.
7. **Lặp lại (Iteration)**:
    
    - Quá trình này được lặp lại cho đến khi đạt được tiêu chí dừng, chẳng hạn như số thế hệ tối đa hoặc đạt được độ thích nghi đủ tốt.

### Ứng dụng của Thuật Toán Di Truyền

- Tối ưu hóa hàm (Function Optimization).
- Giải quyết các bài toán tổ hợp (Combinatorial Problems).
- Học máy (Machine Learning).
- Lập kế hoạch (Scheduling).
- Phân tích dữ liệu (Data Mining).
## 2.14 
Dưới đây là lược đồ cho thuật toán tìm kiếm lân cận biến đổi (Hill Climbing), mô tả các bước chính trong quá trình thực hiện thuật toán:

### Lược Đồ Thuật Toán Tìm Kiếm Lân Cận Biến Đổi

1. **Khởi Tạo**:
    
    - Chọn một **giải pháp ban đầu** ngẫu nhiên (current solution).
2. **Đánh Giá**:
    
    - Tính toán **giá trị hàm mục tiêu** cho giải pháp hiện tại (current value).
3. **Lặp Lại Cho Đến Khi Dừng**:
    
    - **Tạo Giải Pháp Lân Cận**:
        
        - Tạo một tập hợp các **giải pháp lân cận** (neighbors) bằng cách thay đổi một số biến trong giải pháp hiện tại.
    - **Tính Toán Giá Trị**:
        
        - Đánh giá giá trị hàm mục tiêu cho từng giải pháp lân cận.
    - **Tìm Giải Pháp Tốt Nhất**:
        
        - Xác định giải pháp lân cận nào có giá trị tốt nhất (best neighbor).
        - So sánh giá trị của giải pháp lân cận tốt nhất với giải pháp hiện tại:
            - **Nếu tốt hơn**:
                - Cập nhật giải pháp hiện tại thành giải pháp lân cận tốt nhất.
            - **Nếu không tốt hơn**:
                - Dừng thuật toán (đạt đến điểm cực trị địa phương).
4. **Kết Quả**:
    
    - Trả về **giải pháp tối ưu** (giải pháp hiện tại) và giá trị tương ứng.
## 2.15
Thuật toán Bees (Bee Algorithm) là một thuật toán tối ưu hóa bầy đàn dựa trên hành vi tìm kiếm thức ăn của đàn ong. Thuật toán này thường được áp dụng cho các bài toán tối ưu hóa phức tạp, như tối ưu hóa hàm số, thiết kế hệ thống, hoặc các bài toán phân hoạch. Dưới đây là lược đồ và các bước cơ bản của thuật toán Bees:

### Lược Đồ Thuật Toán Bees

1. **Khởi Tạo**:
    
    - **Số lượng ong**: Xác định số lượng ong trong bầy.
    - **Vị trí ban đầu**: Tạo ra một số vị trí ngẫu nhiên cho các ong trong không gian tìm kiếm.
    - **Số lần lặp**: Xác định số vòng lặp (iteration) cho quá trình tìm kiếm.
2. **Đánh Giá**:
    
    - Tính toán giá trị hàm mục tiêu cho mỗi vị trí của ong (giải pháp).
3. **Chia Sẻ Thông Tin**:
    
    - Chọn những ong có giá trị tốt nhất (top performers) và chia sẻ thông tin với những ong khác.
    - Sắp xếp ong theo giá trị hàm mục tiêu từ cao đến thấp.
4. **Thực Hiện Khám Phá và Khai Thác**:
    
    - **Khám Phá**:
        - Một phần ong (ong khai thác) sẽ thực hiện tìm kiếm trong không gian mới để khám phá các giải pháp mới. Điều này có thể bao gồm việc tạo ra vị trí ngẫu nhiên trong không gian xung quanh vị trí hiện tại.
    - **Khai Thác**:
        - Phần còn lại của đàn ong (ong khai thác) sẽ tập trung khai thác các vùng xung quanh vị trí tốt nhất đã tìm thấy.
5. **Cập Nhật Vị Trí**:
    
    - Cập nhật vị trí của các ong dựa trên kết quả tìm kiếm mới.
    - Lặp lại quy trình từ bước 2 cho đến khi đạt được số lần lặp đã định hoặc thỏa mãn tiêu chí dừng.
6. **Kết Quả**:
    
    - Trả về vị trí tốt nhất tìm thấy và giá trị hàm mục tiêu tương ứng.

### Ưu Điểm và Nhược Điểm

- **Ưu Điểm**:
    
    - Tìm kiếm toàn cục: Khả năng khám phá các vùng rộng lớn của không gian tìm kiếm.
    - Linh hoạt: Có thể điều chỉnh để áp dụng cho nhiều loại bài toán khác nhau.
- **Nhược Điểm**:
    
    - Độ phức tạp tính toán cao khi kích thước không gian lớn.
    - Cần tinh chỉnh các tham số như số lượng ong, số vòng lặp, v.v., để đạt hiệu quả tốt nhất.

### Ứng Dụng

Thuật toán Bees thường được sử dụng trong các lĩnh vực như:

- Tối ưu hóa hàm số.
- Lập lịch và phân phối tài nguyên.
- Vấn đề phân tích và thiết kế hệ thống.
## 2.16
Để xây dựng một thuật toán metaheuristic cho bài toán Định tuyến xe (Vehicle Routing Problem - VRP), ta có thể sử dụng thuật toán Di truyền (Genetic Algorithm - GA). Dưới đây là phác thảo thuật toán và cách áp dụng nó cho VRP.
### 1. Mô tả bài toán VRP
Trong VRP, mục tiêu là xác định một tập hợp các lộ trình cho một đội xe để phục vụ một số lượng khách hàng nhất định, sao cho tổng chi phí vận chuyển được tối thiểu hóa và tuân thủ các ràng buộc như giới hạn tải trọng của xe.
### 2. Các thành phần của thuật toán Di truyền
#### a. Đại diện cá thể
- Mỗi cá thể trong quần thể đại diện cho một lộ trình. Một cá thể có thể là một danh sách các khách hàng được sắp xếp theo thứ tự mà xe sẽ phục vụ.
#### b. Hàm đánh giá (Fitness Function)
- Hàm đánh giá sẽ tính tổng chi phí lộ trình cho cá thể. Hàm này cần xem xét khoảng cách giữa các khách hàng và đảm bảo rằng không có xe nào vượt quá tải trọng tối đa.
#### c. Quần thể khởi tạo
- Tạo ra một quần thể ban đầu với nhiều cá thể ngẫu nhiên.

#### d. Phép lai (Crossover)

- Thực hiện phép lai giữa hai cá thể cha mẹ để tạo ra cá thể con. Một phương pháp có thể là Crossover một điểm, nơi chọn một điểm trong danh sách và trao đổi các phần của hai cá thể.

#### e. Đột biến (Mutation)

- Đột biến có thể thực hiện bằng cách hoán đổi vị trí của hai khách hàng trong lộ trình.

#### f. Lọc quần thể

- Chọn lọc các cá thể tốt nhất để tạo ra thế hệ tiếp theo. Phương pháp chọn lọc có thể là chọn lựa tự nhiên, nơi các cá thể với hàm đánh giá tốt hơn có khả năng được chọn cao hơn.
```cpp
// Hàm chạy thuật toán Di truyền cho VRP
void GeneticAlgorithmVRP() {
    int populationSize = 100; // Kích thước quần thể
    int generations = 500; // Số thế hệ
    vector<Individual> population = initializePopulation(populationSize);

    for (int generation = 0; generation < generations; ++generation) {
        vector<Individual> newPopulation;

        // Lặp qua quần thể để chọn và lai tạo
        while (newPopulation.size() < populationSize) {
            Individual parent1 = selection(population);
            Individual parent2 = selection(population);
            Individual child = crossover(parent1, parent2);
            mutation(child);
            newPopulation.push_back(child);
        }

        // Đánh giá quần thể mới và lọc
        population = evaluatePopulation(newPopulation);
    }

    // Tìm cá thể tốt nhất
    Individual bestSolution = findBestIndividual(population);
    printSolution(bestSolution);
}
```
Để xây dựng một thuật toán metaheuristic cho bài toán Lập lịch, ta có thể sử dụng thuật toán Simulated Annealing (SA). Bài toán lập lịch thường bao gồm việc sắp xếp một tập hợp các công việc vào các máy để tối thiểu hóa thời gian hoàn thành hoặc chi phí.
### 1. Mô tả bài toán Lập lịch
Trong bài toán lập lịch, mục tiêu là xác định thứ tự thực hiện các công việc để giảm thiểu thời gian hoàn thành (makespan) hoặc tối ưu hóa một tiêu chí nào đó (ví dụ: chi phí, độ trễ).

### 2. Các thành phần của thuật toán Simulated Annealing

#### a. Đại diện cá thể

- Mỗi cá thể có thể được đại diện bởi một danh sách sắp xếp các công việc.

#### b. Hàm đánh giá (Fitness Function)

- Hàm đánh giá sẽ tính thời gian hoàn thành (makespan) của một lịch trình. Nếu mục tiêu là tối thiểu hóa thời gian hoàn thành, hàm này sẽ trả về giá trị nhỏ hơn cho các lịch trình tốt hơn.

#### c. Khởi tạo

- Tạo một lịch trình ngẫu nhiên làm lịch trình khởi đầu.

#### d. Thay đổi ngẫu nhiên (Neighbor Solution)

- Tạo một lịch trình lân cận bằng cách hoán đổi vị trí của hai công việc trong lịch trình hiện tại.

#### e. Điều kiện dừng

- Thuật toán sẽ dừng sau một số lần lặp hoặc khi không còn cải thiện đáng kể nào trong hàm đánh giá.
```cpp
#include <vector>
#include <algorithm>
#include <cmath>
#include <cstdlib>
#include <ctime>

// Hàm tính makespan của một lịch trình
int calculateMakespan(const std::vector<int>& schedule) {
    int makespan = 0;
    // Giả sử mỗi công việc mất một khoảng thời gian nhất định để hoàn thành
    for (int job : schedule) {
        makespan += job; // Thay thế bằng logic cụ thể hơn nếu cần
    }
    return makespan;
}

// Hàm tìm lịch trình lân cận
std::vector<int> getNeighbor(const std::vector<int>& schedule) {
    std::vector<int> neighbor = schedule;
    int pos1 = rand() % schedule.size();
    int pos2 = rand() % schedule.size();
    std::swap(neighbor[pos1], neighbor[pos2]); // Hoán đổi hai công việc
    return neighbor;
}

// Hàm Simulated Annealing cho bài toán lập lịch
void SimulatedAnnealingScheduling() {
    srand(static_cast<unsigned>(time(0))); // Khởi tạo seed cho random
    std::vector<int> currentSchedule = { /* Danh sách công việc */ };
    int currentMakespan = calculateMakespan(currentSchedule);
    int bestMakespan = currentMakespan;
    std::vector<int> bestSchedule = currentSchedule;

    double temperature = 1000.0;
    double coolingRate = 0.99; // Tốc độ làm lạnh

    while (temperature > 1) {
        std::vector<int> neighbor = getNeighbor(currentSchedule);
        int neighborMakespan = calculateMakespan(neighbor);

        // Nếu lịch trình lân cận tốt hơn hoặc chấp nhận lịch trình kém hơn với xác suất
        if (neighborMakespan < currentMakespan || 
            (exp((currentMakespan - neighborMakespan) / temperature) > (double)rand() / RAND_MAX)) {
            currentSchedule = neighbor;
            currentMakespan = neighborMakespan;
        }

        // Cập nhật lịch trình tốt nhất
        if (currentMakespan < bestMakespan) {
            bestMakespan = currentMakespan;
            bestSchedule = currentSchedule;
        }

        // Giảm nhiệt độ
        temperature *= coolingRate;
    }

    // In ra kết quả
    std::cout << "Best Makespan: " << bestMakespan << "\n";
    std::cout << "Best Schedule: ";
    for (int job : bestSchedule) {
        std::cout << job << " ";
    }
    std::cout << "\n";
}

```
## 2.17
### Thuật toán Min-Max

**Mục tiêu**: Tìm nước đi tốt nhất cho người chơi trong một trò chơi đối kháng, giả định rằng đối thủ sẽ luôn chơi tối ưu.

**Cách hoạt động**:

1. **Cây trò chơi**: Tạo cây trò chơi, trong đó mỗi nút biểu thị một trạng thái của trò chơi. Các nút lá là kết quả cuối cùng (thắng, thua, hòa).
2. **Min-Max Value**:
    - Người chơi tối ưu (Max) sẽ cố gắng tối đa hóa điểm số của mình.
    - Đối thủ (Min) sẽ cố gắng tối thiểu hóa điểm số của Max.
3. **Đệ quy**:
    - Bắt đầu từ các nút lá, tính giá trị cho các nút cha bằng cách đi lên cây:
        - Nếu là nút của Max: chọn giá trị lớn nhất từ các con.
        - Nếu là nút của Min: chọn giá trị nhỏ nhất từ các con.
4. **Quyết định**: Người chơi sẽ chọn nước đi tương ứng với nút Max có giá trị lớn nhất.
```
function MinMax(node, depth, maximizingPlayer):
    if depth == 0 or node is a terminal node:
        return evaluate(node)

    if maximizingPlayer:
        maxEval = -∞
        for each child in node:
            eval = MinMax(child, depth - 1, false)
            maxEval = max(maxEval, eval)
        return maxEval
    else:
        minEval = +∞
        for each child in node:
            eval = MinMax(child, depth - 1, true)
            minEval = min(minEval, eval)
        return minEval

```
### Thuật toán Alpha-Beta Pruning

**Mục tiêu**: Tối ưu hóa thuật toán Min-Max bằng cách loại bỏ các nhánh không cần thiết trong cây trò chơi.

**Cách hoạt động**:

1. **Alpha và Beta**:
    - `Alpha` là giá trị tốt nhất mà người chơi Max hiện có (tối đa hóa).
    - `Beta` là giá trị tốt nhất mà người chơi Min hiện có (tối thiểu hóa).
2. **Cắt tỉa**:
    - Khi duyệt cây, nếu tại bất kỳ nút nào, giá trị của Min lớn hơn hoặc bằng Alpha, hoặc giá trị của Max nhỏ hơn hoặc bằng Beta, có thể dừng duyệt các nhánh đó, vì chúng sẽ không ảnh hưởng đến kết quả cuối cùng.
3. **Quyết định**: Quy trình tương tự như thuật toán Min-Max nhưng với việc kiểm tra và cập nhật Alpha và Beta trong quá trình duyệt cây.
```
function AlphaBeta(node, depth, alpha, beta, maximizingPlayer):
    if depth == 0 or node is a terminal node:
        return evaluate(node)

    if maximizingPlayer:
        maxEval = -∞
        for each child in node:
            eval = AlphaBeta(child, depth - 1, alpha, beta, false)
            maxEval = max(maxEval, eval)
            alpha = max(alpha, eval)
            if beta <= alpha:
                break // β cut-off
        return maxEval
    else:
        minEval = +∞
        for each child in node:
            eval = AlphaBeta(child, depth - 1, alpha, beta, true)
            minEval = min(minEval, eval)
            beta = min(beta, eval)
            if beta <= alpha:
                break // α cut-off
        return minEval

```
### Ứng dụng

- Cả hai thuật toán đều được sử dụng trong các trò chơi hai người, đặc biệt là những trò chơi có quy tắc xác định rõ ràng và trạng thái có thể được biểu diễn bằng cây trò chơi.
- Alpha-Beta Pruning giúp giảm số lượng trạng thái cần kiểm tra, do đó cải thiện hiệu suất và tốc độ của thuật toán Min-Max.