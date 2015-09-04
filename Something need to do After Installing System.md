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
更改原来的shell
```
chsh -s /bin/zsh
```
###更改主题
编辑配置文件```sudo vim ~/.zshrc``` 修改theme即可，theme可到官网查找
