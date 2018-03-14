# 5.Package manament 
| Command |Sample |Descrption |
|---------|-------|-----------|
|apt|apt list –installed |Hiển thị tất cả các program đã được install |
||apt-get install sinichi|Khi cài đặt một gói online máy sẽ kiểm tra|
|||trong /etc/apt/sources.list để tìm đến địa chỉ chứa package |
|||để download và cài đặt pakage và các package phụ thuộc|
||apt-get 	remove sinichi|Gỡ|
||apt-get update	package|Cập nhật các package available chưa được install |
||apt-get 	upgrade package|	Cập nhật các package lên phiên bản mới nhất|
|dpkg|dpkg --list|Hiển thị tất cả các program đã được install|
||dpkg --install sinion.deb|install offline|
||dpkg --remove sinth|gỡ|
