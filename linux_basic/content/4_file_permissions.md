# 4.File permissons 
- File permissons thể hiện quyền của owner(u), group(g) và o(other) đối với 1 file/thư mục như là quyền đọc(r),ghi(w)và thực thi(x).
- Để xem quyền của sử dụng option -l của lệnh ls.``rwxrw-r--``đây thể hiện quyền: ``rwx`` đầu tiên thể hiện quyền của owner là đọc ghi và thực thi, ``rw-`` tiếp thieo thể hiện quyền của group sở hữu là đọc và ghi ,``r--`` cuối cùng là quyền của user khác.
- Ngoài cách thể hiện như trên còn có thể thay thế bằng số. ``764`` : 7 tương ứng thể hiện quyền của owner với 7 = 4(r) + 2(w) + 1(x) tương tự với các số sau

| Command |Sample| Descrption|
|---------|------|-----------|
|chown|chown dung1 file1|Chuyển quyền sở hữu của |
|chgrp|chgrp group1 filex|Chuyển quyền sở hưu của group|
|chmod|chmod r--r--r-- filef|thay đổi quyền|
||chmod 777 filec|thay đổi quyền|
||chmod u+x filex|owner thêm quyền thực thi|
