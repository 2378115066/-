# 1.redis数据库

Redis 是一个字典结构的存储服务器，而实际上一个Redis 实例提供了多个用来存储数据的字典，客户端可以指定将数据存储在哪个字典中。这与我们熟知的在一个关系数据库实例中可以创建多个数据库类似，所以可以将其中的每个字典都理解成一个独立的数据库。
每个数据库对外都是一个从0开始的递增数字命名，**Redis 默认支持16 个数据库(可以通过配置文件支持更多，无上限)**，可以通过配置 databases 来修改这一数字。客户端与 Redis **建立连接后会自动选择0号数据库**，不过可以随时使用SELECT命令更换数据库，如要选择1号数据库：

```
	select 1
```

然而这些以数字命名的数据库又与我们理解的数据库有所区别。**首先 Redis 不支持自定义数据库的名字，每个数据库都以编号命名**，开发者必须自己记录哪些数据库存储了哪些数据。**另外 Redis 也不支持为每个数据库设置不同的访问密码，所以一个客户端要么可以访问全部数据库，要么连一个数据库也没有权限访问**。最重要的一点是多个数据库之间并不是完全隔离的，**比如 FLUSHALL 命令可以清空一个 Redis 实例中所有数据库中的数据**。综上所述，这些数据库更像是一种命名空间，而不适宜存储不同应用程序的数据。比如可以使用0号数据库存储某个应用生产环境中的数据，使用1号数据库存储测试环境中的数据,但不适宜使用0号数据库存储A应用的数据而使用1号数据库B应用的数据，**不同的应用应该使用不同的Redis 实例存储数据**。由于 Redis 非常轻量级，**一个空 Redis 实例占用的内存只有 1M** 左右，所以不用担心多个 Redis 实例会额外占用很多内存。

Redis **一个实例默认有 16个数据库**

删除数据库中数据
**flushdb 删除当前数据库中数据**
**flushall 删除所有数据库中数据**

# 2.数据类型

## 1).字符串类型

```
字符串类型的reids操作命令
设置键值对，获得键值
```

```mysql
set name 'xining'               //设置键值对

get name					//获取键值
```

## 2).hash类型

```
Redishash 是一个string类型的field(字段)和value(值)的映射表，hash 特别适合用于存储对象。
Redis中每个hash可以存储232-1 键值对(40多亿)。
```

```mysql
							键值对的设置与获取
hmset person name 'xinjing' sex 'nv' age 14                //设置键值对
hmget person name										//获取键值
hmget person age										//获取键值
hgetall person										    //获取键值
```

```mysql
                               键值对的删除与判定存在
hdel person age										//删除键值对
hgetall person										//获取所有键值对
hexists person name									//判断键是否存在
```

## 3).列表List

```
Redis 列表是简单的字符串列表,按照插入顺序排序。你可以添加一个元素到列表的头部(左边)或者尾部(右边)一个列表最多可以包含232-1个元素(4294967295,每个列表超过40亿个元素)。
```

```ruby
								头部进出	
栈式操作命令:	lpush lpop lrange lindex llen 
LPUSH key value：将一个或多个值插入到列表头部。
LPOP key：移除并返回列表的第一个元素。
LRANGE key start stop：获取列表中从索引 start 到索引 stop（不包括 stop）的元素。
LINDEX key index：获取列表中索引为 index 的元素。
LLEN key：返回列表的长度。

LPUSH：将值插入到列表头部。
LPUSH mylist "world"
    
LPOP：移除并返回列表的第一个元素。
LPOP mylist
    
LRANGE：获取列表中指定范围内的元素。
LRANGE mylist 0 -1
    
LINDEX：通过索引获取列表中的元素。
LINDEX mylist 0
    
LLEN：获取列表的长度。
LLEN mylist
    
请注意，这些命令中的 key 是列表的键名，而 value、start、stop 和 index 是你要操作的值或索引。索引是基于0的，即列表中的第一个元素的索引是0。

在实际使用Redis时，你需要根据具体的需求选择合适的命令来操作列表。例如，
当你需要添加新元素到列表开头时，可以使用 LPUSH；
当你需要移除并获取列表的第一个元素时，可以使用 LPOP；
当你需要获取列表中的所有元素或特定范围内的元素时，可以使用 LRANGE；
当你需要通过索引获取或设置列表中的元素时，可以使用 LINDEX；
当你需要获取列表的长度时，可以使用 LLEN。


lpush country china     	//将元素 "china" 插入到名为 "country" 的列表头部。
lpush country india         //将元素 "india" 插入到名为 "country" 的列表头部
keys *					//返回数据库中所有键的名称。
lpush country USA        //将元素 "USA" 插入到名为 "country" 的列表头部。
lrange country 0 10      //获取 "country" 列表中从索引0开始到索引10（不包括10）的元素。
lindex country 1		//获取 "country" 列表中索引为1的元素
lindex country 0         //获取 "country" 列表中索引为0的元素
lpop country			//移除并返回 "country" 列表中的第一个元素
```

```
                                尾部进出
LPUSH  RPUSH

LPUSH key value1 [value2 ...]：将一个或多个值插入到列表头部，如果列表不存在则创建一个新的列表。
RPUSH key value1 [value2 ...]：将一个或多个值插入到列表尾部，如果列表不存在则创建一个新的列表。

例如，使用 LPUSH 命令将元素 "apple"、"banana" 和 "orange" 插入到名为 "fruits" 的列表中:
LPUSH fruits apple banana orange

使用 RPUSH 命令将元素 "grape" 和 "watermelon" 插入到名为 "fruits" 的列表中：
RPUSH fruits grape watermelon
```

## 4).集合set

```
Redis的Set是 String 类型的无序集合。集合成员是唯一的，这就意味着集合中不能出现重复的数据。Redis中集合是通过哈希表实现的，所以添加，删除，查找的复杂度都是 O(1)。集合中最大的成员数为232-1(4294967295，每个集合可存储40多亿个成员)。
```

### 集合增加元素

```
sadd nameset "wanggwu"
sadd nameset "list1"
```

### 显示集合所有成员和判定集合成员

```
smembers nameset


smembers nameset list1
```

### 获得集合中元素数量

```
scard nameset
```

### 随机获得集合的一个元素

```
spop nameset
```

### 5).有序集合(sorted set)

Redis 有序集合和集合一样也是 string 类型元素的集合,且不允许重复的成员。

不同的是每个元素都会关联一个 double 类型的分数。redis正是通过分数来为集合中的成员进行从小到大的排序。

有序集合的成员是唯一的,但分数(score)却可以重复。

集合是通过哈希表实现的，所以添加，删除，查找的复杂度都是(1)。集合中最大的成员数为 232-1(4294967295，每个集合可存储 40多亿个成员)。

#### Zadd添加操作

```
zadd namezset 1 xinjin

zadd namezset 2 zhangsan

zadd namezset 3 zhangsan

zrange namezset 0 10
```

