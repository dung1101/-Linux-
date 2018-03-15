# 20.Systemd
|Mục tiêu, công dụng|Cơ chế sử dụng|Ngữ cảnh áp dụng|
|-------------------|--------------|----------------|
|nó quản lý (bật/tắt/khởi động lại...) các dịch vụ chạy trên máy từ lúc bật máy cho đến lúc tắt máy. Nó cũng quản lý luôn cả hệ thống.|sử dụng câu lệnh systemctl để giám sát và điều khiển systemd |quản lý các dịch vụ|

|Command | Descrption |
|--------|------------|
|systemctl start serviceX| chạy serviceX|
|systemctl stop serviceX |dừng serviceX|
|systemctl restart serviceX| restart  serviceX|
|systemctl enable serviceX| chạy serviceX khi khởi động hệ thống|
|systemctl disable serviceX| không chạy serviceX khi khởi động|
|systemctl status serviceX| trạng thái cur service|
