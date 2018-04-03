# 19.Bash shell programming
Shell ngoài thực hiện câu lênh bằng cách trwucj tiếp nhập vào còn có thể thông qua các script
Một script bắt đầu bằng #!/bin/bash để sử dụng bash hoặc có thể /csh,/tcsh,/ksh ...
Để tạo một script lưu tên với phần mở rộng là .sh
Sau đó để thực thi dùng lệnh chmod để thêm quyền thực thi vào file

|Command | Descrption |
|--------|------------|
|#|comment|
|$|biến|
|;|kết thuc câu lệnh|
|$0, $1, $...|biến có thể truyền vào khi thực thi script|
|read smt|đọc giữ liệu từ bàn phím và lưu vào biến smt|
|echo|show trị chuỗi |
|$(command) hoặc (command')|sub command|
|if then else fi|cấu lệnh rẽ nhánh|
|while do done|vòng lặp while |
