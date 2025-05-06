- Là một cấu trúc dữ liệu mà các phần tử trong set khác nhau hoàn toàn và sắp xếp tăng dần theo thứ tự, khi bạn thêm một phần tử mới giống phần tử đã có trong set thì sẽ không thêm được
- hàm thường dùng
	- count: trả về số lần xuất hiện của 1 phần tử trong set.
	- find: trả về [[iterator]] của phần tử
	- erase: xóa phần tử khỏi set
```cpp
#include<bits/stdc++.h>

using namespace std;

int main(){
	set<int> a;
	a.insert(1);
	a.insert(6);
	a.insert(4);
	a.insert(8);
	for(int x : a) cout<<x<<" ";
	cout<<endl;
	cout<<a.size()<<endl;
	cout<<a.count(4)<<endl;
}
```

 Các biến thể của set gồm: [[multi set]], [[unordered set]],....