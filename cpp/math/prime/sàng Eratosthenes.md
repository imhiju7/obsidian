- Sàng số nguyên tố được sử dụng cho bài toán tìm số nguyên tố mà đầu vào là một số vô cùng lớn
- Ví dụ tìm số nguyên tố nhỏ hơn n < 10^7
- Cách làm: Thay vì kiểm tra từng số nhỏ hơn n là số nguyên tố thì ta dùng hàm sàng để sàng các số nguyên tố nhỏ hơn n.
```cpp
void sang(){
    memset( nt, true, sizeof(nt));
    nt[0] = nt[1] = false;
    for(int i = 2; i <= sqrt(maxn);i++){
        if(nt[i]){
            for(int j = i * i; j <= maxn; j+=i){
                nt[j] = false;
            }
        }
    }
}
```
- Ta tạo mảng bool, gán cho các giá trị từ 0 đến maxn là true ( không là số nguyên tố).
- Gán số 0 và 1 là false.
- Thực hiện vòng lặp từ i = 2 đến maxn
	- Nếu là số nguyên tố. Thực hiện vòng lặp while, tìm bội của i và gán bằng false


** Lưu ý: Bài toán chỉ thực hiện các task kiểm tra hàng loạt các số nguyên tố, không phù hợp các bài toán kiểm tra 1 số có phải là nguyên tố hay không. 