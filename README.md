# Những điều cần biết cho sysadmin!

## MỤC LỤC  
[I. Introduction](#introduction)

[II. Working with file](#workingwithfile)  

[III. Redirect](#redirect)  

[IV. File System](#filesystem)  
- [1. Layout](#layout)
- [2. EXT4,XFS,BtrFS,...](#etx4xfs)
- [3. Làm việc với disk, format, mount file, fstab (async,noatime,rw,ro,remount)](#lamviecvoi)
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

**System Admin (Sysadmin) chịu trách nhiệm thiết lập và bảo trì hệ thống máy tính. Họ đảm bảo rằng các máy tính trong mạng của công ty, đặc biệt là máy chủ vận hành trơn tru và an toàn. **  

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

- Chế độ dòng lệnh command mode, những gì được gõ vào sẽ được hiểu như là lệnh của vi. Vi có rất nhiều lệnh như: tìm kiếm, thay thế, xóa, lưu tâp tin…
- Chế độ nhập văn bản insert mode, những gì được gõ vào được hiểu là nội dung của tập tin đang soạn thảo.

Khi bắt đầu sử dụng lệnh **vi**, **vi** mặc định ở command mode. Ấn phím lệnh **i, a, o** hoặc **Inserrt** từ chế độ command mode để chuyển sang insert mode. Ấn **Esc** để chuyển đổi qua lại từ command mode với insert mode.  
Một số lệnh với **vi**:

- **:set nu** hiện thị số dòng
- **:set nonu** bỏ hiện thị số dòng
- Sử dụng phím mũi tên hoặc các phím h,l,j,k để dịch trái, phải, lên, xuống
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