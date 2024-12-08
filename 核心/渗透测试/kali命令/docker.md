```
service docker start   //启动docker服务
 
docker version   //查看docker版本信息
 
docker ps  查看容器
 
docker  images   查看已有的镜像
 
备注：由于国内网络问题，建议使用加速器加快镜像的下载
 
添加加速器方法：
 
编辑这个文件，如果没有对话就创建这个文件
vim /etc/docker/daemon.json
 
内容如下：
 
{
"registry-mirrors": [
"http://hub-mirror.c.163.com"
]
}
 
这里我使用对是国内 163 网易源，其他源可以自行百度替换。
 
配置完成后重启服务才可以生效：命令如下
 
sudo systemctl daemon-reload
sudo systemctl restart docker
```

