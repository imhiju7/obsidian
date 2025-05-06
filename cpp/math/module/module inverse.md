$(A*A^{-1})\%M = 1<=>gcd(A,M) = 1$
$= ((A\%M)*(A^{-1}\%M))\%M$

$A*x+M*y = 1$
$(A*x+M*y)\%M = 1\%M$
$(A\%M)*x + 0 = 1$
$x = A^{-1}$

Muốn tìm $(\frac{A}{B})\%C$, ta tìm $B^{-1}$ => Quay lại bài toán [[ax+by=g]] với b = m và g = 1

**Hoặc**

$A^{M-1}\%M = 1$
$=>A^{-1} = A^{M-2}\%M$
Khi đó 
$(\frac{A}{B})\%C = (A*B^{-1})\%C = (A*(B^{M-2}\%M))\%M$
- Ta áp dụng [[binary power]]  sau đó áp dụng đồng dư của 1 tích để tìm kết quả của $(\frac{A}{B})\%C$
- Complexity:$O(log(max(a,b)))$