# Debian 安装与配置

标签（空格分隔）：MyDebian

---硬件环境：<雷神G150S>　i7-4770MQ, 8G, GTX950M ,Intel Corporation Wireless 3160
##1、镜像安装
　　官网下载镜像，可在windows环境下使用软碟通写入U盘，Linux下写入未测试。安装过程中可能会出现以下错误：
　　【1】探测网络设备：您的一些硬件需要非自由固件文件才能运转，固件可以从可移动介质加载缺失的固件文件是：iwlwifi-3160-9.ucode iwlwifi-3160-8.ucode 如果现在您有可用的介质，请将其插入，然后继续。
　　从可移动介质加载缺失的固件吗？
_ _ _ _ _ _ _ _
遇到这种情况是开源的无线网卡驱动不兼容，请TAB键选择“否”即可，安装完系统后再进行安装闭源驱动。
##2、闭源无线网卡驱动（Intel 3160 WiFi Adapter）的安装
###译自Debian wiki，原网址：https://wiki.debian.org/iwlwifi#Installation
　　
####iwlwifi linux驱动支持的Intel 无线网卡驱动器：

 - Intel Wireless WiFi 5100AGN, 5300AGN, and 5350AGN
 - Intel Wireless WiFi 5150AGN
 - Intel WiFi Link 1000BGN
 - Intel 6000 Series WiFi Adapters (6200AGN and 6300AGN)
 - Intel Wireless WiFi Link 6250AGN Adapter
 - Intel 6005 Series WiFi Adapters
 - Intel 6030 Series WiFi Adapters
 - Intel Wireless WiFi Link 6150BGN 2 Adapter
 - Intel 100 Series WiFi Adapters (100BGN and 130BGN)
 - Intel 2000 Series WiFi Adapters
 - Intel 7260 WiFi Adapter
 - Intel 7265 WiFi Adapter
 - Intel 3160 WiFi Adapter
　　
####进行安装
####【Debian 8 "Jessie"的安装】
1）在源列表中添加"non-free"源：
```
# vi /etc/apt/sources.list
```
然后将以下加入源列表：
```
# Debian 8 "Jessie"
deb http://http.debian.net/debian/ jessie main contrib non-free
```
2）更新源列表：
```
# apt-get update
```
3）安装firmware-iwlwifi 包：
```
# apt-get install firmware-iwlwifi
```
4）重新插入iwlwifi模块来访问安装的固件:
```
# modprobe -r iwlwifi ; modprobe iwlwifi
```
5）重新启动电脑，在网络中便会找到wifi连接，大功告成。
####【Debian 7 "Wheezy"的安装】
1）在源列表中添加"non-free"源：
```
# vi /etc/apt/sources.list
```
然后将以下加入源列表：
```
# Debian 7 "Wheezy"
deb http://http.debian.net/debian/ wheezy main contrib non-free
```
2）更新源列表：
```
# apt-get update
```
3）安装firmware-iwlwifi 包：
```
# apt-get install firmware-iwlwifi
```
4）重新插入iwlwifi模块来访问安装的固件:
```
# modprobe -r iwlwifi ; modprobe iwlwifi
```
5）重新启动电脑，在网络中便会找到wifi连接，大功告成。

【故障排除】
安装完驱动，使用蓝牙时WIFI可能会遇到问题，使用以下方法解决：
```
# options iwlwifi bt_coex_active=0 swcrypto=1 11n_disable=8
```
 　　
【支持的PCI驱动】

 - PCI: 8086:0082 Intel Corporation Centrino Advanced-N 6205 [Taylor Peak]
 - PCI: 8086:0083 Intel Corporation Centrino Wireless-N 1000 [Condor Peak]
 - PCI: 8086:0084 Intel Corporation Centrino Wireless-N 1000 [Condor Peak]
 - PCI: 8086:0085 Intel Corporation Centrino Advanced-N 6205 [Taylor Peak]
 - PCI: 8086:0087 Intel Corporation Centrino Advanced-N + WiMAX 6250 [Kilmer Peak]
 - PCI: 8086:0089 Intel Corporation Centrino Advanced-N + WiMAX 6250 [Kilmer Peak]
 - PCI: 8086:008A Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak]
 - PCI: 8086:008B Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak]
 - PCI: 8086:0090 Intel Corporation Centrino Advanced-N 6230 [Rainbow Peak]
 - PCI: 8086:0091 Intel Corporation Centrino Advanced-N 6230 [Rainbow Peak]
 - PCI: 8086:0885 Intel Corporation Centrino Wireless-N + WiMAX 6150
 - PCI: 8086:0886 Intel Corporation Centrino Wireless-N + WiMAX 6150
 - PCI: 8086:0887 Intel Corporation Centrino Wireless-N 2230
 - PCI: 8086:0888 Intel Corporation Centrino Wireless-N 2230
 - PCI: 8086:088E Intel Corporation Centrino Advanced-N 6235
 - PCI: 8086:088F Intel Corporation Centrino Advanced-N 6235
 - PCI: 8086:0890 Intel Corporation Centrino Wireless-N 2200
 - PCI: 8086:0891 Intel Corporation Centrino Wireless-N 2200
 - PCI: 8086:0892 Intel Corporation Centrino Wireless-N 135
 - PCI: 8086:0893 Intel Corporation Centrino Wireless-N 135
 - PCI: 8086:0894 Intel Corporation Centrino Wireless-N 105
 - PCI: 8086:0895 Intel Corporation Centrino Wireless-N 105
 - PCI: 8086:0896 Intel Corporation Centrino Wireless-N 130
 - PCI: 8086:0897 Intel Corporation Centrino Wireless-N 130
 - PCI: 8086:08AE Intel Corporation Centrino Wireless-N 100
 - PCI: 8086:08AF Intel Corporation Centrino Wireless-N 100
 - PCI: 8086:08B1 Intel Corporation Wireless 7260
 - PCI: 8086:08B2 Intel Corporation Wireless 7260
 - PCI: 8086:08B3 Intel Corporation Wireless 3160
 - PCI: 8086:08B4 Intel Corporation Wireless 3160
 - PCI: 8086:095A Intel Corporation Wireless 7265
 - PCI: 8086:095B Intel Corporation Wireless 7265
 - PCI: 8086:24F3 Intel Corporation Wireless 8260
 - PCI: 8086:24F4 Intel Corporation Wireless 8260
 - PCI: 8086:422B Intel Corporation Centrino Ultimate-N 6300
 - PCI: 8086:422C Intel Corporation Centrino Advanced-N 6200
 - PCI: 8086:4232 Intel Corporation WiFi Link 5100
 - PCI: 8086:4235 Intel Corporation Ultimate N WiFi Link 5300
 - PCI: 8086:4236 Intel Corporation Ultimate N WiFi Link 5300
 - PCI: 8086:4237 Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
 - PCI: 8086:4238 Intel Corporation Centrino Ultimate-N 6300
 - PCI: 8086:4239 Intel Corporation Centrino Advanced-N 6200
 - PCI: 8086:423A Intel Corporation PRO/Wireless 5350 AGN [Echo Peak] Network Connection
 - PCI: 8086:423B Intel Corporation PRO/Wireless 5350 AGN [Echo Peak] Network Connection
 - PCI: 8086:423C Intel Corporation WiMAX/WiFi Link 5150
 - PCI: 8086:423D Intel Corporation WiMAX/WiFi Link 5150
##３、sudo的安装
　　网络安装的镜像安完的debian是什么都没有的，包括gcc和sudo。使用终端命令sudo ** 会出现 sudo 不是命令的提示，需要手动下载安装，安装前需要先更新源，这里以163的镜像为例：
```
$ su
# wget http://mirrors.163.com/.help/sources.list.squeeze
# mv sources.list.squeeze sources.list
```
因为配置文件中有一个源已经失效了，所以要修改一个地方，使用```vi sources.list```打开，把倒数第二个源注释掉。
```
deb http://http.us.debian.org/debian squeeze main contrib non-free
# deb http://non-us.debian.org/debian-non-US squeeze/non-US main contrib non-free
deb http://security.debian.org squeeze/updates main contrib non-free
```
接着更新源
```
mv sources.list /etc/apt/
apt-get update
```
这样把软件源配好之后，你再执行```apt-get install```才能够正确的安装东西，接下来是sudo的安装
```
apt-get install sudo
```
安装玩之后，如果使用sudo提示不在sudoers中，使用以下方法解决：

1)切换到root用户并查看soduers文件权限
```
su
ll /etc/sudoers
```
2）若提示没有可写的权限，如：-r--r-----. 1  root root 4030 8月  15 09:55 /etc/sudoers，则修改权限然后再次查看。
```
chmod 777 /etc/sudoers
ll /etc/sudoers
```
3)会提示-rwxrwxrwx. 1 root root 4030 8月  15 09:57 /etc/sudoers，接下来修改/etc/sudoers文件内容找到字段
```
#open the file
vi /etc/sudoers
#add the nextline word
root    ALL=(ALL)    ALL
```
在此行字段下面追加
```
username    ALL=(ALL)     ALL
#username 即用户名字
```
4）保存退出并恢复文件原来的权限
```
:wq
chmod 400 /etc/sudoers
```
##3、连接VPN
Debian没有自带的vpn连接，需要下载安装pptp-linux和network-manager-pptp-gnome即可正常使用。
```
sudo apt-get install pptp-linux
sudo apt-get install network-manager-pptp-gnome
```
重新启动电脑，大功告成。
