# 15.iSCSI
## 15.1 iSCSI(internet Small Computer System Interface)
|Mục tiêu, công dụng|Cơ chế sử dụng|Ngữ cảnh áp dụng|
|-------------------|--------------|----------------|
|Tạo một local disk trên máy với mọi chức năng nhưng dung lượng thực tế được quản lý ở trên máy chủ thông qua internet|	Máy chủ nơi chứa ổ cứng thật được gọi là iSCSI target và máy kết nối đến iSCSI được gọi là initiator|	Khi muốn tạo một local disk với dung lượng thực tế đặt ở chỗ khác |
## 15.2 Cấu hình target
| Command | Descrption |
|---------|------------|
|apt-get install iscsitarget iscsitarget-dkms|install|
|mkdir /var/iscsi_disk|tạo dir|	
|dd if=/dev/zero of =/var/iscsi_disk/disk01.img count=0 bs=1 seek=10G|Tạo img|
|nano /etc/default/iscsitarget|	thay đổi ISCSITARGET_ENABLE = true|
|nano /etc/iet/ietd.conf|thêm vào |
||Target iqn.2018-03.sinionth:diskX|
||Lun 0 Path =/var/iscsi_disk/disk01.img,Type fileio|
||Initiator-address 192.168.92.129|
||Incominguser dung1 1|
|service iscsitarget restart|Restart| 
## 15.3 Cấu hình initiator
| Command | Descrption |
|---------|------------|
|apt-get install open-iscsi|	install|
|nano /etc/iscsi/iscsid.conf|sửa: node.session.auth.authmethod = CHAP |
||node.session.auth.username =dung1| 
||node.session.auth.password =1|
|service open-iscsi restart|Restart| 
|iscsiadm –m discovery –t sendtarget –p 10.0.0.3|tìm target|
|iscsiadm –m  node –o show	|Show status|
|iscsiadm –m node --login	|Login to target|
|iscsiadm –m session –o show|	Kiểm tra xem đã thiết lập| 
