# 1.docker安装

```bash
Docker search redis

Dockerpul 镜像名字 这种情况下速度比较慢

docker run -d -p 6379:6379 -v $PWD/conf/redis.conf:/usr/local/etc/redis/redis.conf -v $PWD/data:/data --name docker-redis docker.io/redis redis-server /usr/local/etc/redis/redis.conf --appendonly yes
特别慢，不建议使用
```

# 2.编译安装

```bash
# yum install -y gcc tcl

# wget http://download.redis.io/releases/redis-6.2.13.tar.gz

# tar -xzf redis-6.2.13.tar.gz

# cd redis-6.0.8

# make && make install

```

**注意**

```shell
Make 会报错，需要升级 gcc
yum -y install centos-release-scl
yum -y install devtoolset-9-gcc devtoolset-9-gcc-c++ devtoolset-9-binutils
scl enable devtoolset-9 bash

需要注意的是scl命令启用只是临时的，退出shell 或重启就会恢复原系统 gcc版本。
如果要长期使用 gcc 9.3 的话:
echo "source /opt/rh/devtoolset-9/enable" >> /etc/profile

yum install -y tcl-devel
curl -o /etc/yum.repos.d/CentOS-Base.repo http://mirrors.163.com/.help/CentOS7-Base-163.repo

ps -ef | grep redis
kill -9 进程号(pid)
```



### a.直接在下载目录下安装

```bash
执行完 make 命令后,redis-6.0.8 的src目录下会出现编译后的 redis 服务程序 redis-server,还有用于测试的客户端程序redis-cli:
启动redis 服务:使用默认配置
# cd src
# ./redis-server

可以通过启动参数告诉 redis 使用指定配置文件使用下面命令启动。配置文件redis.conf(redis-6.0.8) 也可以根据需要使用自己的配置文件
# cd src
# ./redis-server &  ../redis.conf     指定配置文件后台运行#

Shutdown客户端退出redis-serverf服务
Quit 退出客户端

启动redis 服务进程后，使用测试客户端程序redis-cli 和redis 服务交互了
# cd src
#./redis-cli     运行客户端
redis> set foo "bar"
OK
redis> get foo
Keys *      查看所有键
```

### (b)可设置安装路径

```bash
make install PREFIX=/usr/local/redis

后台运行
> ./redis-server --daemonize yes
```

### (c)修改配置文件，直接后台启动，不需要加参数设置

```bash
cp redis.conf /usr/local/redis/bin/
cd /usr/local/redis/bin
vi redis.conf      设置 redis.conf 文件，把 daemonize no 改为 daemonize yes

后台启动   
./redis-server  redis.conf
```

# 3.yum安装

```bash
yum install epel-release -y            #如果找不到redis，先装这个
yum install redis					#安装redis
find / -name    "redis*"     		#查看redis服务安装位置
service  redis  start                #打开redis服务
```

