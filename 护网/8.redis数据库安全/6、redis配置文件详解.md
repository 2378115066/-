# 1.配置文件位置

### 以配置文件启动

```
Redis的配置文件位于redis安装目录下，文件名为redis.conf(win为redis。Windows.conf)
```

redis**对配置文件对大小写不敏感**

```
						基本单位
1k  ----> 1000 bytes
1kb ---->1024 bytes
1m ----->1000000 bytes
1mb ----->1024*1024 bytes
1g ----->1000000000 bytes1gb => 1024*1024*1024 bytes

					不区分大小写
units are case insensitive so 1GB 1Gb 1gB are all the same.
```

# 2.配置命令

**当前服务中的配置文件修改**

#### 获得配置内容命令

```
config get
config get *
```

#### 设置配置文件命令

```
修改redis.conf文件或使用config set命令来修改配置

config set loglevel debug
```

# 3.配置文件中和安全相关问题

### 1).网络配置(network)

**绑定IP**

```
[bind]


bind ip
```

**保护模式**

```
保护模式默认开启
保护模式为开启如果是远程链接不能进行CRUD等操作

protected-mode yes   //开启，no关闭
```

**设置端口**

```
port 端口号
```

### 2).通用设置

**守护进程**

```
是否以守护进程方式运行(默认是 no)
如果以守护进程方式运行，需要指定一个 PID 进程文件

daemonize no
pidfile /root
```

**Loglevel**

```
日志 debug 测试环境使用 notice 生产环境使用，日志生成的文件位置名，如果空只是控制台输出

loglevel notice
logfile ""
```

**数据库数量**

```
数据库数量和是否显示redis的logo

databases 16
always-show-logo yes 
```

### 3).安全配置

**连接密码**

```
连接密码，默认是不需要密码的，可以通过“requirepass 123456”设置连接密码为“123456可以通过命令设置密码，但设置的密码在服务重新启动之后就失效啦

没有指定用户，进入都是 defautl 用户
acl list 可以看所有权限
Config set requirepass 123456
Config get requirepass
Auth 123456
```

**ACL简介**

```
在 Redis6.0之前的版本中,登陆 Redis Server 只需要输入密码(前提配置了密码 requirepass即可，不需要输入用户名，而且密码也是明文配置到配置文件中，安全性不高。并且应用连接也使用该密码，导致应用有所有权限处理数据，风险也极高。在Redis6.0有了ACL之后，终于解决了这些不安全的因素，可以按照不同的需求设置相关的用户和权限
ACL 命令

acl help
ACL <subcommand> arg arg... arg. Subcommands are:

LOAD   从ACL文件中重新载入用户信息.
SAVE 保存当前的用户配置信息到ACL文件
LIST 以配置文件格式显示用户详细信息.
USERS   列出所有注册的用户名




SETUSER,username>[attribs ...]-创建或则修改一个用户
GETUSER username>     得到一个用户的详细信息
DELUSER <username> [...]    删除列表中的用户
CAT                        列出可用的类别
CAT <category>             列出指定类别中的命令.
GENPASS [<bits>]           生成一个安全的用户密码
WHOAMI          返会当前的连接用户
L0G [<count> | RESET]           显示ACL日志条目
```

**新建用户**

```
							不带密码
acl setuser a1

							带密码
并切换用户，但是没有任何权限访问被拒绝
acl setuser xinjing on >123
auth xinjing 123
whoami
allkeys +@all
acl setuser a2 ~z*+@string-@hash
```

**列出所用用户**

```
acl list
```

###### acl参数说明

```
user代表用户
default代表默认用户(反之为自己创建的用户)

on 代表激活(反之off,默认新增的为off)

~* 代表可以访问的key

+@all 代表可以操作的command

key的说明



得到一个用户详细信息
acl getuser al

给用户赋予权限
acl setuser xinjing allkeys +@all
acl setuser a1 +@string
acl setuser a2 ~z*+@string -@hash



acl whoami
```

```
+<command>:将命令添加到用户可以调用的命令列表中，如+@hash

-<command>:将命令从用户可以调用的命令列表中移除

+@<category>:添加一类命令，如:@admin, @set, @hash.. 可以 ACL CAT 查看具体的操作指令。特殊类别@all表示所有命令，包括当前在服务器中存在的命令，以及将来将通过模块加载的命令

@<category>:类似+@<category>，从客户端可以调用的命令列表中删除命令

+<command>|subcommand:允许否则禁用特定子命令。注意，这种形式不允许像-DEBUG|SEGFAULT 那样，而只能以“+"开头

allcommands:+@all 的别名，允许所有命令操作执行。注意，这意味着可以执行将来通过模块系统加载的所有命令。

nocommands:-@al 的别名，不允许所有命令操作执行
```

**最大客户端连接数**

```
Maxclients

maxclinents num
```

### 4).内存设置

```
redis最大内存容量
配置文件中maxmemory

maxmemory <bytes>
```

```
						内存达到上限的处理策略
常见的内存替换策略
	1.LRU(Leastrecentlyused)最近最少使用，如果数据最近被访问过，那么将来被访问的几率也更高。
	2.LFU(Least frequentlyused)最不经常使用，如果一个数据在最近一段时间内使用次数很少，那么在将来一段时间内被使用的可能性也很小。
	3.FIFO(Fist in firstout)先进先出,如果一个数据最先进入缓存中，则应该最早淘汰掉。
	
volatile-lru:只对设置了过期时间的 key 进行 LRU(默认值)
allkeys-lru :删除lru算法的key
volatile-lfu:
allkeys-lfu
volatile-random:随机删除即将过期key
allkeys-random:随机删除
volatile-ttl :删除即将过期的
noeviction :永不过期，返回错误
```

# 4.创建普通用户启动redis*

```
cd redis-6.0.8/
user add -s /sbin/nologin -M redis
chmod -R 755 /root/redis-6.0.8
chown redis.redis /root/redis-6.0.8
cd src
sudo -u redis ./redis-server &
ps -ef | grep redis
```

