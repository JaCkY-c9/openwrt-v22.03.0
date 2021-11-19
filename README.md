·固件介绍：

       1.使用官方稳定源码： v21.02.0
       2.软件储存空间调整为： 128m+1024m
       3.官方源自带核显驱动（intel 4415u可用）
       
·编译添加及调整内容(以官方config.buildinfo文件为基础）：

       1.状态显示（netdata）
       2.挂载点（block-mount）
       3.磁盘管理格式化软件（luci-app-diskman)
       4.自动重启（autoreboot）
       5.opencl**
       6.硬盘休眠（hdd-idle）
       7.Terminal终端（luci-app-ttyd）
       8.UPnP
       9.网络文件共享（Samba4）
       10.Docker（luci-app-dockerman) 使用lisaac源,因官方源含有dockerman，lisaac源改名为dockerman3用于区别
       11.网络文件挂载nfs（luci-app-nfs）
       12.网络打印机（luci-app-usb-printer）
       13.中文语言包（luci-i18n-base-zh-cn）
       14.取消dnsmasq，添加dnsmasq-full
       15.LAN IP:192.168.10.1
       
