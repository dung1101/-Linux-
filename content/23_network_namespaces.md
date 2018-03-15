23.Network namespaces
 Trong không gian mạng ảo Linux, network namespaces  cho phép các trường hợp riêng biệt của giao diện mạng và bảng định tuyến hoạt động độc lập với nhau.
 
|Command|Description|
|-------|-----------|
|ip netns add Blue|thêm namespace Blue|
|ip netns delete Yellow|xóa namespace Yellow|
|ip netns list|hiển thị các namespaces|
|/var/run/netns/|thư mục chứa các namespace|
|ip netns exec Blue ip link set dev lo up|bật loopack interfaces của Blue|
|ip netns exec Blue ifconfig|xem thông tin của lo|
|ip link add vetha type veth peer name vethb|tạo 2 interface ảo vetha và vethb|
|ip link set vethb netns Blue|set interface vethb cho Blue|
|ip netns exec Blue ip link set dev vethb up|bật vethb interfaces của Blue|
|ip link set dev vetha up|bật vethb interfaces của name space default |
|ip addr add 192.168.100.1/24 dev vetha|config ip cho interface vetha|
|ip netns exec Blue ip addr add 192.168.100.2/24 dev vethb|config ip cho interface vethb (do Blue không thể giao tiếp với bên ngoài nên phải thông qua 2 inteface vetha và vethb để giao tiếp với host và từ host giao tiếp với bên ngoài)|
