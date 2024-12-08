# 一、Samba文件共享服务器搭建 
## 1.简介
Samba是一个能让Linux系统应用Microsoft网络通讯协议的软件，SMB（Server Message Block）服务器消息块
Samba最大的功能是可以用于Linux与windows系统直接的文件共享和打印共享，既可以用 于Windows与linux之间的文件共享也可以用于linux与linux之间的文件共享

基于客户机/服务器的协议，因而一台Samba服务器既可以充当：
-  文件共享服务器
- Samba客户端

Samba在windows下使用的是NetBIOS协议，要使用linux下共享出来的文件，要确认 windows系统安装了NetBIOS协议
## 2.套件
安装SAMBA 这个服务器总共需要至少三个套件，包括samba、samba-common和sambaclient
- **samba**：这个套件主要包含了 SAMBA 的主要 daemon配置 ( smbd 及 nmbd )、 SAMBA 的文 件档 ( document )、以及其它与 SAMBA 相关的logrotate 设定文件及开机预设选项配置等
- **samba-common**：这个套件则主要提供了 SAMBA 的主要配置(smb.conf) 、 smb.conf 语法检 验的测试程序 ( testparm )等；
- **samba-client**：这个套件则提供了当 Linux 做为SAMBA Client 端时，所需要的工具指令，例如挂 载 SAMBA 配置格式的执行档 smbmount等
## 3.配置文件
amba配置文件目录存放于/etc/samba，几个主要的配置文件有smb.conf、Imhost和smbpasswd 
**smb.conf**：这个是SAMBA 最主要的配置文件。在较为简单的设定当中，这也是唯一的一个配置文件。该配置 文件主要的设定分为两部份，分别为:
- [global] 这个设定主机功能的项目
- [sharedir] 每个分享出去的目录的属性设定
**lmhosts**：该配置的主要目的在对应NetBIOS name 与该主机名称的 IP。由于目前SAMBA 的功能越来越强大， 所以通常只要一启动 SAMBA 时，它就能自己获取 LAN里面的相关计算机的 NetBIOS name 对应 IP 的信息， 因此该配置通常可以不用设定
**smbpasswd**：是SAMBA 存放使用者密码对应表文件。当设定的 SAMBA 服务器需要使用者输入账号与密码后 才能登入的状态时，使用者的密码存放于该文件
**smb.conf配置文件详解**
```
[global] #设置Samba服务器的整体环境
workgroup = MYGROUP #指定工作组名称
server string = Samba Server Version #指定主机注释说明
netbios name = MYSERVER #指定Samba默认主机名
hosts allow = 127. 192.168.12. 192.168.13. #允许访问samba服务器IP地址范围，默认允许所有的IP访
问
security = user #设置安全等级,user模式需用户验证，share模式无需验证。

[homes]
valid users = #指定允许访问用户
invalid users = #指定不允许访问用户
write list = #指定写入用户
read list = #设置只读用户
public = yes #是否可以匿名访问
```
## 4.常用命令
Samba服务器常用命令包括如下: 
**smbpasswd**: 设置samba用户及其密码。常用参数“-a”，表示增加smb用户与配置密码
**smbclient**：查看计算机分享出来的目录与装置。常用参数“-L”后面接需要查看的主机IP， “-U”后面接登录的用户名
**smbmount**： 将远程主机分享的目录挂载到Linux 主机上，与mount功能类似
**testparm**：用于测试Samba的设置是否正确，测试文件为smb.conf，测试无误表示 Samba服务能正常加载该配置
## 5.从指定源安装Samba软件
使用DNF软件管理包工具配置软件源。获取需要安装的Samba工具套件，包括 Samba, Samba-common, Samba-client及其依赖包。 
```
使用DNF添加软件源：
dnf config-manager --add-repo repository_url

使用DNF启用添加的软件源：
dnf config-manager --set-enable repository

使用DNF下载并安装软件：
dnf install samba samba-common samba-client
```
## 6.管理Samba服务、端口、开机启动项
Samba服务安装后，设置Samba服务为开机启动，并启动Samba服务，然后查看其监听端口状态
```
设置Samba为开机启动： 
systemctl enable smb 

启动Samba服务：
systemctl start smb

查看Samba服务运行状态：
systemctl status smb

查看端口监听状态：
netstat -lantp |grep 139
netstat –lantp |grep 445
```
# 二、Samba文件共享服务器用户和权限设置
## 1.根据要求添加用户
当Samba服务器需要基于用户权限进行访问资源控制时，需要在openEuler系统中 创建对应的用户，并设置为可通过Samba服务登录，无法通过openEuler的Shell登 录系统
```
创建openEuler用户smb，不创建用户home目录和无shell登录权限：
[root@openEuler ~]# useradd smb –M –s /sbin/nologin

设置smb用户通过Samba服务器登录，并设置密码：
[root@openEuler ~]# smbpasswd –a smb
```
## 2.准备共享文件与设置文件访问权限
为Samba服务器提供共享目录，需要在openEuler系统中创建对应的共享文件，并设置共享目录的权限
```
创建共享目录share和smb： 
[root@openEuler ~]# mkdir /var/share /var/smb 

更改共享目录share和smb的权限为所有人有所有权限： 
[root@openEuler ~]# chmod 777 /var/share /var/smb

更改共享目录的smb的属主为smb：
[root@openEuler ~]# chown smb:smb /var/smb
```
## 3.配置Samba共享配置
编辑Samba配置文件smb.conf，客户端可用通过匿名访问share目录，访问smb目录需要通过用户认 证才能访问，两个文件都用读写权限
编辑**[global]**配置使用户可以通过匿名访问，添加字段：
```
map to guest = Bad User
```
新建[share]访问目录，设置其权限：
```
[share]
comment = share
path = /var/share
guest ok = yes
browseable = yes
writeable = yes
```
新建[smb]访问目录，并设置其权限：
```
[smb]
comment = smb
path = /var/smb
write list = smb
broweable = yes
writable = yes
read list = smb
valid users = smb
create mask = 0777
```
## 4.测试Samba服务器可成功访问
在window系统通过文件共享的方式访问Samba服务器，连接共享文件服务器后可以成功创建文件
- 通过**\\\Samba IP\share**访问目录，无需登录认证，并且可以创建和删除文件夹或文件
- 通过**\\\Samba IP\smb**访问目录，需要提供smb用户认证信息后，才能打开文件，并且可 以成功在目录smb中创建文件夹或文件
# 三、Samba服务器运维与故障排除
## 1.使用定时任务管理文件
Samba文件共享服务器的共享数据，可以用过设置定时任务每天备份数据。使用Shell脚本与定时周期 任务crontab设置对share目录的数据归档备份到smb目录 
a.创建数据备份脚本/root/backup.sh：
```
#！/bin/sh
mkdir /var/backup #创建临时备份目录
cp -r /var/share/ /var/backup/ #将共享文件夹的数据复制到备份目录
tar -zcPvf /var/smb/backup$(date +%Y%m%d).tar.gz /var/backup #打包共享目录的数据到
/var/backup
rm -rf /var/backup/ #删除临时备份目录
find /var/smb/ -mtime +30 -name "*.tar.gz" -exec rm -rf {} \; #删除30天以上的备份数
```
b.为脚本设置可以执行权限：
```
[root@openEuler ~]# chmod +x backup.sh
```
c.设置周期执行任务，使用crontab命名编辑周期执行任务，执行计划为每天22点0执行备 份脚本backup.sh一次，备份数据到smb目录，并保存文件名为当天时间
```
[root@openEuler ~]# crontab –e
0 22 * * * /root/backup.sh
```
d.完成后，查看备份任务：
```
crontab –l
```
## 2.系统及服务日志
当需要通过日志查看Samba服务器的运行信息或报错信息时，openEuler系统日志 文件保存在/var/log目录下，使用ls命令查找到Samba服务日志文件后，在通过日 志文本查看命令查看最后20条日志记录
- 查看/var/log目录下Samba目录的日志文件名：ls –l /var/log/samba 
- 查看最后20行的日志记录：tail /var/log/samba/log.smbd –n 20
- 查看openEuler系统最后20行日志记录： tail /var/log/messages
## 3.定位文件共享故障与解决方案
在Samba使用过程中，常遇到无法使用文件共享服务的情况，常见的错误包括：
文件共享服务器无法访问，网络连接失败：
```
查看防火墙是否开启，关闭防火墙：
systemctl stop firewalld 

Samba服务未启动，重启服务：
systemctl restart smb
```
文件共享服务器无法启动，配置错误：
```
检查配置文件错误字段，根据提供的提示修改对应的字段：
cd /etc/samba; testparm
```
文件无权限访问或创建文件，共享目录权限配置错误：
```
文件属主错误，更改文件属主为对应的用户：
chown smb:smb /var/smb

文件权限错误，更改文件权限：
chmod 777 smb:smb /var/smb
```