·固件介绍：

       1.使用官方稳定源码： v21.02.0
       2.软件储存空间调整为： 128m+1024m
       3.官方源自带核显驱动（intel 4415u可用）
       
·编译添加及调整内容：

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
       
·固件刷机：
       
       1.u盘刷入系统
       2.格式化u盘剩余储存空间，挂载为/opt用于docker使用。
       3.机械硬盘挂目录：/mnt/sdb1 作为下载及共享目录使用。



·docker容器设置：

       1.·添加cups容器 命令行：
       
       docker run -d
       -p 631:631 
       -v /var/run/dbus:/var/run/dbus 
       --name cupsd olbat/cupsd
       
       
       2.添加jellyfin容器 命令行：
       
       docker run -d
       --name jellyfin
       -v /opt/docker/volumes/jellyfin/config:/config
       -v /opt/docker/volumes/jellyfin/cache:/cache
       -v /目录:/media
       -p 8096:8096
       --device=/dev/dri/renderD128
       --restart unless-stopped
       jellyfin/jellyfin
       
       
       3.添加aria2容器 命令行：
       
       docker run -d \
       --name aria2-pro \
       --restart unless-stopped \
       --log-opt max-size=1m \
       --network host \
       -e PUID=$UID \
       -e PGID=$GID \
       -e UMASK_SET=022 \
       -e RPC_SECRET=password\
       -p 6800:6800 \
       -e RPC_PORT=6800 \
       -e LISTEN_PORT=6888 \
       -p 6888:6888 \
       -p 6888:6888/udp \
       -v /opt/docker/volumes/aria2-config:/config \
       -v /目录/aria2-downloads:/downloads \
       p3terx/aria2-pro
       
       
       4.添加aria2面板容器  命令行：
       
       docker run -d \
       --name ariang \
       --restart unless-stopped \
       --log-opt max-size=1m \
       -p 6880:6880 \
       p3terx/ariang
       
       
       
      5.添加Home assistant容器 命令行：
      
      docker run -d \
      --name homeassistant \
      --privileged \
      --restart=unless-stopped \
      -v /opt/docker/volumes/homeassistant:/config \
      --network=host \
      ghcr.io/home-assistant/home-assistant:stable

·备份配置文件
     
·恢复配置文件
      
      1.fistboot
      2.reboot
      3.上传配置文件
