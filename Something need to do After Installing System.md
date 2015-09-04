##1. Debian 8 -source.list
```
deb http://mirrors.163.com/debian/ jessie main non-free contrib
deb http://mirrors.163.com/debian/ jessie-updates main non-free contrib
deb http://mirrors.163.com/debian/ jessie-backports main non-free contrib
deb-src http://mirrors.163.com/debian/ jessie main non-free contrib
deb-src http://mirrors.163.com/debian/ jessie-updates main non-free contrib
deb-src http://mirrors.163.com/debian/ jessie-backports main non-free contrib
deb http://mirrors.163.com/debian-security/ jessie/updates main non-free contrib
deb-src http://mirrors.163.com/debian-security/ jessie/updates main non-free contrib
```
##2. Install chrome
```
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
```
然后手动双击安装即可。
##3. 记录利用ettercap进行简单的arp欺骗和mitm攻击
先安装ettercap
```
sudo apt-get install ettercap-dbg 
```
再安装图片捕捉工具
```
sudo apt-get install driftnet
```
操作过程
1.Sniff ->> Unified Sniffing 选择网卡 ->>wlan0
2.Hosts ->> Hosts list 列出列表  ->>Scan for hosts 扫描列表
3.根据ip要攻击的对象为目标２　主路由器为目标１
4.Mitm 选择攻击方式　->> ARP poisoning ->> 勾选地一个方框Sniff ...
5.Start ->> Start Sniffing 开始攻击
6.终端sudo drifinet 启动图片捕捉工具
