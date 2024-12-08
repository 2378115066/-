# 				无口令远程登录redis

看看redis内存里面的数据

```bash
狠一点 flushdb      flushall

root@localhost src]#./redis-cli -h 192.168.137.11
192.168.137.11:6379>config get dir

ps -ef | grep redis

keys *

set ip "239"

save

quit

firewall-cmd --list-ports     //6379/tcp
```

