# 21.Samba server 
|Mục tiêu, công dụng|Cơ chế sử dụng|Ngữ cảnh áp dụng|
|-------------------|--------------|----------------|
|cho phép server linux có thể chia sẻ tập tin hiểu và giải đáp các yêu cầu dịch vụ NetBIOS với client window |sử dụng smb service để phục vụ việc chia sẻ tập tin, nmb service để hiểu và giải đáp các yêu cầu dịch vụ NetBIOS|Máy chủ linux có thể chia sẻ tập tin ,hiểu và giải đáp các yêu cầu dịch vụ NetBIOS từ client window|
## Cấu hình
| |Command | Descrption |
|-|--------|------------|
|server linux|apt-get install samba|install|
||nano /etc/samba/smb.conf|thêm vào|
|||[sambashare] |
|||comment = Samba on Ubuntu|
|||guest ok = no|
|||valid users = user1|
|||invalid users = user2 user3|
|||path = /sharedir|
|||writable = yes|
|||browsable = yes|
||service samba restart|restart|
||smbpasswd -a username|đổi pass cho smbuser|
|client window|\\ip-adress\sharedir|truy cập vào share directory,nhập user passwd có thể sử thao tác trên dir|

