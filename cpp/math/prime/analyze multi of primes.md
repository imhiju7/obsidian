
```cpp
void phantich(int n){
    for(int i = 2; i<= sqrt(n); i++){
        while(n % i == 0){
            cout<<i<<" ";
            n/=i;
        }
    }
    if(n > 1) cout<<" = "<<n<<endl;
}
```
- Thực hiện xét i từ 2 đến căn bậc 2 của n
- Thực hiện vòng lặp while với điều kiện n % i   == 0. In ra các số mà n chia hết, sau đó thực hiện n /= i. Ý nghĩa là tìm số lượng số i mà n chia hết.
-  Sau khi thực hiện while, i = i + 1. Tiếp tục tìm kiếm cho đến hết sqrt(n)
- In ra n nếu n > 1;

# Ứng dụng của việc phân tích
- [[division of n]]
