#  一. Web Application Firewall

```
										Web应用防护系统
也称为：网站应用级入侵防御系统。英文：Web Application Firewall，简称：WAF。利用国际上公认的一种说法：Web应用防火墙是通过执行一系列针对HTTP／HTTPS的安全策略来专门为Web应用提供保护的一款产品。
```

```
											产生背景
当WEB应用越来越为丰富的同时，WEB服务器以其强大的计算能力、处理性能及蕴含的较高价值逐渐成为主要攻击目标。SQL注入、网页篡改、网页挂马等安全事件，频繁发生。2007年，国家计算机网络应急技术处理协调中心（简称CNCERT／CC）监测到中国大陆被篡改网站总数累积达61228个，比2006年增加了1.5倍。其中，中国大陆政府网站被篡改各月累计达4234个。
```

```
企业等用户一般采用防火墙作为安全保障体系的第一道防线。但是在现实中，难以预防，因为这些问题是普通防火墙难以检测和阻断的，由此产生了WAF（Web应用防护系统）。

```

## 作用：

```
Web应用防护系统（Web Application Firewall，简称：WAF）
代表了一类新兴的信 息安全技术，用以解决诸如防火墙一类传统设备束手无策的Web应用安全问题。
与传统防火墙不同，WAF工作在应用层，因此对Web应用防护具有先天的技术优势。
基于对Web应用业务和逻辑的深刻理解，WAF对来自Web应用程序客户端的各类请求进行内容检测和验证，确保其安全性与合法性，对非法的请求予以实时阻断，从而对各类网站站点进行有效防护。
```

## 1、WAF安全防护的主要功能：

```
漏洞攻击防护：WAF安全防护目前可拦截常见的web 漏洞攻击，例如SQL注入、xSS跨站、获取敏感信息、利用开源组件漏洞的攻击等常见的攻击行为。

虚拟补丁：WAF安全防护可提供0Day，NDay漏洞防护。当发现有未公开的0Day
漏洞，或者刚公开但未修复的NDay漏洞被利用时，WAF可以在发现漏洞到用户修复漏洞这段空档期对漏洞增加虚拟补丁，抵挡黑客的攻击，防护网站安全。
```

##  2、WAF安全防护系统特点：

```
实时防护：WAF安全防护可以实时阻断黑客通过web漏洞试图入侵服务器、危
害用户等恶意行为；可以实时屏蔽恶意扫描程序爬虫，为您的系统节省带宽和资源
```

## 3、WAF安全防护的用途：

```
												提供安全保护
网站安全防护（WAF）专门保护网站免受黑客攻击，能有效阻挡黑客拖库、恶意扫描等行为；同时在0day漏洞爆发时，可以快速响应，拦截针对此类漏洞的攻击请求。

												防护漏洞攻击
网站安全防护（WAF）目前可拦截常见的web漏洞攻击，例如SQL
注入，XSS跨站、获取敏感信息、利用开源组件漏洞的攻击等常见的攻击行为。
```

## 4、网站安全防护的工作原理：

```
网站安全防护（WAF）基于对http请求的分析，如果检测到请求是攻击行为，则会对请求进行阻断，不会让请求到业务的机器上去，提高业务的安全性，为web应用提供实时的防护。

								基于http和https协议
```

```
1，安装相应依赖
yum install -y wget epel-release

2,安装依赖工具
yum install -y httpd httpd-devel pcre pcre-devel libxml2-devel gcc lua-devel yajl-devel ssdeep-devel curl-devel


3,编译Modsecurit
	1)modsecurity安装包上传至/usr/local (.tar.gz)
	2)tar -zxvf modsecurity-2.9.3.tar.gz
	3)cd modsecurity-2.9.3
	4)./configure --enable-standalone-module --disable-mlogc
	5)make
	
4,安装nginx
	1)cd /usr/local
	2)wget http://nginx.org/download/nginx-1.16.1.tar.gz
	3)tar -xvzf nginx-1.16.1.tar.gz
	4)cd /usr/local/nginx-1.16
	5)./configure --add-module=/usr/local/modsecurity-2.9.3/nginx/modsecurity/ --prefix=/usr/local/nginx
	make
	make install
	#启动nginx
	/usr/local/nginx/sbin/nginx
```

```
1)ifconfig     #查看ip
				#SQL注入
	192.168.122.1/?param=%22%3E%3Cscript%3Ealert(1);%3C/script%3E
	
2)配置文件
	mkdir -p /usr/local/nginx/modsecurity/
	cp //usr/local/modsecurity-2.9.3/modsecurity.conf-recommended
	/usr/local/nginx/conf/modsecurity/modsecurity.conf
	cp /usr/local/modsecurity-2.9.3/unicode.mapping
	usr/local/nginx/conf/modsecurity/unicode.mapping
	
6)	
	将规则表解压后复制 crs-setup.conf.example    						
	/usr/local/nginx/conf/modsecurity/下并重命名为crs-setup.conf;
	复制rules文件夹到/usr/local/nginx/conf/modsecurity/下，同时修改REQUEST-900-EXCLUSION-RULES-BEFORE-CRS.conf.example与REQUEST-900-EXCLUSION-RULES-AFTER-CRS.conf.example两个文件的名称，将.example删除，可将自己写的规则放置于此两个文件中

7)编辑nginx.conf
在http或server节点中添加以下内容（ps:在http节点添加表示全局配置，在server节点添加表示为指定网络配置）
ModSecurityEnabled on;
ModSecurityConfig modsecurity/modsecurity.conf;

8)编辑modsecurity.conf
		在末尾添加以下内容
Include crs-setup.conf
Include rules/*.cnf

9)重新加载Nginx测试效果
/usr/local/nginx/sbin/nginx -s reload
```

#  二.ModSecurity简介

## 1、简介

```
ModSecurity是目前世界上使用最多的开源WAF产品，可谓是WAF界的鼻祖，很多其他WAF产品都或多或少受其影响，如OpenWAF。

ModSecurity是一个开源的、跨平台的Web应用防火墙（WAF），被称为WAF界 的“瑞士军刀”。它可以通过检查 Web服务接收到的数据，以及发送出去的数据来对网站进行安全防护。
```

## 2、ModSecurity 功能介绍 

```
SQL Injection （SQLi）：阻止SQL注入

Cross Site Scripting（XSS）：阻止跨站脚本攻击 

Local File Inclusion（LFI）：阻止利用本地文件包含漏洞进行攻击 Remote File Inclusione（RFI）：阻止利用远程文件包含漏洞进行攻击

北玄-u＿656 Remote Code Execution（RCE）：阻止利用远程命令执行漏洞进行攻击

PHP Code Injectiod：阻止PHP代码注入

HTTP Protocol Violations：阻止违反HTTP协议的恶意访问 

HTTPoxy：阻止利用远程代理感染漏洞进行攻击

Sshllshock：阻止利用 Shellshock 漏洞进行攻击

Session Fixation：阻止利用 Session会话ID不变的漏洞进行攻击

Scanner Detection：阻止黑客扫描网站

Metadata／Error Leakages：阻止源代码／错误信息泄露 

Project Honey Pot Blacklist：蜜罐项目黑名单

GeoIP Country Blocking：根据判断IP地址归属地来进行IP阻断 
```

```
社区
官方：https://github.com/SpiderLabs/ModSecurity
中文社区：http://modsecurity.cn

```

#  三. BYPASS WAF

```
BYPASS WAF 实际上是去寻找位于WAF设备之后处理应用层数据包的硬件／软件的特性。利用特性构造WAF不能命中，但是在应用程序能够执行成功的载荷，绕过防护。

那些特性就像是一个个特定的场景一样，一些是已经被研究人员发现的，一些是还没被发现，等待被研究人员发现的。当我们的程序满足了这一个个的场景，倘若WAF没有考虑到这些场景，我们就可以利用这些特性bypass掉WAF了。
```

```
例如我们现在需要bypass一个云WAF／IPS／硬件WAF，此处我们可以利用的点就是：

1．Web架构层bypass

2．Web服务器层bypass 

3．Web应用程序层 bypass 

4．数据库层bypass

5．WAF层bypass
```

## 1,WAF的分类

```
1、云WAF

在配置云WAF时（通常是CDN包含的WAF），DNS需要解析到CDN的jp上去，在请求uri时，数据包就会先经过云WAF进行检测，如果通过再将数据包流给主机。

 														2、主机防护软件

在主机上预先安装了这种防护软件，可用于扫描和保护主机（废话），和监听 web 端口的流量是否有恶意的，所以这种从功能上讲较为全面。这里再插一嘴，mod security、ngx—lua—WAF 这类开源 WAF虽然看起来不错，但是有个弱点就是升级的成本会高一些。

													3、硬件ips／ids防护、硬件WAF
使用专门硬件防护设备的方式，当向主机请求时，会先将流量经过此设备进行流量清洗和拦截，如果通过再将数据包流给主机。

														4、软WAF

软件WAF 则是安装在需要防护的服务器上，实现方式通常是WAF 监听端口或以Web 容器扩展方式进行请求检测和阻断。
```

```
假设客户端访问 url：http：／／www．miku．com／1．php？id＝1＇and＇1＇＝＇1，该请求请求的数据是服 务器上数据库中id为1的记录。
假设这台服务器使用了相关云WAF。
1）一个完整的过程，首先会请求DNS，由于配置云WAF的时候，会修改DNS的解析。我们发送DNS请求之后，域名会被解析到云WAF的ip上去。DNS解析完成之后，获取到域名信息，然后进入下一个步骤。
2）HTTP协议是应用层协议，月是tco协议，因此会首先夫做TCP的三次握手，此处不去抠三次握手的细节，假设三次握手建立完毕。
3）发送 HTTP 请求过去，请求会依次经过云 WAF，硬件 IPS/IDS 设备，硬件 WAF 设备，服务器，web 服务器，主机防护软件/软 WAF，WEB 程序，数据库。 云 WAF，硬件IPS/IDS，硬件 WAF 均有自己处理数据的方式。

在获取 HTTP 数据之前会做 TCP 重组，重组主要目的是针对互联网数据包在网络上传输的时候会出现乱序的情况，数据包被重组之后就会做协议解析，取出相关的值。如http method=GET，http payload=xxx 等等。这些值就对应了IPS 规则中相关规则的值。从而来判断规则匹配与不匹配。
```

## 2，Web架构层bypass 

```
架构层面绕过

										1、寻找真实IP

云WAF通过修改DNS解析隐藏了真实IP地址
查找域名解析记录
利用邮件发送功能来抓包，获取直实IP

										2，畸形数据包BYPASS
 GET型请求转POST型
Content-Length头长度大于4008 
正常参数放在垃圾数据后面
```

## 3,Web Server 层 bypass 

### 1、Apache

​	

```
									1.1、畸形method
某些 apache 版本（version 2．＊）在做 GET 请求的时候，无论 method 为何值均会取出GET的内容，如请求为的method为DOTA2，依然返回了aid为2的结果。
如果某些WAF在处理数据的时候严格按照 GET，POST 等方式来获取数据，就会因为apache的宽松的请求方式导致bypass。
实例:
我们使用实体机安装DVWA＋phpstudy 搭建测试环境，测试的内容是某些 apache 版本与waf解析 request时的不同.
							1.2，php＋apache 畸形的boundary
php在解析 multipart data的时候有自己的特性，对于boundary的识别，只取了逗号 前面的内容，例如我们设置的boundary 为————aaaa，123456，php 解析的时候只识别了————aaaa，后面的内容均没有识别。然而其他的如WAF 在做解析的时候，有可能获取的是整个字符串，此时可能就会出现BYPASS。
										什么是multipart data？
Multipart／form—data 的请求方式来完成上传图片等服务器交互的操作，这需要我们去严格按照规范的格式来组装请求体，每一个换行每一个空格都是不可忽略的。
Multipart／form-data的基础方法是POST，也就是说是由POST方法来组合实现的. Multipart／form-data与POST方法的不同之处在于请求头和请求体
Multipart／form-data的请求头必须包含一个特殊的头信息：Content-Type，且其值也必须规定为 multipart／form—data，同时还需要规定一个内容分割符用于分割请求体中的多个POST的内容，如文件内容和文本内容自然需要分割开来，不然接收方就无法正常解析和还原这个文件了
Multipart／form—data的请求体也是一个字符串，不过和post的请求体不同的是它的构造方式，post是简单的name＝value值连接，而Multipart／form-data则是添加了分隔 符等内容的构造体
请求的头部信息如下：
Content-Type：multipart／form-data；boundary＝你的自定义boundary
我们先说一下请求头部的信息boundary这个参数是分界线的意思，也就是说你在请求头中指定分界线为：你的自定义boundary，那么请求体中凡是你的自定义boundary这样的字段都会被视为分界线，这个分界线参数具体是什么你可以随意自定义。
 我们可以看到：
				Content-Disposition： form-data； name＝＂upload＂； filename＝＂img.jpg”
这一行中name 后面跟着一个字符串，其中包含该字段的内容引用的HTML 字段的名称。在同一字段中处理多个文件（例如元素的 multiple 属性＜input type＝file＞）时，可能会有几个具有相同名称的子部分。
filename 后面是一个包含传输文件的原始名称的字符串。文件名始终是可选的，不能被应用程序言目使用：路径信息应该被删除，并且应该转换为服务器文件系统规则。该参数提供大部分指示性信息。当与其结合使用时 Content-Disposition： attachment， 它被用作提供给 user.filename的最终“另存为”对话框的默认文件名
参数“filename”和“filename＊”的区别仅在于“filename＊”使用 RFC 5987中定义的编码。
当“文件名”和“文件名＊”都出现在单个标题字段值中时，“文件名＊”优于“文件名”。将post请求修改成以上摸样后点击forward，我们可以看到上传成功。那么也就是说，php在解析分隔符时会自动忽略，之后的内容正常解析请求，然而某些waf会把这数个 content-disposition 识别为一整串内容，从而达到bypass的效果。 
```

### 2、iis

```
								2.1、 1％特性
在asp＋iis的环境中存在一个特性，就是特殊符号％，在该环境下当们我输入 s％elect的
北玄-u＿656 时候，在WAF层可能解析出来的结果就是s％elect，但是在iis＋asp的环境的时候，解
析出来的结果为select。
本地搭建asp＋iis环境测试：
1)首先在实体机或是虚拟机中安装iis＋asp 环境，安装配置方法自行查找，本课程中不再涉及
2)随后我们在存放本地页面的文件夹中创建一个名为index.asp的文件用记事本打开后输入以下内容并保存：

<form method="get" action="simpleform.asp"><
<p>First Name: <input type="text" name="fname" /></p><
北玄-u＿656 <p>Last Name: <input type="text" name="Iname" /></p><
<input type="submit" value="Submit" />< </form>


3)随后我们创建第二个新的名为simpleform.asp的文件
用记事本打开后输入以下内容保存:
我们可以看到一个简单的submit框
 分别输入：
		wa%sj
		Inc 
随后点击 submite 

这是我们发现，在url地址栏中的的％并没有被iis＋asp解析出来，页面上显示的及
俄国为 welcome wasj inc。
因此这就是iis环境中的％特性，我们可以依次这个特性构造诸如sel＠ect的语句利用waf与iis服务器解析的差异达到bypass效果。

									2.2、u％特性
lis 服务器支持对于unicode的解析，例如我们对于select 中的字符进行 unicode 编码，可以得到如下的s％u006c％u0006ect，这种字符在IIS接收到之后会被转换为select，但是对于WAF层，可能接收到的内容还是 s％u006c％u0006ect，这样就会形成bypass的可能。
我们搭建asp＋iis和aspx＋iis的环境：
在index.asp页面我们分别输入以下内容：
						s%u0065%u006cect
						select 
我们可以看到，我们用unicode 编码％u0065与％u006c来替换掉字母e和l，但iis服务器在此处处理时将其％u0065转化成了％25u0065。因此我们将该页面url地址改为：http://localhost:8099/simpleform.asp?fname=s%u0065%u006cect&Iname=selects
敲击回车我们即可看到iis在接收到该地址之后会自动将 unicode 字符％u0065
与％u006c 解析为字母转化为select，而一些 waf 则会原原本本的接受北玄-u＿656
s％u0065％u006cect，从而产生差异达到bypass的效果。 

								2.3、另类％u特性
该漏洞主要利用的是unicode 在iis 解析之后会被转换成 multibyte，但是转换的过程中可能出现：多个 widechar会有可能转换为同一个字符。
打个比方就是譬如select中的e对应的 unicode为％u0065，但是％u00f0同样会被转换成为e。
s%u0065lect->select 
s%u00fOlect->select<
北玄-u＿656 WAF层可能能识别s％u0065lect的形式，但是很有可能识别不了s％u00fOlect的形式。
这样就可以利用起来做WAF的绕过。
实例如下，无论是s％u0065lect还是％u00fOlect 都被处理成为了字母e
```

 **安装配置dvwa的具体步骤不再详细给出**

 **XP.cN小皮**

## 4. Web应用程序层bypass

### 1.1、双重url编码

```
双重url编码，即对于浏览器发送的数据进行了两次urlencode 操作，如s做一次
url编码是％73，再进行一次编码是％25％37％33。一般情况下数据经过WAF 设备的时候只会做一次url解码，这样解码之后的数据一般不会匹配到规则，达到了bypass的效果。
效果如下所示：
					一次url编码
			
PS: 注意，虽然此处我们的实验并不存在 waf，但本质的原理是一样的，就是通过 waf
可能存在的没有多重解码的漏洞达到bypass效果。
```

### 1.2、扩展：nginx url解码问题带来的waf绕过漏洞

```
Nginx ngx unescape uri 函数在处理 url decode 时没有遵照标准的 url decode， 从而引起一系列使用该函数解码的waf都存在绕过漏洞。
 出现该问题的函数位于src＼core＼ngx＿string.c 代码中 ngx unescape uri（u char ＊＊dst，u char ＊＊src， size＿t size，ngx uint t type）该函数在处理％号编码时，如果％后面第一个 字符非16进制范围则会丢弃％，否则第二个字符非16进制范围则会丢弃％和第一个字符，具体表现为Sql注入关键字 select 如果写成 s％elect 经过ngx编码处理后则会变成 slect 从而绕过waf 过滤规则，例如IIS asp 对 s％elect的编码处理结果为select，还有％and经过ngx解码函数后会变为nd等等。
 例如上面提到的 s％elct 编码处理后会变成 slect，所以该代码依然存在编码处理畸形Waf规则被绕过的问题，除了select还有其他的很多关键字都可以绕过。
 这里不仅是NAXSI，很多使用nginx 解码代码的模块都存在该问题，例如nginx lua 模块中的 ngx.unescape uri 和 ngx.req.get uri args 等
```

### 1.3、请求获取方式

```
								1.3.1、变更请求方式
1)GET,POST.COOKIE
在web环境下有时候会出现统一参数获取的情况，主要目的就是对于获取的参数进行统一过滤。例如我获取的参数t＝select 1 from 2 这个参数可以从get参数中获取，可以从post参数获取，也可以从cookie参数中获取。
典型的dedecms，在之前测试的时候就发现了有些 waf.厂商进行过滤的时候过滤了get和post，但是cookie没有过滤，直接更改cookie参数提交 payload，即绕过.
2)ydencode 和 form-data POSTe
在提交数据的时候有两种方式，第一种方式是使用 udlencode的方式提交，第二种方式是使用form—data的方式提交。当我们在测试站点的时候，如果发现POST提
交的数据被过滤掉了，此时可以考虑使用form—data的方式去提交。
实例：
我们继续使用dwwa 靶场来进行实验，在虚拟机中打开 dywa.靶场页面，进入 sslinjection一栏。将安全级别切换至low
随后我们在在该页面试图进行sal注入，注入语句如下所示：
					?id=-1' union select 1, version()#

该语句旨在向我们返回该数据库版本。
Bp将会为我们拦截下该条请求,随后我们再次点击 send，我们便得到了同 get 一样的 responce
那么接下来我们尝试用另一种格式的post来进行请求
Bp 工具相当方便的可以一键转换 urlencode 和 form—data。同样在上个页面，我们右键后点击 change body encoding,就取得了当前数据库的版本号。
因此，我们可以通过转换 post 请求与 get 请求，并且改变 post 请求格式来达到bypass的效果。
1.3.2、①asp／asp．net request 解析
在asp和asp.net 中使用参数获取用户的提交的参数一般使用 request 包，譬如使用request［＂］来获取的时候可能就会出现问题。
当使用request［＂］的形式获取包的时候，会出现GET，POST分不清的情况，譬如可以
构造一个请求包，METHOD为GET，但是包中还带有POST的内容和 POST的content-type。
我们搭建一个实例： 
我们创建一个letmetest.aspx的界面获取用户提交的内容，并且将request［＇t］的内容打印出来。

 									1.4、HPP
HPP是指HTTP参数污染。形如以下形式：
？id＝1＆id＝2＆id＝3的形式，此种形式在获取id值的时候不同的web技术获取的值是不一样的。
假设提交的参数即为：1
id=1&id=2&id=3
Asp.net+jis:id=1.2.3
Asp+js:id=1.2,3 
Php+apache: id=3
如此可以分析：当WAF获取参数的形式与WEB程序获取参数的形式不一致的时候，就可能出现WAF bypass的可能。

Ps.此处关键还是要分析 WAF 对于获取参数的方式是如何处理的。这里也要再提一下的，beR的灵活运用，譬如有些cms，基于url的白名单，因此可以利用bep的方式在参数一的位置添加白名单目录，参数2的位置添加恶意的 payload。形如jndex,pho?a=[whitelist]&a=select 1 union select 2
```



## 5.数据库层bypass

数据库层bypass常常是在bypass waf的sql注入防护规则。我们需要针对数据库使用该数据库的特性即可。如 mxsal，salserver等等。 

Ps.目前数据库被暴露出来的特性很多很多，基本上很多特性综合利用就已经够用了，因此特性知不知道是一方面，能不能灵活运用就得看测试者自己了。

### 1、mxsql数据库

```
就目前来看 mysgl是使用最多的，也是研究人员研究最深的数据库。测试的角度上我一般有测试下面的过滤点，因为一般绕过了select from 就基本可以sgl注入获取数据了。
 								1.1、常见过滤的位置
					第一：参数和union之间的位置
1).Wunion，的形式
mysql> select runoob author from runoob_tbl where runoob_id=\Nunion select schem a_name from information_schema.schemata;
2).浮点数的形式如：1.1，8.0
mysql> select runoob author from runoob_tbl where runoob_id=1.lunion select sche ma_name from information_schema.schemata;
3).8e0的形式： mysql>
mysql> select runoob_author from runoob_tbl where runoob_id=8eOunion select schema_name from information_schema.schemata;
4).利用／＊！50000＊／的形式
mysql> select runoob_author from runoob_tbl where runoob_id=-3/*!50000*/union se lect schema_name from information_schema.schemata;

					第二：union和 select之前的位置
1）空白字符
Mxsal中可以利用的空白字符有：％09，％0a，％Ob，％Oc，MOd，％a0； 
2）注释
使用空白注释
MYSQL中可以利用的空白字符有：
 			/**/
 			/letmetest/ 
3）使用括号
	常见过滤函数:
		字符串截取函数:
					Mid(version0.1.1)
					Substr(version0.1.1)
					Substring(version0.1.1)
					Lpad(verson0.1,1)
					Road(version0.1.1)
					reverse(right(reverse(version()).
		字符串连接函数:
					concat(version().T.user0):
					concat ws(T.1.2,3) 

	字符转换
Ascii（1）此函数之前测试某云waf的时候被过滤了，然后使用asci（1）即可
		Char(49)
		Hex("a') 
		Unbex(61) 

4）讨滤了语号
						limit处的逗号： 
								limit 1 offset 0
字符串截取处的逗号mid处的逗号： mid(version() from 1 for 1)
mysql> select runoob author from runoob tbl where runoob id=1 union select mid(\ersion() from 1 for 10);
						union处的逗号： 
								通过join拼接。
mysql> select runoob_author,runoob_id from WASJ.runoob_tbl where runoob id=8e0u nion select * from (select 1)a jpin (select{x schema_name} from-information_sche ma.schemata limit 1)b;
```



### 2 .sqlserver数据库

```
									1）常见过滤位置 

					1,select from 后的位置 空白符号：
01,02,03,04,05,06,07.08.09,0A,OB,OC,OD,0E,OF,10.11,12,13,14,15,16.17.18,19,1A,1B,1C,1D 1E.1F.20
需要做 urencode salserver中的表示空白字符比较多，靠黑名单去阻断一般不合适。
注释符号Mssgl也可以使用注释符号／＊／其他符号：符号
实例：
我们拉取并启动sqlserver2017 官方镜像（不再演示）
使用命令：
CREATE DATABASE TestDB 
GO
创建演示用数据库TestDB,之后使用命令
USE TestDB:
CREATE TABLE Inventory (id INT, name NVARCHAR(50), quantity INT)
INSERT INTO Inventory VALUES (1, 'banana', 150); INSERT INTO Inventory VALUES (2,'orange', 154);
GO
创建表并插入数据
随后我们输入语句：
Select • from t1;
GO
随后我们在注入点添加
Select • from Invertory
GO
可到到相同结果
				2,select from之间的位置
空白符号：
01,02,03.04.05,06.07.08.09.0A,OB.OC,OD.OE.OF,10.11,12.13,14,15,16,17.18,19,1A,1B,1C,1D
注释符号Mssal也可以使用注释符号／＊＊／
SELECT FROM Tnventory
go 
							：号 sal server2017不再适用
				3,and之后的位置
空白符号： 
01,02,03.04.05,06.07.08,09,0A,0B,OC,OD.0E,OF,10.11,12,13,14.15,16,17,18,19,1A,1B,1C.1D ,1E,1F,20
注释符号
PS:Mssal也可以使用注释符号／＊／
SELECT /**/*FROM Inventory
go
					:号：server2017不再适用 

										
										
										
										2）常见过滤函数
			（1）字符串截取函数

Substring(@@version.1.1) 
Left(@@version.1)

 			（2）字符串转换函数
Ascii（＇a＇）这里的函数可以在括号之间添加空格的，一些waf过滤不严会导致bypassChar('97)

			（3）其他方式
Mssql.支持多语句查询，因此可以使用；结束上面的查询语句，然后执行自己构造的语句。

使用exec的方式：
例如我们构造语句使返回查询结果的时间向后延迟五秒钟
select * from Inventory where quantity>152; exec('wa'+'itfor delay''0:0:5***) 
go

即可发现确实能够执行后半部分延迟五秒的效果。
使用sp executesal的方式，我们发现同样可以得到延迟效果。
使用这类可以对自己的参数进行拼接，可以绕过WAF防御。
如使用该类特性然后加上上面提到的：的特性就可以绕过安全狗的注入防御。
```



## 6.WAF层bypass



### 1、性能 bypass

```
WAF 在设计的时候都会考虑到性能问题，例如如果是基于数据包的话会考虑检测，数据包的包长，如果是基于数据流的话就会考虑检测一条数据流的多少个字节。一般这类算检测的性能，同时为了保证WAF的正常运行，往往还会做一个bypass设计在性能如 Gpu 高于 80%或则内存使用率高于如 80%是时候，会做检测 bypass，以保证设备的正常运行。
 
WAF等设备都是工作在应用层之上的，如HTTP.FTP.SMTP等都是应用层的协议，这些数据要被处理都会被进行数据解析，协议分析。最终获取应用层的数据。如HTTP的方法是什么， HTTP的querystring.是什么，以及HTTP的requestbody是什么。然后将这些实时获取的值与 WAF设计的规则进行匹配，匹配上着命中规则做相应的处理。
```



#### 1.1、性能检测 bypass

```
现在问题就是检测多长呢？例如我用HTTP POST上传一个2G的文件，明显不可能2G
全做检测不但耗CPU，同时也会耗内存。因此在设计WAF的时候可能就会设计一个默认值，有可能是默认多少个字节的流大小，可能是多少个数据包。

测试安全狗的，大致原理应该是通过一个脚本，不断的向HTTP POST添加填充数据，当将填充数据添加到一定数目之后，发现POST中的sgl注入恶意代码没有被检测了。最终达到了hynass的目的
```

### 1.2、性能负载 bypass

```
一些传统硬件防护设备为了避免在高负载的时候影响用户体验，如延时等等问题，会考虑在高负载的时候 bypass掉自己的防护功能，等到设备的负载低于门限值的时候又恢复正常工作。
一些高性能的WAF可能使用这种方法可能不能bypass，但是一些软WAF使用这种方式还是可以bypass的。
一个bypass的例子，将请求并发同时发送多次，多次访问的时候就有几次漏掉了，没有触发waf的拦截。
例如制造了一个payload，同时添加了大量的无效数据，使用脚本发送该请求，发现请求的时候有些通过了WAF，有些被WAF所拦截了。应该就是性能问题导致了 bypass。
```

### 1.3、fuzz bypass

```
 使用脚本去探测WAF设备对于字符处理是否有异常，上面已经说过WAF 在接收到网
符解析出错，造成全局的bypass。我测试的时候常常测试的位置：
					1）：get请求处
					2）：header请求处 
					3）：post urlencode内容处 
					4）： post form-data 内容处 

然后模糊测试的基础内容有：
					1）编码过的0—255字符
					2）进行编码的0—255字符
					3）utf gbk字符
			实例1：
在一次测试安全狗的过程中，使用post的方式提交数据，提交数据包括两个参数，一个是正常的fuzz点，另一个参数包含一个sgl注入语句。当在测试前面的fuzz点的时候，处理到＼x00的字符的时候，没有提示安全狗阻拦。应该是解析这个字符的时候不当，导致了bypass。
 			实例2：
在一次测试云WAF中，使用get方式提交数据，提交内容包括一个参数，参数为字符＋sgl注入的语句。当在fuzz字符的时候，发现云waf.在处理到＆字符的时候，没有提
示云 wat.阻拦。由于＆字符的特殊性，猜测是由于和url.请求中的＆没有处理好导致的。北玄-u＿
由于mxsgl.中＆＆同样可以表示and，因此拼凑一下sgl语句就达到了bypass的目的。
```



### 1.4、白名单 bypass

```
WAF在设计之初一般都会考虑白名单功能。如来自管理IP的访问，来自cdn，服务器的访问等等。这些请求是可信任的，不必走WAF检测流程。

获取白名单的jp，地址如果是从网络层获取的jp，这种一般bypass不了，如果采用应用层的数据作为白名单，这样就可能造成bypass。-
之前有一篇文章：
http://h30499.www3.hp.com/t5/Fortify-Application- Security/Bypassing-web-application-firewalls-using-HTTP-headers/ba-p/6418366#.VGmhx9Yi5Mu 7

文章内容是通过修改http的header来bypass waf，这里我们截取文章中部分内容：
这些header常常用来获取IP，可能还有其他的，例如nginx-lua-waf 

function etClientin()
				IP=ngx.req.get_headers()["X-Real-IP"] 
				if IP== nil then
							IP ngx.var.remote_addr 
				end
							if IP =m nil then IP="unknown" 
				end
							return IP 
end

获取 clientip，使用了 X-Real-jp，的header。
此种方法还可以用来绕过如登陆锁jg，登陆多次验证码，后台验证等等的场景。
```

