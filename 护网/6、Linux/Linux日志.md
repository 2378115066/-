## Linux日志概述

```
日志是记录系统运行过程中各种重要信息的文件，在系统运行过程中由各进
程创建并记录。
日志的作用是记录系统的运行过程及异常信息，这些日志可以帮助我们对系
统进行审核以及对一些故障进行排查，一般这些日志存储在/var/log目录中。

常见日志文件及记录信息如下
/var/log/messages					＃系统日志信息
/var/log/secure						＃用户认证相关的安全事件信息
/var/log/maillog					＃与邮件相关的日志文件
/var/log/cron						＃与定时任务相关的日志
/var/log/boot.log					＃与系统启动有关的日志
```

## rsyslog服务

```
rsyslog是一个开源工具，它被广泛应用于Linux系统，它除了可以将收集的日志信息保存在本地外还可以通过TCP、UDP等协议将日志消息转发到其他主机。

rsyslog的主配置文件为/etc/rsyslog.conf

日志采集规则格式：日志类型.日志级别 执行动作

常见日志类型分为：
			auth						＃pam产生的日志
			authpriv					＃与验证有关的日志
			cron						＃定时任务相关
			kern						＃内核产生的日志
			mail						＃邮件收发信息
			lpr							＃打印产生的日志
			user						＃用户程序产生的日志信息
```

```
日志级别用来指出消息的优先等级，即消息的重要程度。其优先级别如下
（数字等级越小，优先级越高，消息越重要，但记录的信息越少:

0 emerg（紧急）：会导致主机系统不可用的情况。
1 alert（警告）：必须马上采取措施解决的问题。
2 crit（严重）：比较严重的情况。rsyslog服务
3 err （错误）：运行出现错误。--
4 warning（提醒）：可能影响系统功能，需要提醒用户的重要事件。中＊＊＊＊＊
5 notice（注意）：不会影响正常功能，但是需要注意的事件。
6 info（信息）：一般信息。
7 debug（调试）：程序或系统调试信息等。

除此之外，“日志类型”与＂日志级别”可以使用星号（＊）代表所有，因此＊.＊就表示来自所有类型的所有级别的消息。
```

```
“执行动作”字段则用来定义如何处理接收到的消息，可以指定如下几项内容：

／PATH／FILENAME 将消息存储到指定的文件中，文件必须以斜线（／）开4w*
头的绝对路径命名；

:omusrmsg：USERNAME将消息发送给指定的已经登录的用户；

@HOSTNAME 将消息转发到指定的日志服务器；一个@表示通过UDP发送，两个@表示通过TCP发送

:omusrmsg：*将消息发送给所有已经登录的用户。
```



## 搭建日志服务器

```
作用：将多台主机的日志发送到一台主机上，对一台主机的管理远简单于多台主机的日志管理。

UDP与TCP的区别：
			UDP不需要应答、速度快、但不稳定（一般用于公司内部文件的传输）
			TCP需要应答、稳定但速度较慢.
```

### 日志远程同步的做法步骤：

```
在日志发送方： 
vim/etc/rsyslog.conf 更改配置文件
将任何类型的任意级别的日志发送到日志服务器
*.*			@接收方IP地址
重启服务:
		systemctl restart rsyslog
```

### 自定义日志采集格式:

```
$template 自定义格式名,"%timegenerated% %FROMHOST-IP% %slogtag% %msg%/n"
"%timegenerated%					＃显示日志时间
%FROMHOST-IP%						＃显示主机IP
%syslogtag%							＃日志记录目标
%msg%								＃日志内容 
\n									＃换行

在指定的日志中采用自定义格式
日志类型.日志级别 执行动作;自定义格式名

修改系统默认日志采集格式为自定义格式
$ActionFileDefaultTemplate 自定义格式名
```

### 日志查看工具：journalctl

```
journalctl：日志查看工具

-n 3					＃查看最近3条日志
-p err					＃查看错误日志
-o verbose				＃查看日志的详细参数
--sincce				＃查看从什么时间开始的日志
--until					＃查看到什么时间为止的日志
```



```

由于日志是在系统内存中的，而systemd—journald默认是不保存系统日志到硬盘的，所以关机后再次开机只能看到本次开机之后的日志，关机之前的日志是无法查看的，想要保存日志需要进行如下操作

mkdir/var/log/journal
chgrp systemd-journal /var/log/journal
chmod g+s /var/log/journal
killall -1 systemd-journald
ls /var/log/journal
```

