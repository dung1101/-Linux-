# Logrotate
[https://cuongquach.com/linux-tim-hieu-hoat-dong-va-cau-hinh-logrotate-tren-linux.html](https://cuongquach.com/linux-tim-hieu-hoat-dong-va-cau-hinh-logrotate-tren-linux.html)

```
/var/log/gunicorn/*.log {
    daily
    missingok
    notifempty
    dateext
    dateformat -%Y-%m-%d
    dateyesterday
    rotate 30   
    compress
    delaycompress
}
```
