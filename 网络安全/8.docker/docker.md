## 1.docker是什么？

```
软件的打包技术，就是将算乱的多个文件打包为一个整体，打包技术在没有docker容器之前，一直是有这种需求的，比如上节课我把我安装的虚拟机给你们打包了，前面的这种打包方式是将整个虚拟机打包了，对吧，这样打包出来的体积太大了，而且如果你只是单纯的想要一个安装好的程序，比如sqlserver数据库，不想自己安装，就想要个安装好的，按照之前的打包方式，太费事费力的，你打包个安装了sqlserver数据库的虚拟机，光虚拟机本身的操作系统可能就占用了20个G，sqlserver本身可能也就1个G，这是不是就太不合适了，当然我们自己不会或者不想安装sqlserver的时候，可以选择找个哥们帮你安装一下，但是如果100个人都找你安装，你是不是累死了，所以在这种情况，容器技术就诞生了，容器技术中的佼佼者，就是docker，它的底层实现原理我们现在不用纠结。用它来打包出来的软件，体积会非常小。比如如果在一个虚拟机上安装了nginx，那么这个虚拟机怎么也要1G以上，但是用docker打包的已经安装好的nginx，可能也就100M左右，体积小很多。接下来我们感受一下docker的使用。后面我们可以将很多部署起来很繁琐的靶场环境都通过docker来打包。所以现在网上也有很多使用docker跑起来的靶场，复用性非常好，别人打包好的，你直接拿来就用。而且docker有个东西叫做仓库，打包的东西直接放在仓库里面，全世界都可以共享。docker是2013年诞生的。

docker打包出来的每个软件，称之为docker镜像。可以说整个IT领域，不管是哪个工种，都需要好好学习docker。

docker是CS架构的程序，客户端控制服务端来做各种事情。
```

#### 概念

```
镜像：images，是个压缩包文件，里面存放着安装好的程序。
容器：Container，Docker利用容器来运行应用。容器是从镜像创建的运行实例。它可以被启动、开始、停止、删除。每个容器都是相互隔离的、保证安全的平台。
```

## 2、docker的安装

**centos7安装docker**

```bash
# centos7上面用yum安装
yum install docker -y

#启动docker
systemctl start docker

#设置开机自启
systemctl enable docker

#体验docker版nginx最新版
docker run -d -p 80:80 nginx

#体验docker版nginx 1.16
docker run -d -p 81:80 nginx:1.16

#体验wordpress
docker run --name mysql -e MYSQL_ROOT_PASSWORD=123456  -d mysql:5.7
docker run -d  --link mysql:mysql -p 86:80 wordpress:5.6
```

 **kali安装docker**

```bash
#添加docker的gpg密钥，签名用的
curl -fsSL https://mirrors.tuna.tsinghua.edu.cn/docker-ce/linux/debian/gpg | sudo apt-key add -

#添加docker的apt源
echo 'deb https://mirrors.tuna.tsinghua.edu.cn/docker-ce/linux/debian/ buster 
stable' | sudo tee /etc/apt/sources.list.d/docker.list

#更新apt缓存
apt update

#安装docker
sudo apt-get install docker docker-compose -y
或
sudo apt-get install docker.io

#安装完成之后，docker就自动启动了
systemctl status docker   

#查看docker版本
docker -v 
```

体验一下docker下载安装运行nginx镜像

```bash
#体验docker版nginx最新版，本地没有nginx镜像的话，会自动去仓库中拉去镜像并运行
docker run -d -p 80:80 nginx
#体验docker版的特定版本的nginx 1.16
docker run -d -p 81:80 nginx:1.16
#docker run -d -p 82:80 nginx:1.18

#直接浏览器访问：http://192.168.2.121/ 就能看到nginx首页了。在响应数据中就能看到nginx的版
本
#是不是感受到了安装不同版本nginx的便利之处了，如果不是用docker，你想去安装一些特定的老版本还是比较麻烦的，好多时候只能编译安装

#体验wordpress，需要启动两个docker镜像，一个数据库的，一个代码程序，这个比较大，所以速度可能会慢一些

docker run --name mysql -e MYSQL_ROOT_PASSWORD=123456  -d mysql:5.7  # 5.7版本的
MySQL，镜像名称是mysql

docker run -d  --link mysql:mysql -p 86:80 wordpress:5.6  # 5.6版本的wordpress，最
新版本应该已经到了6.x了，但是值得说明的一点就是封装wordpress的人为了将镜像做的比较小，没有安装中文包，所以只能是看英文的了，他会自动连接数据库。如果你发现你安装的镜像不是你要的版本，那么可能是版本指定错误了，或者是官方镜像仓库中的wordpress镜像版本有点问题了。

# 可以更改docker镜像库的源 
cd /etc/docker 
vim docker.json 
# 添加如下内容，并保存退出
{
 "registry-mirrors": ["https://registry.docker-cn.com"]
 }    

# 可以重启docker服务
systemctl restart docker
systemctl start docker
systemctl enable docker
systemctl stop docker

#Docker中国区官方镜像
https://registry.docker-cn.com

#阿里云容器，不过这个好像不更新了，大家可以去阿里官方关注一下
https://cr.console.aliyun.com/
```

```
docker run首先检测你本地是否已经有了软件镜像，如果没有，他会自动去下载镜像，然后运行，
运行 起来的镜像，我们称之为容器，可以理解为每个软件都安装在了一个自己的小空间里面。 
docker  镜像  容器 
镜像-->安装了某些特定程序的文件 -->压缩文件 
容器-->镜像运行起来之后，就叫做容器。
```

## 3、镜像常用命令

```bash
docker search 
	#搜索镜像(只搜索官方仓库的，官方仓库地址：hub.docker.com)
	# docker search tomcat
	# docker search apache
 	# 我们拉取的镜像tomcat\apache等名字很短对吧，这都是官方仓库中的官方镜像，官方仓库中支持用户上传自己封装的镜像，用户镜像和官方镜像的差别在名字上面，比如我们可以去docker官方去注册一个账号，用户自己的镜像前面都会有作者的用户名或者用户所在组织的名字，比如jaden/nginx、
jaden/tomcat等。

docker images 
	#查看本地镜像列表，image就是图像、镜像的意思
	# 本地有的镜像，就不要再去下载了，而且可以将本地镜像导出来分享给别人

docker pull   
	#下载镜像，拉取镜像
	# docker pull tomcat:latest
	# docker images

docker push   
	#上传镜像，推送镜像，推到官方仓库，推送不是那么简单的，不然早就满了，需要在本地登录一下官方账号才能推，后面再演示

docker rmi     
	#删除镜像，rm image的意思，直接rm不加i表示要删除容器，可以通过名称加版本来删除，或者直接通过镜像id值来删除
	#docker rmi tomcat:latest  或者 docker rmi imageid值
	#可以同时删除多个镜像：docker rmi tomcat:latest tomcat:jre17-temurin-jammy
	#如果这个镜像处于运行状态的是删除不了的，比如有容器在使用这个镜像，就不能删除镜像，比如

docker rmi nginx:1.16会报错
	#查看镜像的运行状态docker container ls，其实这是查看容器的状态，但是可以看到哪些镜像被使了
		
docker save   
	#导出镜像(压缩包) docker save 镜像名称:版本 -o docker_nginx1.20.tar.gz
	#docker save nginx:1.16 -o docker.nginx1.16.tar.gz
	#ls 就看到了 docker.nginx1.16.tar.gz

docker load   
	#导入镜像 docker load -i docker_nginx1.20.tar.gz，会自动解压并导入到docker服务中
```

## 4.容器的常用命令

```bash
docker run 运行一个新容器
docker ps === docker container ls #参数: 默认之显示up状态的容器，-a查看所有容器，或者-
all

docker stop  停止容器  #例子 docker stop  容器id或者容器名字

docker kill  杀掉容器  #强制关闭容器，尽量不要用，很容易就启动不了了

docker start 启动容器  #例子 docker start 容器id或者容器名字

docker restart 重启重启  #例子 docker restart  容器id或者容器名字

docker rm      删除容器  #例子 docker rm  容器id或者容器名字，同时删除多个，就空格隔开，处于up状态是不能直接删除的，强制删除是可以删除up状态的容器的，docker rm f 容器名称或者id

docker rm -f `docker ps -a -q` #删除所有容器，-q是只显示容器id，反引号中的指令优先执行

docker top   查看容器内的进程  #例子docker top 容器id或者容器名字

docker stats 查看容器的资源占用情况 

docker exec    进入容器  #例子： docker exec -it 容器id或者容器名字
# 直接交互指令：docker exec -it 76738703b7b2 ls # 执行ls指令
# 进入终端：docker exec -it 76738703b7b2 /bin/bash或者/bin/sh  #/bin/bash打开一个终端窗口，exit指令退出终端，但是docker容器内容一般不会安装额外的软件，所以导致大量的指令是用不了的，比如ifconfig、ps、ip addr等


docker inspect -f '{{.Name}} => {{.NetworkSettings.IPAddress }}' $(docker ps 
aq) 
#可以查看所有容器的ip地址的，容器的ip地址是从`172.17.0.1`开始分的。docker容器类似于一个微型的虚拟机，它占用的都是宿主机(物理机)的资源。在物理机上是可以看到容器所运行的程序的。每个容器都有自己的ip地址。


docker inspect --format='{{.Name}} - {{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' $(docker ps -aq) | grep "容器名称或者id"

# curl -I 加网址，可以看到http响应数据
┌──(root㉿jadenkali)-[/home/jaden]
 └─# curl -I http://172.17.0.4
 HTTP/1.1 200 OK
 Server: nginx/1.23.4
 
# netstat -lntup可以看到给docker的端口映射
# docker run -d -p 80:80 nginx  #-p 80:80，端口映射，表示宿主机的80端口映射到了nginx容器的80端口。
```

![image-20240523202353441](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240523202353441.png)

**docker run**

```bash
-d  #放后台运行-p  端口映射 #例子： 

-p 宿主机端口:容器端口

--name 指定容器的名字 # docker run -it --name jaden 镜像id或者名称

--link 关联另一个容器 # 了解即可-e MYSQL_ROOT_PASSWORD #设置容器的一些属性，了解一下即可

-it #是给运行起来的这个容器分配一个终端，就可以进入到容器内部操作了
# 后面想部署什么，直接网上搜索即可。
```

## 5、制作docker镜像并上传

```bash
docker pull debian:latest
docker run -it --name jaden_nginx -p 90:80 debian:latest

# 进入容器
docker exec -it jaden_debian /bin/bash

# 安装nginx
apt update # 更新apt缓存
apt install nginx -y  # 安装nginx
nginx -v # 查看nginx版本，安装好了  

# ip addr
# apt install procps # 安装ps指令
# ps -ef
nginx #启动nginx，systemctl是没有的，没有安装这个指令
exit

# 打包之前做好先停止容器
docker stop jaden_debian
docker commit jaden_nginx syrjaden/debian_nginx:v1  # 根据名字或者id都可以提交，后面加个镜像名称和版本,syrjaden是docker仓库用户名

#上传到官方仓库
docker login  #登录官方仓库
#docker tag debian_nginx:v2 syrjaden/debian_nginx:v2 # 这是改名字，如果名称不冲突就不
用改名字

docker push syrjaden/debian_nginx:v2  # 直接push即可
```

## 6.docker-compose

**docker-compose是批量管理docker容器的工具**

```bash
# 比如前面我们启动的wordpress项目，需要启动两个容器才行，有时候就是这样，需要同时启动多个容器来完成你想要做的事情，但是到底启动多少个容器呢？比如wordpress那个，我们记不住，换一个机器不看笔记很难起来，有了docker-compose就可以解决这个问题了。

#centos7安装docker-compose，我们前面已经安装了，不需要再次安装了
yum install epel-release.noarch -y
yum install docker-compose -y

#kali安装docker-compose
apt install docker-compose -y

# 查看版本
docker-compose -v
```

**配置文件docker-compose.yml，有了这个配置文件，就可以通过docker-compose来控制多个容器了**

```bash
# 为了避免端口冲突，我们可以先关闭所有docker容器
docker stop `docker ps -a -q`

# 为了演示方便，我们可以先创建一个wordpress文件夹，进入到里面创建一个docker-compose.yml名字的文件
mkdir wordpress
cd wordpress/
touch docker-compose.yml
vim docker-compose.yml
# 将如下内容拷贝到文件中保存退出，注意拷贝的时候，把里面我标记的注释去掉。

# 注意，下面这个文件内容是严格要求格式的，多一个空格都不行，通过缩进来表示等级关系，下面的这种配置语法叫做yaml语法
version: '3'  # docker-compose.yml的文件格式版本
services:
   db:  #容器名称
     image: mysql:5.7
     restart: always  # 开机自启动的意思
     environment:
       MYSQL_ROOT_PASSWORD: 123456
       MYSQL_DATABASE: wordpress
       MYSQL_USER: wordpress
       MYSQL_PASSWORD: 123456  # 和下面的WORDPRESS_DB_PASSWORD值要对应上
 
   wordpress:
     depends_on:
       - db
     image: wordpress:5.6  
     ports:
       - "83:80"  # 端口映射
     restart: always
     environment:
       WORDPRESS_DB_HOST: db
       WORDPRESS_DB_USER: wordpress
       WORDPRESS_DB_PASSWORD: 123456


这段代码是一个Docker Compose文件，用于定义和配置两个服务：`db` 和 `wordpress`。
- `version: '3'`：指定了Docker Compose文件的版本为3。
- `services`：定义了要创建的服务列表。
- `db`：定义了一个名为`db`的服务，表示数据库容器。
  - `image: mysql:5.7`：指定使用MySQL 5.7版本的镜像作为基础镜像。
  - `restart: always`：设置容器在启动时自动重启。
  - `environment`：定义了环境变量，包括数据库的用户名、密码、数据库名等。
- `wordpress`：定义了一个名为`wordpress`的服务，表示WordPress容器。
  - `depends_on`：指定该服务依赖于`db`服务，即先启动`db`服务再启动`wordpress`服务。
  - `image: wordpress:5.6`：指定使用WordPress 5.6版本的镜像作为基础镜像。
  - `ports`：定义了端口映射，将主机的83端口映射到容器的80端口。
  - `restart: always`：设置容器在启动时自动重启。
  - `environment`：定义了环境变量，包括WordPress连接数据库的相关信息。

通过这个Docker Compose文件，可以方便地创建一个包含MySQL数据库和WordPress应用程序的多容器应用。
```

```bash
#创建并启动
docker-compose up -d # 启动之后就可以通过浏览器访问了

#停止并删除
docker-compose down

#重启
docker-compose restart

#停止
docker-compose stop

#启动
docker-compose start
```

## 七、docker-compose启动靶场环境  

 

```
 https://vulhub.org/#/environments/
```

