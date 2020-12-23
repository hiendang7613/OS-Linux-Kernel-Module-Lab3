# HỆ ĐIỀU HÀNH
## ĐÔ ÁN 3. TÌM HIỂU VÀ LẬP TRÌNH LINUX KERNEL MODULE

Hình thức: đồ án 3 sinh viên <br>
Deadline: 23h55 ngày 23-12-2020 <br>
Nộp bài qua  moodle môn học, đặt tên file nộp là MSSV1_MSSV2_MSSV3.zip/rar <br>

Nội dung file nộp gồm:  báo cáo những gì mình hiểu (trình bày trên MSWORD), readme của module đã code, và mã nguồn.  <br>

Nội dung đồ án:<br>
Mục tiêu hiểu về Linux kernel module và hệ thống quản lý file và device trong linux, giao tiếp giữa tiến trình ở user space và code kernel space <br>
+ Viết một module dùng để tạo ra số ngẫu nhiên. <br>
+ Module này sẽ tạo một character device để cho phép các tiến trình ở userspace có thể open và read các số ngẫu nhiên.<br>

## TEST
* Chạy với quyền root
```
> insmod mymodule.ko
> cat /dev/chardev0
```
![image](https://user-images.githubusercontent.com/73353492/103017952-fb545e80-4576-11eb-968c-0c9d5a357922.png)

## BUILD & INSTALL MODULE
- Viết Makefile
```
# ./Makefile
KDIR = /lib/modules/`uname -r`/build
all:
  make -C $(KDIR) M=`pwd`
clean:
  make -C $(KDIR) M=`pwd` clean
```
- Viết Kbuild
```
# ./Kbuild
EXTRA_CFLAGS = -Wall
obj-m = mymodule.o
```
- Biên dịch module<br>
```
> gmake
```

- Cài đặt module
```
> insmod mymodule.ko
```
