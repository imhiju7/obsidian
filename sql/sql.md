SQL được dùng để
- Lưu trữ dữ liệu
- Tổ chức dữ liệu
- Phân tích dữ liệu
Truy vấn là yêu cầu về dữ liệu hoặc thông tin từ cơ sở dữ liệu. Khi truy vấn cơ sở dữ liệu, bạn sử dụng SQL để truyền đạt câu hỏi hoặc yêu cầu của mình. Bạn và cơ sở dữ liệu luôn có thể trao đổi thông tin miễn là bạn nói cùng một ngôn ngữ.

- Sử dụng SELECT để chọn các cột bạn muốn trả về.
- Sử dụng FROM để chọn các bảng chứa các cột bạn muốn.
- Sử dụng WHERE để lọc thông tin nhất định

```SQL
SELECT first_name
FROM customer_data.customer_name
WHERE first_name = 'Tony'
```

Truy vấn trên sử dụng ba lệnh để xác định vị trí khách hàng có first_name, 'Tony': 
- SELECT cột có tên first_name FROM bảng có tên customer_name (trong tập dữ liệu có tên customer_data) (Tên tập dữ liệu luôn được theo sau bởi dấu chấm và sau đó là tên bảng .) Nhưng chỉ trả về dữ liệu WHERE first_name = 'Tony'

**Nhiều cột trong một truy vấn**

```SQL
SELECT
    ColumnA,
    ColumnB,
    ColumnC
FROM
    Table where the data lives
WHERE
    Certain condition is met
```

Truy vấn trên sử dụng ba lệnh để xác định vị trí khách hàng có first_name, 'Tony'. 
- SELECT các cột có tên customer_id, first_name và Last_name FROM bảng có tên customer_name (trong tập dữ liệu có tên customer_data) (Tên tập dữ liệu luôn được theo sau bởi dấu chấm và sau đó là tên bảng.) Nhưng chỉ trả về dữ liệu WHERE first_name = 'Tony'
Ví dụ: sẽ hợp lý hơn khi chọn nhiều cột hơn nếu bạn thực sự muốn sử dụng các trường bổ sung trong mệnh đề WHERE của mình. Nếu bạn có nhiều điều kiện trong mệnh đề WHERE, chúng có thể được viết như sau:
```SQL
SELECT
ColumnA,
ColumnB,
ColumnC
FROM
    Table where the data lives
WHERE
    Condition 1
    AND Condition 2
    AND Condition 3
```
Lưu ý rằng không giống như lệnh SELECT sử dụng dấu phẩy để phân tách các trường/biến/tham số, lệnh WHERE sử dụng câu lệnh AND để kết nối các điều kiện. Khi bạn trở thành người viết truy vấn nâng cao hơn, bạn sẽ sử dụng các trình kết nối/toán tử khác như OR và NOT.
```SQL
SELECT
    customer_id,
    first_name,
    last_name
FROM
    customer_data.customer_name
WHERE
    customer_id > 0
    AND first_name = 'Tony'
    AND last_name = 'Magnolia'
```
- Bạn có thể chọn tất cả cột bằng SELECT *
```SQL
SELECT
    * /* this is the last name column */
FROM
    table -- this is the customer data table  
WHERE
    field1 LIKE 'Ch%';
```

```SQL
-- This is an important query used later to join with the accounts table 
SELECT
        rowkey,  -- key used to join with account_id
Info.date,  -- date is in string format YYYY-MM-DD HH:MM:SS
Info.code  -- e.g., 'pub-###'
FROM  Publishers
```
## Comments
```SQL
-- Pull basic information from the customer table
SELECT
    customer_id, --main ID used to join with customer_addresss
    first_name, --customer's first name from loyalty program
    last_name --customer's last name
FROM
    customer_data.customer_name
```

## Aliases

```SQL
SELECT 
    my_table_alias.actual_column_name AS my_column_alias
FROM
    actual_table_name AS my_table_alias
```