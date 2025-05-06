Quên thảm khốc xảy ra vì quá trình tinh chỉnh toàn diện (full fine-tuning) thay đổi các trọng số của LLM gốc. Trong khi điều này dẫn đến hiệu suất tuyệt vời trên nhiệm vụ tinh chỉnh duy nhất, nó có thể làm giảm hiệu suất trên các nhiệm vụ khác.
![[Pasted image 20240701011846.png]]
Ví dụ, trong khi tinh chỉnh có thể cải thiện khả năng của mô hình trong việc phân tích cảm xúc trên một đánh giá và mang lại kết quả chất lượng, mô hình có thể quên cách thực hiện các nhiệm vụ khác.
![[Pasted image 20240701012046.png]]
Mô hình này biết cách thực hiện nhận diện thực thể có tên (named entity recognition) trước khi tinh chỉnh, nhận diện chính xác Charlie là tên của con mèo trong câu. Nhưng sau khi tinh chỉnh, mô hình không còn có thể thực hiện nhiệm vụ này nữa, nhầm lẫn cả thực thể mà nó cần nhận diện và thể hiện hành vi liên quan đến nhiệm vụ mới.

- Sự quên lãng nghiêm trọng là một vấn đề trong cả nhiệm vụ [[supervised learning]] và [[unsupervised learning]]. Trong học không giám sát, điều này có thể xảy ra khi mô hình được huấn luyện trên một tập dữ liệu mới khác với tập dữ liệu được sử dụng trong quá trình huấn luyện trước.
- Sự quên lãng nghiêm trọng xảy ra khi một mô hình học máy quên thông tin đã học trước đó khi học thông tin mới.