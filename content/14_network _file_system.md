# 14.Network file system
## 14.1 NFS
| |Mục tiêu, công dụng|Cơ chế sử dụng|Ngữ cảnh áp dụng|
|-|-------------------|--------------|----------------|
|Network file system (NFS)|là một giao thức dùng để chia sẻ tập tin và người dùng có thể thao tác với tập tin như trên máy của mình|NFS sử dụng thủ tục RPC(remotr procedure calls)để gửi nhân yêu cầu giữa mấy chủ và máy trạm.Dịch vụ portmap:dịch vụ quản lý yêu cầu RPC.|khi máy chủ muốn chia sẻ tập tin cho các máy trạm|
## 14.2 Cấu hình nfs và sử dụng
| Command | Descrption |
|---------|------------|
|nano /etc/export| chỉnh sửa lưu trữ danh sách tập tin được chia sẻ , địa chỉ ip được cấp quyền sử dụng và quyền là gì ví dụ /home 220.123.14.14(rw)|
|/etc/init.d/nfs restart |restart|
|mount ipmaychu:/thumucchiase /thumucduocmount|đọc dữ liệu từ máy trạm cách 1|
|nano file /etc/fstab|đọc dữ liệu từ máy trạm cách 2 tenserver:/thumucchise /thumucduocmount nfs|
