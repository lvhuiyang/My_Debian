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
###操作过程
```
1.Sniff ->> Unified Sniffing 选择网卡 ->>wlan0
2.Hosts ->> Hosts list 列出列表  ->>Scan for hosts 扫描列表
3.根据ip要攻击的对象为目标２　主路由器为目标１
4.Mitm 选择攻击方式　->> ARP poisoning ->> 勾选地一个方框Sniff ...
5.Start ->> Start Sniffing 开始攻击
6.终端sudo drifinet 启动图片捕捉工具
```
##4. 安装配置oh my zsh
两种途径下载并安装zsh
第一种，直接用包管理器下载安装
```
sudo apt-get install zsh
```
第二种，github上下载安装
```
curl -L https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh | ZSH=~/.dotfiles/zsh sh
```

将文件库克隆到本地
```
git clone git://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh
```
先创建配置文件
```
touch ~/.zshrc
```
备份原文件（此部可省略）
```
cp ~/.zshrc ~/.zshrc.orig
```
创建新的配置文件
```
cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
```
更改原来的shell，将zsh设置为默认shell
```
chsh -s /bin/zsh
```
重新启动电脑，大功告成
###如需更改主题
编辑配置文件```sudo vim ~/.zshrc``` 修改theme即可，theme可到官网查找
##5. grub引导修复
双系统的情况下先装完linux再装Windows会出现win引导覆盖Linux的问题，实验室以及我的PC上都是双硬盘双系统，这样比较容易实现修复引导，下面说一下整体思路
####1.先装的是linux，装在硬盘0（此时硬盘1为空）
####2.BIOS设定第一启动项为硬盘0，这时正常启动linux（添加引导后有时不需要设定便能直接启动硬盘0）
####3.将Windows装在硬盘1，并添加引导。这时新添加的Windows引导会覆盖原linux，开机会直接启动硬盘1上的Windows
####4.Windows设定完毕后重启进入BIOS设置，将硬盘0重新设定为第一启动项
####5.重启后会进入linux的grub引导界面，此时并无windows选项
####6.linux终端输入命令```sudo update-grub```重新检测引导项，不出意外会检测到Windows并自动添加
####7.重启，grub会出现Windows选项，实现最终双硬盘双系统。
####（注意）此方法用于双硬盘双系统，单硬盘双系统推荐先装win再装linux以免折腾，若需要进入急救模式修改grub配置文件```sudo vim /boot/grub/grub.cfg```
