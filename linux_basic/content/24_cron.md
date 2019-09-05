## 1) Cron
>The software utility **cron** is a time-based job scheduler in Unix-like computer operating systems.
**cron** là một tiện ích lập lịch dựa trên thời gian thực hiện các tác vụ một cách tự động theo định kỳ.

>**crontab** is a file which contains the schedule of cron entries to be run and at specified times. 
**crontab** là một file chứa đựng bảng biểu (schedule) của các entries được chạy.

>**cron job**, **cron task** or **cron schedule** is a specific set of execution instructions specifing day, time and command to execute.
**cron job**, **cron task** hoặc **cron schedule** là các lệnh thực thi hành động đặt trước vào thời điểm nhất định.

## 2) Operation
A crontab is a text file. Each user has own crontab that locates in `/var/spool/cron`. The crontab file can't create or edit with any text editor directly, you have to use `crontab` command. 

Một crontab đơn giản là một text file. Mỗi người dùng có một crontab riêng, file này thường nằm ở `/var/spool/cron`. Crontab files không cho phép bạn tạo hoặc chỉnh sửa trực tiếp với bất kỳ trình text editor nào, trừ phi bạn dùng lệnh crontab.

Common command:
- `crontab -e`:    Edit crontab file, or create one if it doesn’t already exist.
- `crontab -l`:    crontab list of cronjobs , display crontab file contents.
- `crontab -r`:    Remove your crontab file.

Câu lệnh thường dùng:
- `crontab -e`: chỉnh sửa hoặc tạo mới crontab file khi không tồn tại
- `crontab -l`:  liệt kê các cronjob, hiển thị nội dung crontab
- `crontab -r`: xóa crontab file

## 3) Crontab file structure
Một crontab file có 5 trường xác định thời gian, cuối cùng là lệnh sẽ được chạy định kỳ, cấu trúc như sau:
```
# ┌───────────── minute (0 - 59)
# │ ┌───────────── hour (0 - 23)
# │ │ ┌───────────── day of the month (1 - 31)
# │ │ │ ┌───────────── month (1 - 12)
# │ │ │ │ ┌───────────── day of the week (0 - 6) (Sunday to Saturday;
# │ │ │ │ │                                   7 is also Sunday on some systems)
# │ │ │ │ │
# │ │ │ │ │
# * * * * * command to execute
```
[https://crontab.guru/](https://crontab.guru/)



```
crontab -l | sed '/DJANGO/s/^/#/' | crontab -
```
