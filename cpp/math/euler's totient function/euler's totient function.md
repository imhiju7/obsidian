Công thức phi hàm Euler
$\phi(N) = n \prod_{p \mid n} \left( 1 - \frac{1}{p} \right)$

```cpp
int eulerPhi(int n) { // = n (1-1/p1) ... (1-1/pn)
    if (n == 0) return 0;
    int ans = n;
    for (int x = 2; x*x <= n; ++x) {
        if (n % x == 0) {
            ans -= ans / x;
            while (n % x == 0) n /= x;
        }
    }
    if (n > 1) ans -= ans / n;
    return ans;
}
```
- Trường hợp $N = p^k$:
$\phi(N) = p^{k-1} (p - 1)$