# 2.Working with file 
Khi các lệnh được thực hiện, mặc định có ba luồng file hoặc mô tả để sử dụng:
* standard input (stdin):thông thường là bàn phím hoặc có thể là output của một câu lệnh
* standard output (stdout):thường được in ra terminal cũng có thể là 1 file
* standard error (stderr):giống như stdout

| Command |Sample|Descrption |
|---------|------|-----------|
|<||	đọc file |
|>|ls /etc > file1|In kết quả câu lệnh ra file và ghi đè từ đầu|
|>>|ls /etc>> file2|In kết quả câu lệnh ra file và ghi tiếp|
|2>|ls /etc/sdf 2> file3|in lỗi ra file|
|&>|ls /etc/afc &> file4| in cả lỗi và kết quả câu lệnh|
| \| | cat file5 \| grep etc|Sử dụng 2 câu lệnh kết quả câu lệnh thứ nhất là đầu vào cho câu lệnh thứ 2|
|find|find /etc conkien	|Tìm kiếm file hoặc thư mục có chứa thông tin cần tìm trên thư mục|
|locate|locate caikim|Tìm kiếm kiếm đường dẫn trong một cơ sở dữ liệu tại /var/lib/mlocate/mlocate.db |
|||dữ liệu được up date tự động bằng updatedb.Do đó tốc độ sẽ nhanh hơn find |
|||tuy nhiên kết quả còn phụ thuộc vào dữ liệu đã được update hay chưa|
|cat|cat filex|in dữ liệu từ file ra console| 
|tac|tac xelif|Tương tự cat nhưng in ngược|
|less|less filed|Đọc dữ liệu theo trang|
|more|more filev|Đọc dữ liệu theo trang|
|tail|tail	filet|Chọn hiển thị n dòng cuối mặc định không |
|head|head fileh|Chọn hiên thị n dòng đầu|
|touch|touch co.txt|Tạo file|
|mkdir|mkdir convoi|	Tạo thư mục|
|diff	|diff file1 file2|So sánh 2 file/folder|
|file	|file concua.py|in kiểu dữ liệu trong file|
