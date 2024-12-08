# dnsmap

参数说明 :



```
-w:后加字典文件
-f:指定结果用常规格式输出文件
-c:指定结果用csv去输出-d 设置延迟
-i :设置忽略ip（当你遇到一个虚假ip时很有用）
```

案例:

```
dnsmap example.com
dnsmap example.com-w yourwordlist.txt-r /tmp/domainbf_results.txt 
dnsmap example.com-r /tmp/ -d 3000
dnsmap example.com-r ./domainbf_results.txt
```