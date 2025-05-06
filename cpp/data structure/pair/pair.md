- là cấu trúc cặp đôi, tương tự như tọa độ trong trục oxy. gồm có 2 phần, first và second.
- hàm thường dùng
	- make_pair: dùng để trả về một pair từ cặp giá trị nào đó
```cpp
#include<bits/stdc++.h>

using namespace std;

int main(){
	pair<int,int> a = make_pair(4,5);
	cout<<a.first<<" "<<a.second<<endl;
}
```