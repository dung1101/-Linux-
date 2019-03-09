## 1.User
>User là người có thể truy cập đến hệ thống.<br>
User có username và password.<br>
Có hai loại user: super user và regular user.<br>
Mỗi user còn có một định danh riêng gọi là UID.<br>
Định danh của người dùng bình thường sử dụng giá trị bắt đầu từ 500.

## 2.Group
>Group là tập hợp nhiều user lại.<br>
Mỗi user luôn là thành viên của một group.<br>
Khi tạo một user thì mặc định một group được tạo ra.<br>
Mỗi group còn có một định danh riêng gọi là GID.<br>
Định danh của group thường sử dụng giá trị bắt đầu từ 500.

## 3.Tập lệnh quản lý User và Group
###  3.1 Tạo User:
Cú pháp: 
```
useradd [option] <username>
-c “Thông tin người dùng”
-d <Thư mục cá nhân>
-m : Tạo thư mục cá nhân nếu chưa tồn tại
-g <nhóm của người dùng>
```
Ví dụ: 
```
useradd –c “Nguyen Van A – Server Admin” –g serveradmin vana
```
### 3.2 Thay đổi thông tin cá nhân:
Cú pháp: 
```
usermod [option] <username>
```
Những option tương tự Useradd

Ví dụ: 
```
usermod –g kinhdoanh vana  //chuyển vana từ nhóm server admin sang nhóm kinh doanh.
```
### 3.3 Xóa người dùng
Cú pháp : 
```
userdel [option] <username>
```
Vídụ :  
```
userdel  –r  vana
```
### 3.4 Khóa/Mở khóa người dùng
```
passwd –l <username>  /  passwd –u <username>
usermod –L <username> /  usermod –U <username>
```    
Trong /etc/shadow có thể khóa tài khoản bằng cách thay từ khóa x bằng từ khóa *.

### 3.5 Tạo nhóm:
Cú pháp:
```
groupadd <groupname>
```    
Ví dụ: 
```
groupadd serveradmin
```
### 3.6 Xóa nhóm
Cú pháp: 
```
groupdel <groupname>
```    
Ví dụ: 
```
groupdel <serveradmin>
```
### 3.7 Xem thông tin về User và Group
Cú pháp:
```
id <option> <username>
```    
Ví dụ: 
```
id -g vana //xem GroupID của user vana
```

Cú pháp: 
```
groups <username>
```
Ví dụ: 
```
groups vana //xem tên nhóm của user vana
```
## 4. Những file liên quan đến User và Group
`/etc/passwd` Mỗi dòng trong tập tin gồm có 7 trường, được phân cách bởi dấu hai chấm.

`/etc/group` Mỗi dòng trong tập tin gồm có 4 trường, được phân cách bởi dấu hai chấm.

`/etc/shadow` Lưu mật khẩu đã được mã hóa và chỉ có user root mới được quyền đọc.

## 5. Quyền hạn
Trong Linux có 3 dạng đối tượng :
- Owner (người sở hữu).
- Group owner (nhóm sở hữu).
- Other users (những người khác).

Các quyền hạn :
- Read – r – 4  : cho phép đọc nội dung.
- Write – w – 2  : dùng để tạo, thay đổi hay xóa.
- Execute – x – 1  : thực thi chương trình.

Vídụ : Với lệnh ls –l ta thấy :
```
[root@task ~]# ls -l
total 32
-rw-------. 1 root root  1416 Jan 10 14:06 anaconda-ks.cfg
-rw-r--r--. 1 root root 15522 Jan 10 14:06 install.log
-rw-r--r--. 1 root root  5337 Jan 10 14:06 install.log.syslog
drwxr-xr-x  6 root root  4096 Feb  9 10:02 softs
```
Ngoài ra, chúng ta có thể dùng số.

Vídụ : quyền r, w, x : 4+2+1 = 7

Tổ hợp 3 quyền trên có giá trị từ 0 đến 7.

## 6. Các lệnh liên quan đến quyền hạn
Lệnh `chmod` : dùng để cấp quyền hạn.
Cú pháp : 
```
chmod  <specification> <file>
```
Ví dụ: 
```
chmod 644 baitap.txt   //cấp quyền cho owner có thể ghi các nhóm các chỉ có quyền đọc với file taptin.txt
```

Lệnh `chown` : dùng thay đổi người sở hữu.
Cú pháp : 
```
chown  <owner>  <filename>
```

Lệnh `chgrp` : dùng thay đổi nhóm sở hữu.
Cú pháp : 
```
chgrp  <group>  <filename>
```
