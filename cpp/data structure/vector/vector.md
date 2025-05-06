- là một cấu trúc tương tự mảng nhưng điểm khác biệt là khi khai báo không cần cho biết số lượng phần tử của mảng. có thể khởi tạo ra một vector có n phần tử giống nhau.
```cpp
	#include<bits/stdc++.h>
	using namespace std;
	int main(){
		int n = 10;
		vector<int> vt(n,454);
		// thêm phần từ vào vector bằng cách
		vt.push_back(100);
		vt.push_back(200); // giá trị thêm vào có kiểu dữ liệu tương ứng
		cout<<vt[1]<<endl;
		// xóa phần tử cuối ra khỏi vector
		vt.pop_back();
		cout<<vt[1]<<endl;
	}
```
- vòng lặp với vector
```cpp

#include<bits/stc++.h>
using namespace std;
int main(){
	vector<int> a;
	a.push_back(100);
	a.push_back(200);
	a.push_back(300);
	for(int i = 0; i < a.size(); i++) {
        cout << a[i] << " ";
    }
    cout << endl;
    for(int x : a){
        cout << x << " ";
    }
    cout << endl;
    for(auto x : a){
        cout << x << " ";
    }
}
```
- hàm với vector
	- reverse(): đảo ngược vector
		```cpp
		#include<bits/stdc++.h>
		using namespace std;
		int main(){
			vector<int> a;
			a.push_back(100);
			a.push_back(200);
			a.push_back(300);
			reverse(a.begin(),a.end());
			for(auto x : a){
		        cout<<x<<" ";
		    }
		}
		```
	- sort(): sắp xếp lại vector theo thứ tự
		```cpp
		#include<bits/stdc++.h>
		using namespace std;
		int main(){
			vector<int> a;
			a.push_back(200);
			a.push_back(100);
			a.push_back(300);
			sort(a.begin(),a.end());
			for(auto x : a){
		        cout<<x<<" ";
		    }
		}
		```
- thêm phần tử vào vector
```cpp
#include <bits/stdc++.h>

using namespace std;

int main(){
	vector<int> a;
	for(int &i: a) cin>> i;
}
```