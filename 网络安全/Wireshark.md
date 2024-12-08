Wireshark 的主要功能包括：

- **实时数据捕获**：能够捕获实时流量并对其进行分析。
- **数据包解码**：支持数百种网络协议，能够解码并显示各种协议的详细信息。
- **过滤功能**：提供强大的过滤功能，可以根据特定条件筛选数据包。
- **数据包重组**：能够重组和分析分片的数据包，以查看完整的通信内容。
- **统计和图表**：提供多种统计和图表功能，帮助用户进行流量分析和趋势预测。

Wireshark 的界面设计简洁明了，主要包括以下几个部分：

![图片](https://mmbiz.qpic.cn/mmbiz_png/6OibpDQ66VYS4FM28l63UPGnLC7t2iap2DEYcRUHabT6YL3V7t93cXDTuBc27hpLow5JURGcvlsnJaRCbNoOH39A/640?wx_fmt=png&from=appmsg&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

1. **菜单栏和工具栏**：
	- **菜单栏**：提供文件操作、编辑、查看、捕获、分析等选项，可以通过菜单访问各种功能。
	- **工具栏**：常用功能的快捷按钮，包括开始和停止捕获、打开和保存捕获文件、显示过滤器等。
2. **捕获选项和启动按钮**：
	- **捕获接口选择**：选择要捕获数据包的网络接口，可以是以太网、Wi-Fi等。
	- **捕获选项**：配置捕获参数，如数据包长度、捕获过滤器、环形缓冲区等。
	- **启动按钮**：开始和停止数据包捕获。
3. **数据包列表窗口**：
	- **数据包列表**：显示捕获的数据包，每个数据包一行，包含时间戳、源地址、目的地址、协议、长度等基本信息。
	- **列排序和过滤**：可以根据不同列进行排序和过滤，方便查找特定数据包。
4. **数据包详情窗口**：
	- **数据包解码详情**：选中一个数据包后，在详情窗口中显示其解码信息，按照协议层次结构显示，包括链路层、网络层、传输层和应用层的详细字段。
	- **展开和折叠**：可以展开和折叠各协议层次，查看具体字段的值和含义。
5. **数据包字节窗口**：
	- **字节视图**：以十六进制和ASCII格式显示选中数据包的原始字节数据，帮助用户查看数据包的实际内容。
	- **字节高亮**：与数据包详情窗口联动，高亮显示对应字段的字节数据。
6. **显示过滤器输入框**：
	- **过滤器输入框**：用于输入显示过滤器，筛选显示满足条件的数据包。
	- **过滤器提示**：提供过滤器语法提示和自动完成功能，帮助用户快速输入正确的过滤器。

## 抓包过滤基础

Wireshark 中的过滤器是其最强大和最常用的功能之一。通过使用过滤器，用户可以从庞大的数据包捕获中筛选出感兴趣的特定数据包，从而更高效地进行网络分析和故障排除。

抓包过滤是指在数据包捕获和分析过程中，使用特定的规则和条件，筛选出满足条件的数据包。Wireshark 提供了两种主要的过滤器类型：显示过滤器和捕获过滤器。

- **显示过滤器**：用于在捕获后筛选和显示特定的数据包。显示过滤器是在数据包已经被捕获之后应用的，它不会影响实际的数据包捕获过程。
- **捕获过滤器**：用于在捕获过程中筛选数据包。捕获过滤器是在数据包捕获之前应用的，它会直接影响捕获到的数据包数量和内容。

Wireshark 支持两种类型的过滤器：显示过滤器和捕获过滤器。它们的语法和使用方式有所不同。

下面我们详细介绍一下这两种过滤器。

![图片](https://mmbiz.qpic.cn/mmbiz_png/6OibpDQ66VYS4FM28l63UPGnLC7t2iap2DxfJA7FiaAd69jsGr6as7MOkZCrgUXCMn9cl0WdXKvkgd02IyMXUl8mQ/640?wx_fmt=png&from=appmsg&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

## 显示过滤器

显示过滤器是 Wireshark 中用于在数据包捕获之后，根据特定条件筛选和显示数据包的工具。显示过滤器的语法相对简单，使用字段名、运算符和值来构建过滤条件。

显示过滤器的基础语法包括：

- **字段名**：指定要过滤的数据包字段，如 `ip.addr`、`tcp.port` 等。
- **运算符**：用于比较字段值的运算符，如 `==`、`!=`、`>`、`<`、`>=`、`<=` 等。
- **值**：与字段名进行比较的值，可以是数值、字符串、布尔值等。

示例：

- 过滤特定 IP 地址的数据包：

```
ip.addr == 192.168.1.1
```

- 过滤特定端口的数据包：

```
tcp.port == 80
```

- 过滤特定协议的数据包：

```
http
```

### 常用的显示过滤器

一些常用的显示过滤器包括：

1. **IP 地址过滤**：

- 过滤特定源 IP 地址的数据包：

```
ip.src == 192.168.3.9
```

> 瑞哥本机地址是`192.168.3.9`

![图片](https://mmbiz.qpic.cn/mmbiz_png/6OibpDQ66VYS4FM28l63UPGnLC7t2iap2DkicvvaEuFUxmlIo8cdDEZWVmJBWKhm36icaQaicGmtW7NqISktuic74EicQ/640?wx_fmt=png&from=appmsg&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

- 过滤特定目的 IP 地址的数据包：

```
ip.dst == 192.168.3.66
```

![图片](https://mmbiz.qpic.cn/mmbiz_png/6OibpDQ66VYS4FM28l63UPGnLC7t2iap2DJdA9lUFI4BuP9JOEuuEmGUD1CsEpY8BP8WRDibMFxF1CSnoSmaReoAw/640?wx_fmt=png&from=appmsg&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

- 过滤特定 IP 地址的数据包（无论源还是目的）：

```
ip.addr == 192.168.3.9
```

![图片](https://mmbiz.qpic.cn/mmbiz_png/6OibpDQ66VYS4FM28l63UPGnLC7t2iap2DSImJbuyYJac6hfwzw85pF6gQXyMs8iayyRaZX3q4wjF0QwW6ticrpLDg/640?wx_fmt=png&from=appmsg&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

1. **端口号过滤**：

- 过滤特定源端口的数据包：

```
tcp.srcport == 80
```

![图片](https://mmbiz.qpic.cn/mmbiz_png/6OibpDQ66VYS4FM28l63UPGnLC7t2iap2DFTh8yTyT0bIUKg24uM1QhjqEm5LrZofUqicfSY4R7shibe0iaic6JY0saQ/640?wx_fmt=png&from=appmsg&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

- 过滤特定目的端口的数据包：

```
tcp.dstport == 443
```

![图片](https://mmbiz.qpic.cn/mmbiz_png/6OibpDQ66VYS4FM28l63UPGnLC7t2iap2DheXTFX92NINLz0icxrt7lYemDeoS5ERmfMOZaAF77WrlxwjmY5EErhA/640?wx_fmt=png&from=appmsg&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

- 过滤特定端口的数据包（无论源还是目的）：

```
tcp.port == 80
```

![图片](https://mmbiz.qpic.cn/mmbiz_png/6OibpDQ66VYS4FM28l63UPGnLC7t2iap2DZ1eoRiaSz9Gib3aiclOfy36RxgXZI47Tw0SY6JCgKZATicEgicP0Mw3I8Hw/640?wx_fmt=png&from=appmsg&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

1. **协议过滤**：

- 过滤 HTTP 协议的数据包：

```
http
```

![图片](https://mmbiz.qpic.cn/mmbiz_png/6OibpDQ66VYS4FM28l63UPGnLC7t2iap2DStR0zTjV7g2QSRRqDB4h2hogAuO5DK72gf75G3Asr29vY4NOyIG6qQ/640?wx_fmt=png&from=appmsg&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

- 过滤 TCP 协议的数据包：

```
tcp
```

![图片](https://mmbiz.qpic.cn/mmbiz_png/6OibpDQ66VYS4FM28l63UPGnLC7t2iap2DAKBjBhgwjAOhUmbN0cULc5hricRgs82ylhf4mcHDSLXsy0xTR6syy3Q/640?wx_fmt=png&from=appmsg&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

- 过滤 ICMP 协议的数据包：

```
icmp
```

1. **排除特定流量**：

- 排除 ICMP 协议的数据包：

```
!icmp
```

### 过滤 HTTP 流量

HTTP 流量是网络分析中常见的一部分，通过显示过滤器可以筛选和分析特定的 HTTP 请求和响应。

1. **过滤所有 HTTP 流量**：

```
http
```

1. **过滤特定主机的 HTTP 流量**：

```
http.host == "www.example.com"
```

1. **过滤特定 URI 的 HTTP 请求**：

```
http.request.uri contains "/login"
```

1. **过滤特定方法的 HTTP 请求**：

```
http.request.method == "POST"
```

1. **过滤特定状态码的 HTTP 响应**：

```
http.response.code == 200
```

### 过滤 DNS 流量

DNS 流量也是网络分析中常见的内容，通过显示过滤器可以筛选和分析 DNS 查询和响应。

1. **过滤所有 DNS 流量**：

```
dns
```

1. **过滤特定域名的 DNS 查询**：

```
dns.qry.name == "example.com"
```

1. **过滤特定类型的 DNS 查询**：

```
dns.qry.type == 1  // A记录查询
```

1. **过滤特定响应码的 DNS 响应**：

```
dns.flags.rcode == 0  // No error
```

1. **过滤特定 IP 地址的 DNS 响应**：

```
dns.a == 192.168.1.1
```

### 过滤 TCP 流量

TCP 是传输层的主要协议之一，通过显示过滤器可以筛选和分析特定的 TCP 会话和流量。

1. **过滤所有 TCP 流量**：

```
tcp
```

1. **过滤特定源端口的 TCP 流量**：

```
tcp.srcport == 80
```

1. **过滤特定目的端口的 TCP 流量**：

```
tcp.dstport == 443
```

1. **过滤特定 TCP 标志位的流量**：

```
tcp.flags.syn == 1  // SYN 包
```

1. **过滤特定 TCP 会话的流量**：

```
tcp.stream eq 1
```

### 过滤 UDP 流量

UDP 是传输层的另一主要协议，通过显示过滤器可以筛选和分析特定的 UDP 会话和流量。

1. **过滤所有 UDP 流量**：

```
udp
```

1. **过滤特定源端口的 UDP 流量**：

```
udp.srcport == 53
```

1. **过滤特定目的端口的 UDP 流量**：

```
udp.dstport == 123
```

1. **过滤特定 UDP 会话的流量**：

```
udp.stream eq 1
```

### 过滤 ICMP 流量

ICMP 是网络层的重要协议，通过显示过滤器可以筛选和分析特定的 ICMP 报文。

1. **过滤所有 ICMP 流量**：

```
icmp
```

1. **过滤特定类型的 ICMP 报文**：

```
icmp.type == 8  // Echo Request
```

1. **过滤特定代码的 ICMP 报文**：

```
icmp.code == 0
```

1. **过滤特定 ID 的 ICMP 报文**：

```
icmp.ident == 0x1234
```

1. **过滤特定序列号的 ICMP 报文**：

```
icmp.seq == 0x1
```

### 显示过滤器的高级用法

显示过滤器还支持更复杂的条件组合和表达式，例如：

1. **多个条件的组合**：

- 过滤特定源 IP 和目标端口的数据包：

```
ip.src == 192.168.3.9 && tcp.dstport == 8080
```

1. **范围过滤**：

- 过滤帧长度在 100 到 200 字节之间的数据包：

```
frame.len >= 100 && frame.len <= 200
```

1. **使用正则表达式**：

- 过滤 URI 包含 "login" 的 HTTP 请求：

```
http.request.uri matches ".*login.*"
```

1. **复杂逻辑过滤**：

- 过滤源 IP 为 192.168.1.1 且目的端口为 80，或源 IP 为 192.168.1.2 且目的端口为 443 的数据包：

```
(ip.src == 192.168.3.9 && tcp.dstport == 80) || (ip.src == 192.168.3.66 && tcp.dstport == 443)
```

## 捕获过滤器

捕获过滤器在数据包捕获过程中起作用，通过预先定义的条件，仅捕获满足条件的数据包。捕获过滤器使用 Berkeley Packet Filter (BPF) 语法，能够在捕获时减少不必要的数据包，提升捕获效率。

捕获过滤器的基础语法包括：

- **字段名**：指定要过滤的数据包字段，如 `host`、`port`、`net` 等。
- **运算符**：用于比较字段值的运算符，如 `==`、`!=`、`>`、`<`、`>=`、`<=` 等。
- **值**：与字段名进行比较的值，可以是数值、字符串、布尔值等。

> 💡捕获过滤器最终的效果和显示过滤器差不多，所以下面瑞哥的截图会少点，大家可以自己尝试。

示例：

- 过滤特定 IP 地址的数据包：

```
host 192.168.3.9
```

- 过滤特定端口的数据包：

```
port 80
```

- 过滤特定协议的数据包：

```
tcp
```

### 常用的捕获过滤器

一些常用的捕获过滤器包括：

1. **IP 地址过滤**：

- 过滤特定 IP 地址的数据包：

```
host 192.168.1.1
```

- 过滤特定源 IP 地址的数据包：

```
src host 192.168.1.1
```

- 过滤特定目的 IP 地址的数据包：

```
dst host 192.168.3.66
```

1. **端口号过滤**：

- 过滤特定端口的数据包：

```
port 80
```

- 过滤特定源端口的数据包：

```
src port 80
```

- 过滤特定目的端口的数据包：

```
dst port 443
```

1. **协议过滤**：

- 过滤 TCP 协议的数据包：

```
tcp
```

- 过滤 UDP 协议的数据包：

```
udp
```

- 过滤 ICMP 协议的数据包：

```
icmp
```

1. **排除特定流量**：

- 排除特定 IP 地址的数据包：

```
not host 192.168.1.1
```

- 排除特定端口的数据包：

```
not port 80
```

### 捕获 HTTP 流量

通过捕获过滤器筛选 HTTP 流量可以减少捕获的数据量，尤其是在只需要分析特定的 HTTP 请求和响应时。

1. **捕获所有 HTTP 流量**：

```
tcp port 80
```

1. **捕获特定主机的 HTTP 流量**：

```
tcp port 80 and host www.example.com
```

### 捕获 DNS 流量

通过捕获过滤器筛选 DNS 流量，可以有效地捕获特定的 DNS 查询和响应。

1. **捕获所有 DNS 流量**：

```
udp port 53
```

1. **捕获特定域名的 DNS 查询**：

```
udp port 53 and host example.com
```

### 捕获 TCP 流量

通过捕获过滤器筛选 TCP 流量，可以捕获特定会话和特定条件下的 TCP 报文。

1. **捕获所有 TCP 流量**：

```
tcp
```

1. **捕获特定源端口的 TCP 流量**：

```
src port 80
```

1. **捕获特定目的端口的 TCP 流量**：

```
dst port 443
```

1. **捕获特定 TCP 标志位的流量**：

```
tcp[tcpflags] & tcp-syn != 0  // SYN 包
```

### 捕获 UDP 流量

通过捕获过滤器筛选 UDP 流量，可以捕获特定会话和特定条件下的 UDP 报文。

1. **捕获所有 UDP 流量**：

```
udp
```

1. **捕获特定源端口的 UDP 流量**：

```
src port 53
```

1. **捕获特定目的端口的 UDP 流量**：

```
dst port 123
```

### 捕获 ICMP 流量

通过捕获过滤器筛选 ICMP 流量，可以捕获特定类型和特定条件下的 ICMP 报文。

1. **捕获所有 ICMP 流量**：

```
icmp
```

1. **捕获特定类型的 ICMP 报文**：

```
icmp[icmptype] == icmp-echo
```

1. **捕获特定代码的 ICMP 报文**：

```
icmp[icmpcode] == 0
```

### 捕获过滤器的高级用法

捕获过滤器支持更复杂的条件组合和表达式，例如：

1. **多个条件的组合**：

- 过滤源 IP 和目标端口同时满足的数据包：

```
src host 192.168.1.1 and dst port 80
```

1. **范围过滤**：

- 过滤特定网段的数据包：

```
net 192.168.1.0/24
```

1. **复杂逻辑过滤**：

- 过滤源 IP 为 192.168.1.1 且目标端口为 80，或源 IP 为 192.168.1.2 且目标端口为 443 的数据包：

```
(src host 192.168.1.1 and dst port 80) or (src host 192.168.1.2 and dst port 443)
```

1. **字段存在检查**：

- 过滤存在特定字段的数据包：

```
tcp[tcpflags] & tcp-syn != 0
```

## 高级过滤技巧

Wireshark 过滤器不仅可以用于简单的条件筛选，还支持更复杂的逻辑运算和组合，从而实现更精细的过滤。

### 组合过滤条件

通过组合多个过滤条件，可以实现更复杂的筛选逻辑。

1. **AND 逻辑组合**：

- 过滤源 IP 为 192.168.1.1 且目的端口为 80 的数据包：

```
ip.src == 192.168.1.1 && tcp.dstport == 80
```

1. **OR 逻辑组合**：

- 过滤源 IP 为 192.168.1.1 或目的端口为 443 的数据包：

```
ip.src == 192.168.1.1 || tcp.dstport == 443
```

1. **混合逻辑组合**：

- 过滤源 IP 为 192.168.1.1 且（目的端口为 80 或 443）的数据包：

```
ip.src == 192.168.1.1 && (tcp.dstport == 80 || tcp.dstport == 443)
```

### 使用正则表达式

Wireshark 的显示过滤器支持正则表达式，可以用来匹配更复杂的字符串模式。

1. **匹配 HTTP 请求 URI 中包含特定字符串**：

- 过滤 URI 包含 "login" 的 HTTP 请求：

```
http.request.uri matches ".*login.*"
```

1. **匹配 HTTP 头部中的特定字段**：

- 过滤 User-Agent 包含 "Mozilla" 的 HTTP 请求：

```
http.request.header.User-Agent matches ".*Mozilla.*"
```
### 字段存在检查

通过检查字段是否存在，可以筛选出包含特定字段的数据包。
1. **检查 IP 选项字段是否存在**：
- 过滤包含 IP 选项字段的数据包：

```
ip.options
```

1. **检查 TCP 选项字段是否存在**：

- 过滤包含 TCP 选项字段的数据包：

```
tcp.options
```

### 使用偏移量和掩码

Wireshark 过滤器支持通过偏移量和掩码筛选特定位的数据。

1. **过滤 TCP 标志位中的 SYN 包**：

- 使用位运算过滤 TCP SYN 包：

```
tcp.flags & 0x02 != 0
```

1. **过滤特定字节偏移量的数据包**：

- 过滤 TCP 数据包中包含特定数据模式的包：

```
tcp[13] & 0x02 != 0
```