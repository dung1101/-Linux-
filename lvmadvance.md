# LVM advance

## Snapshot
  Snapshot là một tính năng rất hay của LVM, ý nghĩa của nó như sau:
*Giúp lưu lại tình trạng của một logical volume (snapshot chỉ lưu những thay đổi so với lúc tạo snapshot)
*Hỗ trợ khôi phục máy tính về một thời điểm đã được tạo snapshot trước đó
*Snapshot giúp cho việc restore trở nên đơn giản hơn 
*Nếu xảy ra bất cứ trục trặc gì, chỉ cần restore lại trạng thái đã tạo snapshot là xong.
```
#tạo snapshot cho lvdemo1
lvcreate -L 1G -s lvdemo1snap /dev/vgdemo/lvdemo1

#xóa snapshot
lvremove /dev/vgdemo/lvdemo1

#tăng dung lượng
lvextend -L +1G /dev/vgdemo/lvdemo1 

#tăng dung lượng tự động
nano /etc/lvm/lvm.conf
#thêm 2 dòng
snapshot_autoextend_threshold =100
snapshot_autoextend_percent =20
#khi mà dung lượng đạt 100% thì sẽ tăng thêm 20% dung lượng

#restore snapshot
umount /lvdemo1
lvconvert --merge /dev/vgdemo/lvdemo1snap
#saukhi quá trình kết thúc snapshot sẽ bị xóa 
```
## Thin Provisioning Volumes
Có khả năng tạo ra những logical volume có tổng dung lượng có thể vượt quá tổng dung lượng hiện có,tuy nhiên chỉ có thể sử dụng được dung lượng bằng đúng dung lượng thật mà thôi
```
#Tạo thin pool
lvcreate -L 10G --thinpool thinpooldemo vgdemo

#Tạo các thin có tổng dung lượng vượt quá thinpooldemo
lvcreate -V 5G --thin -n thindemo1 vgdemo/thinpooldemo
lvcreate -V 5G --thin -n thindemo2 vgdemo/thinpooldemo
lvcreate -V 5G --thin -n thindemo3 vgdemo/thinpooldemo
```
## LVM Striping
LVM Striping là tính năng cho phép ghi dữ liệu lên nhiều ổ thay vì chỉ một ổ Physical volume.
```
#Tạo strip ghi trên 3 ổ cứng
lvcreate -L 10G -n lvstripdemo -i3 vgdemo
```
## LVM Migration
Tính năng này cho phép di chuyển dữ liệu từ logical volumes sang một ổ mới mà không làm mất dữ liệu hoặc downtime. Có thể áp dụng với disk SATA,SSD,SAN storage iSCSI or FC
```
#migration dữ liệu sang ổ mới
lvconvert -m 1 /dev/vgdemo/lvdemo1 /dev/sdc1

#Check 
lvs -o+devices

#Khi đã tạo 1 mirror mới thì bạn có thể bỏ ổ cũ
lvconvert -m 0 /dev/vg-migration/lv-migration /dev/sdb1

#Check lại  
lvs -o+devices

#có thể dùng pvremove để thay thế lvconvert
pvremove -n /dev/vg-migration/lv-migration /dev/sdb1 /dev/sdc1
```
## Permanent mount
```
nano /etc/fstab
#thêm 
/dev/mapper/vgdemo-lvdemo1	/mnt/lvdemo1	ext4	defauls 0 0

#kiểm tra
mount -av
```
