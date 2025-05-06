- ứng dụng của [[euclid algorithm]]
$\gcd(a, b) = \begin{cases} a,b \# 0 & \\ \gcd(b, a \% b) & \end{cases}$

```cpp
ll gcd(ll a,ll b){
    if(b == 0) return a;
    else return gcd(b,a%b);
}
```