# 10.Process
## 10.1	Type of process
|Type|	Description|
|----|-------------|
|interactive| 	Chạy bởi user thông qua câu lênh hoặc giao diên đồ họa|
|batch	|Tiến trình tự động được lên lịch và kết thúc bởi terminal |
|Deamons|	Tiến trình sẽ chạy khi khởi động máy và chờ đợi request từ user và system|
|Threads|	Luồng tiến trình chạy dưới nền process chia sẻ tài nguyên |
|Kernel thread	|Tiến trình mà user không thể can thiệp được. Thực hiện các tác vụ như là chuyển thread từ CPU này sang CPU khác …|
## 10.2	Câu lệnh
| Command | Descrption |
|---------|------------|
|ps	|Thông tin về các tiến trình hiện đang chạy PID:process id,TTY,TIME,CMD:name program use process|
|pstree|	Hiện thi tiến trình dưới dạng cây |
|top	|Thông tin về các tiến trình có cạp nhật theo thời gian.Dòng đầu tiên chứa thông tin về thời gian mở máy ,số user và load average(>1 hệ thống  gặp vấn đề).Dòng thứ 2 chứa thông tin về tổng ps , số ps run,sleep,stop,zombie.Dòng thứ 3 chưa thông tin về % thời gian mà CPU danh cho user ,system …Dòng thứ 4 chứa thông tin về RAM.Dòng thứ 5 chứa thông tin vè SWAP.Các dòn bên dưới là bảng hiển thị thông tin các ps như là pid, priority, nice value,virtual ,physic , share,status,%CPU,%MEM,cmd|
|Kill –SiGKILL PID|Dừng tiến trình theo PID|
|Kill -9 PID	|Dừng tiến trình theo PID|
|At now + 5minutes	|Lên lịch cho process hoạt dộng|
|Sleep	|Delay process|
