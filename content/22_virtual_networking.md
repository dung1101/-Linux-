# 22.Linux Virtual Networking
## 22.1 Libvirt Virtual Networking 
Hỗ trợ 4 chế độ mạng ảo:
* NAT mode
* Routed mode
* Isolated mode
* Bridged mode

|Mode|Hoạt động|
|----|---------|
|NAT|Các máy ảo sẽ sử dụng IP của host như là public id để giao tiếp với bên ngoài|
|Routed|Máy ảo kết nối đến physical host LAN và phải cấu hình lại router ở host để có thể kết nối tới mạng bên ngoài|
|Isolated|Các máy ảo có thể giao tiếp với nhau và với host tuy nhiên không thể giao tiếp được với bên ngoài|
|Bridged|Máy ảo sẽ liên kết trực tiếp với card mạng vật lý của host và giao tiếp với bên ngoài thông qua card này|

### cấu hình NAT mode
* install libvirt :apt-get install lirvirt 
* Khi trình libvirt được cài đặt lần đầu tiên trên host, nó sẽ đi kèm với cấu hình mặc định này ở chế độ NAT. Cấu hình được lưu trữ trong tệp XML '/etc/libvirt/qemu/networks/default.xml.' Một interface virbr0 cũng được tạo ra trên host.
### cấu hình bridged mode
|Command|Description|
|-------|-----------|
|virsh net-destroy default| disable NAT mode|
|cp /etc/libvirt/qemu/networks/default.xml /etc/libvirt/qemu/networks/bridged_network.xml|tạo một bản sao của cấu hình đổi tên thành bridged_network.xml và đổi tên bridge name trong file|
|virsh net-start bridged_network|khởi động mạng|
|brctl addbr mybridge0|add bridge|
|nano /etc/sysconfig/network-scripts/ifcfg-mybridge0|DEVICE=mybridge0 TYPE=Bridge BOOTPROTO=none IPADDR=10.10.10.98 PREFIX=24 GATEWAY=10.10.10.1 DNS1=8.8.8.8 DEFROUTE=yes IPV4_FAILURE_FATAL=no ONBOOT=yes DELAY=0 NM_CONTROLLED=no|
|nano /etc/sysconfig/network-scripts/ifcfg-enp0s25|TYPE=Ethernet BOOTPROTO=none DEFROUTE=yes IPV4_FAILURE_FATAL=no IPV6INIT=no NAME=enp0s25 UUID=48d129a3-89df-4f8b-9b99-5e3518edc111 ONBOOT=yes HWADDR=00:24:81:0D:3F:8D BRIDGE=mybridge0 NM_CONTROLLED=no IPV4_FAILURE_FATAL=no|
|brctl addif mybridge0 enp0s25||

### cấu hình routed mode
|Command|Description|
|-------|-----------|
|virsh net-define /etc/libvirt/qemu/networks/router.xml|mạng được định nghĩa theo file router.xml|
|virsh net-start router|khởi động router mode network|
|virsh net-autostart router|set auto start|
## 22.2 Tạo máy ảo
|Command|Description|
|-------|-----------|
|apt-get install virt-install|install |
|virt-install --name VM1 --ram 2048 --vcpu 2 --network network=default --graphics none --os-type linux --disk path=/data/vm-images/vm1.img,size=10 --location /tmp/ubuntu-14.04.1-server-amd64.iso --extra-args 'console=ttyS0,115200n8 serial'|Tạo một máy ảo|
|virsh console VM1|login vào máy ảo VM1|
