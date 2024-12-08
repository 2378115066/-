## Metasploit：端口扫描

```
实验靶机：metasploitable2
IP:192.168.152.129 
```

### 用Nmap扫描

```
nmap 192.168.152.129
```

### 用Metasploit模块扫描

```
search portscan
```

### 使用模块

```
use auxiliary/scanner/portscan/tcp
```

### 查看需要设置的参数

```
show options
```

### 设置参数

```
set rhosts 192.168.152.129
```

## Metasploit：SMB扫描 获取系统信息

### 什么是SMB

```
SMB（全称是Server Message Block）是一个协议名，它能被用于Web连接和客户端与服务 器之间的信息沟通。
中文名：服务器信息块
通过扫描SMB，可以识别目标的系统信息
```

### 扫描服务器的 SSH服务

```
msf5> search ssh
```

