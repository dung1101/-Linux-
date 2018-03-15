# 13.Network
| Command/location | Descrption |
|---------|------------|
| /etc/network/interfaces|cat /etc/network/interface| File chứa cấu hình ip cho card mạng |
|ifconfig|Hiển thị thông tin về ip|
|route| Hiển thị routing table destination/gate way/mark/flag/metric/ref/used/iface |
||route add -net 192.168.92.9 netmask 255.255.255.0 gw 192.168.92.1 eth0|	Thêm route vào routing table des/mask/gate/iface|
||route del-net 192.168.92.9 netmask 255.255.255.0 gw 192.168.92.1 eth0|Xóa route|
## Routing table
Bảng này được gán tương ứng mỗi địa chỉ đích với một địa chỉ Router cần đến ở chặng tiếp theo.Bảng địa chỉ đích trong bảng có thể bao gồm các địa chỉ mạng, mạng con, các hệ thống độc lập. Trong bảng định tuyến có thể bao gồm một tuyến mặc định, được biểu diễn bằng địa chỉ 0.0.0.0. Bảng định tuyến của mỗi giao thức định tuyến là khác nhau, nhưng có thể bao gồm nhữnh thông tin sau : 
* Địa chỉ đích của mạng, mạng con hoặc hệ thống. 
* Địa chỉ IP của Router chặng kế tiếp phải đến. 
* Giao tiếp vật lý phải sử dụng để đi đến Router kế tiếp. 
* Mặt nạ mạng của địa chỉ đích. 
* Khoảng cách đến đích (thí dụ : số lượng chặng để đến đích). 
* Thời gian (tính theo giây) từ khi Router cập nhật lần cuối. 

## Cấu hình ip tĩnh 
| Command | Descrption |
|---------|------------|
|nano /etc/network/interfaces|mở file cấu hình chỉnh sửa|
||auto eth0|
||iface eth0 inet static|
||address 192.168.92.129|
||netmask 255.255.255.0|
||gateway 192.168.92.1|

## Cấu hình ip động 
### DHCP(Dynamic Host Congfiguration Protocol)
|Mục tiêu, công dụng|Cơ chế sử dụng|Ngữ cảnh áp dụng|
|-------------------|--------------|----------------|
|Giao thức cấp địa chỉ ip động cho card mạng|Hoạt động theo mô hình client-server theo 3 cơ chế:|	Khi cần cấp địa chỉ động cho card mạng|
||Auto allocation :gán địa chỉ ip thường trực||
||Dynamic : gán địa chỉ trong 1 khoảng thời gian||
||Manual : người quản trị DHCP server sẽ cấp địa chỉ bằng tay||

| Command | Descrption |
|---------|------------|
|nano /etc/network/interfaces|mở file cấu hình chỉnh sửa|
||auto eth0|
||iface eth0 inet dhcp|
