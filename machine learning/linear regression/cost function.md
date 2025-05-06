- Là hàm sinh ra để tạo đường tuyến tính tốt nhất cho bộ dữ liệu
$J(\theta_{0},\theta_{1}) = \frac{1}{2m} \sum_{i = 1}^{m}(h_{x^{i}} - y^{i})^{2}$
$h_{\theta}(x) = h(x) = \theta_{0} + \theta_{1}x$
với $\theta_{i}$'s là tham số của hàm
![[Pasted image 20240619203212.png]]

![[Pasted image 20240619203539.png]]
- Chọn $\theta_{0},\theta_{1}$ sao cho h(x) gần với y với bộ dữ liệu huấn luyện (x,y)
- $minimize_{\theta_{0},\theta_{1}} \frac{1}{2m} \sum_{i = 1}^{m}(h_{x^{i}} - y^{i})^2$
- $h(x^{i}) = \theta_{0} + \theta_{1}x^{i}$
- Mục tiêu là tìm giá trị $\theta_{0},\theta_{1}$ để $\frac{1}{2m} \sum_{i = 1}^{m}(h_{x^{i}} - y^{i})^2$ đạt cực tiểu