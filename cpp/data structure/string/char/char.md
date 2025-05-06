- Là một kiểu dữ liệu trong cpp
- Có kích thước là 1byte 
- Lưu trữ dữ liệu số từ -128 đến 127 ( $-2^{7}$ đến $2^{7}-1$)
- ABC... ở dạng char sau khi chuyển sang int có giá trị từ 65 - 90
- abc... sau khi chuyển sang int thì có giá trị từ 97 - 122

- Để chuyển 1 kí tự int hoa sang int thường thì cộng thêm 32 đơn vị, ngược lại trừ đi 32 đơn vị
```cpp
#include <bits/stdc++.h>
#include <string.h>
using namespace std;

int main(){
    char c = 'A'; //1byte
    int m = (int)c;
    char t = (char)(m+32);
    cout<<c<<" "<<t<<endl;
}
```

- Các hàm về kí tự trong cpp
	- islower(): kiểm tra là in thường
	- isupper(): kiểm tra là in hoa
	- isalpha(): kiểm tra là chữ cái alphabet
	- isdigit(): kiểm tra là kí tự số hay không
	- tolower(): trả về mã ascci của một kí tự ở dạng in thường
	- toupper(): trả về mã ascci của một kí tự ở dạng in hoa