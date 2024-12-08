# 一.IDS的简介、分类与发展

## 1、Intrusion Detection System

```
入侵检测技术是软件和硬件的结合，
		作用：
用于监控网络或系统以识别恶意活动并立即发出警报，从而保护系统资源的完整性、私密性和可用性。

		区别：
入侵检测技术与其他安全技术不同，它是一种积极主动的防御技术，可以有效防止未知攻击。可以如此形容入侵检测系统—假如防火墙为一幢大厦的门锁，那么入侵检测系统 就是这幢大厦里的监控系统，一旦小偷进入了大厦，或内部人员有越界的行为，监控系统能够立即发出警报。

因此，入侵检测系统应当“放置”在所关注流量数据必经的链路上。入侵检测系统的架构如图1所示事件产生器是从整个网络中获取事件，并将获取的事件提供给系统的其他部分；事件分析器是分析获取的事件，若发现异常，则通知响应单元；响应单元是对分析的结果做出相应的反应；事件数据库中存放过程数据。

```

​												**框架**

![image-20240227232923951](C:\Users\ling\AppData\Roaming\Typora\typora-user-images\image-20240227232923951.png)

## 2、IDS的分类

```
入侵检测系统按照数据源、检测方法、工作方式和体系结构进行分类。其具体分类如下所示：
基于数据源的分类
	基于主机的入侵检测
	基于网络的入侵检测
基于检测方法分类
	基于误用的入侵检测
		基于专家系统的误用检测方法
		基于状态迁移分析的误用检测方法
		基于健盘监控的误用检测方法
		基于条件概率的误用检测方法	
	基于异常的入侵检测
		基于神经网络的异常检测技术
		基于模式预测的异常检测技术
		基于数据挖掘的异常检测技术
基于工作方式分类
	在线检测
	离线检测
基于体系结构分类
	集中式
	分布式
```

```
从技术上，入侵检测也可分为两类：一种基于特征（误用检测）（signature—based），另一种基于异常情况（anomaly—based）。而我们接下来所使用的 Snort 就是基于误用检测的入侵检测系统，也称为基于特征的入侵检测系统。
对于基于标识的检测技术来说，首先要定义违背安全策略的事件的特征，如网络数据包的某些头信息。检测主要判别这类特征是否在所收集到的数据中出现。此方法非常类似杀毒软件。
而基于异常的检测技术则是先定义一组系统“正常”情况的数值，如CPU利用率、内存利用率、文件校验和等（这类数据可以人为定义，也可以通过观察系统、并用统计的办法得出），然后将系统运行时的数值与所定义的“正常”情况比较，得出是否有被攻击的迹象。这种检测方式的核心在于如何定义所谓的“正常”情况。
SNORT是一个强大的轻量级的网络入侵检测系统，它具有实时数据流量分析和日志IP网络数据包的能力，能够进行协议分析，对内容搜索或者匹配。它是一个基于特征检测的入侵检测系统。
```

## 3、发展应用趋势

```
机器学习（深度学习、强化学习、联邦学习）等技术的使用、分布式入侵检测(DIDS)
```

## 4、IDS的局限性

```
·对用户知识要求较高，配置、操作和管理使用较为复杂
·网络发展迅速，对入侵检测系统的处理性能要求越来越高，现有技术难以满足实际需要
·高虚警率，用户处理的负担重北玄-u＿
北玄-u＿656
·由于警告信息记录的不完整，许多警告信息可能无法与入侵行为相关联，难以
得到有用的结果
·在应对自身的攻击时，对其他数据的检测也可能会被抑制或受到影响
```





## 5、IDS与WAF的区别

```
IDS（入侵检测系统）是IPS的前身，本质上是被动的。该设备未与流量串北玄-u＿
联插入，而是并行（带外放置）。通过交换机的流量也同时发送到IDS进行检查。如果在网络流量中检测到安全异常，则IDS只会向管理员发出警报，
北玄-u＿656 但无法阻止流量。与IPS相似，IDS设备还主要使用已知安全攻击和漏洞利
用的特征来检测入侵企图。为了将流量发送到IDS，交换设备必须配置一个SPAN端口，以便复制流量并将其发送到IDS节点。尽管IDS在网络中是被动的（即它不能主动阻止流量），但是有些模型可以与防火墙配合使用以阻止安全攻击。例如，如果IDS检测到攻击，则IDS可以向防火墙发送命令以阻止特定的数据包。
WAF（Web应用程序防火墙）专注于保护网站（或通常的Web应用程序）。它在应用程序层工作以检查HTTPWeb流量，以检测针对网站的恶意攻击。例如，WAF将检测SQL注入攻击，跨站点脚本，Javascript攻击，RFI／LFI 改大等一当于光会与多数网些（HTTP），因此WAF还可以通过终止SSL会话并在WAF本身上检查连接内部的流量来提供SSL加速和SSL检查；带有WAF的防火墙，它被放置在网站的前面（通常）在防火墙的DMZ区域中。有了WAF，管理员可以灵活地限制对网站特定部分的Web访问，提供强身份验证，检查或限制文件上传到网站等。
```

# 二. 开源IDS-Snort的简介

```
SNORT 是一个强大的轻量级的网络入侵检测系统，它具有实时数据流量分析和日志 IP网络数据包的能力，能够进行协议分析，对内容搜索或者匹配。
它是一个基于特征检测的入侵检测系统。
官网链接：https：／／www.snort.org／
snort 有三种工作模式：嗅探器、数据包记录器、网络入侵检测系统。


嗅探器模式仅仅
是从网络上读取数据包并作为连续不断的流显示在终端上。

数据包记录器模式把数据包记录到硬盘上。

网路入侵检测模式是最复杂的，而且是可配置的。我们可以让snort分析网络数据流以匹配用户定义的一些规则，并根据检测结果采取一定的动作。
```

## 1. Snort的安装与部署

### 1、预装dag．所需程序

```
					输入命令:
-yum install -y gcc flex bison zlib libpcap pcre libdnet tcpdumpe 
					输入命令下载依赖工具:
-yum install-y zlib-devel libpcap-devel pere-devel libdnet devel openssl-devel libnghttp2-devel luait-devel
					输入命令下载daq 包：
-wget https://www.snort.org／downloads/snort/daq-2.0.6.tar.gz
					输入命令解压tar包：
-tar-xzvf daq-2.0.6．tar．gz 
					输入命令进入文件夹：
—cd /daq—2.0.6
					依次输入命令编译安装：
—/configure
-make
-make install
```

## 2、安装Snort

```
在官网下载Snort-2.9.9.0，移动到/usr/local目录
					输入命令：
-tar -xzvf snort-2.9.9.0.tar.gz
					输入命令进入目录:
-cd snort-2.9.9.0/
					依次输入命令编译安装
./configure
-make
-make install
					此时输入命令验证是否成功：
-snort -v
```



## 3、Snort的配置

```
创建snort配置（及规则）目录，创建运行需要目录
-mkdir -p /etc/snort/rules
-mkdir /usr/local/lib/snort.dynamicrules 

首先将解压出来的etc下的默认配置文件复制到snort配置目录下，可通过命令
行或直接复制粘贴的形式进行。

```

```
						打开终端依次输入命令启用社区规则文件：
-echo " >> /etc/snort/snort.conf
-echo '# enable community rule' >> /etc/snort/s 
-echo 'include $RULE_PATH/community-rules' >> /etc/snort/snort.conf
-sed -i 's/var RULE_PATH..Vrules/var RULE_PATH.Vrules/' 
/etc/snort/snort.conf
-sed -i 's/var RULE_PATH_Vrules/var RULE_PATH.Vrules/' /etc/snort/snort.conf
-sed -i 's/var WHITE_LIST_PATH..Vrules/var WHITE_LIST_PATH.Vrules/
/etc/snort/snort.conf
-sed -i 's/var BLACK_LIST_PATH..Vrules/var BLACK_LIST_PATH.Vrules/ '/etc/snort/snort.conf

```

## 4、创建默认使用的白名单文件

```
-touch/etc/snort/rules/white list.rules
```

## 5、创建默认的黑名单文件

```
-fouch/etc/snort/rules/black list.rules
```

## 6、创建默认自己设置的规则文件（之后自己创建的规则都写到这个规则集里)

```
-touch/etc/snort/rules/local.rules
```

## 7、注释掉所有默认要加载的规则文件

```
-sed -i 's/include \$RULE\_PATH/#include \SRULE\_PATH/' /etc/snort/snort conf

测试配置文件是否有误，用命令jnort -T -c /etc/snort/snort.conf
```

## 8，在snort.conf文件中加入新建文件集路径

```
#enable community rule
#include $RULE_PATH/community-rules/community.rules
include $RULE_PATH/local.rules
#include $RULE_PATH/black list.rules
#include $RULE_PATH/white list.rules



```

## 9、 安装 xampp


输入命令下载

```
					下载命令：
xampp-wget https://www.apachefriends.org/xampp-files/8.1.6/xampp-linux-x64-8.1.6-0-installer.run --no-check-certificate
					输入命令：
		-chmod 777 xampp-linux-x64-8.1.6-0-installer.run
					输入命令安装：
-./xampp-linux-x64-8.1.6-0-installer.run

启动 musal database 和 apache web server
打开浏览器输入 localhost
```

## 10、建立一个测试网页

```
/opt/lampp/htdocs
```

```
<meta charset="utf-8">
<title>test</title>
</head>
<body>
	<h1>successful</h1>
	<p></p>
 </body>
</html>
```

在终端中将centos虚拟机的防火墙设置为桥接模式。
输入命令:

```
-systemctl stop firewalld.service
```

这样既可在实体机中访问虚拟机的网络

```
输入:
host：8088／test．html
```

## 11、编写规则

```
打开/etc/snort/rules/local.rules文件，输入
alert tcp ![192.168.0.100] any -> 192.168.0.100 8088 (logto:"task1";msg:"this is task 1";sid:1000001)


1）alert 表示这是一个警告。

2）tcp表示要检测所有使用tcp协议的包，因为http／部分。

3）接下来的一部分表示源IP地址，其中“！”表示除了后面IP的所有IP，因此！［192.168.43.73］表示的就是除了本机之外的所有主机。

4）再后面的一个表示端口，any表示源IP地址任何一个端口，也就是说源
IP地址的主机不管哪个端口发送的包都会被检测。—＞表示检测的包的传送方向，表示从源IP传向目的IP。下面的一个字段表示目的IP，在这里表示主机。

5）括号中的规则选项部分，logto表示将产生的信息记录到文件，msg表示在屏幕上打印一个信息，sid表示一个规则编号，如果不在规则中编写这个编号，则执行过程中会出错，而且这个编号是唯一的能够标识一个规则的凭证，1000000以上用于用户自行编写的规则。


输入命令：
snort -dev -l /var/log/snort-h 192.168.43.73 -c /etc/snort/snort.conf 

其中／var／log／snort为警报日志生成的位置。
```

## 12、再次通过windows 访问 test．html网页

