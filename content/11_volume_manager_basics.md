# 11.Volume manage basic
## 11.1	Chia partition cho ổ cứng
| Command | Descrption |
|---------|------------|
|Fdisk  /dev/sdx	|Cấu hình cho ổ cứng sdx : chia partition, thêm ,sửa ,xóa, chuyển đổi kiểu file…|
|Fdisk –l |	Xem thông tin ổ cứng|
|mkfs.ext4 /dev/sdx1|format ổ theo định dạng ext4|
|mount /dev/sdx1 /hoctap|mount mềm sau khi reboot sẽ mất|
|nano /etc/fstab|thêm vào /etc/fstab /hoctap ext4 default 0 0|
## 11.2	LVM
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
