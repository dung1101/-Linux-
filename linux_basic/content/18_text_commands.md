|Command|Sample |Descrption|
|-------|-------|----------|
|cat|cat filex|hiển thị nội dung file|
|echo|echo filex|giống cat|
|sed|sed -e "s/foo/bar/g" test.txt|thay đổi nội dung file thông qua câu lệnh|
|awk|awk "BEGIN { i=0 } { i++ } END { print i }" filename|giống sed|
|sort|sort filex|sắp xếp dòng theo thứ tự|
|uniq|uniq file.txt|xóa dòng bị trùng|
|paste|paste file1 file2|kết hợp các dòng từ nhưng file khác nhau|
|join|file2 file3|kết hợp các file có cột giống nhau|
|grep|grep hello|hiển thị nội dung chứa từ mong muốn|
|tr|tr|thay đổi hoặc xóa ký tự|
|tee|tee file|lấy kết quả một câu lệnh và lưu vào file giống như >|
|wc|wc -l filec.txt|đếm số lượng dòng ,từ hoặc ký tự|
|cut|cut -f filex.txt|cắt theo cột|
|head|head -20 filex|hiển thị n dòng đầu tiên|
|tail|tail -15 filex|hiển thị n dòng cuối|
