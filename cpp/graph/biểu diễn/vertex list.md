- thường được biểu diễn khi đồ thị thưa (6*V <= E)
- đối với đồ thị vô hướng nếu tồn tại cạnh giữa hai đỉnh u,v. chỉ cần liệt kê cạnh (u,v), thường chọn u < v.
- thường liệt kê các cạnh theo thứ tự tăng dần đỉnh đầu của các cạnh
![[Pasted image 20240710084455.png]]- sau khi nhận danh sách cạnh, ta chuyển sang dạng danh sách kề
```cpp
#include <bits/stdc++.h>

using namespace std;
vector<int> adj[1001];

int main(){
	freopen("input.txt","r",stdin);
	freopen("output.txt","w",stdout);
	int n,m;cin>>n>>m;
	int temp = m;
	while(temp--){
		int x,y;
		cin>>x>>y;
		adj[x].push_back(y);
		adj[y].push_back(x);
	}
}
```
