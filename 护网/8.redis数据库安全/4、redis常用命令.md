# 1.客户端范例

## redis-cli 

```bash
quit 退出客户端

Shutdown 停止redis 服务

Ping 测试服务是否运行

Echo 打印字符串

AUTH password 验证密码是否正确 默认没有 password

Del key 删除键

EXISTS key 检査 key 是否存在

info 査看 redis 信息

Move key db
```

![image-20240526195703172](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240526195703172.png)

```
检测是否有安装redis-cli 和redis-server;

shell 里面find/-name "redis*"

检测后台进程是否存在
ps -ef | grep redis

检测6379端口是否在监听
netstat -Intp | grep 6379

停止 redis:
使用客户端:redis-cli shutdowr
因为 Redis可以妥善处理 SIGTERM 信号，所以直接kil -9也是可以的
kill -9 PID
```

