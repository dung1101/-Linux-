# 10.User envinronment
| Command/Location|Sample| Descrption |
|---------|------|------------|
|/etc/passwd|cat /etc/passwd|Thông tin về các user : username,pass,UID,GID,name ….|
|/etc/shadow|cat /etc/shadow|Thông tin về password|
|/etc/group|cat /etc/group |Thông tin về group,các user trong group|
|/etc/sudoers|cat /etc/sudoers|Thông tin về các group có quyền root|
|useradd|useradd dung2	|Thêm user|
|userdel|userdel dung2	|Xóa user|
|passwd|passwd dung2|Thay dổi passwd|
|groups|groups dung1|List các group mà user  thuộc về|
|usermod|usermod -G groupX dung3|	Thêm user vào group|
||usermod -g	groupX dung3|Thay đổi primirary group của user|
|groupadd|groupadd groupX	|Thêm group|
|groupdel|groupdel	groupY|Xoa group|
|su	|su dung2|Thay đổi user|
