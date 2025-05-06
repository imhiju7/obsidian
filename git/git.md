- Git là một hệ thống quản lí phiên bản phân tán, dùng để lưu trữ mã nguồn từ chục dòng code đến hàng triệu dòng code.
- [[repository]] là nơi chứa tất cả soure code của các project.
- Tại một thời điểm, mỗi khi có sự thay đổi trong mã nguồn thì Git chỉ thay đổi việc lưu trữ tại sự thay đổi mã nguồn đó chứ không có thay đổi toàn bộ mã nguồn.
- Trong thời gian thực hiện project, ta có thể quay lại bất kì thời điểm nào trong project dựa vào[[snapshot in Git]].

#### Câu lệnh sử dụng trong Git
-  git --version : Nhằm kiểm tra phiên bản hiện tại của Git.
- Khai báo tài khoản cá nhân
	- git config --global user.name "Your name": Khai báo user name của người dùng.
	- git config --global user.email "Your email": Khai báo email của người dùng.
	- cat ~/.gitconfig : Nhằm kiểm tra thông tin user trên máy.
- Tạo một [[repository]]
	- mkdir "Folder name" : Tạo folder
	- cd "Folder name" : Đi vào trong folder
	- git init : Khởi tạo local repository
- Hoạt động trên [[repository]]
	- git add "file name" : Add một file vào repository, để add toàn bộ file vào thì thay file name =  . ( Nó sẽ auto add những file mới ),
	- git commit -m "Message":  Nhằm để xác nhận sự thay đổi được thực hiện ở git add
	- git status: Kiểm tra trạng thái hiện tại của repository
	 