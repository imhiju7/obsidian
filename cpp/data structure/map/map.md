- là cấu trúc có sự dung hòa từ 2 cấu trúc [[pair]] và [[set]]
- với first là key và second là value
- key không trùng nhau
```cpp
#include<bits/stdc++.h>

using namespace std;

int main(){
	map<int,int> a;
	a.insert({3,5});
	a.insert({4,3});
	a.insert({1,7});
	a.insert({3,5});
	a.insert({8,9});
	for(map<int,int>::iterator x : a) cout<<x.first<<" "<<x.second<<endl;
	// truy cap phan tu dau tien
	map<int,int>::iterator it = a.begin();
	cout<<(*it).first<<" "<<(*it).second<<endl;
	// truy cap phan tu cuoi cung
	map<int,int>::iterator it = a.rbegin();
	--it;
	cout<<(*it).first<<" "<<(*it).second<<endl;
}
```