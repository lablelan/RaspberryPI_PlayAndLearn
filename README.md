

## RaspberryPI Zero W 系统安装
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

## RaspberryPI Zero W 使用ssh连接RaspberryPi
1.在sd卡boot目录下新建空白文件ssh（注意不能带文件后缀）
2.通过路由器找到树莓派IP
3.使用PuTTY连接树莓派（端口：22）
4.输入默认用户密码（Raspbian默认的用户名密码是pi/raspberry）


## RaspberryPI Zero W + Qplug USB连接以太网
1.下载raspbian-jessie版本镜像（需2016.10之后的版本）

2.安装系统

3.创建ssh文件

4.配置 CONFIG.TXT 和 CMDLINE.TXT 文件
```javascript
# 修改boot分区里的config.txt文件，在新一行增加如下内容
dtoverlay=dwc2
# 修改boot分区里的cmdline.txt文件，在rootwait后面增加如下内容，注意每个参数之间空格分开，且都是在同一行
modules-load=dwc2,g_ether
```

5.安装Bonjour（Bonjour被包含在iTunes与Adobe CS软件中）

6.连接windows，windows会自动识别安装驱动

7.用PuTTY连接，如果一切正常连接树莓派的地址 raspberrypi.local 即可

8.设置共享互联网连接。打开 控制面板-网络和Internet-网络连接 ，找到RNDIS/Ethernet Gadget” 的设备类型，右键属性-共享 下拉菜单中找到树莓派的连接名称

PS：如果出现 错误提示 “Unable to open connection to raspberrypi.local. Host does not exist”，那么需要安装RNDIS驱动

```javascript 
安装方法：
    1.保持树莓派与电脑的连接，打开 Windows 的 设备管理 中找到 RNDIS/Ethernet Gadget , 右键选择 更新驱动程序 。
    2.选择 流量计算机以查找驱动软件-从计算机的设备驱动程序列表中选择
    3.找到网络适配器  
    4.找到Microsoft Corporation 选择 Remote NDIS Compatible Device 安装驱动
```
    
    



