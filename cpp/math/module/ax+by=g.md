Ứng dụng [[euclid algorithm]]

$a\%b = a - \frac{a}{b}*b$

$a*x + b*y =  g$ $(1)$
$b*x_{1} + (a\%b)*y_{1} = g$
$b*x_{1} + (a-\frac{a}{b}*b)*y_{1} = g$
$a*y_{1} + b*\left(x_{1} - \frac{a}{b}*y_{1}\right)= g$ $(2)$

$(1)(2)=>$ $\begin{cases} x = y_{1} & \\ y = x_{1} -\frac{a}{b}*y_{1} & \end{cases}$

```cpp
void donthuc(int a,int b){
    if(b == 0){
        x = 1;
        y = 0;
        g = a;
    }
    else{
        donthuc(b,a%b);
        int temp = x;
        x = y;
        y = temp - (int)(a/b)*y;
    }
}
```
