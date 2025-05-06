- Khi tính a^b chia dư cho số c nào đó thì khi thực hiện bằng cách đồng dư thì với b lớn thì độ phức tạp là O(b). Điều đó dẫn đến trường hợp TLE. Vì vậy cần thực hiện tối ưu.
- Dựa trên dạng nhị phân của số mũ b
$a^{13}$
$13= 1101 =  1*2^0+0*2^1+1*2^2+1*2^3$
=> $a^{13} = a*a^{4}*a^{8}$

```cpp
ll binPOW(ll a, ll b){
    ll res = 1;
    while(b > 0){
        if(b%2==1){
            res = res*a;
        }
        b=b/2;
        a = a*a;
    }
    return res;
}
```