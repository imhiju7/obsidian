- là cấu trúc hàng đợi được cài đặt theo cấu trúc max heap. phần tử đầu tiên là phần tử có giá trị lớn nhất trong hàng đợi ưu tiên
```cpp
#include <bits/stdc++.h>

using namespace std;
int main(){
	priority_queue<int> pq;
	pq.push(1);
	pq.push(6);
	pq.push(4);
	pq.push(7);
	cout<<pq.top()<<endl;
	cout<<pq.size()<<endl;
	pq.pop(); // xóa phần tử lớn nhất ra khỏi hàng đợi
	cout<<pq.top()<<endl;
	return 0;
}
```