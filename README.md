# Những điều cần biết cho sysadmin!

## MỤC LỤC  
[I. Introduction](#introduction)

[II. Working with file](#workingwithfile)  

[III. Redirect](#redirect)  

[IV. File System](#filesystem)  
- [1. Layout](#layout)
- [2. Tùy chọn file system](#tuychonfilesystem)
- [3. Làm việc với disk, format, mount file, fstab](#lamviec)
- [4. Inode, symlink, hardlink](#inode)  

[V. Package Management](#packagemanagement)  

[VI. Boot process](#bootprocess)
- [1. Power Supply Unit](#power)
- [2. BIOS and CMOS](#biosandcmos)
- [3. POST tests](#posttests)
- [4. Reading the Partition Table](#reading)
- [5. The Bootloader](#thebootloader)
- [6. The Kernel and the Ramdisk](#thekernel)
- [7. OS Kernel and Init](#oskernelandinit)
- [8. Runlevels](#runlevels)
- [9. Getty](#getty)  

[VII. Tools](#tools)
- [1. Tunnel all traffic](#tunnelalltraffic)
- [2. Reverse Tunneling](#reversetunneling)
- [3. Tunneling stdin and stdout](#tunnelingstdin)  

[VII. Networking](#Networking)
- [1. Mô hình OSI, TCP/IP](#mohinhositcpip)
- [2. TCP/UDP](#tcpudp)
- [3. Subnetting, netmasks and CIDR](#subnetting)
- [4. Private address (IPv4 shared address space)](#privareaddress)
- [5. Cable (Copper, Fiber)](#cable)
- [6. Fiber (Multi mode, Single mode, Optical Connector, Transceivers](#fiber)
- [7. Route, NAT, VLAN, Static route, Dynamic routing, GRE, VPN](#route)  


============================================

<a name="introduction"></a>
# I. Introduction

**System Admin** **(Sysadmin)** **chịu trách nhiệm thiết lập và bảo trì hệ thống máy tính. Họ đảm bảo rằng các máy tính trong mạng của công ty, đặc biệt là máy chủ vận hành trơn tru và an toàn.**  

Vai trò của một `System Admin (Sysadmin)` chủ yếu tập trung vào 
vận hành hệ thống công nghệ thông tin, ngăn chặn sự cố 
và cải thiện hiệu năng của toàn hệ thống. 
Họ giúp hệ thống mạng của công ty được an toàn và hoạt động hiệu quả.
```  
Công việc của System Admin gồm có:  

- Cấu hình và bảo trì hệ thống mạng máy tính, bao gồm phần cứng, phần mềm hệ thống và ứng dụng.
- Đảm bảo dữ liệu được lưu trữ an toàn và sao lưu thường xuyên.
- Chẩn đoán và giải quyết các vấn đề phát sinh về phần cứng, phần mềm, mạng và hệ thống.
- Thay thế và nâng cấp các thành phần, thiết bị bị lỗi hoặc lỗi thời khi cần thiết.
- Giám sát hiệu suất hệ thống để đảm bảo mọi thứ chạy trơn tru và an toàn.
- Nghiên cứu và đề xuất các phương pháp mới để cải thiện hệ thống mạng máy tính.
- Cung cấp hỗ trợ kỹ thuật khi được yêu cầu.
- Nghiên cứu, đề xuất quy trình tiêu chuẩn để nhân viên tuân thủ từ đó hạn chế sai sót hoặc lỗi cho hệ thống máy tính, hệ thống mạng.
```

<a name="workingwithfile"></a>
# II. Working with file

- **Lệnh ls - list**  
`ls` liệt kê nội dung (file và thư mục) trong thư mục hiện hành. Nó cũng tương tự với việc bạn mở một thư mục và xem nội dung trong đó trên giao diện người dùng.
<img src=https://i.imgur.com/xiKWnGw.png>

- **Lệnh cat - concatenate and print files**  
`cat` đọc và in ra nội dung của file ra màn hình.
<img src=https://i.imgur.com/czm6KtM.png>

- **Lệnh more**  
`more` dùng mở một tệp để đọc tương tác, cho phép di chuyển lên xuống và tìm kiếm.  
```
Dưới đây là một số tùy chọn điển hình của lệnh #more :  
    -num: Chỉ định kích thước màn hình (số dòng).
    -d: more sẽ hiện lên thông báo "[Press space to continue, 'q' to quit.]" và hiển thị "[Press 'h' for instructions.]" thay vì tiếng chuông reo khi nhấn sai ký tự.
    -l: more luôn luôn xử lý ^L (ký tự nạp giấy) như là ký tự đặc biệt, và dừng lại sau dòng có ký tự này.
    -f: Khiến more đếm một cách logic, thay vì tính theo dòng hiển thị (ví dụ dòng dài không được bẻ dòng).
    -p: Không cuộn, thay vào đó xóa màn hình và hiển thị trang kế.
    -c: Không cuộn, thay vào đó khi kéo màn hình từ trễn xuống, sẽ xóa phần còn lại của mỗi dòng khi nó được hiển thị.
```
<img src=https://i.imgur.com/tdk6f2v.png>

- **Lệnh tail - print TAIL**  
`tail` dùng để xem những dòng đầu của tệp tin (theo mặc định là 10 dòng). Lệnh tail rất hữu ích khi khắc phục sự cố tệp nhật ký.
```
tail [tùy chọn] [tên file]

Tùy chọn có thể là:
    -n, --lines=[-]n: In số dòng n cuối cùng của mỗi tệp
    -n, --lines=[+]n: In tất cả các dòng từ n về sau
    -c, --byte=[-]n: In số byte n đầu cuối cùng mỗi tệp
    -q: Không in tiêu đề đầu ra
    -f: Tiếp tục đọc tập tin cho đến khi CTRL + C
    --help: Hiển thị các trợ giúp
    --version: Thông tin về phiên bản và thoát
```
<img src=https://i.imgur.com/4ZH4RwB.png>

- **Lệnh head - print HEAD**  
`head` dùng để xem những dòng đầu của tệp tin (theo mặc định là 10 dòng đầu tiên).
```
head [tuỳ chọn] [tên file]

Trong đó tùy chọn có thể là:
    -n, --lines=[-]n: In số dòng n đầu tiên của mỗi tệp
    -c, --byte=[-]n: In số byte n đầu tiên của mỗi tệp
    -q: Không in tiêu đề xác định tên tệp
    -v: Luôn in tiêu đề xác định tên tệp
    --help: Hiển thị các trợ giúp
    --version: Thông tin về phiên bản và thoát
```

- **Ứng dụng vi/vim**  
Vi Editor là trình soạn thảo văn bản ban đầu được tạo ra cho hệ điều hành Unix/Linux. Ngoài ra có một phiên bản mở rộng của Vi Editor là Vim Editor với nhiều chức năng hơn.  
Để cài đặt bộ soạn thảo **vi/vim** trên Ubuntu:  
`sudo apt-get install vim`  
Bộ soạn thảo **vi/vim** chạy ở hai chế độ khác nhau:  

- Chế độ dòng lệnh **command mode**, những gì được gõ vào sẽ được hiểu như là lệnh của vi. Vi có rất nhiều lệnh như: tìm kiếm, thay thế, xóa, lưu tâp tin…
- Chế độ nhập văn bản **insert mode**, những gì được gõ vào được hiểu là nội dung của tập tin đang soạn thảo.

Khi bắt đầu sử dụng lệnh **vi**, **vi** mặc định ở **command mode**. Ấn phím lệnh **i, a, o** hoặc **Inserrt** từ chế độ **command mode** để chuyển sang **insert mode**. Ấn **Esc** để chuyển đổi qua lại từ command mode với insert mode.  
Một số lệnh với **vi**:

- **:set nu** hiển thị số dòng
- **:set nonu** bỏ hiển thị số dòng
- Sử dụng **phím mũi tên** hoặc các phím **h,l,j,k** để dịch trái, phải, lên, xuống
- **:1** để nhảy đến dòng đầu tiên của file
- **:n** nhảy đến dòng n
- **$** nhảy xuống cuối dòng
- **:$** nhảy đến dòng cuối của file.
- **0** nhảy về đầu dòng
- **:0** nhảy về dòng đầu tiên của file.
- **dd** xóa một dòng hiện tại
- **ndd** xóa n dòng
- **/** hay **?** để tìm kiếm
- **:w!** lưu tập tin
- **:x!** lưu tập tin và thoát
- **:wq** lưu tập tin và thoát
- **:q!** không lưu và thoát

<a name="redirect"></a>
# III. Redirect

Trước khi đi vào các lệnh chúng ta đều biết rằng, chương trình đều sinh ra output. Output thì thường bao gồm 2 phần, output mong muốn của một chương trình, và các error messages.  
Một chương trình chạy trên Linux sẽ gửi đầu ra vào một file đặc biệt là **stdout** (standard output) và error messages đến **stderr** (standard error). Hai file này được link đến màn hình và không được save lại trong file.  
Thêm vào đó, các chương trình thường lấy đầu vào từ **stdin** (standard input) được đính kèm với bàn phím.  
I/O rediretion cho phép chúng ta thay đổi nơi output ra và nơi input đến.

## Redirect standard output  
Để redirect output của một lệnh hay một chương trình ra một file khác **stdout**, chúng ta sử dụng ký hiệu `> [tên file]`. Dưới đây là cách để redirect output của lệnh ls ra một file tên là `list.txt` :  
<img src=https://i.imgur.com/oXbgs7y.png>
Chúng ta sẽ thấy lệnh `ls` ở trên không in kết quả vì kết quả đã được redirect đến `list.txt` rồi.  

## Redirect standard error  

Chúng ta đã biết 3 loại file stream là **stdin, stdout, stderr**.
Shell tham chiếu chúng tương ứng với 3 file descriptor là `0, 1, 2`.
Shell cho phép chúng ta định nghĩa I/O redirecion bằng cách sử dụng `file descriptor number`.  

Để redirect error chúng ta file sử dụng `file descriptor number` tương ứng là 2:  
<img src=https://i.imgur.com/rbUJFf6.png>
Như vậy chúng ta đã không thấy thông báo output error hiển thị trên màn hình nữa mà nó đã được đưa vào trong file `error.txt`.

## Redirect output & error ra cùng một file

Chúng ta có thể sử dụng cách sau để redirect cả error và output ra cùng một file:  
`> [tên file] 2>&1`  
Theo cách này, ta sẽ redirect **stdout** ra một file sau đó redirect **stderr** ra **stdout** (lưu ý đúng thứ tự trên nếu không sẽ không chính xác).  

## Redirect standard input

Khi chúng ta sử dụng lệnh `cat` mà không có tham số truyền vào, nó sẽ nhận nội dung mà ta nhập từ bàn phím và sau đó in chúng ra màn hình.  
Do đó nếu chúng ta redirect đầu vào từ bàn phím thành 1 file, kết quả như sau:  
<img src=https://i.imgur.com/2BxF2dN.png>
Sau khi tạo file `input.txt` và nhập vào file này bằng Vi một dòng chữ **Viet Nam** sau đó dùng lệnh `cat` với input đầu vào là file này, chúng ta sẽ có kết quả là dòng chữ **Viet Nam** trên màn hình.  

<a name="filesystem"></a>
# IV. File System

<a name=layout></a>
## 1. Layout  

**File system** là các phương pháp và các cấu trúc dữ liệu mà một hệ điều hành sử dụng để theo dõi các tập tin trên ổ đĩa hoặc phân vùng. Có thể tạm dịch **file system** là hệ thống tập tin. Đó là cách các tập tin được tổ chức trên ổ đĩa.  
Nếu như một người dùng đã sử dụng quen trên môi trường Window, thì khi chuyển sang môi trường Linux sẽ phân vân và khó hiểu về cấu trúc file system của nó. Hình bên dưới cung cấp cho ta cái nhìn tổng quan:  
<img src=https://i.imgur.com/nDILK6H.png>

Hệ điều hành Linux hình thành từ nhiều thư mục và tập tin khác nhau. Các thư mục có thể lập thành nhiều file system khác nhau, tùy vào cách cài đặt bạn đã chọn. Nhìn chung, đa phần hệ điều hành nằm ở hai file system: **root file system** (file system gốc) được ký hiệu là /, và một file system khác được kết nối theo **/usr** (đọc là user).  
Thư mục **/bin** chứa các chương trình thi hành được, còn gọi là các binaries (nhị phân). Chúng là chương trình hệ thống chủ yếu. Nhiều lệnh của Linux, chẳng hạn như `ls`, là các chương trình nằm tại các thư mục ấy.  

Thư mục **/sbin** chứa các file nhị phân hệ thống. Hầu hết các tập tin ở đây dùng để quản trị hệ thống. (superuser-bin).  

Thư mục **/etc** rất quan trọng vì chứa nhiều file cấu hình Linux. File mật khẩu passwd nằm ở thư mục này, cũng như fstab , danh sách các file system cần nạp vào khi khởi động máy. Ngoài ra thư mục còn chứa các script khởi động cho Linux, danh sách các host kèm địa chỉ IP, cùng với nhiều thông tin cấu hình khác.  

Các thư viện dùng chung được chứa trong thư mục **/lib**. Khi dùng chung thư viện, nhiều chương trình sẽ sử dụng lại cùng loại mã, hơn nữa khi được chứa cùng chỗ, thư viện sẽ giúp giảm thiểu kích cỡ chương trình ở khía cạnh thời gian chạy.  \

Thư mục **/dev** chứa các file đặc biệt gọi là device files (file thiết bị, được hệ thống sử dụng để chạy các phần cứng).  

Thư mục **/tmp** chứa các file tạm mà chương trình tạo ra trong khi chạy. Nếu bạn biết hệ thống máy mình có chương trình tạo ra nhiều file tạm với kích cỡ lớn, bạn nên tạo thư mục /tmp thành một file system riêng thay vì đặt nó vào file system gốc như là một thư mục bình thường. Bởi vì với đà chất chứa các file tạm ngày càng nhiều, file system gốc sẽ nhanh chóng bị đầy.  

Thư mục **/home** là thư mục cơ sở của các home directory cho các user. Quản trị viên thường đặt /home thành file system riêng rẽ nhằm tạo nhiều khoảng trống cho user sử dụng. Ngoài ra nếu hệ thống máy bạn có nhiều user, bạn nên chia thư mục /home thành nhiều file system khác nhau.  

Thư mục **/var** lưu các file có thể thay đổi kích thước theo thời gian. Nhiều file đăng nhập hệ thống (system log file) thường nằm trong thư mục này.  

<a name=tuychonfilesystem></a>
## 2. Tùy chọn file system  

### EXT4  
**Ext4** cũng giống như Ext3, lưu giữ được những ưu điểm và tính tương thích ngược với phiên bản trước đó. Như vậy, chúng ta có thể dễ dàng kết hợp các phân vùng định dạng Ext2, Ext3 và Ext4 trong cùng 1 ổ đĩa trong Ubuntu để tăng hiệu suất hoạt động. Trên thực tế, Ext4 có thể giảm bớt hiện tượng phân mảnh dữ liệu trong ổ cứng, hỗ trợ các file và phân vùng có dung lượng lớn… Thích hợp với ổ SSD so với Ext3, tốc độ hoạt động nhanh hơn so với 2 phiên bản Ext trước đó, cũng khá phù hợp để hoạt động trên server, nhưng lại không bằng Ext3.  

### XFS
**XFS** được thiết kế lần đầu bởi Silicon Graphics để hoạt động như một hệ thống tập tin có journaling 64-bit. XFS cũng được thiết kế để duy trì hiệu năng cao với các file lớn và hệ thống tập tin.
Ngoài ra, hỗ trợ cho một số hệ thống tập tin bên ngoài hoạt động, để dễ dàng trao đổi các file với các hệ điều hành khác. Các hệ thống tập tin bên ngoài hoạt động giống như các chương trình gốc, ngoại trừ việc chúng thường thiếu một số tính năng UNIX thông thường hoặc có những hạn chế kì lạ khác.  

### BtrFS  
**BtrFS** – thường phát âm là Butter hoặc Better FS, hiện tại vẫn đang trong giai đoạn phát triển bởi Oracle và có nhiều tính năng giống với ReiserFS. Đại diện cho B-Tree File System, hỗ trợ tính năng pool trên ổ cứng, tạo và lưu trữ snapshot, nén dữ liệu ở mức độ cao, chống phân mảnh dữ liệu nhanh chóng... được thiết kế riêng biệt dành cho các doanh nghiệp có quy mô lớn.
Mặc dù BtrFS không hoạt động ổn định trên 1 số nền tảng distro nhất định, nhưng cuối cùng thì nó vẫn là sự thay thế mặc định của Ext4 và cung cấp chế độ chuyển đổi định dạng nhanh chóng từ Ext3/4. Do vậy, BtrFS rất phù hợp để hoạt động với server dựa vào hiệu suất làm việc cao, khả năng tạo snapshot nhanh chóng cũng như hỗ trợ nhiều tính năng đa dạng khác.
Bên cạnh đó, Oracle cũng đang cố gắng phát triển 1 nền tảng công nghệ nhằm thay thế cho NFS và CIFS gọi là CRFS với nhiều cải tiến đáng kể về mặt hiệu suất và tính năng hỗ trợ. Những cuộc kiểm tra trên thực tế đã chỉ ra BtrFS đứng sau Ext4 khi áp dụng với các thiết bị sử dụng bộ nhớ Flash như SSD, server database...  

### ZFS  
**ZFS** hiện tại vẫn đang trong giai đoạn phát triển bởi Oracle với nhiều tính năng tương tự như Btrfs và ReiserFS. Mới xuất hiện trong những năm gần đây vì có tin đồn rằng Apple sẽ dùng nó làm file hệ thống mặc định. Phụ thuộc vào thỏa thuận điều khoản sử dụng, Sun CDDL thì ZFS không tương thích với hệ thống nhân kernel của Linux, tuy nhiên vẫn hỗ trợ toàn bộ Linux’s Filesystem in Userspace – FUSE để có thể sử dụng được ZFS. Người sử dụng có thể gặp khó khăn khi cài đặt hệ điều hành Linux vì có yêu cầu FUSE và có thể không được hỗ trợ bởi distributor. 

<a name=lamviec></a>
## 3. Làm việc với disk, format, mount file, fstab  

Không giống như trong Windows, để có thể truy cập dữ liệu được lưu trữ trong USB, đĩa CD/DVD, file ISO, phân vùng ổ cứng, các tài nguyên được chia sẻ qua mạng (gọi chung là thiết bị)… trong Linux thì trước hết các thiết bị này các được gắn kết (**mount**) vào 1 thư mục trống (gọi là **mount point**) đã tồn tại sẵn trong cây thư mục. Và khi muốn tháo gỡ thiết bị đang hoạt động khỏi hệ thống thì bạn phải ngắt kết nối (**unmount**) giữa thiết bị với **mount point** trước. 2 công cụ: **mount** và **umount** giúp bạn thực hiện công việc gắn kết và tháo gỡ trên.  

### File fstab  
**fstab** là một tập tin cấu hình chứa các thông tin về các phân vùng trên ổ cứng cũng như các thiết bị lưu trữ khác trong máy tính của bạn. Tập tin này nằm trên thư mục **/etc**. **/etc/fstab** chứa các thông tin cần thiết để xác định xem một phân vùng hay thiết bị của bạn được mount như thế nào và mount vào đâu trong cấu trúc thư mục.Nếu như bạn không thể truy xuất các phân vùng của Windows (NTFS hoặc FAT32) từ Linux, không thể mount CD hoặc ghi file lên ổ mềm với quyền hạn user bình thường, hoặc gặp vấn đề với CD-RW của bạn, có lẽ bạn đã không cấu hình đúng file **/etc/fstab** rồi. Để có thể điều chỉnh fstab bạn cần có quyền root và dùng một chương trình xử lý văn bản như `vi` hoặc `gedit` để điều chỉnh.  

### Cách mount thiết bị  
Linux có khả năng tự nhận biết được các `filesystem` đang được kết nối với hệ thống. Tuy nhiên, để có thể sử dụng được các `filesystem` này, bắt buộc bạn phải làm một công việc gọi là **mount**.  
Bạn có thể sử dụng lệnh mount để mount filesystem, hoặc có thể **mount** tự động thông qua file cấu hình `/etc/fstab`.  
Một số điểm lưu ý khi thực hiện **mount**:  
- Những thiết bị không có mặt trong file /etc/fstab thì chỉ có root mới có thể mount được.
- Người dùng bình thường chỉ có thể mount được những thiết bị có trong file /etc/fstab và thiết bị này phải có tùy chọn user được bật lên.  
Khi mount, bạn cần chỉ định thiết bị cần mount và vị trí của mount point.  

Ví dụ để mount ổ CD bạn sử dụng lệnh :

`mount /dev/cdrom /media/cdrom`

Trong đó, **/dev/cdrom** là đường dẫn tới ổ CD-ROM cần mount và **/media/cdrom** là mount point.

Bây giờ, khi bạn truy cập tới thư mục **/media/cdrom** thì bạn mới thực sự truy cập được nội dung trong đĩa CD.  

### Các tùy chọn mount  

- **auto**: tự động mount thiết bị khi máy tính khởi động.
- **noauto**: không tự động mount, nếu muốn sử dụng thiết bị thì sau khi khởi động vào hệ thống bạn cần chạy lệnh mount.
- **user**: cho phép người dùng thông thường được quyền mount.
- **nouser**: chỉ có người dùng root mới có quyền mount.
- **exec**: cho phép chạy các file nhị phân (binary) trên thiết bị.
- **noexec**: không cho phép chạy các file binary trên thiết bị.
- **ro** **(read-only)**: chỉ cho phép quyền đọc trên thiết bị.
- **rw** **(read-write)**: cho phép quyền đọc/ghi trên thiết bị.
- **sync**: thao tác nhập xuất (I/O) trên filesystem được đồng bộ hóa.
- **async**: thao tác nhập xuất (I/O) trên filesystem diễn ra không đồng bộ.
- **defaults**: tương đương với tập các tùy chọn rw, suid, dev, exec, auto, nouser, async.

<a name=inode></a>
## 4. Inode, symlink, hardlink  

### Inode  

Muốn nắm rõ bản chất của hai khái niệm `symlink, hardlink` ta cần biết hệ điều hành quản lý file như thế nào. Lấy ví dụ một file chứa dữ liệu có tên là **filename**. Về phía người dùng ta có thể dễ dàng phân biệt với các file khác dựa vào tên **filename**, nhưng về phía hệ điều hành các file được phân biệt định danh bằng chỉ số `inode`. Mỗi một tên file có một chỉ số `inode` đi kèm, chỉ số `inode` tham chiếu đến một vùng bộ nhớ trong đó có chứa địa chỉ vùng bộ nhớ lưu trữ dữ liệu. File là vậy và các thư mục cũng được quản lý tương tự.  
```
Inode là một cấu trúc dữ liệu trong hệ thống tệp truyền thống của các họ Unix ví dụ như UFS hoặc EXT3. Inode lưu trữ thông tin về 1 tệp thông thường, thư mục, hay những đối tượng khác của hệ thống tệp tin.  
```
<img src=https://i.imgur.com/QN8ovMl.png>

Trong một `inode` có các metadata sau:

- Dung lượng file tính bằng bytes.
- Device ID : id của thiết bị lưu file.
- User ID : id chủ sở hữu của file.
- Group ID: id nhóm của chủ sở hữu file.
- File mode : gồm kiểu file và cách thức truy cập file.
- Timestamps: các mốc thời gian khi: bản thân inode bị thay đổi (ctime, inode change time), nội dung file thay đổi (mtime, modification time) và lần truy cập mới nhất (atime, access time).
- Link count : số lượng hard links trỏ đến inode. Các con trỏ chỉ đến các blocks trên ổ cứng dùng lưu nội dung file. Các con trỏ cho biết file nằm ở đâu để đọc nội dung.
- ...  

Có hai chú ý trong nội dung `inode`:
- Inode không chứa tên file, thư mục.
- Các con trỏ là thành phần quan trọng nhất: nó cho biết địa chỉ các block lưu nội dung file và tìm đến các block đó có thể truy cập được nội dung file.

### Hardlink  

Trong hình dưới đây ta có file nguồn tên là `filename`, có chỉ số inode là `inode`, địa chỉ bộ nhớ `addresses`, vùng lưu trữ dữ liệu là `data`. Khi tạo hard link có tên file `othername`, thì chỉ số đi kèm với nó sẽ chính là `inode` của `filename`.  
<img src=https://i.imgur.com/JTTiraZ.png>  
Lệnh tạo hardlink như sau:
```
ln [file nguồn] [file đích]
```
<img src=https://i.imgur.com/XSOoy2b.png>  
Ở ví dụ trên ta thấy khi tạo file `link.txt` và sau đó tạo hardlink là `hardlink.txt` thì 2 file này có chỉ số inode giống nhau, nên khi xóa file `link.txt` thì nội dung có trong file `hardlink.txt` vẫn còn.  
Khi sử dụng lệnh `rm` để xóa file thì làm giảm đi 1 `hardlink`. Khi số lượng `hardlink` giảm còn 0 thì không thể truy cập tới nội dung của file được nữa.  

### Symlink  

Khi tạo symbolic link với tên là `othername` thì hệ thống sẽ tạo ra một chỉ số inode khác tương ứng với tên file đó. `Inode` này sẽ tham chiếu đến một vùng nhớ khác chứa địa chỉ, địa chỉ này sẽ trỏ đến một vùng nhớ chứa dữ liệu lưu trữ đường dẫn đến file gốc `filename`.  
<img src=https://i.imgur.com/0cl2W6F.png>  

Lệnh tạo symlink như sau:  
```
ln -s [file nguồn] [file đích]
```
<img src=https://i.imgur.com/bUbgLv5.png>  
Ở đây ta nhận ra khi tạo file symlink là `symlink.txt` tương ứng với với file `link.txt` thì 2 file này có chỉ số inode khác nhau là 1060499 và 1060500. Ta xóa file `link.txt` thì nội dung trong file `symlink.txt` cũng không còn.  
Nội dung của `symlink.txt` không hiển thị được vì `symlink.txt` trỏ đến một tập tin khác, mà tập tin này không tồn tại.  

