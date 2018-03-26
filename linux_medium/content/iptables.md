# 2.Iptables
## 2.1 Tổng quan 
Iptables là một ứng dụng dòng lệnh và là một bức tường lửa Linux mà bạn có thể sử dụng để thiết lập, duy trì và kiểm tra các bảng để lọc các gói tin. Bạn có thể thiết lập nhiều bảng khác nhau, mỗi bảng có thể chứa nhiều chuỗi, mỗi một chuỗi là một bộ quy tắc. Mỗi quy tắc định nghĩa phải làm gì với gói tin nếu nó phù hợp với gói đó.
## 2.2 Các loại bảng trong iptables:
`Mangle table`: chịu trách nhiệm biến đổi quality of service bits trong TCP header.

`Filter queue`: chịu trách nhiệm thiết lập bộ lọc gói tin (packet filtering), có ba loại built-in chains được mô tả để thực hiện các chính sách về firewall (firewall policy rules)
* INPUT – được sử dụng để điều khiển các gói tin đến tới máy chủ. Bạn có thể chặn hoặc cho phép kết nối dựa trên cổng, giao thức hoặc địa chỉ IP nguồn.
* FORWARD – được sử dụng để lọc các gói dữ liệu đến máy chủ nhưng sẽ được chuyển tiếp ở một nơi khác.
* OUTPUT – được sử dụng để lọc các gói tin đi ra từ máy chủ của bạn.

`NAT queue`: thực thi chức năng NAT (Network Address Translation), cung cấp hai loại built-in chain sau đây:
* Pre-routing chain: thay đổi địa chỉ đến của gói dữ liệu khi cần thiết.
* Post-routing chain: thay đổi địa chỉ nguồn của gói dữ liệu khi cần thiết.
## 2.3 Luồng làm việc
![](./iptables-workflow.jpg)
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
