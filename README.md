# 1.File system 
## 1.1	File system
File system ( hệ thống tập tin) đó là cách tập tin được tổ chức .
Linux hỗ trợ các file : ext3, ext4, btrfs, xfs(của linux) và vfat , ntfs, hfs(của các hệ điều hành khác).
Trước khi sử dụng một file system thì phải mount lên cây thư mục
File ẩn được bắt đầu bằn dấu '.'

## 1.2 Cấu trúc thư mục
|Directory|	Usage|
|---------|------|
|/home|	Mỗi user có một dir riêng và ở trong /home đây là mặc định khi tạo user ta có thể chỉnh sửa được khi sử dụng useradd để tạo user chọn option –d hoặc là fix cứng trong file /etc/default/useradd |
|/bin|	Chứa các file thực thi của các chương trình|
|/sbin|	Chứa các file thực thi liên quan đến quản trị hệ thống|
|/dev|	Chứa các node thiết bị khi nó được tạo ra như ổ cứng ,..|
|/var|	Chứa các file dự kiến thay đổi về kích thước khi hệ thống đang chạy : system log  file /log, web /www|
|/etc|	Chứa các file cấu hình :cho user  /passwd /shadow  ,cho net /network/interfaces …|
|/boot|	Chứa các file cần thiết cho boot|
|/lib	|Chứa thư viện cần thiết cho các chương trình| 
|/opt	|Optional |
|/tmp	|Chứa các file tạm|
|/sys	|Chứa các file |
|/media|	các thiết bị như CD ,USB khi được phat hiện hệ thống sẽ tự mount tại thư mục này| 
|/usr| 	Các ứng dụng nhiều người dùng ,dữ liệu ..|
|/usr/bin	|giống /bin|
|/usr/sbin	|giông /sbin|
|/usr/include|	Chứa các header file|
|/usr/lib	|Chứa thư viện cho file thực thi|
|/usr/share|	Share data|
|/usr/src	|Source code|
|/usr/local|	Local machine|
# 2.Shell
 Là một chương trìnhthông dịch cho phép người dùng tương tác với hệ điều hành bằng dòng lệnh.Có nhiều shell như là sh ,csh, zsh, bash nhưng phổ biến nhất là bash .
Cách thức hoạt động : shell sẽ đọc các lệnh đó là tìm vị trí các file thực thi để thực hiện. Các file thực thi thường được lưu tại thư mục /bin, /sbin, /usr/bin, /usr/sbin, /opt.
Có thể nhập trực tiếp hoặc thông qua shell script.
Khi thực thi một câu lệnh shell sẽ tìm kiếm file thực thi của lênh đó thông qua PATH(biến môi trường chứa danh sách các thư mục cho file thực thi)
| Command | Descrption |
|---------|------------|
|finger  username|	Kiểm tra xem shell nào được sử dụng|
|export  |Thay đổi giá trị các biến môi trường|
# 3.Basic command
| Command | Descrption |
|---------|------------|
|Which  |	Tìm vị trí file thực thi của một chương trình|
|Whereis|	Tìm vị trí Package|
|Cd	|Thay đổi thư mục làm việc|
|Pwd	|In thư mục hiên tại đang làm việc|
|Ls	|Liêt kê danh sách thư mục và file|
|Tree|	Giống ls nhưng tổ chức theo hình cây|
|Ln|	Tạo symbolink giống như con trỏ|
|man command|hiển thị hướng dẫn cho câu lệnh,có thể gõ /tucantim để tìm kiếm  |
|command --help|Hiển thị hỗ trợ cho câu lệnh|
* sử dụng phím TAB để gợi ý file/dir
# 4.Working with file 
| Command | Descrption |
|---------|------------|
|Command < inputfile|	đọc file |
|Command > outputfile|	In kết quả câu lệnh ra file|
|Command 2> outputfile| in lỗi ra file|
|Command &> outputfile| in cả lỗi và kết quả câu lệnh|
|Command1 | command 2	|Sử dụng 2 câu lệnh|
|Locate	|Tìm kiếm|
|Find	|Tìm kiếm|
|Cat	|in dữ liệu từ file ra console| 
|tac	|Tương tụ cat nhưng in ngược|
|less	|Đọc dữ liệu|
|More	|Đọc dữ liệu|
|tail	|Chọn hiển thị n dòng cuối|
|head	|Chọn hiên thị n dòng đầu|
|touch|Tạo file|
|mkdir|	Tạo thư mục|
|diff	|So sánh 2 file/folder|
|file	|Kiểm tra kiểu dữ liệu trong file|
# 5.Files permission
| Command | Descrption |
|---------|------------|
|Chown user  file/dir|	Chuyển quyền sở hữu cho user|
|Chgrp user file/dir	|Chuyển quyền sở hưu cho group|
|Chmod smt file/dir	|Thay đổi quyền hạn Smt : rw-rw-r hoặc 664 hoặc O+w|
# 6.Package manament 
| Command | Descrption |
|---------|------------|
|apt list –installed 	Hiển thị tất cả các program đã được install 
|apt-get install package|	Khi cài đặt một gói online máy sẽ kiểm tra trong /etc/apt/sources.list để tìm đến địa chỉ chứa package để download và cài đặt pakage và các package phụ thuộc|
|apt-get 	remove package|	Gỡ|
|apt-get update	package|Cập nhật các package available chưa được install |
|apt-get 	upgrade package|	Cập nhật các package lên phiên bản mới nhất|
|dpkg	file.deb|Cài đặt package offline bằng file .deb|
# 7.Data back up
| Command | Descrption |
|---------|------------|
|rsync	|Câu lênh copy giữ liệu như là câu lệnh cp nhưng có kiểm tra xem có thay đổi gì về nội dung hay ngày tháng hay không.Nếu không có thay đổi gì về nội dung thì sẽ chỉ cập nhật lại ngày tháng vì vậy tốc độ sẽ nhanh hơn cp|
|dd if=/dev/sda  of=/dev/sdb|	Copy disk if : input file of: output file  |
|dd if=/dev/sda  of=./bu.img|	Tao boot disk|
|tar-cvf	|Tạo file tar|
|tar-xvf	|Giải nén file tar|
|tar-zcvf	|Tạo file nen tar.gz|
|	tar-zxvf	|Giải nén|
|	tar-jcvf	|Tọa file nén tar.bz2|
|	tar-jxvf	|Giải nén|
|zip	|Tạo file nen .zip|
|unzip	|Giải nén |
# 8.System info
| Command | Descrption |
|---------|------------|
|/etc/* release	|File chứa thông tin về phiên bản linux|
|uname -r	|Kiểm tra phiên bản kernel|
|/proc/cpuinfo|	Thông tin về cpu|
|/proc/meminfo	|Thông tin về memory|
|df|	File system|
# 9.Swap
| |Mục tiêu, công dụng|Cơ chế sử dụng|Ngữ cảnh áp dụng|
|-|-------------------|--------------|----------------|
|SWAP|	Dự phòng cho RAM khi thiếu dung lượng tránh cho việc bị dừng cả hệ thống|	Sử dụng một vùng trên ổ cứng tạo thành một vùng nhớ ảo|Khi ram bị thiếu dung lượng|
# 10.User envinronment
| Command | Descrption |
|---------|------------|
|/etc/passwd	|Thông tin về các user : username,pass,UID,GID,name ….|
|/etc/shadow	|Thông tin về passwd|
|/etc/group	|Thông tin về group|
|/etc/sudoers	|Thông tin về các group có quyền root|
|useradd	|Thêm user|
|userdel	|Xóa user|
|passwd	|Thay dổi passwd|
|groups	|List các group mà user  thuộc về|
|usermod -G|	Thêm user vào group|
|usermod -g	|Thay đổi primirary group của user|
|groupadd	|Thêm group|
|groupdel	|Xoa group|
|su	|Thay đổi user|
|history	Lịch sử câu lênh đã thực thi|
# 11.Process
## 11.1	Type of process
|Type|	Description|
|----|-------------|
|interactive| 	Chạy bởi user thông qua câu lênh hoặc giao diên đồ họa|
|batch	|Tiến trình tự động được lên lịch và kết thúc bởi terminal |
|Deamons|	Tiến trình sẽ chạy khi khởi động máy và chờ đợi request từ user và system|
|Threads|	Luồng tiến trình chạy dưới nền process chia sẻ tài nguyên |
|Kernel thread	|Tiến trình mà user không thể can thiệp được. Thực hiện các tác vụ như là chuyển thread từ CPU này sang CPU khác …|
## 11.2	Câu lệnh
| Command | Descrption |
|---------|------------|
|ps	|Thông tin về các tiến trình hiện đang chạy PID:process id,TTY,TIME,CMD:name program use process|
|pstree|	Hiện thi tiến trình dưới dạng cây |
|top	|Thông tin về các tiến trình có cạp nhật theo thời gian.Dòng đầu tiên chứa thông tin về thời gian mở máy ,sô user và load average(>1 hệ thống  gặp vấn đề).Dòng thứ 2 chứa thông tin về tổng ps , số ps run,sleep,stop,zombie.Dòng thứ 3 chưa thông tin về % thời gian mà CPU danh cho user ,system …Dòng thứ 4 chứa thông tin về RAM.Dòng thứ 5 chứa thông tin vè SWAP.Các dòn bên dưới là bảng hiển thị thông tin các ps như là pid, priority, nice value,
virtual ,physic , share,status,%CPU,%MEM,cmd|
|Kill –SiGKILL PID|Dừng tiến trình theo PID|
|Kill -9 PID	|Dừng tiến trình theo PID|
|At now + 5minutes	|Lên lịch cho process hoạt dộng|
|Sleep	|Delay process|
# 12.Volume manage 
## 12.1	Chia partition cho ổ cứng
| Command | Descrption |
|---------|------------|
|Fdisk  /dev/sdx	|Cấu hình cho ổ cứng sdx : chia partition, thêm ,sửa ,xóa, chuyển đổi kiểu file…|
|Fdisk –l |	Xem thông tin ổ cứng|
## 12.2	LVM
|Mục tiêu, công dụng|Cơ chế sử dụng|Ngữ cảnh áp dụng|
|-------------------|--------------|----------------|
|LVM	là một kỹ thuật cho phép tạo ra một vùng ổ cứng ảo cho phép dễ dàng thay đổi dung lượng,hay gom nhiều ổ cứng vật lý lại |	Đầu tiên ta tạo các Physical Volume từ ổ cứng vật lý sau đó gom lại vào volume group va sau cho chia ra cac logical volume với dung lượng tùy ý nhỏ hơn dung lượng của group.Sau đó để sử dụng được ổ đĩa ảo ta phải format và mount	|Khi cần gom nhiều ổ đĩa thành một ổ đĩa lớn. hoặc tạo ra các ổ đĩa có thể tùy chỉnh dung lượng một cách linh hoạt|
| Command | Descrption |
|---------|------------|
|vcreate /dev/sdb1 /dev/sdc1|	Tạo physical volume từ sdb1 và sdc1|
|pvremove	|Xóa pv|
|pvdisplay	|Hiển thị thông tin các pv hiện có|
|vgcreate  xgroup /dev/sdb1 /dev/sdc1|	Tạo vg từ 2 pv|
|vgremove	|Xóa vg|
|vgextend	|Mở rộng vg|
|vgreduce	|Thu nhỏ vg|
|vgdisplay	|Hiển thị thông tin các vg|
|lvcreate –n  lvm1 –L 10G xgroup|	Tạo 1 lv  tên lvm1 dung lượng  10Gtừ vg| 
|lvremove	|Xóa lv|
|lvextend	|Mở rộng lv|
|lvreduce	|Thu nhỏ lv|
|lvdisplay	|Hiển thị thông tin các lv|
|mkfs.ext4 /dev/xgroup/lvm1|	format ổ  |
|wipefs 	|Xóa file hệ thống|
|mount /dev/xgroup/lvm1 /lv	|Mount đến một /lv tự tạo|
|resize2fs	|Thay đổi kich thước ổ |
# 13.Network
| Command | Descrption |
|---------|------------|
| /etc/network/interfaces | File chứa cấu hình ip cho card mạng |
|ifconfig|Hiển thị thông tin về ip|
|route| Hiển thị routing table destination/gate way/mark/flag/metric/ref/used/iface |
|Route add|	Thêm route vào routing table cho đến khi reboot sẽ mất|
|Route del	|Xóa route|
# 14.Network file system
## 14.1 NFS
| |Mục tiêu, công dụng|Cơ chế sử dụng|Ngữ cảnh áp dụng|
|-|-------------------|--------------|----------------|
|Network file system (NFS)|là một giao thức dùng để chia sẻ tập tin và người dùng có thể thao tác với tập tin như trên máy của mình|NFS sử dụng thủ tục RPC(remotr procedure calls)để gửi nhân yêu cầu giữa mấy chủ và máy trạm.Dịch vụ portmap:dịch vụ quản lý yêu cầu RPC.|khi máy chủ muốn chia sẻ tập tin cho các máy trạm|
## 14.2 Cấu hình nfs và sử dụng
| Command | Descrption |
|---------|------------|
|nano /etc/export| chỉnh sửa lưu trữ danh sách tập tin được chia sẻ , địa chỉ ip được cấp quyền sử dụng và quyền là gì ví dụ /home 220.123.14.14(rw)|
|/etc/init.d/nfs restart |restart|
|mount ipmaychu:/thumucchiase /thumucduocmount|đọc dữ liệu từ máy trạm cách 1|
|nano file /etc/fstab|đọc dữ liệu từ máy trạm cách 2 tenserver:/thumucchise /thumucduocmount nfs|
# 15.iSCSI
## 15.1 iSCSI
| |Mục tiêu, công dụng|Cơ chế sử dụng|Ngữ cảnh áp dụng|
|-|-------------------|--------------|----------------|
|iSCSI(internet Small Computer System interface)|Tạo một local disk trên máy với mọi chức năng nhưng dung lượng thực tế được quản lý ở trên máy chủ thông qua internet|	Máy chủ nơi chứa ổ cứng thật được gọi là iSCSI target và máy kết nối đến iSCSI được gọi là initiator|	Khi muốn tạo một local disk |
## 15.2 Cấu hình target
| Command | Descrption |
|---------|------------|
|apt-get install iscsitarget iscsitarget-dkms|install|
|mkdir /var/iscsi_disk|tạo dir|	
|dd if=/dev/zero of =/var/iscsi_disk/disk01.img count=0 bs=1 seek=10G|	Tạo img|
|nano /etc/default/iscsitarget|	thay đổi ISCSITARGET_ENABLE = true|
|nano /etc/iet/ietd.conf|thêm vào 'Target iqn.year-month.domain: name' 'Lun 0 Path =/var/iscsi_disk/disk01.img,Type fileio' 'Initiator      -address 202.20.24.2' 'Incominguser user password'|
|Service iscsitarget restart| 	Restart| 
## 15.3 Cấu hình initiator
| Command | Descrption |
|---------|------------|
|apt-get install open-iscsi|	install|
|Nano /etc/iscsi/iscsid.conf|  sửa: node.session.auth.authmethod = CHAP node.session.auth.username = username node.session.auth.password = password|
|Service open-iscsi restart| 	Restart| 
|iscsiadm –m discovery –t sendtarget –p 10.0.0.3| 	tìm target|
|iscsiadm –m  node –o show	|Show status|
|iscsiadm –m node --login	|Login to target|
|iscsiadm –m session –o show|	Kiểm tra xem đã thiết lập| 
# 16.Security
## 16.1 Sự khác biệt giữa su và sudo
|su|sudo|
|--|----|
|Để sử dụng su phải biết root passwd|	Để sử dụng sudo user phải là sudoers và phải nhập passwd của chính user để có thể chạy|
|Đăng nhập vào một lần có thể là mộ thứ user root có thể theo ý muốn|	Hệ thống sẽ quy định một khoảng thời gian sau khi gõ đúng pass user sử dụng sudo sẽ không phải nhập lại pass|
## 16.2 
| |Mục tiêu, công dụng|Cơ chế sử dụng|Ngữ cảnh áp dụng|
|-|-------------------|--------------|----------------|
|Password encryption|	Mã hóa passwd|	Sử dụng hàm băm SHA-512|Áp dụng để mã hóa dữ liệu trong các giao thức SSH,SSL,TLS…|
|Password aging|	Nhắc nhở người dùng thay đổi pass sau một khoảng thời gian|	Sử dụng câu lênh change |	|
|Private /public key|	Thay thế cho user passwd phục vụ cho việc đăng nhập server từ xa nâng cao tính bảo mật|Private key được lưu trữ tại máy client và public key được lưu trữ tại máy server|ứng dụng trong SSH|
## 16.3 Tạo pirvate / public key 
|  |Command | Descrption |
|--|--------|------------|
|Server|apt-get install openssh-server| Install ssh server|
||ufw allow 22| tường lửa cho phép truyền nhậ dữ liệu qua port 22|
||ssh-keygen –t sra|Tạo key sử dụng thuật toán RSA Private key:  /root/.ssh/id_rsa Public key : /root/user/.ssh/id_rsa.pub|
||chmod 700 ~/.ssh|Thay đổi quyền|
||chmod 600 ~/.ssh/id_rsa|	Thay đổi quyền| 
||cat id_rsa.pub>>~/.ssh/authorized_keys|Install pub key vào list|
||rm –rf ~/.ssh/id_rsa.pub|	xóa key|  
||	scp ~/.ssh/id_rsa root@clientmachine:/root/.ssh|Gửi private key cho client|
||rm –rf ~/.ssh/id_rsa|	xóa key|
|client|apt-get install openssh-client	|Install ssh|
||Ssh –i  ~/.ssh/id_rsa root@servermachine|	Đăng nhập |
