adb 命令
-----------

<!-- toc orderedList:0 depthFrom:1 depthTo:6 -->

  * [adb 命令](#adb-命令)
* [adb 介绍](#adb-介绍)
* [管理设备](#管理设备)
* [服务相关](#服务相关)
* [获取设备硬件信息](#获取设备硬件信息)
* [管理设备App](#管理设备app)
* [文件操作](#文件操作)

<!-- tocstop -->

# adb 介绍

adb的全称为Android Debug Bridge 调试桥，是连接Android手机与PC端的桥梁，通过adb可以管理、操作模拟器和设备，如安装软件、系统升级、运行shell命令等。

# 管理设备
注:android手机、模拟器统一称为“设备”
```
adb devices  // 显示连接到计算机的设备
adb get-serialno // 获取设备的ID和序列号serialNumber
------------------重启----------------------------------------------
adb reboot  // 重启设备
adb reboot bootloader  // 重启到bootloader，即刷机模式
adb reboot recovery  // 重启到recovery，即恢复模式
------------------发送命令到设备--------------------------------------
adb [-d|-e|-s <serialNumber>] <command>
-d 发送命令给usb连接的设备
-e 发送命令到模拟器设备
-s <serialNumber> 发送命令到指定设备
------------------cpu、内存和进程--------------------------------------
adb shell top //查看设备cpu和内存占用情况
adb shell top -m 6 //查看占用内存前6的app
adb shell top -n 1 //刷新一次内存信息，然后返回
adb shell procrank //查询各进程内存使用情况
adb shell kill [pid] //杀死一个进程
adb shell ps //查看进程列表
adb shell ps -x [PID] //查看指定进程状态
adb shell service list //查看后台services信息
adb shell cat /proc/meminfo //查看当前内存占用
adb shell cat /proc/iomem //查看IO内存分区
```

# 服务相关
```
adb kill-server // 终止adb服务进程
adb start-server // 重启adb服务进程
adb root // 已root权限重启adb服务
adb wait-for-device // 在模拟器/设备连接之前把命令转载在adb的命令器中
adb shell cat /data/misc/wifi/*.conf //查看wifi密码
```
# 获取设备硬件信息
```
adb shell  cat /sys/class/net/wlan0/address  // 获取mac地址
adb shell cat /proc/cpuinfo  // 获取cpu序列号
```

# 管理设备App
```
aapt d badging <apkfile> // 获取apk的packagename 和 classname
------------------安装----------------------------------------------
adb install <apkfile>  // 安装apk
adb install -r <apkfile> // 保留数据和缓存文件，重新安装apk，
adb install -s <apkfile>  // 安装apk到sd卡
------------------卸载----------------------------------------------
adb uninstall <package>  // 卸载app
adb uninstall -k <package>  // 卸载app但保留数据和缓存文件
------------------启动app-------------------------------------------
adb shell am start -n <package_name>/.<activity_class_name> // 启动应用
------------------查看内存占用----------------------------------------
adb shell top  // 查看设备cpu和内存占用情况
adb shell top -m 6 // 查看占用内存前6的app
adb shell top -n 1 // 刷新一次内存信息，然后返回
adb shell procrank // 查询各进程内存使用情况
adb shell kill [pid] // 杀死一个进程
adb shell ps // 查看进程列表
adb shell ps -x [PID] // 查看指定进程状态
adb shell service list // 查看后台services信息
adb shell cat /proc/meminfo // 查看当前内存占用
adb shell cat /proc/iomem // 查看IO内存分区
```

# 文件操作

```
/android中，sdcard代表内置存储，不同系统中tf卡的设备名可能不同，使用查看adb shell ls mnt查看所有存储设备名。
adb remount  // 将system分区重新挂载为可读写分区
adb push <local> <remote> // 从本地复制文件到设备
adb pull <remote>  <local> // 从设备复制文件到本地
adb shell ls // 列出目录下的文件和文件夹，等同于dos中的dir命令
adb shell cd <folder> // 进入文件夹，等同于dos中的cd 命令
adb shell rename path/oldfilename path/newfilename // 重命名文件
adb shell rm /system/avi.apk  // 删除system/avi.apk
adb shell rm -r <folder> // 删除文件夹及其下面所有文件
adb shell mv path/file newpath/file // 移动文件
adb shell chmod 777 /system/fonts/DroidSansFallback.ttf // 设置文件权限
adb shell mkdir path/foldelname // 新建文件夹
adb shell cat <file> // 查看文件内容
```

[Android adb命令官网](https://developer.android.com/studio/command-line/adb.html#Enabling)
