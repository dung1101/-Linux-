# 13.Network
| Command | Descrption |
|---------|------------|
| /etc/network/interfaces | File chứa cấu hình ip cho card mạng |
|ifconfig|Hiển thị thông tin về ip|
|route| Hiển thị routing table destination/gate way/mark/flag/metric/ref/used/iface |
|Route add|	Thêm route vào routing table cho đến khi reboot sẽ mất|
|Route del	|Xóa route|
# 14.Network file system
# 15.iCSI
| |Mục tiêu, công dụng|Cơ chế sử dụng|Ngữ cảnh áp dụng|
|-|-------------------|--------------|----------------|
|iSCSI(internet Small Computer System interface)|Tạo một local disk trên máy với mọi chức năng nhưng dung lượng thực tế được quản lý ở trên máy chủ thông qua internet|	Máy chủ nơi chứa ổ cứng thật được gọi là iSCSI target và máy kết nối đến iSCSI được gọi là initiator|	Khi muốn tạo một local disk |
## 15.1 Cấu hình target
| Command | Descrption |
|---------|------------|
|apt-get install iscsitarget iscsitarget-dkms|install|
|mkdir /var/iscsi_disk|tạo dir|	
|dd if=/dev/zero of =/var/iscsi_disk/disk01.img count=0 bs=1 seek=10G|	Tạo img|
|nano /etc/default/iscsitarget|	thay đổi ISCSITARGET_ENABLE = true|
|nano /etc/iet/ietd.conf|thêm vào 'Target iqn.year-month.domain: name' 'Lun 0 Path =/var/iscsi_disk/disk01.img,Type fileio' 'Initiator      -address 202.20.24.2' 'Incominguser user password'|
|Service iscsitarget restart| 	Restart| 
## 15.2 Cấu hình initiator
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



