

# 1，换源

**进入vim模式**

进入root 模式`

```
sudo su
```



编辑软件源配置文件`

```
vim /etc/apt/sources.list

```

刚安装完成的Kali Linux是非常干净的，什么软件都没有安装，所以需要手动修改一下源，并更新。以下为常用kali源

```text
#中科大
deb http://mirrors.ustc.edu.cn/kali kali-rolling main non-free contrib
deb-src http://mirrors.ustc.edu.cn/kali kali-rolling main non-free contrib
#阿里云
deb http://mirrors.aliyun.com/kali kali-rolling main non-free contrib
deb-src http://mirrors.aliyun.com/kali kali-rolling main non-free contrib
#清华大学
deb http://mirrors.tuna.tsinghua.edu.cn/kali kali-rolling main contrib non-free
deb-src https://mirrors.tuna.tsinghua.edu.cn/kali kali-rolling main contrib non-free
#163
deb http://mirrors.163.com/debian wheezy main non-free contrib
deb-src http://mirrors.163.com/debian wheezy main non-free contrib
deb http://mirrors.163.com/debian wheezy-proposed-updates main non-free contrib
deb-src http://mirrors.163.com/debian wheezy-proposed-updates main non-free contrib
deb-src http://mirrors.163.com/debian-security wheezy/updates main non-free contrib
#东软大学
deb http://mirrors.neusoft.edu.cn/kali kali-rolling/main non-free contrib
deb-src http://mirrors.neusoft.edu.cn/kali kali-rolling/main non-free contrib
#官方源
deb http://http.kali.org/kali kali-rolling main non-free contrib
deb-src http://http.kali.org/kali kali-rolling main non-free contrib
```

我这里挑选阿里云的源，执行命令修改/etc/apt/sources.list文件，并保存关闭。

# 2，汉化

```
sudo dpkg-reconfigure locales
```



# 3，安装中文输入法

## 安装输入法框架

```
apt-get install fcitx 

apt-get install ibus ibus-pinyin
sudo apt install fcitx5 fcitx5-pinyin
```



## 安装搜狗输入法

```
sudo dpkg -i sogoupinyin_版本号_amd64.deb
```



## 安装谷歌输入法

```
apt-get install fcitx-googlepinyin 
```

## 重启

```
启动ibus:im-config

reboot 
```



## 4.在Kali系统里配置SSH服务并开机自动启动

```
1. 修改SSH配置文件
vim /etc/ssh/sshd_config
34行 把#去掉，并修改为yes
#PermitRootLogin prohibit-password
修改为
PermitRootLogin yes

2. 设置开机启动
systemctl enable ssh

3. 重启ssh服务
systemctl restart ssh

4. 查看22端口服务状态
netstat -apn |grep ssh

5. 此时ssh服务器已经开启，可以使用xshell或者secure CRT 连接kali服务器。
```





