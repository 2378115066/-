# 安装

## 1、配置源并更新

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

执行以下命令进行更新：

```text
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean
```

等待命令执行完成后，安装python3、pip、git

```text
sudo apt-get install python3
sudo apt-get install git
sudo apt-get install python3-pip
```

## 2，简单配置

### **安装Kali Linux工具包**

1. 安装标准工具包

```text
sudo apt install kali-linux-default
```

2.安装大工具包（大概7 8G）

```text
sudo apt install kali-linux-large
```

3、安装Kali Linux常用工具

这里推荐使用GitHub上一位老哥的项目，可以一键进行安装

项目地址：[https://github.com/rikonaka/katoolin4china](https://link.zhihu.com/?target=https%3A//github.com/rikonaka/katoolin4china)

下面安装第三方工具：

```text
git clone https://github.com/rikonaka/katoolin4china
cd katoolin4china
sudo pip3 install .
```

（注意第三条命令最后有个点）

使用命令打开第三方工具

```text
sudo k4c
```

![img](https://pic1.zhimg.com/v2-4903b5a0874abf7e4d8926eaac6eb588_b.jpg)

第一步输入2，进行工具安装选项

第二步输入0，安装所有工具。

![img](https://pic2.zhimg.com/v2-dcdf0039dff6665cef545102a7a0b115_b.jpg)

耐心等待安装完成。

最后msfconsole、sqlmap等工具就可以直接使用了，从此不用再等待虚拟机开机。





# 卸载

## 1、查看当前环境安装的wsl

```
wsl --list
```



## 2、注销（卸载）当前安装的Linux的Windows子系统

```
wsl --unregister Ubuntu
```



### 3、卸载成功，查看当前安装的Linux的Windows子系统

```
wsl --list
```



### 4、查看可安装的Linux的Windows子系统

```
wsl --list --online
```

