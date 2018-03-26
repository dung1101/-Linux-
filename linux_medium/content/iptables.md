# 2.Iptables
## 2.1 Tổng quan 
Iptables là một ứng dụng dòng lệnh và là một bức tường lửa Linux mà bạn có thể sử dụng để thiết lập, duy trì và kiểm tra các bảng để lọc các gói tin. Bạn có thể thiết lập nhiều bảng khác nhau, mỗi bảng có thể chứa nhiều chuỗi, mỗi một chuỗi là một bộ quy tắc. Mỗi quy tắc định nghĩa phải làm gì với gói tin nếu nó phù hợp với gói đó.
## 2.2 Kiến trúc iptables
Về tổng quan, iptables có thể chứa nhiều tables, mỗi tables có thể chứa nhiều chains. Mỗi chains có thể chứa nhiều rule. Mỗi rule được định nghĩa cho từng packets.
### 2.2.1 Table & chain
`Mangle table`: chịu trách nhiệm biến đổi quality of service bits trong TCP header.
* PREROUTING chain
* OUTPUT chain
* FORWARD chain
* INPUT chain
* POSTROUTING chain

`Filter queue`: chịu trách nhiệm thiết lập bộ lọc gói tin (packet filtering), có ba loại built-in chains được mô tả để thực hiện các chính sách về firewall (firewall policy rules)
* INPUT – được sử dụng để điều khiển các gói tin đến tới máy chủ. Bạn có thể chặn hoặc cho phép kết nối dựa trên cổng, giao thức hoặc địa chỉ IP nguồn.
* FORWARD – được sử dụng để lọc các gói dữ liệu đến máy chủ nhưng sẽ được chuyển tiếp ở một nơi khác.
* OUTPUT – được sử dụng để lọc các gói tin đi ra từ máy chủ của bạn.

`NAT queue`: thực thi chức năng NAT (Network Address Translation), cung cấp hai loại built-in chain sau đây:
* Pre-routing chain: thay đổi địa chỉ đến của gói dữ liệu khi cần thiết.
* Post-routing chain: thay đổi địa chỉ nguồn của gói dữ liệu khi cần thiết.
* OUTPUT chain – NAT cho locally sinh ra packets trên firewall

`Raw table` : sử dụng cho việc loại trừ các cấu hình. Raw table chứa các chains
* PREROUTING chain
* OUTPUT chain

## 2.3 Luồng làm việc
![](../image/iptables-workflow.jpg)
### INPUT
Gói dữ liệu đến mạng A, tiếp đó nó được kiểm tra bởi mangle table PREROUTING chain (nều cần). Tiếp theo là kiểm tra gói dữ liệu bởi nat table's PREROUTING chain để kiểm tra xem gói dữ liệu có cần DNAT hay không? DNAT sẽ thay đổi địa chỉ đích của gói dữ liệu. Rồi gói dữ liệu được chuyển đi hướng đi vào trong bên trong firewall, nó sẽ được kiểm tra bởi INPUT chain trong mangle table, và nếu gói dữ liệu qua được các kiểm tra của INPUT chain trong filter table, nó sẽ vào trong các chương trình của server bên trong firewall.
### FORWARD
Gói dữ liệu đến mạng A, tiếp đó nó được kiểm tra bởi mangle table PREROUTING chain (nều cần). Tiếp theo là kiểm tra gói dữ liệu bởi nat table's PREROUTING chain để kiểm tra xem gói dữ liệu có cần DNAT hay không? DNAT sẽ thay đổi địa chỉ đích của gói dữ liệu. Rồi gói dữ liệu được chuyển đi vào một mạng khác, thì nó sẽ được lọc bởi FORWARD chain của filter table, và nếu cần gói dữ liệu sẽ được SNAT trong POSTROUTING chain để thay đổi IP nguồn trước khi vào mạng B.
### OUT
Khi firewall cần gửi dữ liệu ra ngoài. Gói dữ liệu sẽ được dẫn vào đi qua sự kiểm tra của OUTPUT chain trong mangle table (nếu cần), tiếp đó là kiểm tra trong OUTPUT chain của nat table để xem DNAT (DNAT sẽ thay đổi địa chỉ đến) có cần hay không và OUTPUT chain của filter table sẽ kiểm tra gói dữ liệu nhằm phát hiện các gói dữ liệu không được phép gởi đi.Cuối cùng trước khi gói dữ liệu được đưa ra lại Internet, SNAT and QoS sẽ được kiểm tra trong POSTROUTING chain.
## 2.3 Cài đặt
iptables được cài đặt mặc định trong hầu hết các bản phân phối cửa linux.Tuy nhiên nếu chưa cài đặt có thể cài đặt thủ công
```
apt-get update
apt-get install iptables
```
## 2.4 Cấu hình
### Liệt kê các rules hiện có
```
iptables -L -v
```
chúng ta có các cột như TARGET, PROT, OPT, IN, OUT, SOURCE, DESTINATION, ý nghĩa của mỗi cột là như sau:
* TARGET: Hành động sẽ thực thi cho mỗi chuỗi quy tắc : accept(cho phép gói tin được đi qua),drop(gói tin sẽ bị drop), return (bỏ qua chain hiện tại)
* PROT: Là viết tắt của chữ Protocol, nghĩa là giao thức. Tức là các giao thức sẽ được áp dụng để thực thi quy tắc này. Ở đây chúng ta có 3 lựa chọn là all, tcp hoặc udp.
* IN: Thiết bị mạng nhận kết nối vào được áp dụng cho quy tắc, chẳng hạn như lo, eth0, eth1.
* OUT: Thiết bị mạng phục vụ nhu cầu gửi kết nối ra ngoài được áp dụng quy tắc.
* SOURCE :Địa chỉ của nguồn được phép áp dụng quy tắc
* DESTINATION: Địa chỉ của đích cập được phép áp dụng quy tắc.
### Thêm rules 
```
sudo iptables -A <INPUT/FORWARD/OUT>  -i <interface> -p <protocol (tcp/udp)> -s <source> --dport <port no.>  -j <target>
```
Cho phép truy cập trên các cổng HTTP, SSH, SSL
```
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -p tcp --dport 443 -j ACCEPT
```
Lọc các gói tin 
```
#Cho phép các gói tin từ IP 192.168.1.3
iptables -A INPUT -s 192.168.1.3 -j ACCEPT
#Từ chối các gói tin từ  IP 192.168.1.4
iptables -A INPUT -s 192.168.1.4 -j DROP
#Từ chối các gói tin từ một dãy IP
iptables -A INPUT -m iprange --src-range 192.168.1.100-192.168.1.200 -j DROP
```
Xóa các rules
```
#Xóa tất cả
iptables -F
#Xóa từng rules khác nhau theo tham số -D
iptables -L --line-numbers
iptables -D INPUT 3
```
Lưu giữ các thay đổi
```
/sbin/iptables-save
```
