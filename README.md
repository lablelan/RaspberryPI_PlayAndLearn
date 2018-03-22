

## RaspberryPI Zero W 系统安装[TOC]
[raspbian_lite下载](https://downloads.raspberrypi.org/raspbian_lite/images/).

[raspbian_lite_destop下载](https://downloads.raspberrypi.org/raspbian/images/).

[相关工具下载](https://pan.baidu.com/s/1t4ZDyHNjRRUz8s_061OO4g). key：hc3o

安装步骤：

1.用读卡器读取sd卡

2.使用win32diskimager选择对应镜像

3.将系统烧录到sd卡

等待几分钟系统安装完成

## RaspberryPI Zero W 无线上网相关配置
准备工作：
1.使用[VM虚拟机](https://pan.baidu.com/s/1nKCUIUoV0sKJye5Xjfm0GQ)安装linux环境（Winodws下无法识别ext3系统格式 key:24ye）

2.[Ubuntu](https://www.ubuntu.com/download/desktop)镜像下载

修改配置：

1.在sd卡etc/network/目录下修改interfaces文件
```javascript
auto lo
iface lo inet loopback

iface eth0 inet manual

allow-hotplug wlan0
auto wlan0
iface wlan0 inet dhcp
    wpa-conf /boot/wpa.conf
```

2.在sd卡的boot/目录下新建wpa.conf文件
```javascript
network={
    ssid="WIFI-Name"
    key_mgmt=NONE
    priority=4
}
```



