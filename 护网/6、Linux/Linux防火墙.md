## Firewalld防火墙简介

```
firewalld防火墙是 Centos7系统默认的防火墙管理工具，取代了之前版本的iptables 防火墙

firewalld防火墙工作在网络层，属于包过滤防火墙

防火墙规则设置由firewalld服务的firewall-cmd命令进行管理

如果安装了图形化界面的Linux可以使用firewall—config命令调出图形化工具
```

```
查看已开启的端口
firewall-cmd --list-ports

查看防火墙状态
firewall-cmd --state

开启防火墙
systemctl start firewalld

开启端口
firewall-cmd --zone=public --add-port=6379/tcp --permanent

重启防火墙
firewall-cmd --reload
```



```
firewall-cmd --add-port=端口/通讯协议 --permanent

firewall-cmd			是防火墙管理命令
--add-port=端口/通讯协议 			用来指定添加的端口号和协议3

设置完成规则后执行命令：firewall—cmd --reload 重新加载防火墙使配置生效 
```



```
查看开放的服务： 
firewall-cmd--list-services !

rich rules：富规则，即更细致、更详细的防火墙规则策略允许192.168.3.68主机访问:
firewall-cmd --add-rich-rule="rule family="ipv4" source address="192.168.3.68"accept" --permanen


禁止192.168.3.68主机访问：
firewall-cmd --add-rich-rule="rule family="ipv4" source address="192.168.3.68"reject" --permanent 


允许192.168.0.100主机访问ssh服务：
firewall-cmd --add-rich-rule='rule family="ipv4" source address="192.168.0.100"service name="ssh" accept' --permanent


禁止192.168.0.100主机访问http服务：
irewall-cmd --add-rich-rule='rule family="ipv4" source address="192.168.0.100"servic name="http" reject' --permanent 


禁止192.168.0.0/24网段主机访问http服务：
firewall-cmd --add-rich-rule='rule family="ipv4" source address="192.168.0.0/24"service name="http" reject' --permanent


删除放行的某个端口:
firewall-cmd --remove-port＝端口/通讯协议 --permanent

firewall-cmd --add-port=开始端口-结束端口/通讯协议 --permanent

查看开放的端口:
firewall-cmd --list-ports



开放http服务： 5
firewall-cmd --add-service=http --permanent
```