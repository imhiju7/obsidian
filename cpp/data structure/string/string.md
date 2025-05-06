- string là kiểu dữ liệu cho một mảng [[char]] trong cpp
- index của string bắt đầu từ 0 đến n-1

- input string
	- không dùng cin>>x, với cin thì không phù hợp với chuỗi có kí tự space trong chuỗi
	- nên dùng hàm getline(cin,x) để nhập chuỗi vào.
	- [[cin-ignore]]

- hàm dùng với string
	- length(): trả về độ dài của một chuỗi
	- stringstream: dùng để chuyển một chuỗi thành một luồng tách từ trong một chuỗi dựa vào kí tự.
		```cpp
			#include<bits/stdc++.h>
			using namespace std;
			int main(){
				string s ="Toi-la-Hiju";
				stringstream ss(s);
				string word;
				while(getline(ss,word,'-')) cout<<word<<endl;
				return 0;
			}
		```
	- sort: dùng để sort một string theo thứ tự sắp xếp của các kí tự trong mã ascii
		```cpp
		#include<bits/stdc++.h>
		using namespace std;
		int main(){
			string s = "Toi-la-Hiju";
			sort(s.begin(),s.end(),greater<char>());
			cout<<s<<endl;
			return 0;
		}
		```
	- to_string(): chuyển 1 số dạng long long sang string
		```cpp
		#include<bits/stdc++.h>
		using namespace std;
		long long a = 8459847835;
		int main(){
			cout<<to_string(a)<<endl;
		}	
		```
	- stoi(): chuyển 1 xâu về dạng int
		```cpp
		#include<bits/stdc++.h>
		using namespace std;
		int main(){
			string a = "454";
			cout<<stoi(a)<<endl;
		}
		```
	- stoll(): chuyển 1 xâu về dạng long long
		```cpp
		#include<bits/stdc++.h>
		using namespace std;
		int main(){
			string s = "45454353";
			cout<<stoll(s)<<endl;  
		}
		```
- lưu ý:
	- để nối hai xâu với nhau thì ta có thể thực hiện cộng được
		```cpp
		#include<bits/stdc++.h>
		using namespace std;
		string a = "code";
		string b = "r";
		string c = a+b;
		int main(){
			cout<<a<<" + "<<b<<" = "<<c<<endl;
			return 0;
		}
		```
	- có thể sử dụng toán tử == , != , <= , >=, > , < để thực hiện so sánh chuỗi
	- đối với các kí tự số, để chuyển đổi sang dạng int thì phải trừ đi '0'
		```cpp
		#include<bits/stdc++.h>
		using namespace std;
		string a = "463762374";
		int main(){
			for(int i = 0; i < a.size();i++){
				if(isdigit(a[i])) sum = sum + a[i] - '0';
			}
			cout<<sum<<endl;
			return 0;
		}
		```
	- sử dụng vòng lặp for cho chuỗi
		```cpp
		#include<bits/stdc++.h>
		using namespace std;
		string a = "463762374";
		int main(){
			for(char t : a){
				if(isdigit(t)) sum = sum + t - '0';
			}
			cout<<sum<<endl;
			return 0;
		}
		```
