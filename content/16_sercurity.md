# 16.Security
## 16.1 Sự khác biệt giữa su và sudo
|su|sudo|
|--|----|
|Để sử dụng su phải biết root passwd|	Để sử dụng sudo user phải là sudoers và phải nhập passwd của chính user để có thể chạy|
|Đăng nhập vào một lần có thể là mộ thứ user root có thể theo ý muốn|	Hệ thống sẽ quy định một khoảng thời gian sau khi gõ đúng pass user sử dụng sudo sẽ không phải nhập lại pass|
## 16.2 Password encryption & pasword aging
| |Mục tiêu, công dụng|Cơ chế sử dụng|Ngữ cảnh áp dụng|
|-|-------------------|--------------|----------------|
|Password encryption|	Mã hóa passwd|	Sử dụng hàm băm SHA-512|Áp dụng để mã hóa dữ liệu trong các giao thức SSH,SSL,TLS…|
|Password aging|	Nhắc nhở người dùng thay đổi pass sau một khoảng thời gian|	Sử dụng câu lênh change |Thay đổi pass theo chu kì nhằm tăng tính bảo mật	|

## 16.3 Pirvate key & Public key 
|Mục tiêu, công dụng|Cơ chế sử dụng|Ngữ cảnh áp dụng|
|-------------------|--------------|----------------|
|	Thay thế cho user passwd phục vụ cho việc đăng nhập server từ xa nâng cao tính bảo mật|Private key được lưu trữ tại máy client và public key được lưu trữ tại máy server|ứng dụng trong SSH|
## Tạo key
|  |Command | Descrption |
|--|--------|------------|
|Server|apt-get install openssh-server| Install ssh server|
||ufw allow 22| tường lửa cho phép truyền nhậ dữ liệu qua port 22|
||ssh-keygen –t sra|Tạo key sử dụng thuật toán RSA |
|||Private key:  /root/.ssh/id_rsa|
|||Public key : /root/user/.ssh/id_rsa.pub|
||chmod 700 ~/.ssh|Thay đổi quyền|
||chmod 600 ~/.ssh/id_rsa|	Thay đổi quyền| 
||cat id_rsa.pub>>~/.ssh/authorized_keys|Install pub key vào list|
||rm –rf ~/.ssh/id_rsa.pub|	xóa key|  
||scp ~/.ssh/id_rsa root@clientmachine:/root/.ssh|Gửi private key cho client|
||rm –rf ~/.ssh/id_rsa|	xóa key|
|client|apt-get install openssh-client	|Install ssh|
||ssh –i  ~/.ssh/id_rsa root@servermachine|	Đăng nhập |
