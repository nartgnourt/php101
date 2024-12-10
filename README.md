# PHP101

## Challenge 1

Bắt đầu với một thử thách siêu đơn giản, chúng ta chỉ cần xem HTML source của trang web bằng cách nhấn tổ hợp phím `Command + U` trên MacOS (hoặc `Ctrl + U` trên Windows) là có được flag.

![image](images/challenge-1/image-1.png)

## Challenge 2

![image](images/challenge-2/image-1.png)

Thử thách này tác giả cho chúng ta biết chuỗi flag đã bị mã hoá và đoạn code PHP của trang web.

Chúng ta có thể thấy, flag ban đầu được xử lý lần lượt qua các hàm theo thứ tự như sau:

1. `str_rot13()`
2. `bin2hex()`
3. `strrev()`
4. `hex2bin()`
5. `base64_encode()`

Vậy chúng ta sẽ thực hiện ngược lại đối với chuỗi flag đã bị mã hoá.

Mình có viết đoạn script PHP bên dưới để nhận về flag ban đầu.

```php
<?php
$encodedFlag = "1wc39mNzY4NDE1NTk9JD5vbm0mNDQ0PSQ5MHU9L2g+YHQ2NTB7dF5JU1";

$flag = base64_decode($encodedFlag);
$flag = bin2hex($flag);
$flag = strrev($flag);
$flag = hex2bin($flag);
$flag = str_rot13($flag);

echo $flag; # FLAG{c564ca8b-5c94-4446-aba4-955148676bfc}

```
