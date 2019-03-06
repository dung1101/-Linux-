# 3.File system 
## 3.1	File system
* Hệ điều hành Linux coi tất cả đều là các tệp tin (file) thậm chí cả các thiết bị cũng như ổ đĩa. Nó quản lý tất cả trên một hệ thống tệp tin duy nhất, bắt đầu ở gốc là một thư mục `root` và đây là thư mục ở mức cao nhất.
* Linux hỗ trợ các filesystem : ext3, ext4, btrfs, xfs(của linux) và vfat , ntfs, hfs(của các hệ điều hành khác).
## 3.2 Cấu trúc thư mục
ta có thể tìm hiểu cấu trúc thư mục bằng câu lệnh `man hier`


|Directory|	Usage|
|---------|------|
|`/`|Root: Đây là thư mục ở mức cao nhất.Tất cả các tệp tin và thư mục đều nằm trong thư mục này|
|`/bin`|User Binaries: Bao gồm các tập tin thực thi nhị phân. Những lệnh linux mà bạn thường sử dụng trong chế độ đơn người dùng được đặt trong thư mục này. Các lệnh được sử dụng bởi tất cả người dùng của hệ thống được đặt ở đây. Ví dụ: `ps`, `ls`, `ping`, `grep`, `cp` ...|
|`/sbin`|System Binaries: Cũng giống như `/bin`, `/sbin` cũng chứa các tập tin thực thi nhị phân. Tuy nhiên, các lệnh đặt trong thư mục này được sử dụng thường bởi người quản trị hệ thống, với mục đích bảo trì hệ thống. Ví dụ: iptables, reboot, fdisk, ifconfig, swapon …|
|`/boot`|Boot Loader:chứa các tệp tin khởi động và cả nhân kernel là vmlinuz|
|`/dev`|Device Files:chứa tệp tin đại diện cho các thiết bị như ổ đĩa, cổng COM v.v.. |
|`/etc`|Configuration Files:Chứa file cấu hình cho các chương trình hoạt động. Chúng thường là các tệp tin dạng text thường|
|`/home`|Home Directories:chứa thông tin, dữ liệu , cấu hình riêng cho từng user|
|`/lib`|System Libraries:Chứa các file library hỗ trợ cho các file thực binary. Tên của các file library thường là ld,lib hoặc so|
|`/lost+found`|Vì một lý do bất ngờ nào đó như lỗi phần mềm, mất điện v..v, hệ thống có thể đổ vỡ. Khi khởi động lại, hệ thống sẽ kiểm tra lại hệ thống filesystem bằng lệnh fchk và cố gắng phục hồi lại các lỗi mà nó tìm thấy. Kết quả của việc này sẽ được lưu giữ trong thư mục /lost+found.|
|`/media`|Removable Media Devices:Chứa thư mục dùng để mount cho các thiết bị removable. Ví dụ như USB,ổ cứng di động v.v..|
|`/mnt`|Mount Directory:Chứa các thư mục dùng để system admin thực hiện quá trình mount. Như đã nói, hệ điều hành Linux coi tất cả là các file và lưu giữ trên một cây chung. Đây chính nơi tạo ra các thư mục để ‘gắn’ các phân vùng ổ đĩa cứng cũng như các thiết bị khác vào. Sau khi được mount vào đây, các thiết bị hay ổ cứng được truy cập từ đây như là một thư mục|
|`/opt` |Optional add-on Applications:Chứa các phần mềm và phần mở rộng không nằm trong phần cài đặt mặc định, thường là của hãng thứ ba|
|`/proc`| Process Information|Chứa đựng thông tin về quá trình xử lý của hệ thống,thông tin về các process đang chạy ,thông tin tài nguyên hệ thống|
|`/tmp`|Temporary Files:chứa các file được tạo với mục đích dùng tạm thời bởi hệ thống cũng như user. Các file bên dưới thư mục này được xóa đi khi hệ thống reboot hay shutdown|
|`/usr`|User Programs:Chứa các file binary, library, tài liệu, source-code cho các chương trình nhiều người dùng|
|`/usr/bin`|chứa file binary cho các chương trình của user. Nếu như một user trong quá trình thực thi một lệnh ban đầu sẽ tìm kiếm trong /bin, nếu như không có thì sẽ tiếp tục nhìn vào /usr/bin|
|`/usr/sbin` |chứa các file binary cho system administrator. Nếu như ta không tìm thấy các file system binary bên dưới /sbin thì ta có thể tìm ở trong /usr/sbin|
|`/usr/lib`| chứa các file libraries cho /usr/bin và /usr/sbin|
|`/sbin`|System Binaries: Cũng giống như `/bin`, `/sbin` cũng chứa các tập tin thực thi nhị phân. Tuy nhiên, các lệnh đặt trong thư mục này được sử dụng thường bởi người quản trị hệ thống, với mục đích bảo trì hệ thống. Ví dụ: iptables, reboot, fdisk, ifconfig, swapon …|
|`/var`|Variable Files:Chứa đựng các file có sự thay đổi trong quá trình hoạt động của hệ điều hành cũng như các ứng dụng|
|| Nhật ký của hệ thống /var/log|
||database file /var/lib|
||email /var/mail|
||Các hàng đợi in ấn: /var/spool|
||lock file: /var/lock|
||Các file tạm thời cần cho quá trình reboot: /var/tmp|
||Dữ liệu cho trang web: /var/www|
