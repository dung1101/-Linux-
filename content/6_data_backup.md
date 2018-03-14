# 6.Data back up
| Command|Sample| Descrption |
|--------|------|------------|
|rsync|rsync filec /home/ |Câu lênh copy giữ liệu như là câu lệnh cp nhưng có kiểm tra xem có|
|||thay đổi gì về nội dung hay là ngày tháng hay không.Nếu không sẽ chỉ cập nhật lại ngày tháng|
|dd|dd if=/dev/sda  of=/dev/sdb|	Copy disk if : input file of: output file |
||dd if=/dev/sda of=sda.mbr bs=512 count=1||
||dd if=/dev/sda  of=./bu.img|	Tao boot disk|
|tar|tar-cvf folderx|Tạo file tar|
||tar-xvf	foldex.tar|Giải nén file tar|
||tar-zcvf	folderx|Tạo file nen tar.gz|
||	tar-zxvf	folderx.tar.gz|Giải nén|
||	tar-jcvf	folderc|Tọa file nén tar.bz2|
||	tar-jxvf	folderc.tar.bz2|Giải nén|
|zip|zip folder	|Tạo file nen .zip|
|unzip|unzip folder.zip	|Giải nén |
