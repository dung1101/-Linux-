# 1.SELinux là gì 
SELinux (Security-Enhanced Linux) : là một tiện ích tạo ra các rule để khóa truy cập vào ứng dụng, file... Mục đích để tăng tính bảo mật cho hệ thống.
# 2.Các phương pháp điều khiển truy nhập
|Phương pháp|Mô tả|
|-----------|-----|
|DAC:discretionary access control|Các hệ thống dựa trên Unix dùng pp này.Phương pháp giới hạn truy cập vào các đối tượng dựa trên các nhóm mà chúng thuộc về.ơ chế điều khiển cồng kềnh này nảy sinh một vấn đề, vì một chương trình xâm nhập vào hệ thống sẽ thừa hưởng quyền truy cập của user thực thi chương trình. Do đó chương trình có thể làm mọi việc mà user đó được quyền.|
|MAC:mandatory access control|Phương pháp định nghĩa các chương trình chỉ có thể làm những gì chúng cần để thực hiện nhiệm vụ, ngoài ra không được làm gì khác. Ví dụ, nếu bạn có một chương trình đáp ứng các yêu cầu đến một socket mà không cần phải truy cập vào file system, thì chương trình đó chỉ được phép lắng nghe trên một socket cố định và không có quyền đụng đến file system.|
|RBAC:role-based access control|Trong cơ chế RBAC, permission được cung cấp dựa trên các vai trò (role) được gán bởi hệ thống bảo mật. Khái niệm của một role khác với khái niệm của một “group” truyền thống ở chỗ một group đại diện cho một hay nhiều user. Một role có thể đại diện cho nhiều user, nhưng nó cũng đại diện cho các permission mà một tập các user có thể thực hiện.|

SELinux bổ sung cả cơ chế MAC và RBAC cho hệ thống GNU/Linux. 
# 3.Các chế độ của SELinux
SELinux có hai thành phần chính trên hệ thống:
* kernel mechanism :cơ chế hạt nhân thi hành một loạt các quy tắc truy cập áp dụng cho các tiến trình và tệp tin. 
* file labels: mọi tệp trong hệ thống của bạn có thêm các nhãn gắn liền với nó, nó kết hợp với các quy tắc truy cập bên trên.
SELinux có hai trạng thái enable và disable.Khi disable chỉ duy nhất phương pháp MAC được sử dụng.KHi enable thì SELinux hoạt động ở 2 chế độ enforcing và permissive.<br>
Kiểm tra trạng thái:
```
~]$ sestatus
SELinux status:                 enabled
SELinuxfs mount:                /selinux
Current mode:                   enforcing
Mode from config file:          enforcing
Policy version:                 24
Policy from config file:        targeted
```
Kiểm tra riêng mode
```
~]$ getenforce
Enforcing
```
## enforcing
Mặc định SELinux sẽ chạy ở chế độ enforcing.Khi chạy ở chế độ này SELinux từ chối truy cập dựa trên các quy tắc chính sách SELinux.
## permissive
SELinux sẽ không từ chối truy cập nhưng sẽ ghi vào file log `/var/log/audit/audit.log` những hành động sẽ bị từ chối truy cập ở chế độ enforcing.

Có thể chuyển đổi giữa 2 chế độ này bằng câu lệnh:
```
#Chuyển sang chế độ enforcing
setenforce 1
#Chuyển sang chế độ permissive
setenforce 0
```
# 4.SELinux context
Các tiến trình và file được dán nhãn với một SELinux context chứa thêm các thông tin như :SELinux user, role, type, and, optionally, a level.Khi chạy SELinux,tất cả các thông tin đó được sử dụng để đưa ra quyết định điều khiển truy nhập.<br>
Sử dụng câu lệnh `ls -Z` để thấy được SElinux context:

# 5.Cách tắt SELinux:

# 6.Mối liên quan giữa 2 file selinux ở 2 thư mục khác nhau?

*Tài liệu tham khảo https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/security-enhanced_linux/
