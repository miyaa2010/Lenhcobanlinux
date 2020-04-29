# Lệnh Cơ Bản Trong Linux (CLI)
Tổng hợp các lệnh cơ bản trong Linux
1. Lệnh tar
Tạo tar archive mới.

$ tar cvf archive_name.tar dirname/

Xuất từ tar archive đã có.

$ tar xvf archive_name.tar

Xem tar archive đã có.

$ tar tvf archive_name.tar

2. Lệnh grep

Tìm một string trong file (không phân biệt chữ hoa và chữ thường)

$ grep -i "the" demo_file

In dòng có kết quả trùng khớp, kèm theo 3 dòng dưới đó.

$ grep -A 3 -i "example" demo_text

Tìm kiếm đệ quy string trong tất cả file

$ grep -r "ramesh" *

3. Lệnh find

Tìm file theo tên (không phân biệt chữ hoa và chữ thường)

# find -iname "MyCProgram.c"

Thực thi lệnh lên file tìm được

$ find -iname "MyCProgram.c" -exec md5sum {} \;

Tìm tất cả file rỗng trong thư mục home

# find ~ -empty

4. Lệnh ssh

Login vào remote host

ssh -l jsmith remotehost.example.com

Debug ssh client

ssh -v -l jsmith remotehost.example.com

Hiển thị phiên bản ssh

$ ssh -V

OpenSSH_3.9p1, OpenSSL 0.9.7a Feb 19 2003

5. Lệnh sed

Khi bạn copy file DOS vào Unix, bạn có thể tìm \r\n ở cuối mỗi dòng. Ví dụ sau chuyển đổi format file DOS sang format file Unix với lệnh sed.

$sed 's/.$//' filename

In nội dung file theo thứ tự đỏ ngược

$ sed -n '1!G;h;$p' thegeekstuff.txt

Thêm số dòng vào tất cả dòng (không trống) trong file

$ sed '/./=' thegeekstuff.txt | sed 'N; s/\n/ /'

6. Lệnh awk

Loại bỏ dòng trùng lặp với awk

$ awk '!($0 in array) { array[$0]; print }' temp

In tất cả dòng từ /etc/passwd có cùng uid và gid

$awk -F ':' '$3==$4' passwd.txt

Chỉ in trường cụ thể từ file

$ awk '{print $2,$5;}' employee.txt

7. Lệnh vim

Nhảy đến dòng 143 của file

$ vim +143 filename.txt

Nhảy đến kết quả trùng khớp đầu tiên tìm được

$ vim +/search-term filename.txt

Mở file ở chế độ read only

$ vim -R /etc/passwd

Lệnh diff
Bỏ qua khoảng trắng khi so sánh

# diff -w name_list.txt name_list_new.txt

2c2,3

< John Doe --- > John M Doe

> Jason Bourne

Lệnh sort
Xếp file theo thứ tự tăng dần (ascending)

$ sort names.txt

Xếp file theo thứ tự giảm dần (descending)

$ sort -r names.txt

Xếp file passwd theo trường thứ 3

$ sort -t: -k 3n /etc/passwd | more

10. Lệnh export

Để xem biến môi trường liên quan đến oracle

$ export | grep ORACLE
declare -x ORACLE_BASE="/u01/app/oracle"
declare -x ORACLE_HOME="/u01/app/oracle/product/10.2.0"
declare -x ORACLE_SID="med"
declare -x ORACLE_TERM="xterm"

Xuất biến môi trường:

$ export ORACLE_HOME=/u01/app/oracle/product/10.2.0

11. Lệnh xargs

Chép tất cả hình ảnh sang ổ cứng ngoài

# ls *.jpg | xargs -n1 -i cp {} /external-hard-drive/directory

Tìm kiếm tất cả hình ảnh jpg trong hệ thống và lưu trữ vào archive

# find / -name *.jpg -type f -print | xargs tar -cvzf images.tar.gz

Tải tất cả URLs được nhắc đến trong file url-list.txt:

# cat url-list.txt | xargs wget –c

12. Lệnh ls

Hiển thị filesize ở dạng đọc được (như KB, MB,…)

$ ls -lh
-rw-r----- 1 ramesh team-dev 8.9M Jun 12 15:27 arch-linux.txt.gz

Order Files Based on Last Modified Time (In Reverse Order) Using ls -ltr

$ ls -ltr

Phân loại File có ký tự đặc biệt bằng ls -F

$ ls -F

13. Lệnh pwd

Lệnh in các thư mục đang làm việc pwd có lẻ đã quá đỗi quen thuộc.

14. Lệnh cd

Dùng cd- để chuyển giữa hai thư mục gần nhất

Dùng shopt -s cdspell để tự động sửa tên thư mục gõ nhầm trên cd

15. Lệnh gzip

Tạo file nén *.gz

$ gzip test.txt

Giải nén file *.gz

$ gzip -d test.txt.gz

Hiển thị tỷ lệ nén của file đã nén bằng gzip -l

$ gzip -l *.gz

Tỷ lệ nén/chưa nén uncompressed_name

23709 97975 75.8% asp-patch-rpms.txt

16. Lệnh bzip2

 

Tạo file nén *.bz2

$ bzip2 test.txt

Giải nén file *.bz2

bzip2 -d test.txt.bz2

17. Lệnh upzip

 

Giải nén file *.zip

$ unzip test.zip

Xem nội dung file *.zip (mà không cần giải nén):

$ unzip -l jasper.zip
Archive: jasper.zip
Length Date Time Name
-------- ---- ---- ----
40995 11-30-98 23:50 META-INF/MANIFEST.MF
32169 08-25-98 21:07 classes_
15964 08-25-98 21:07 classes_names
10542 08-25-98 21:07 classes_ncomp

18. Lệnh shutdown

 

Shutdown hệ thống và tắt nguồn ngay

# shutdown -h now

Shutdown hệ thống sau 10 phút

# shutdown -h +10

Reboot hệ thống bằng lệnh shutdown

# shutdown -r now

Bắt buộc kiểm tra filesystem trong khi reboot

# shutdown -Fr now

19. Lệnh ftp

 

Cả ftp và secure ftp (sftp) đề gồm các lệnh giống nhau, để kết nối đến remote server và tải nhiều file, nhập lệnh

$ ftp IP/hostname
ftp> mget *.html

Để xem tên file nằm trên remote server trước khi download, dùng lệnh mls ftp theo như bên dưới

ftp> mls *.html -
/ftptest/features.html
/ftptest/index.html
/ftptest/othertools.html
/ftptest/samplereport.html
/ftptest/usage.html

20. Lệnh crontab

 

Xem crontab entry cho người dùng cụ thể

# crontab -u john -l

Lên lịch cron job mỗi 10 phút

*/10 * * * * /home/ramesh/check-disk-space

21. Lệnh service

 

Lệnh service được sử dụng để chạy system V init scripts, như: thay vì call scripts nằm trong thư mục /etc/init.d/ bằng đường dẫn hoàn chỉnh, bạn có thể sử dụng lệnh service.

Kiểm tra trạng thái service

# service ssh status

Kiểm tra trạng thái tất cả service

service --status-all

22. Lệnh ps

Lệnh ps được sử dụng để hiển thị thông tin về các process đang chạy trên hệ thống.

Có rất nhiều đối số (argument) có thể chuyển vào lệnh ps, sau đây là một số lệnh cơ bản.

$ ps -ef | more

Để theo dõi các process đang chạy trong cấu trúc cây

$ ps -efH | more

23. Lệnh ps

Lệnh này được sử dụng để hiển thị memory trống/đã sử dụng đang có trong hệ thống.

Output lệnh trống thông thường. Output được hiển thị theo byte.

$ free
total used free shared buffers cached
Mem: 3566408 1580220 1986188 0 203988 902960
-/+ buffers/cache: 473272 3093136
Swap: 4000176 0 4000176

Nếu bạn muốn nhanh chóng kiểm tra số GB RAM của hệ thống, hãy dùng tùy chọn -g. Tùy chọn -b hiển thị byte, -k hiển thị theo kilo byte, -m hiển thị theo mega byte.

$ free -g
total used free shared buffers cached
Mem: 3 1 1 0 0 0
-/+ buffers/cache: 0 2
Swap: 3 0 3

Nếu bạn muốn xem tổng bộ nhớ (kể cả swap), hãy dùng -t switch, cho ra kết quả như dưới

ramesh@ramesh-laptop:~$ free -t
total used free shared buffers cached
Mem: 3566408 1592148 1974260 0 204260 912556
-/+ buffers/cache: 475332 3091076
Swap: 4000176 0 4000176
Total: 7566584 1592148 5974436

24. Lệnh top

Lệnh top hiển thị các process đứng đầu hệ thống (mặc định đánh giá theo mức sử dụng CPU). Để xếp output đứng đầu theo bất cứ cột nào, nhấn O (chữ O) để hiển thị tất cả cột (khả thi) mà bạn có thể sắp xếp được

Current Sort Field: P for window 1:Def

Lựa chọn trường sắp xếp (sort) thông qua ký tự của trường đó, gõ phím bất kỳ để quay lại

a: PID = Process Id v: nDRT = Dirty Pages count
d: UID = User Id y: WCHAN = Sleeping in Function
e: USER = User Name z: Flags = Task Flags
........

Để chỉ hiển thị các process thuộc về user cụ thể, hãy dùng tùy chọn -u. Đoạn lệnh sau sẽ chỉ hiển thị các process đứng đầu thuộc về người dùng oracle

$ top -u oracle

25. Lệnh df

Hiển thị dung lượng do file system sử dụng. Theo mặc định, df -k hiển thị output theo byte.

$ df -k
Filesystem 1K-blocks Used Available Use% Mounted on
/dev/sda1 29530400 3233104 24797232 12% /
/dev/sda2 120367992 50171596 64082060 44% /home

df -h hiển thị output theo dạng dễ đọc, ví dụ như theo GB.

ramesh@ramesh-laptop:~$ df -h
Filesystem Size Used Avail Use% Mounted on
/dev/sda1 29G 3.1G 24G 12% /
/dev/sda2 115G 48G 62G 44% /home

Dùng tùy chọn -T để hiển thị kiểu file system

ramesh@ramesh-laptop:~$ df -T
Filesystem Type 1K-blocks Used Available Use% Mounted on
/dev/sda1 ext4 29530400 3233120 24797216 12% /
/dev/sda2 ext4 120367992 50171596 64082060 44% /home

26. Lệnh kill

Dùng lệnh kill để xác định process. Trước hết, dùng lệnh ps -ef để nhận process id, sau đó sử dụng kill -9 để kill các Linux process đang chạy như bên dưới. Bạn cũng có thể dùng killall, xkill để xác định unix process.

$ ps -ef | grep vim
ramesh 7243 7222 9 22:43 pts/2 00:00:00 vim

$ kill -9 7243

27. Lệnh rm

Xác nhận trước khi xóa file

$ rm -i filename.txt

Lệnh này rất hữu ích khi chuyển giao shell metacharacters trong name argument.

In filename và nhận xác nhận trước khi xóa bỏ file.

$ rm -i file*

Ví dụ sau xóa (kiểu đệ quy) tất cả file và thư mục trong thư mục example. Lệnh này xóa chính thư mục example.

$ rm -r example

28. Lệnh cp

Sao chép file1 sang file2 giữ nguyên mode, ownership, và timestamp.

$ cp -p file1 file2

Sao chép file1 và sang file2. Nếu file2 đã tồn tại, cần xác nhận trước khi overwrite

$ cp -i file1 file2

29. Lệnh mv

Đổi tên file1 thành file2. Nếu file2 đã tồn tại, cần xác nhận trước khi overwrite

$ mv -i file1 file2

Lưu ý: mv -f thì ngược lại, overwrite file 2 ngay mà không yêu cầu xác nhận.

mv -v sẽ in tất cả sự kiện trong quá trình rename file, thường rất hữu ích khi chỉ định shell metacharacters trong file name argument.

$ mv -v file1 file2

30. Lệnh cat

Bạn có thể cùng lúc xem nhiều file. Câu lẹnh ví dụ sau sẽ in nội dung của file1 kèm với file2 đến stdout

$ cat file1 file2

Khi hiển thị file, lệnh cat -n sau sẽ thêm số dòng vào trước mỗi dòng output.

$ cat -n /etc/logrotate.conf
1 /var/log/btmp {
2 missingok
3 monthly
4 create 0660 root utmp
5 rotate 1
6 }

31. Lệnh mount

Để mount file system, trước hết bạn nên tạo thư mục và mount như bên dưới

# mkdir /u01

# mount /dev/sdb1 /u01

Bạn cũng có thể thêm đoạn sau vào fstab để mount tự động (như mỗi khi hệ thống khởi động lại, file system sẽ được mount)

/dev/sdb1 /u01 ext2 defaults 0 2

32. Lệnh chmod

Lệnh chmod được dùng để thay đổi permission cho một file hoặc thư mục

Trao truy cập toàn quyền (đọc, việt thực thi) file nhất định cho user và group

$ chmod ug+rwx file.txt

Thu hồi tất cả quyền truy cập file nhất định của group

$ chmod g-rwx file.txt

Áp dụng (đệ quy) permisson cho mọi file trong thư mục con

$ chmod -R ug+rwx file.txt

33. Lệnh chown

Lệnh chown được sử dụng để thay đổi owner và nhóm file.

Để thay đổi onwer sang oracle và group sang db trên file. Như thay đổi cả owner và group cùng lúc

$ chown oracle:dba dbora.sh

Sử dụng -R để thay đổi (đẹ quy) ownership

$ chown -R oracle:dba /home/oracle

34. Lệnh passwd

Thay đổi password từ dòng lệnh bằng passwd. Lệnh này sẽ yêu cầu password cũ, theo sau là password mới.

$ passwd

Super user có thể dùng lệnh passwd để reset các password khác. Lệnh này sẽ không yêu cầu password hiện nay của user

# passwd USERNAME

Xóa password của một user. Root user có thể vô hiệu hóa password cho user đó. Khi password đã được vô hiệu hóa, user có thể login mà không cần nhập password.

# passwd -d USERNAME

35. Lệnh mkdir

Ví dụ sau sẽ tạo thư mục có tên temp ngay trong thư mục home

$ mkdir ~/temp

Tạo thư nhiểu thư mục lồng vào nhau bằng một lệnh mkdir duy nhất. Nếu có bất cứ thư mục nào đã tồn tại, vẫn sẽ không có lỗi. Nếu không tồn tại, máy sẽ tạo mới.

$ mkdir -p dir1/dir2/dir3/dir4/

36. Lệnh ifconfig

Dùng lệnh ifconfig để xem hoặc tinh chỉnh giao diện network trên hệ thống Linux.

Xem tất cả giao diện cùng với trạng thái.

$ ifconfig -a

Bắt đầu hoặc ngưng giao diện nhất định bằng lệnh up và down như dưới đây

$ ifconfig eth0 up

$ ifconfig eth0 down

37. Lệnh uname

Lệnh command hiển thị các thông tin quan trọng về hệ thống như Kernel name, Host name, Kernel release number, Processor type,…

Output mẫu từ laptop Ubuntu được hiển thị dưới đây

$ uname -a
Linux john-laptop 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 i686 GNU/Linux

38. Lệnh whereis

Khi muốn xem liệu một lệnh Unix tồn tại ở đâu, bạn có thể thực thi lệnh sau

$ whereis ls
ls: /bin/ls /usr/share/man/man1/ls.1.gz /usr/share/man/man1p/ls.1p.gz

Khi muốn tìm kiếm executable (thực thi được) từ một đường dẫn chứ không phải từ tùy chọn whereis mặc định, bạn có thể dùng tùy chọn -B và nhập vào đó đường dẫn dưới dạng argument. Lệnh này sẽ tình kiếm (và hiển thị nếu có thể) executable lsmk trong thư mục /tmp

$ whereis -u -B /tmp -f lsmk
lsmk: /tmp/lsmk

39. Lệnh whatis

Lệnh whatis hiển thị description về một lệnh nào đó

$ whatis ls

ls (1) – list directory contents

$ whatis ifconfig

ifconfig (8) – configure a network interface

40. Lệnh locate

Khi sử dụng lệnh command, bạn có thể nhanh chóng tìm kiếm vị trí của một (nhóm) file cụ thể. Lệnh locate sẽ sử dụng database do updatedb tạo ra.

Ví dụ bên dưới cho thấy tất cả file trong hệ thống có chứa từ crontab trong đó.

$ locate crontab
/etc/anacrontab
/etc/crontab
/usr/bin/crontab
/usr/share/doc/cron/examples/crontab2english.pl.gz
/usr/share/man/man1/crontab.1.gz
/usr/share/man/man5/anacrontab.5.gz
/usr/share/man/man5/crontab.5.gz
/usr/share/vim/vim72/syntax/crontab.vim

41. Lệnh man

Hiển thị man page của một lệnh cụ thể

$ man crontab

Khi man page của một lệnh nằm dưới (nhiều hơn) một section, bạn có thể xem man page cho lệnh đó từ một section cụ thể như bênh dưới

$ man SECTION-NUMBER commandname

8 section có trong man page

General commands
System calls
C library functions
Special files (usually devices, those found in /dev) and
drivers
File formats and conventions
Games and screensavers
Miscellaneous
System administration commands and daemons
Ví dụ như, khi bạn thực hiện whatis crontab, bạn sẽ nhận thấy rằng crontob có hai man page (section 1 và section 5). Để xem section  của crontab man page, hãy làm như sau

$ whatis crontab

crontab (1) – maintain file crontab cho người dùng cá nhân(V3)

crontab (5) – bảng cho driving cron

$ man 5 crontab

42. Ví dụ tail command

Mặc định in 10 dòng cuối của file

$ tail filename.txt

In N dòng của file tên filename.txt

$ tail -n N filename.txt

Xem nội dung của file theo thời gian thực bằng đuôi -f, rất hiệu quả khi xem file log đang mở rộng. Dùng CTRL-C để terminate lệnh này.

$ tail -f log-file

43. Lệnh less

Lệnh less, vì không load cả file, nên rất phù hợp với file log dung lượng lớn.

$ less huge-log-file.log

Khi mở file bằng lệnh less, bạn nên để ý hai tổ hợp phím tiện dụng sau

CTRL+F – forward one window
CTRL+B – backward one window

44. Lệnh su

Chuyển sang một user account khác bằng lệnh su. Người dùng su có thể chuyển đến bất cứ user nào mà không cần nhập password.

$ su - USERNAME

Thực thi một lệnh duy nhất từ một tên tài khoản khác. Trong ví dụ sau, John có thể thực thi lệnh ls dưới tên raj. Sau khi lệnh được thực thi, tài khoản John sẽ mặc định trở lại

[john@dev-server]$ su - raj -c 'ls'

[john@dev-server]$

Login vào user account cụ thể, và thực thi shell tùy ý, thay cho shell mặc định

$ su -s 'SHELLNAME' USERNAME

45. Lệnh mysql

mysql là database nguồn mở được sử dụng phổ biến nhất trên Linux. Để kết nối đếm remote mysql database, dùng lệnh dưới. Lệnh này sẽ yêu cầu password

$ mysql -u root -p -h 192.168.1.2

Để kết nối đến local mysql database

$ mysql -u root -p

Nếu bạn muốn định rõ mysql root password ngay từ trong dòng lệnh, hãy nhập ngay và luôn (không có dấu cách)

46. Lệnh yum

Để cài đặt apache bằng yum

$ yum install httpd

Để cập nhật apache bằng yum

$ yum update httpd

Để uninstall/remove apache bằng yum

$ yum remove httpd

47. Lệnh rpm

Để cài đặt apache bằng rpm

# rpm -ivh httpd-2.2.3-22.0.1.el5.i386.rpm

Để cập nhật apache bằng rpm

# rpm -uvh httpd-2.2.3-22.0.1.el5.i386.rpm

Để uninstall/remove apache bằng rpm

# rpm -ev httpd

48. Lệnh ping

Ping remote host chỉ với 5 packet

$ ping -c 5 gmail.com

49. Lệnh date

Cài đặt giờ hệ thống

# date -s "01/31/2010 23:59:53"

Khi đã thay đổi ngày hệ thống, bạn đã có thể đồng bộ hóa hardware clock với system date như dưới

# hwclock –systohc

# hwclock --systohc –utc

50. Lệnh wget

Phương thức tải phần mềm, nhạc và video từ ineternet nhanh gọn và hiện quả với lệnh wget

$ wget http://prdownloads.sourceforge.net/sourceforge/nagios/nagios-3.2.1.tar.gz

Tải và lưu trữ dưới tên khác

$ wget -O taglist.zip http://www.vim.org/scripts/download_script.php?src_id=7701
