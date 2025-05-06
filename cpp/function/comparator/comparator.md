- Là yếu tố quyết định quy luật sắp xếp của hàm sort. 
	- comp là một hàm, trả về true nếu bạn muốn a đứng trước, trả về false nếu b đứng trước a.
```cpp
#include<bits/stdc++.h>
using namespace std;
bool comp(int a,int b){
	if(a > b) return true;
	else return false;
}
int main(){
	int a[10] = {1,3,2,6,4,7,3,7,8,6};
	sort(a,a+10,comp);
	for(int i : a) cout<<i<<" ";
}
```