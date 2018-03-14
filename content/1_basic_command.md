# 1.Basic command
##Shell
* Là một chương trìnhthông dịch cho phép người dùng tương tác với hệ điều hành bằng dòng lệnh.Có nhiều shell như là sh ,csh, zsh, bash nhưng phổ biến nhất là bash .
* Cách thức hoạt động : shell sẽ đọc các lệnh đó là tìm vị trí các file thực thi của lênh đó thông qua PATH(biến môi trường chứa danh sách các thư mục cho file thực thi). Các file thực thi thường được lưu tại thư mục /bin, /sbin, /usr/bin, /usr/sbin, /opt.
* Có thể nhập trực tiếp câu lệnh hoặc thông qua shell script.

| Command |Sample| Descrption |
|---------|------|------------|
|which |which ls|Tìm vị trí file thực thi của một câu lệnh|
|whereis |whereis ls |Tìm vị trí file thực thi ,source và manual page file của một câu lệnh |
|cd	|cd /etc/passwd|Thay đổi thư mục làm việc|
||cd -|trở lại thư mục vừa mới chuyển đi|
||cd ..|di chuyến đến thư mục cha của thư mục hiện tại|
|./|./|thay thế cho đường dẫn đến thư mục hiện tại|
|~/|~/|thay thế cho đường dẫn đến thư mục của user|
|pwd|pwd	|In thư mục hiên tại đang làm việc|
|ls	|ls |Liêt kê danh sách thư mục và file chứa trong thư mục hiện tại|
||ls /etc|liệt kê file và thưc mục trong thư mục etc|
|tree|tree|Giống ls nhưng tổ chức theo hình cây không cài mặc định khi cài os mà phải tự cài|
|ln|ln file1 file2|Tạo link giữa các file khi một trong 2 thay đổi sẽ thay đổi cả 2|
|man|man ln|hiển thị hướng dẫn cho câu lệnh,có thể gõ /tucantim để tìm kiếm |
* sử dụng phím TAB để gợi ý file/dir
