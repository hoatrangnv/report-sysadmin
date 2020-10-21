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

**System Admin (Sysadmin) chịu trách nhiệm thiết lập và bảo trì hệ thống máy tính. Họ đảm bảo rằng các máy tính trong mạng của công ty, đặc biệt là máy chủ vận hành trơn tru và an toàn. Mô tả công việc của System Admin sẽ cung cấp thêm thông tin về vị trí việc làm này.**  

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
