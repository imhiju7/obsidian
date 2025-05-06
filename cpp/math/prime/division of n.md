$n = p_1^{\ell_1} \cdot p_2^{\ell_2} \cdot p_3^{\ell_3} \cdots p_k^{\ell_k}$
$180 =2^{2} \cdot 3^{2} \cdot 5^{1}$
- D(n) là số lượng ước  của n. Ví dụ:
$D(n) = (\ell_1 + 1)(\ell_2 + 1)(\ell_3 + 1) \cdots (\ell_k + 1)$
$D(n) = (2 + 1)(2 + 1)(1 + 1) = 18$
- Tích tất cả các ước của n
$U(n) =  n^{d(n)/2}$
$U(180) = 18^\frac{18}{2}=18^9$

```cpp
int soluong_uoc(int n){
	int sl_uoc = 1;
    for(int i = 2; i<= sqrt(n); i++){
	    int s = 1;
        while(n % i == 0){
            cout<<i<<" ";
            s = s + 1;
            n/=i;
        }
        sl_uoc = sl_uoc *s;
    }
    return sl_uoc;
}
```