#  一、Redis基本命令及常识

①：连接服务端：
```
./redis-cli -h 127.0.0.1 -p 6379
```
②：Redis默认是有16个数据库的（0~15）通过select命令来切换数据库
```
    select 1    -- 连接到第 2 个数据库 0开始计算
```
③：往数据库设置string类型值
```
    set name zhangsan
```
④：查看数据库中key的数量
```
    dbsize
```
⑤：查看刚才添加的key的值
```
    get name
```
⑥：查看所有key的值
```
    keys *
```
⑦：清空全部数据库和清空当前库
```
flushall（清空全部库）
flushdb（清空当前库）  
```
⑧：删除添加的name key键
```
    del name
```
# 二、Key值命令
```
key值命令可以说是一些类型的公共命令，比如有设置定时时间，排序，数据迁移等等
```
## 1.判断
```
语法：exists(key_name)
说明：判断一个键是否存在
```
```
语法：type(key_name)
说明：返回当前指定的key的类型。可返回的类型是: string,list,set,zset,hash和stream
```
## 3.删除
```
语法：delete(key_name)
说明：删除一个键
```
```
语法：del key [key ...]
说明：删除指定的key
    del name age address
语法：unlink key [key ...]
说明：其实这个和删除del命令很像，也是存在key删除，不存在则忽略；删除几个键值，则返回删除的个数
    unlink name1 name2 name3
    注：del和unlink区别
        del：它是线程阻塞的，当执行del命令是，del在没执行完时，其它后续的命令是无法进入的（要安全就使用del）
        unlink:它不是线程阻塞的，当执行unlink命令时，它会将要删除的键移交给另外线程，然后将当前要删除的键与数据库空间断开连接
                后续则由其它线程异步删除这些键（要效率快就使用unlink）
```
```
语法：flushdb
说明：删除当前选择数据库中的所有键
```
```
语法：flushall
说明：删除所有数据库中的所有键
```
## 2.修改
```
语法：move(name,db)
说明：将键移动到其他数据库
```
```
语法：rename key newkey
说明：修改key名称，存在原来则覆盖，不存在则抛错；如果修改key1为key2，key2存在，则key1覆盖key2的值
```
```
语法：renamenx key newkey
说明：修改key名称存在则覆盖，不存在则抛错；如果修改key1为key2，key2存在，则key1修改不成功
```
```
语法：copy source destination [db destination-db] [replace]
说明：拷贝当前某一个key的值，存放到新的key中（可以跨库拷贝）返回 1 成功 0 失败
    copy name1 name2  -- 把 name1 的值 拷贝到 name2 里
    copy name1 name2 db 5 -- 把 name1 的值拷贝到第6号数据库name2里
    copy name1 name2 replace -- 把 name1 的值拷贝到name2里，存在则强行覆盖
```
```
语法：move key db
说明：把指定的键值移动到选定的数据库db当中。如果key在目标数据库中已存在，或者key在源数据库中不存，则key不会被移动。
    move name 2 -- 把name移动到三号数据库里
```
```
语法：touch key [key ...]
说明：修改指定key的最后访问时间。忽略不存在的 key。（我的理解是这个键被设置/更新成功，并且被放到数据库则是成功，会返回1）
    touch name1 name2 name3     -- 返回被设置成功的键个数
```
## 3.查看
```
语法：keys pattern
说明：用来匹配和查看指定的key
    pattern：查询条件
        h?llo       匹配 hello, hallo 和 hxllo
        h*llo       匹配 hllo 和 heeeello
        h[ae]llo    匹配 hello 和 hallo, 不匹配如 hillo
        h[^e]llo    匹配 hallo, hbllo, ... 不匹配如 hello
        h[a-e]llo   匹配 hallo 和 hbllo, [a-e]说明是a~e这个范围 ，如hcllo也可以匹配
        若想匹配如转义字符的如下,就需要使用 \ 转义你想匹配的特殊字符。
        set na\me zhangsan
        keys na[\\]me
```
```
语法：exists key [key ...]
说明：返回要查询的key是否存在，存在则返回1，如果设置四个key都存在则会返回4；返回0则代表没有
    exists name -- 查看是否存在name的key
    exists name name  -- 重复写两次name ，如果name存在则返回2
    exists name address -- 查看当前是否存在name和address键
    注：exists后面不管携带单个，多个或者有重复的，最终是存在一个就累加1
```
```
语法：randomkey
说明：随机返回一个key名称
```
```
语法：dbsize
说明：获取当前数据库中键的数目
```
## 4.时间
### a.删
```
语法：persist key
说明：清除当前有定时时间的键值，设置永不过期（和普通键值一样了），关闭后并不会删除已有的键值
    persist name    -- 关闭存在定时的键值
```
### b.改
```
语法：expire (name) (time)
说明为一个存在的key设置过期时间 秒
```
```
语法：pexpire key milliseconds [nx|xx|gt|lt]
    为一个存在的key设置过期时间 毫秒
```
```
语法：ttl(key_name)
说明： 获取键的 过期时间，单位为秒，-1表示永久不过期
```

```
语法：expireat key timestamp [nx|xx|gt|lt]
    为一个存在的key设置过期时间 格式是uinx时间戳并精确到秒
```
```
语法：pexpireat key milliseconds-timestamp [nx|xx|gt|lt]
    为一个存在的key设置过期时间 格式是uinx时间戳并精确到毫秒
说明：先设置一个key，并指定过期时间 秒/毫秒/时间戳秒/时间戳毫秒 ；返回 1 成功 0 失败
    expire name 300 -- 把name键设置300秒过期
    pexpire name 3000 -- 把name键设置3000毫秒过期（3秒）
    expireat name 1633190400 -- 把name键设置为2021-10-2 00:00:00到期(精确秒)
    pexpireat name 1633190400000 -- 把name键设置为2021-10-2 00:00:00到期(精确毫秒)
    注:使用del可以删除定时的key
       使用set可以覆盖定时的key；
       使用getset可以返回并设置值，并会删除定时
       如使用rename修改key名称，那么key定时器会被携带不会被删除
```
### c.查
```
语法：ttl key
说明：查看当前有定时key的剩余时间，返回秒
```
```
语法：pttl key
说明：查看当前有定时key的剩余时间，返回毫秒
    ttl name
    pttl name
    注：没过期反剩余时间 过期反-2  没设置过期时间的key反-1
```
# 三、String（字符串）类型命令
```
字符串类型的reids操作命令,设置键值对，获得键值
```
## 1.增
```
语法：set key_name value 
说明：给数据库中键名为name的string赋予value值
```
```
语法：setnx key value
说明：设置键值，存在此键则返回0不覆盖，否则正常设置
    setnx name zhangsan     -- 设置name为键，并赋值
```
```
语法：getset key value
说明：设置更新key值，设置前先把原有的值返回出来，并设置新的值，如果key不存在时使用getset则返回nil，并设置新值
```
```
语法：setrange name offset value
说明：设置指定键的value值的子字符串
```
```
语法：mset namekey1 value  namekey2 value2
说明：批量赋值
```
```
语法：msetnx namekey1 value  namekey2 value2
说明：键均不存在时才批量赋值
```
## 2.删
```
语法：getdel key
说明：先获取到指定的key后，再删除获取的那个key；最终返回被删除的值
```
```
语法：getdel key
说明：先获取到指定的key后，再删除获取的那个key；最终返回被删除的值
```
## 3.改
```
语法：setrange key offset value
说明：偏移量offset>=0开始， 用value参数覆盖键key储存的字符串值。不存在的键key当作空白字符串处理。
    set name zhangsan   --创建原始键值
    setrange name 5 ' yu xiao'
        -- 把原有的 zhangsan 从第五位之后更改（0下标）；最终变为 "zhang yu xiao"
    setrange name 14 out
        -- 超出偏移则使用空格 '\x00' 代替一个空格；最终变为 "zhang yu xiao\x00out"
    setrange address 2 anhui
        -- 如果设置的键不存在则会新建，但是偏移量会以空格代替；最终变为 "\x00\x00anhui"
```
```
语法：append key value
说明：用于为指定的key追加值，成功后返回当前键里面的字符串全部长度（如果追加有空格需要使用 ''）
    append name 'good good boy'     -- 追加有空格的，并且成功后返回当前key的全部长度
```
```
语法：mget key [key ...]
说明：批量获取键的值，如果获取的某个不存在则返回（nil），其它正常返回
    mget name aaa   -- 批量获取name和aaa的值（aaa键不存在则返回nil）
```
```
语法：setex key seconds value
说明：将键key的值设置为value ，并将键key的过期时间设置为seconds秒钟，如果key存在则覆盖原有值
    setex name 60 zhangsan  -- 设置key为name，并且设置60秒过期时间
```
```
语法：psetex key milliseconds value
说明：将键key的值设置为value ，并将键key的过期时间设置为milliseconds毫秒，如果key存在则覆盖原有值
    psetex name 70000 zhangsan  -- 设置key为name，并且设置70秒过期时间
```
```
语法：msetnx key value [key value ...]
说明：当且仅当所有给定键都不存在时，为所有给定键设置值（如果添加的其中键在当前数据库存在则都不成功）
    msetnx是一个原子性(atomic)操作，所有给定键要么就全部都被设置，要么就全部都不设置
    msetnx name zhangsan age 22 -- 设置name和age两个键值
```
```
语法：msetnx key value [key value ...]
说明：当且仅当所有给定键都不存在时，为所有给定键设置值（如果添加的其中键在当前数据库存在则都不成功）
    msetnx是一个原子性(atomic)操作，所有给定键要么就全部都被设置，要么就全部都不设置
    msetnx name zhangsan age 22 -- 设置name和age两个键值
```
```
语法：incr key
说明：将key中储存的数字值增一，并返回增加后的值（只能用在整型，字符串啥的会报错）
```
```
语法：incrby key increment
说明：将key中储存的数字值增加指定步长increment，并返回增加后的值（只能用在整型，字符串啥的会报错）
```
```
语法：incrbyfloat key increment
说明：将key中储存的数字值增加指定步长increment，并返回增加后的值（只能用在浮点型，字符串啥的会报错）
    incrbyfloat salary 333.33   -- 对salary添加步长333.33
```
```
语法：decr key
语法：将key中储存的数字值减一，并返回减后的值（只能用在整型，字符串啥的会报错）
```
```
语法：decrby key decrement
说明：将key中储存的数字值减指定步长increment，并返回减后的值（只能用在整型，字符串啥的会报错）
```
## 4.查
```
语法：get key
说明：如果键key不存在，那么返回特殊值nil；否则返回键key的值。
    get name -- 获取name键的值
```
```
语法：getset key_name value
说明：给数据库中键名为name的string赋予值value并返回上次的 value
```
```
语法：mget(keys,*aIgS)
说明：返回多个键对应的value 组成的列表
```
```
语法：setnx(name,value)
说明：如果不存在这个键值对，则更新 value,否则不变
```
```
语法：getrange key start end
说明：获取指定的范围值，start（从0开始）end（从0开始）
    set name zhangsan
    getrange name 2 5  -- 获取范围值，最终返回 'angs'
    getrange name 3 -2 -- 获取范围值，最终返回 'ngsa'
    注：若使用getrange name 0 -1 (其中-1代表从后往前数)
```
```
语法：getex key_name time value
说明：设置可以对应的值为string类型的value，并指定此键值的有效期
```
```
语法：strlen key
说明：获取指定key所储存的字符串值的长度。当key储存的不是字符串类型时，返回错误。
```
```
语法：substr name start end=-1
说明：返回键名为name的string 的子字符串
```

# 四、Hash（哈希表）类型命令
```
Redishash 是一个string类型的field(字段)和value(值)的映射表，hash 特别适合用于存储对象。
Redis中每个hash可以存储232-1 键值对(40多亿)。
```
## 1.增
```
语法：hset key field value [field value ...]
说明：用于为存储在key中的哈希表的field字段赋值value
    hset student name zhangsan age 22   -- 设置key为student但里面存储着name和age字段
```
```
语法：hmset key field value [field value ...]
说明：用于同时将多个field-value(字段-值)对设置到哈希表中。此命令会覆盖哈希表中已存在的字段
    注：Redis4.0.0起被废弃，推荐使用hset，它也可以一次性添加多个
```
```
语法：hsetnx key field value
说明：用于为存储在key中的哈希表的field字段赋值value；如果当前field存在则添加失败（不可覆盖添加）
```
## 2.删
```
语法: hdel key_name field
说明：删除哈希表
```
## 3.查
```
语法：hget key field
说明：用于返回哈希表中指定字段field的值
    hget student name  -- 获取哈希表里的field字段
```
```
语法：hmget key field [field ...]
说明：用于返回哈希表中指定字段field的值；但是可以一次性返回多个field值
     hmget student name age     --  获取哈希表里的field多个字段
```
```
语法：hdel key field [field ...]
说明：用于删除哈希表key中的一个或多个指定字段，不存在的字段将被忽略。如果key不存在，会被当作空哈希表处理并返回0
     hdel student name  -- 删除哈希表中key为student里的name字段
```
```
语法：hexists key field
说明：用于查看哈希表的指定字段field是否存在，1存在，0不存在
    hexists student name    -- 查看哈希表中key为student里的name字段是否存在
```
```
语法：hgetall key
说明：用于返回存储在key中的哈希表中所有的field和value。
```
```
语法：hkeys key
说明：返回存储在key中哈希表的所有field
```
```
语法：hvals key
说明：返回存储在key中哈希表的所有value
```
```
语法：hincrby key field increment
说明：为哈希表key中的field的值加上指定的增量，并返回增量后的值（增量正数累加，增量负数递减）
    hincrby student age 2       -- 对年龄累加
    hincrby student age -28     -- 对年龄递减
    注：当前命令只可操作整数类型，而字符串，浮点类型啥的会报错
```
```
语法：hincrbyfloat key field increment
说明：为哈希表key中的field的值加上指定的增量，并返回增量后的值（增量正数累加，增量负数递减）
    hincrby student salary 300.3       -- 对工资累加
    hincrby student salary -432.84     -- 对工资递减
    注：当前命令只可操作整数类型、浮点类型，而操作字符串会报错
```
```
语法：hstrlen key field
说明：返回存储在key中给定field相关联的值的字符串长度（string length）
```
```
语法：hlen key
说明：用于获取哈希表中字段(fields)的数量
```
```
语法：hrandfield key [count [withvalues]]
说明：随机返回key里的field字段
    count：返回的field个数，如果是正数且超过key里的field总数则全部返回，
                          如果是负数且超过key里的field总数绝对值则返回空，
        整数则返回不重复字段，负数则可能返回重复字段
        注：在传 1 或 -1 它是随机在key里面选择，
        在传 2 则随机返回key里的2个field字段，这两个field不可能存在重复
        在传-2 则随机返回key里的2个field字段，这两个field可能会存在重复
    withvalues：返回field字段时后面还返回当前field的值
```
```
语法：hscan key cursor [match pattern] [count count]
说明：用于遍历哈希表中的键值对
    cursor：游标（告诉迭代器从哪开始迭代）
    [match pattern]：过滤筛选条件
    [count count]：迭代的个数
    hscan student 0 match * count 2
        -- 迭代student里的field字段，下标0开始，过滤条件*全部，但是每次迭代count为2，但2不起作用（没研究）
        -- 具体可以查看我些的scan命令，全文搜索
```
# 五、List（集合）类型命令
```
Redis 列表是简单的字符串列表,按照插入顺序排序。你可以添加一个元素到列表的头部(左边)或者尾部(右边)一个列表最多可以包含232-1个元素(4294967295,每个列表超过40亿个元素)。
```
## 1.增
```
语法：sadd name values
说明：添加多个值
```
```
语法：rpush key values
说明：将一个或多个值插入到集合key的尾部（尾插法），如果当前key不存在则创建新的
```
```
语法：lpush key element [element ...]
说明：将一个或多个值插入到集合key的头部（头插法），如果当前key不存在则创建新的
     lpush listNumber 8.4 13 14 10.5 4 19.6 10 14 5.2 10 3 2.5 7 4.7 10 11.2 8 2.2 15.7 20.9
     lpush listString  remini Momen Pledg Memo Tende Biode Revie silen Romanti AusL Simpl 　　　　　　Promis Romanti Bautifu smil Initiall sunse lemo firs Chaffere
        -- 插入两个案例，后面以这个说明
```
```
语法：lpushx key element [element ...]
说明：往集合左边插入一个元素；若集合key不存在无法插入
```
```
语法：rpushx key element [element ...]
说明：往集合右边插入一个元素；若集合key不存在无法插入
```
## 2.删
```
语法：lpop key [count]
说明：从集合左边（头部）弹出（删除）指定的count个元素删除
lpop listString 2   -- 从集合左边弹出两个元素删除
```
```
语法：rpop key [count]
说明：从集合右边（尾部部）弹出（删除）指定的count个元素删除
```
```
语法：blpop key [key ...] timeout
说明：移出并获取集合头部第一个元素，如果集合没有元素会阻塞集合直到等待超时或发现可弹出元素为止，它是lpop的阻塞版
    key：如果当前key不存在或者key内部没元素，则一直阻塞等待，等待其它客户端创建此key和元素，会立马弹出
        但是超出延迟时间的话还没有弹出元素则会在最后弹出(nil)
    [key ...]：设置多个key时，如果第一个key不存在则会考虑弹出第二个key,第三个key....，如果每个key都不存在或没元素
        则当前客户端会进入一个阻塞状态，直到有元素弹出，或者自动超时弹出(nil)
    127.0.0.1:6379> blpop listA mylist 480
```
```
语法：brpop key [key ...] timeout
说明：移出并获取集合尾部第一个元素，如果集合没有元素会阻塞集合直到等待超时或发现可弹出元素为止，它是lpop的阻塞版
```
```
语法：lmove source destination left|right left|right
说明：用于原子地从source集合左边或者右边弹出一个元素，添加到destination新集合里的左边或右边
    source：源集合
    destination：目标集合
    left|right left|right：
        第一个：代表从源集合的左边或者右边弹出元素
        第二个：代表从目标集合的左边或者右边添加
    lmove listString mylist left right
        -- 从listString源集合的左边弹出个元素，添加到mylist目标集合的右边
```
```
语法：rpoplpush source destination
说明：原子地从集合source中移除并返回最后一个元素，然后把这个元素插入集合destination的第一个元素
    source：源集合
    destination：目标集合
    注：此方法在Redis6.2.0被废除（使用lmove代替）
```
```
语法：blmove source destination left|right left|right timeout
说明：用于原子地从source集合左边或者右边弹出一个元素，添加到destination新集合里的左边或右边，但是它时lmove的阻塞版本
    blmove listString mylist left right 60  -- 从集合listString左边弹出一个元素放到目标集合mylist的尾部
         但是存在60秒的超时时间，超过60秒没有弹出元素则自动失败，返回(nil)
```
```
语法：brpoplpush source destination timeout
说明：原子地从集合source中移除并返回最后一个元素，然后把这个元素插入集合destination的第一个元素（已废弃使用blmove代替）
    brpoplpush listString mylist 50 -- 从集合listString尾部弹出一个元素添加到目标mylist集合的头部，超时时间50秒
```
## 3.改
```
语法：linsert key before|after pivot element
说明：把element元素插入到指定集合key里，但是还要以pivot内部的一个元素为基准，看是插到这个元素的左边还是右边
    before|after：插入元素的前后位置选项
    pivot：集合里的参考元素
    element：待插入的元素
    注：当集合key不存在时，这个list会被看作是空list，什么都不执行
    注：当集合key存在，值不是列表类型时，返回错误
    注：当给定的参考元素pivot不存在是则返回-1，因为程序不知道往哪插入
    linsert listString after Romanti niubi -- 把niubi插入到listString集合里，插入参考Romanti元素的后面
```
```
语法：linsert key before|after pivot element
说明：把element元素插入到指定集合key里，但是还要以pivot内部的一个元素为基准，看是插到这个元素的左边还是右边
    before|after：插入元素的前后位置选项
    pivot：集合里的参考元素
    element：待插入的元素
    注：当集合key不存在时，这个list会被看作是空list，什么都不执行
    注：当集合key存在，值不是列表类型时，返回错误
    注：当给定的参考元素pivot不存在是则返回-1，因为程序不知道往哪插入
    linsert listString after Romanti niubi -- 把niubi插入到listString集合里，插入参考Romanti元素的后面
```
```
语法：ltrim key start stop
说明：修订一个已经存在的集合；修订一个指定范围的元素放到当前集合中
```
## 4.查
```
语法：llen key
说明：获取到集合里元素的总个数
```
```
语法：lrange key start stop
说明：查询集合元素，并设置查询区间
    start：起始值，设置正数则从左往右，设置负数则从右往左开始
    stop：终点值，设置正数则从左往右，设置负数则从右往左开始
    注：start（0） stop（-1）代表查询全部
    lrange listString -5 -3
        -- 起点从尾部往前数5个，终点从尾部往前数3个；最终显示 -5，-4，-3这三个元素
    lrange listString -5 -8
        -- 起点从尾部往前数5个，终点从尾部往前数8个；最终显示(empty array)
```
```
语法：lindex key index
说明：返回集合key里索引index位置存储的元素，0~n从左往右索引、-1~-n从右往左索引
    lindex listString -1    --  获取集合listString里的最后一个索引的元素
```
```
语法：lrem key count element
说明：从集合key中删除前count个值等于element的元素
    count > 0: 从头到尾删除值为 value 的元素
    count < 0: 从尾到头删除值为 value 的元素
    count = 0: 移除所有值为 value 的元素
    lrem listString -2 Romanti
        -- 移除集合listString中的Romanti元素，删除个数-2（代表从尾部查找并删除两个），并返回删除成功个数
```
```
语法：lset key index element
说明：设置集合key中index位置的元素值为新的element，index为正数则从头到位索引，为负数从尾到头索引查询
     lset listString 2 yyds  -- 修改集合listString中索引为2的元素为yyds
```
```
语法：lpos key element [rank rank] [count num-matches] [maxlen len]
说明：返回集合key中匹配给定element成员的索引
    key：要查询的集合key
    element：要查询索引的元素
    [rank rank]：选择匹配上的第几个元素，若超出集合指定元素的个数则返回(nil)
    [count num-matches]：返回匹配上元素的索引个数，默认返回1个
    [maxlen len]：告知lpos命令查询集合的前len个元素，限制查询个数
    lpos listString Romanti     -- 查询集合listString里的Romanti出现的索引位置（0开始索引）
    lpos listString Romanti rank 2  -- 查询Romanti元素的第二个索引位置
    lpos listString Romanti rank 1 count 3  -- 查询Romanti索引的三条记录
    lpos listString Romanti rank 1 count 3 maxlen 20    -- 限制查询下标为0~20
```
# 七、Set（无序集合）类型命令

```
Redis的Set是 String 类型的无序集合。集合成员是唯一的，这就意味着集合中不能出现重复的数据。Redis中集合是通过哈希表实现的，所以添加，删除，查找的复杂度都是 O(1)。集合中最大的成员数为232-1(4294967295，每个集合可存储40多亿个成员)。
```
## 1.增
```
语法：sadd key member [member ...]
说明：将一个或多个元素加入到集合中，添加已存在的集合元素将被忽略（不会添加上），返回添加成功的元素个数
127.0.0.1:6379> sadd mysetA zhangsan lisi wangwu mazi zhangsan
-- 成功添加四个元素，其中一个为重复的，无法添加
```
```
语法：sscan key cursor [match pattern] [count count]
说明：用于遍历集合中键的元素，sscan继承自scan，具体可以参考scan，上面第三章有说明
    key：迭代指定元素
    cursor：游标（告诉迭代器从哪开始迭代）
    [match pattern]：过滤筛选条件
    [count count]：迭代的个数
```
## 2.删
```
语法：srem key member [member ...]
说明：删除指定的元素；如果指定的元素不是集合成员则被忽略，返回被删除元素个数，不含不存在的元素
```
```
语法：spop key [count]
说明：从集合key中删除一个或多个随机元素，并返回删除的元素
```
```
语法：srandmember key [count]
说明：随机返回集合key中的一个或多个随机元素，若返回个数的count大于集合总数则返回全部
    注：srandmember随机返回不删除原集合，spop返回并删除原集合返回的元素
```
```
语法：sdiff key [key ...]
说明：返回第一个集合与其它集合之间的差异；说白就是第一个集合的某个元素在其它集合都不存在则这个元素会被返回，
    key1 = {a,b,c,d}
    key2 = {c}
    key3 = {a,c,e}
    SDIFF key1 key2 key3  = {b,d}
    注：如果只携带一个key比较则会返回当前集合全部元素
```
## 3.改
```
语法：sdiff key [key ...]
说明：返回所有给定键的集合的差集
    key1 = {a,b,c,d}
    key2 = {c}
    key3 = {a,c,e}
    SDIFF key1 key2 key3  = {b,d}
    注：如果只携带一个key比较则会返回当前集合全部元素
```
```
语法：sdiffstore dest keys
说明：求差集并将差集存到dest集合
    127.0.0.1:6379> sdiffstore newmyset mysetA mysetB
    (integer) 2
```
```
语法：sinter key [key ...]
说明：返回第一个集合与其它集合之间的交集；说白就是第一个集合的某个元素在其它集合都存在则这个元素会被返回，
    key1 = {a,b,c,d}
    key2 = {c}
    key3 = {a,c,e}
    SINTER key1 key2 key3 = {c}
    注：如果只携带一个key比较则会返回当前集合全部元素
    举例：
        127.0.0.1:6379> sadd mysetA zhangsan lisi wangwu mazi zhangsan
        (integer) 4
        127.0.0.1:6379> sadd mysetB anhui shanghai zhangsan mazi
        (integer) 4
        127.0.0.1:6379> sinter mysetA mysetB
```
```
语法：sinterstore dest keys
说明：此命令和sinter功能差不多，不同的是它将结果保存到destination集合，并返回成功添加到新集合上的个数。
    127.0.0.1:6379> sinterstore newmyset mysetA mysetB
    (integer) 2
destination：结果集
keys：键名序列
```
```
语法：sunion keys
说明：用于返回所有给定集合的并集
    key1 = {a,b,c,d}
    key2 = {c}
    key3 = {a,c,e}
    sunion key1 key2 key3 = {a,b,c,d,e}
    注：如果只携带一个key比较则会返回当前集合全部元素
    举例：
        127.0.0.1:6379> sadd mysetA zhangsan lisi wangwu mazi zhangsan
        (integer) 4
        127.0.0.1:6379> sadd mysetB anhui shanghai zhangsan mazi
        (integer) 4
        127.0.0.1:6379> sunion mysetA mysetB
```
```
语法：sunionstore destination keys
说明：类似于sunion，不同的是不返回结果集，而是把返回存储在destination集合中。
    127.0.0.1:6379> sunionstore newset mysetA mysetB
    (integer) 6
```
```
语法：scard key
说明：返回集合中元素的数量（整型值）
```
```
语法：smembers key
说明：返回存储在key中的集合的所有的成员，此命令可以使用携带单个key的sdiff、sinter、sunion命令替代
```
```
语法：sismember key member
说明：判断元素member是否是集合key的成员，是返回1，否则0
    127.0.0.1:6379> sismember mysetA zhangsan
```
```
语法：smove source destination member
说明：从集合source中移动成员member到集合destination；
    注：返回1代表成功，返回0代表移动element元素在source不存在
    注：移动成功后会把element元素在原集合上删除
    注：若被移动的元素在两个集合都存在，则会覆盖移动，再删除原集合上的元素
    smove mysetA mysetB  zhangsan   -- 把元素zhangsan从集合mysetA移动到mysetB上
```
## 4.查
```
语法：smove src dst value
说明：从src对应的集合移除元素并将其添加到dst对应的集合中
src:源集合
dst:目标集合
```
```
语法：smembers key_name
说明：返回键名为name的集合的所有元素
```
```
语法：sscan key cursor [match pattern] [count count]
说明：用于遍历集合中键的元素，sscan继承自scan，具体可以参考scan，上面第三章有说明
    key：迭代指定元素
    cursor：游标（告诉迭代器从哪开始迭代）
    [match pattern]：过滤筛选条件
    [count count]：迭代的个数
```
```
语法：scard key_name
说明：返回键名为name的集合的元素个数
```
## 5.判断
```
语法：sismember key member
说明：判断元素member是否是集合key的成员，是返回1，否则0
    127.0.0.1:6379> sismember mysetA zhangsan
```
```
语法：smismember key member [member ...]
说明：批量判断元素members是否是集合key的成员，是返回1，否则0
    127.0.0.1:6379> smismember mysetA zhangsan lisi
```
```
语法：smove source destination member
说明：从集合source中移动成员member到集合destination；
    注：返回1代表成功，返回0代表移动element元素在source不存在
    注：移动成功后会把element元素在原集合上删除
    注：若被移动的元素在两个集合都存在，则会覆盖移动，再删除原集合上的元素
    smove mysetA mysetB  zhangsan   -- 把元素zhangsan从集合mysetA移动到mysetB上
```

# 八、SortedSet（有序集合）类型命令
## 1.增
```
语法：zadd key [nx|xx] [gt|lt] [ch] [incr] score member [score member ...]
说明：用于将一个或多个member元素及其score值加入到有序集key当中，若添加的member已存在则更新当前分数
    [nx|xx]:
        nx：只能做添加操作
        xx：只能做更新操作
    [gt|lt]:
        gt：更新的元素分数必须比原分数大
        lt：更新的元素分数必须比原分数小
    [ch]：返回添加和更新成功的个数
    [incr]：累加操作，score代表更新member的步长
    注：gt,lt 和 nx 三者互斥不能同时使用
    注：分数的取值范围-9007199254740992到9007199254740992
```
```
语法：zincrby key  member increment
说明：为有序集key的成员member的score值加上增量increment
    注：若key不存在，或者member不是当前key成员，则此命令自动转换为zadd命令
zincrby chinas 4 Anhui  -- 在有序集合上的Anhui元素分数增量 +4
```
## 2.删
```
语法：zrem key_name values
说明：删除键名为name的 zset 中的元素
```
```
语法：zrem key member [member ...]
说明：用于从有序集合key中删除指定的多个成员member。如果member不存在则被忽略
```
```
语法：zremrangebyrank key start stop
说明：移除有序集key中，指定排名(rank)区间start和stop内的所有成员，下标参数start和stop都是从0开始计数
    注：按照下标删除元素
    zremrangebyrank myzsetA 0 -2 -- 删除从左边开始到右边倒数第二个的范围元素
```
```
语法：zremrangebylex key min max
说明：删除成员名称按字典由低到高排序介于min和max之间的所有成员；按照元素删除的话推荐在分数相同
     的情况下使用，因为每次添加带有不同分数的元素会找到自己的位置插入添加，不是按照字典由低到高插入添加
     所有我们后期删除时结果由于分数的影像导致删除不准确
    注：按照元素删除元素
    zremrangebylex myzsetA [aa (kk -- 删除元素在aa ~ kk 之间的（包括aa，不包括kk）
```
```
语法：zremrangebyscore key min max
说明：移除有序集key中，所有score值介于min和max之间(包括等于min或max)的成员
    注：按照分数删除元素
    zremrangebyscore myzsetA (-2 (30    -- 根据分数删除指定范围的元素（不包含-2和30）
```
```
语法：zpopmax key [count]
说明：删除分数最高的count个元素，如果未指定count则默认为1 ，删除会按照排序从高到低删除指定count个元素
```
```
语法：zpopmin key [count]
说明：删除分数最低的count个元素，如果未指定count则默认为1 ，删除会按照排序从低到高删除指定count个元素
```
```
语法：bzpopmax key [key ...] timeout
说明：和zpopmax一样，只不过是阻塞删除（若没有指定集合或元素则等待被创建），一次性删除一个，超时就自动退出
```
```
语法：bzpopmin key [key ...] timeout
说明：和zpopmin一样，只不过是阻塞删除（若没有指定集合或元素则等待被创建），一次性删除一个，超时就自动退出
```
## 3.查
```
语法：zrange key min max [byscore|bylex] [rev] [limit offset count] [withscores]
说明：返回有序集中，指定区间内的成员，其中成员查询可以按照下标，分数，元素来获取指定范围
    key：要查询的有序集合
    min：查询范围的最小值，按照不同的方式写不同的最小值
        下标查询写下标值（默认）,分数查询写分数值（设置byscore），元素查询写元素值（设置bylex）
    max：查询范围的最大值，按照不同的方式写不同的最大值
        下标查询写下标值（默认）,分数查询写分数值（设置byscore），元素查询写元素值（设置bylex）
    [byscore|bylex]：
        byscore：按照分数排序，此时查询时只会按照分数的范围查询，切记不能写字符啥的
            -inf +inf byscore 代表查询分数在负无穷 ~ 正无穷
            -20 20    byscore 代表查询分数在 -20 ~ 20之间的元素(包含-20和20)
            10 (20    byscore 代表查询分数在 10 ~ 20之间的元素(包含10，不包含20)
        bylex：按照元素属性ASCLL来排序，此时查询时只会按照元素范围查询

   - + bylex       代表查询元素范围为全部
		   - [cc bylex     代表从开头查询到元素 cc 位置（包含cc）
			[aa [dd bylex   代表查询元素为aa ~ dd之间的范围（包含aa和dd）
			  (cc [ff bylex   代表查询元素为cc ~ ff之间的范围（包含ff，不包含cc）
			  (aa (ee bylex   代表查询元素为aa ~ ee之间的范围（不包含aa和ee）
			[rev]：设置倒序排列，这时候我们就得注意写最大值和最小值要反过来写
			[limit offset count]：筛选后的结果排序
			    offset：起始位（0下标开始数）
			    count：查询元素个数
			[withscores]：最终查询结果显示分数，但是只适用于byscore查询和默认下标查询
注：下标查询时是默认的，不用写[byscore|bylex]，下面写-1，代表右边第一个，所有0 -1代表查询全部
注：若某个有序集合使用元素查询时（bylex），那么我推荐你最好使用分数都是相同的有序集合！
因为分数会打乱原有我们添加的顺序，下面举个普通例子：
执行命令=>：zadd newKey 6 aa 3 bb 4 cc
有序集合存储元素变为=>：3 bb 4 cc 6 aa
它会按照分数排序了，这样按照元素获取范围就不准了，如获取[aa [bb bylex
127.0.0.1:6379> zrange newKey 0 -1
	1) "bb"
	2) "cc"
	3) "aa"
127.0.0.1:6379> zrange newKey [aa [cc bylex
	4) "bb"
	5) "cc"
	6) "aa"
127.0.0.1:6379> zrange newKey [aa [bb bylex
	7) "bb"
此时会发现有点不对劲，[aa [bb bylex 为什么没有aa呢？因为分数打乱了顺序
其实用到元素查询那么有序集合里面的每个元素分数都是相同的，添加相同分数，元素会强行按照字典ASCII进行排序
执行命令=>：zadd newKey1 0 bb 0 aa 0 cc
执行时插入时遇到分数相同的则会对元素的ASCII排序
127.0.0.1:6379> zrange newKey1 0 -1
	8) "aa"
	9) "bb"
	10) "cc"
127.0.0.1:6379> zrange newKey1 [aa [bb bylex
	11) "aa"
	12) "bb"
```
```
语法：zinter numkeys key [key ...] [weights weight [weight ...]] [aggregate sum|min|max] [withscores]
说明：计算numkeys个有序集合的交集（就是把几个相同元素的分数进行处理）
    numkeys：计算交集的key个数
    key | [key ...]：设置要处理交集的有序集合，按照我们给出的numkeys写指定个数的key
    [weights weight [weight ...]]：权重计算（乘法因子）；要设置权重的话，则有几个key就得写几个权重值
        若key1 key2 weights 10 15 说明：第一个key里面的全部分数要乘于10，第二个key的全部分数乘于15
        注：此属性在交集、并集计算中都存在，只要是符合[交集|并集]的才会计算并返回给客户端
    [aggregate sum|min|max]：你可以指定交集、并集的结果集的聚合方式
        注：指定sum（默认）则交集的元素的分数结合，若指定max，则会选择最大的作为交集的分数
    [withscores]：显示分数
```
```
语法：zunion numkeys key [key ...] [weights weight [weight ...]] [aggregate sum|min|max] [withscores]
说明：计算给定的numkeys个有序集合的并集，并且返回结果
     numkeys：计算交集的key个数
     key | [key ...]：设置要处理交集的有序集合，按照我们给出的numkeys写指定个数的key
     [weights weight [weight ...]]：权重计算（乘法因子）；要设置权重的话，则有几个key就得写几个权重值
         若key1 key2 weights 10 15 说明：第一个key里面的全部分数要乘于10，第二个key的全部分数乘于15
         注：此属性在交集、并集计算中都存在，只要是符合[交集|并集]的才会计算并返回给客户端
     [aggregate sum|min|max]：你可以指定交集、并集的结果集的聚合方式
         注：指定sum（默认）则交集的元素的分数结合，若指定max，则会选择最大的作为交集的分数
     [withscores]：显示分数
     注：并集就是把几个集合的元素并到一起（不漏任何元素），然后单个元素单独计算，多个元素计算后合并到一起
```
```
语法：zinterstore destination numkeys key [key ...] [weights weight [weight ...]] [aggregate sum|min|max]
说明：计算numkeys个有序集合的交集，并且把结果放到destination中；具体操作看zinter，
    destination：新集合名称，用来存放处理好交集的数据
```
```
语法：zunionstore destination numkeys key [key ...] [weights weight [weight ...]] [aggregate sum|min|max]
说明：计算给定的numkeys个有序集合的并集，并且把结果放到destination中。（具体参考zunion）
    destination：计算后的结果返回到指定的有序集合里
```
```
语法：zrangebyscore key min max [withscores] [limit offset count]
说明：（演变）返回有序集中，按照分数来指定区间内的成员，具体参考zrange
    zrangebyscore myzsetA -inf +inf withscores  -- 查询分数在负无穷~正无穷
```
```
语法：zrangebylex key min max [limit offset count]
说明：（演变）返回有序集中，按照元素来指定区间内的成员，具体参考zrange
     zrangebylex myzsetA [aa [dd    -- 查询元素在aa ~ dd之间（包含aa和dd）
```
```
语法：zrangestore dst src min max [byscore|bylex] [rev] [limit offset count]
说明：（演变）指定区间内的成员，其中成员查询可以按照下标，分数，元素来获取指定范围，并存储在dst新的有序集合里
    dst：存储查询结果的有序集合
    src：要查询的有序集合
    注：具体操作和参数介绍看zrange
    zrangestore newzset myzsetA 0 -1 -- 查询的全部元素存放到指定有序集合里，返回添加成功的个数
```
```
语法：zrevrange key start stop [withscores]
说明：（演变）返回有序集key中，指定区间内的成员。其中成员的位置按score值递减(从高到低)来排列获取
     zrevrange myzsetA 0 -1 withscores  -- 查询有序集合中myzsetA的全部元素的分数降序
```
```
语法：zrevrangebyscore key max min [withscores] [limit offset count]
说明：（演变）返回有序集合key中指定分数区间的成员列表。有序集成员按分数值递增(从小到大)次序排列获取
     zrevrangebyscore myzsetA +inf -inf withscores -- 按照分数降序区间查询
```
```
语法：zrevrangebylex key max min [limit offset count]
说明：（演变）返回有序集合key中指定元素区间的成员列表来获取按元素字典排序递增(从小到大)次序排列获取
     zrevrangebylex myzsetA + -     -- 按照元素降序区间查询
```
```
语法：zcard key
说明：获取有序集的成员个数
```
```
语法：zrank key member
说明：返回有序集key中成员member的排名，其中有序集成员按score值从低到高排列，（推荐分数相同时使用）
    注：推荐在有序集合相同分数的情况下使用，具体可以本章的zrange
    zrank myzsetA cc    -- 获取有序集合中myzsetA的cc下标位置
```
```
语法：zrevrank key member
说明：返回有序集key中成员member的排名，其中有序集成员按score值从高到低排列
     zrevrank myzsetA jj  -- 倒序获取有序集合中的 jj 位置下标
```
```
语法：zscore key member
说明：用于返回有序集和key中成员member的分数（不存在的元素返回nil）
```
```
语法：zmscore key member [member ...]
说明：用于返回有序集和key中多个成员member的分数（不存在的元素返回nil）
    zmscore myzsetA aa bb ccc   查看aa、bb、ccc分数（ccc不存在返回nil）
```
```
语法：zrandmember key [count [withscores]]
说明：随机获取有序集合key内部的指定元素个数的，
    注：当count为1 或者 -1 看不出效果
    注：当count为 2 ~ 正无穷 ，则会返回不同的元素，不会重复，若集合5个元素，你count为10，最终也返回5个几个（不能重复）
    注：当count为 -2 ~ 负无穷，则可能会出现返回重复的元素，若集合5个元素，你count为100，最终会随机获取100个返回
    127.0.0.1:6379> zrandmember zsetB 6 withscores      -- 把集合内部的4个元素全部返回出来了，无法返回6个（不能重复）
```
```
语法：zscan key cursor [match pattern] [count count]
说明：迭代遍历集合内部元素（具体查看scan命令）
    cursor：游标（告诉迭代器从哪开始迭代）
    [match pattern]：过滤筛选条件
    [count count]：迭代的个数
    zscan  myzsetA 0 match * count 2
        -- 遍历有序集合myzsetA，从游标0开始（最头部），查询两个
```
## 4.其它

```
语法：zcount key min max
说明：返回有序集key中，score值在min和max之间(min<=score>=max)的成员的数量
    min：最小值，可以使用 -inf 代表负无穷大，默认是包含最小值，source>=min；若不包含可在值前面添加 '(' 如 (-20
    max：最大值，可以使用 +inf 代表正无穷大，默认是包含最大值，source<=max；若不包含可在值前面添加 '(' 如 (20
    举例：
        zcount myzsetA -inf +inf    -- 查询有序集合里的全部成员数量
        zcount myzsetA -20 15       -- 查询成员分数在-20 ~ 15 之间，包含-20和15
        zcount myzsetA (-20 (20     -- 查询成员分数在-20 ~ 20 之间，不包含-20和20

语法：zlexcount key min max
说明：返回有序集合key中，元素在min和max之间的成员数量，元素是按照字典排序（ASCII）的方式存在min和max
    注：关于对元素范围统计，推荐元素的分数都为一个固定的相同值，要不然会有一个偏差，（具体看range参数说明）
    zlexcount zsetC  [bb [gg -- 获取有序集合zsetC里bb ~ gg范围元素个数（包含bb和gg）
```
```
语法：zdiff numkeys key [key ...] [withscores]
说明：计算第一个有序集合与其它集合的元素差异，并返回给客户端，若指定一个有序集合key则返回全部元素
    注：numkeys设置key的数量，必须与key个数对应
    zdiff 2 zsetA zsetB
    1) "xiechao"
    2) "wanger"
        -- 以zsetA为基准计算与其它集合的差异
```
```
语法：zdiffstore destination numkeys key [key ...]
说明：计算第一个有序集合与其它集合的元素差异，并存放到新集合中，若新集合存在则覆盖里面内容
    注：numkeys设置key的数量，必须与key个数对应
    zdiffstore newzset 2 zsetA zsetB
    (integer) 2
         -- 以zsetA为基准计算与其它集合的差异，并存放到newzset集合中
```

# 九、GeoSpatial（地理空间）特殊类型命令

```
geospatial地理位置命令其实底层使用的是zset，我们可以通过type来验证geospatial的空间集合key，会返回zset，那么就可以说明geospatial里面添加的全部元素我基本上可以使用zset的命令处理，但是针对geospatial内的一些特有命令是无法使用zset命令来处理的，我们最多使用zset内的zrange（查询）,zrem（删除）等
```




```
测试数据：geoadd wan 117.30794 31.79322 hefei 118.38548 31.34072 wuhu 116.53949 31.74933 luan 115.77914 33.87641 bozhou 117.56733 30.68673 chizhou 118.75634 30.94622 xuancheng 118.30553 32.2948 chuzhou 116.97728 33.64004 suzou
语法：geoadd key [nx|xx] [ch] longitude latitude member [longitude latitude member ...]
说明：将指定的地理空间(经度、纬度、名称)添加到指定的键中。数据以排序集的形式存储到键中
    [nx|xx]：
        nx：只能进行添加操作，无法更新已经存在的坐标
        xx：只能进行更新操作，无法添加一个不存在的坐标
    [ch]：ch是changed缩写，添加此属性，就会在每次成功后返回添加成功的坐标和更改成功的坐标的次数汇总
        注：geoadd的默认不添加ch的返回值只计算新增元素的数量，而更新的则不统计在内
    longitude：经度
    latitude：纬度
    member：坐标名称
    注：有效经度 -180° ~ 180°
    注：有效纬度 -85.05112878° ~ 85.05112878°
    举例：
        geoadd Anhui 117.30794 31.79322 hefei 118.38548 31.34072 wuhu 116.53949 31.74933 luan
        (integer) 3
            -- 在安徽key里面添加合肥、芜湖、六安三地坐标
        geoadd Anhui 115 32 hefei 119 32 wuhu 117.03424 30.51227 anqing
        (integer) 1
            -- 在安徽key里面更新 合肥、芜湖，并添加一个 安庆 （参考第一条命令）
        geoadd Anhui nx 118.75634 30.94622 xuancheng
        (integer) 1
            -- 用nx修饰，只能添加元素，无法修改，添加 宣城坐标
        geoadd Anhui xx 119.75634 32.94622 xuancheng
        (integer) 0
            -- 用xx修饰，只能修改元素，无法添加，修改 宣城坐标；；这里默认修改是不返回具体数据，只返回0
        geoadd Anhui ch 119 33 xuancheng 118 32 anqing 116.83359  32.63142 huainan
        (integer) 3
            -- 用ch修饰，表示更改、添加都会被记录统计，两次修改一次添加（三次操作）
安徽省16个市的坐标
   经度       纬度      名称
117.30794  31.79322   合肥市
118.38548  31.34072   芜湖市
117.36779  32.94448   蚌埠市
116.83359  32.63142   淮南市
118.84432  31.55856   马鞍山市
116.82803  33.99141   淮北市
117.80103  30.90466   铜陵市
117.03424  30.51227   安庆市
118.14161  30.27296   黄山市
115.85668  32.91303   阜阳市
116.97728  33.64004   宿州市
118.30553  32.2948    滁州市
116.53949  31.74933   六安市
118.75634  30.94622   宣城市
117.56733  30.68673   池州市
115.77914  33.87641   亳州市

语法：geopos key member [member ...]
说明：从键里面返回所有给定位置元素的位置（经度和纬度）
    注：返回的坐标可能不完全是当初添加元素的坐标，可能会有一点点误差
    127.0.0.1:6379> geopos Anhui hefei luan     -- 获取合肥和六安的地理空间经纬度
    1) 1) "117.30793744325637817"
       2) "31.79321915080526395"
    2) 1) "116.53948992490768433"
       2) "31.74933045393131437"

语法：geodist key member1 member2 [m|km|ft|mi]
说明：计算并返回两个元素地理空间之间的距离，若其中一个地理空间不存在则计算返回一个（nil）空
    [m|km|ft|mi]：
    m(meter)：米     km(kilometer)：千米   ft(ft)：英尺   mi(miles)：英里
    1000m = 1km ；5280ft = 1mi ；1mi = 1609.34m
    举例：
        geodist Anhui hefei luan km     -- 计算千米
        "72.8279"
        geodist Anhui hefei luan m      -- 计算米
        "72827.8708"

语法：geohash key member [member ...]
说明：返回一个有效的hash字符串，返回的字符串是11位的字符，它与Redis内部的52位表示精度相差可以忽略
     若两个11位的hash字符串越接近，那么代表坐标越接近
     127.0.0.1:6379> geohash Anhui luan hefei       -- 获取六安和合肥的距离
     1) "wtduegv3qb0"
     2) "wtekv7v0cj0"

语法：georadius key longitude latitude radius m|km|ft|mi [withcoord] [withdist] [withhash] [count count [any]] [asc|desc] [store key] [storedist key]
说明：获取指定空间集合key里空间元素在给定的经纬度范围之内的空间元素，可以用于实现附近的人功能
    （我们提供一个经纬度（中心点），再指定一个之前geoadd添加的空间集和，然后再设置查询范围，看看哪些地理空间元素在空间范围内（参考雷达图））
    注：在Redis6.2.0版本中推荐使用geosearch、geosearchstore，当前方式已废弃并不推荐使用
    key：提供一个我们添加好的空间集合
    longitude：中心点位置经度
    latitude：中心点位置纬度
    radius：半径的值（搜素的范围，参考雷达图）
    m|km|ft|mi：半径的值是以什么为单位
    [withcoord]：返回的结果中包含经纬度
    [withdist]：返回的结果中包含离中心点的位置距离
    [withhash]：返回的结果中包含geohash（此值用来表示经纬度，但是用hash不是太准）
    [count count [any]]：指定返回结果的数量
    [asc|desc]：返回结果按照离中心节点的距离做升序或者降序
    [store key]：（结果存储到外部集合）将返回结果的地理位置信息保存到指定空的空间集合中
    [storedist key]：（结果存储到外部集合）将返回结果的空间元素离中心节点的距离保存到指定空的空间集合中
    注：withcoord、withdist、withhash三个属性不能与store、storedist一起使用，因为前三个with*是用来直接返回展示的
    举例：
        georadius wan 114.22 30.33 440 km
        1) "luan"
        2) "chizhou"
        3) "hefei"
        4) "xuancheng"
        5) "wuhu"
        6) "bozhou"
            -- 获取坐标114.22 30.33在空间集合wan（皖）里中心点440km范围的全部元素

        127.0.0.1:6379> georadius wan 114.22 30.33 440 km withcoord withdist withhash count 1
        1) 1) "luan"
           2) "271.6188"            -- 注：我们设置中心点范围什么单位，这里就什么单位
           3) (integer) 4052658908461674    -- geohash
           4) 1) "116.53948992490768433"    -- 经度
              2) "31.74933045393131437"     -- 纬度
            -- 获取中心点范围的空间元素，并在返回结果中返回当前空间元素经纬度、举例中心点举例、geohash值，并设置返回一个

        127.0.0.1:6379> georadius wan 114.22 30.33 440 km count 1 store map1
        (integer) 1
        127.0.0.1:6379> zrange map1 0 -1 withscores
        1) "luan"
        2) "4052658908461674"
            -- 把结果写出到外部集合中，store代表写出到外部集合，元素为空间名称，”分数store“为geohash

        127.0.0.1:6379> georadius wan 114.22 30.33 440 km count 1 storedist map2
        (integer) 1
        127.0.0.1:6379> zrange map2 0 -1 withscores
        1) "luan"
        2) "271.61880150367676"
            -- 把结果写出到外部集合中，storedist代表写出外部集合（并携带距离中心点距离），
                元素为空间名称，”分数store“为距离中心点的距离

语法：georadiusbymember key member radius m|km|ft|mi [withcoord] [withdist] [withhash] [count count [any]] [asc|desc] [store key] [storedist key]
说明：和georadius命令相似，当前命令是以指定空间名称位置为中心点来往外扩展范围查询
    member：从设置的key内部选择一个空间名称当中心点来计算范围
    注：具体参考georadius；因为georadius以经纬度定位中心点、georadiusbymember以空间元素定位中心点
    注：在Redis6.2.0版本中推荐使用geosearch、geosearchstore，当前方式已废弃并不推荐使用

语法：geosearch key [frommember member] [fromlonlat longitude latitude] [byradius radius m|km|ft|mi] [bybox width height m|km|ft|mi] [asc|desc] [count count [any]] [withcoord] [withdist] [withhash]
说明：计算给定的中心点（空间名称或者经纬度）的指定半径内的全部空间元素，（参考雷达图）
    key：提供一个geoadd的空间集合key
    [frommember member]：在我们指定的空间集合中选择一个空间元素作为中心点
    [fromlonlat longitude latitude]：我们指定经纬度来作为中心点
    [byradius radius m|km|ft|mi]：根据给定的radius范围在圆形区域内搜素（参考雷达图）
    [bybox width height m|km|ft|mi]：根据给定的width X坐标 height Y坐标 中轴对齐的矩形内中心点搜素
    [asc|desc]：返回结果按照离中心节点的距离做升序或者降序
    [count count [any]]：指定返回结果的数量
    [withcoord]：返回的结果中包含经纬度
    [withdist]：返回的结果中包含离中心点的位置距离
    [withhash]：返回的结果中包含geohash（此值用来表示经纬度，但是用hash不是太准）
    注：frommember与fromlonlat不能同时出现，只能选择其一
    注：byradius与bybox不能同时出现，只能选择其一
    举例：
        127.0.0.1:6379> geosearch wan frommember hefei  byradius 500 km count 2 withcoord withdist withhash
        1) 1) "hefei"
           2) "0.0000"
           3) (integer) 4052763834193093
           4) 1) "117.30793744325637817"
              2) "31.79321915080526395"
        2) 1) "luan"
           2) "72.8279"
           3) (integer) 4052658908461674
           4) 1) "116.53948992490768433"
              2) "31.74933045393131437"
           -- 按照指定空间元素为中心点，并以圆形区域搜素；但是hefei自身离自己距离是0.0km也输出

        127.0.0.1:6379> geosearch wan fromlonlat 115.22 29.34 bybox 500 400 km count 2 withcoord withdist withhash
        1) 1) "chizhou"
           2) "271.1848"
           3) (integer) 4052698622569884
           4) 1) "117.56732851266860962"
              2) "30.68672971895555435"
           -- 按照指定经纬度为中心点坐矩形范围查询

语法：geosearchstore destination source [frommember member] [fromlonlat longitude latitude] [byradius radius m|km|ft|mi] [bybox width height m|km|ft|mi] [asc|desc] [count count [any]] [storedist]
语法：和geosearch相似，只不过geosearchstore命令是将结果返回到指定空间集合里
    destination：新空间集合名称（返回的结果保存到此集合）
    source：空间集合key，和geosearch里的key一样
    storedist：storedist代表写出外部集合（并携带距离中心点距离），默认”store分数“为geohash
    举例：
        127.0.0.1:6379> geosearchstore newWan wan fromlonlat 115.22 29.66 byradius 500 km storedist count 1
        (integer) 1
        127.0.0.1:6379> zrange newWan 0 -1 withscores
        1) "chizhou"
        2) "252.94646681717083"
```

# 十、HyperLogLog（超级基数统计）特殊类型命令

　　HyperLogLog主要是用来大数据量统计的类型算法，比如我们统计网站的一天访问量；虽然我们可以使用Redis中String类型的incr、incrby来实现，但是它只能统计访问本网站的每个请求计数累加（除了程序控制），但是我要说每个IP请求多少次都算作一次，对于多个相同IP的请求需要去重计数，在这种环境下HyperLogLog是优选，虽然hash、set、bitmaps可以解决这种问题，但随着数据不断增加，导致占用空间越来越大，对于非常大的数据集是不切实际的；

　　其实HyperLogLog底层还是一个Redis的String类型，只是用特有算法来实现这个数据类型，它是在降低一定的精确度来平衡和减少空间的存储，**标准误差只有0.81%**；对于统计这些数据精确度不是太大的完全够用了，如果需要统计准确的计数，那还是老老实实使用set这些类型，只能牺牲空间来维持精度；

　　HyperLogLog用来做基数统计的算法，优点是在输入元素的数量或者体积非常非常大时，计算基数所需的空间总是固定的、并且是很小的。**每个HyperLogLog键只需要花费12KB内存，就可以计算接近2^64个不同元素的基数**。这和计算基数时，元素越多耗费内存就越多的集合形成鲜明对比。但是**HyperLogLog只会根据输入元素来计算基数，而不会储存输入元素本身**，所以HyperLogLog不能像集合那样，返回输入的各个元素。


```
语法：pfadd key [element [element ...]]
说明：添加指定元素到hyperloglog中，如果指定的键不存在，该命令会自动创建一个空的hyperloglog结构
    注：添加的元素已存在的话将不在执行计数统计，都为相同元素的话将返回0，若有添加成功的都会返回1
    pfadd nameA zhangsan lisi wangwu mazi zhangsan xiejun mazi  -- 添加元素
    pfadd nameB xiechao xiaoyang wangwu xiexiao

语法：pfcount key [key ...]
说明：返回一个或多个键内统计基数（就是返回不相同的元素个数，用来统计），计算统计误差在0.81%
    127.0.0.1:6379> pfcount nameA nameB     -- 统计nameA 和 nameB 里的不重复基数
    (integer) 8

语法：pfmerge destkey sourcekey [sourcekey ...]
说明：统计一个或多个键内统计基数并放到外部集合里
    127.0.0.1:6379> pfmerge newCount nameA nameB    -- newCount为外部集合，nameA，nameB为要统计的数据
    OK
    127.0.0.1:6379> pfcount newCount
    (integer) 8
```


# 十一、BitMap（位图）特殊类型命令

　　BitMap是一串连续的二进制数字（0和1），类似于位数组，每一位所在的位置为偏移量（offset），类似于数组索引，BitMap就是通过最小的单位bit来进行0|1的设置，时间复杂度位O(1)，表示某个元素的值或者状态。由于bit是计算机中最小的单位，使用它进行储存将非常节省空间。特别适合一些数据量大的场景。例如，统计每日活跃用户、统计每月打卡数等统计场景。1天记录1000W用户的活跃统计数据，只需要10000000/8/1024/1024 ≈1.2M。

　　Redis从2.2.0 ~ 6.2.0这些版本中陆陆续续新增了setbit，getbit，bitcount，bitop等几个BitMap相关命令，虽然是新命令，但是并没有增加新的数据类型，它还是属于String类型。Redis中的BitMap最大占用内存大小限制在512M之内，即2^32。


```
基本介绍：
    在计算机中我们常常使用byte（字节）来作为最小单位，每一个byte由8位二进制数组成，即8bit（比特，也称"位"，8位二进制数0和1组成）
    8bit(位) = 1B      [Byte=B]     字节(最小单位)
    1024 B  = 1 KB    [KiloByte]    千字节
    1024 KB = 1 MB    [MegaByte]    兆字节
    1024 MB = 1 GB    [GigaByte]    吉字节
    1024 GB = 1 TB    [TeraByte]    太字节
    1024 TB = 1 PB    [PetaByte]    拍字节
    1024 PB = 1 EB    [ExaByte]     艾字节
    1024 EB = 1 ZB    [ZetaByte]    皆字节
    1024 ZB = 1 YB    [YottaByte]   佑字节
    1024 YB = 1 BB    [Brontobyte]  珀字节
    1024 BB = 1 NB    [NonaByte]    诺字节
    1024 NB = 1 DB    [DoggaByte]   刀字节
BitMap：
    bitMap就是通过最小单位bit来设置值，用来表示不同的两个状态；一个bit只能设置0或者1，所以bit只能存储两个状态
```



**1：常用命令**



```
语法：setbit key offset value
说明：设置或清除存在当前key里指定offset(偏移)位置上的位（可设置0或1，否和是）
    举例：
        setbit  record 0 1     setbit  record 8 1      setbit  record 16 1     setbit  record 24 1
        setbit  record 1 1     setbit  record 9 1      setbit  record 17 1     setbit  record 25 0
        setbit  record 2 1     setbit  record 10 1     setbit  record 18 0     setbit  record 26 0
        setbit  record 3 1     setbit  record 11 0     setbit  record 19 0     setbit  record 27 0
        setbit  record 4 1     setbit  record 12 0     setbit  record 20 1     setbit  record 28 0
        setbit  record 5 1     setbit  record 13 0     setbit  record 21 0     setbit  record 29 0
        setbit  record 6 1     setbit  record 14 0     setbit  record 22 1     setbit  record 30 1
        setbit  record 7 1     setbit  record 15 1     setbit  record 23 1     setbit  record 31 0
    解释：1字节八位，所以我上面是0~7一组、8~15一组、16~23一组、24~31一组，正好可以用来记录一个月的签到情况；
        11111111   11100001   11001011   10000010      ==>存储这几个记录用了 4Byte字节，可以记录一个月
        使用strlen来计算长度   strlen record   等于 4Byte
    注：我们设置值有时不需要一个一个设置，比如
        setbit test 5 1
        setbit test 20 1
        最终存储是这样的 => 00000100   00000000   00001000    【从左往右看或者获取】

语法：getbit key offset
说明：返回存储在key的字符串值中offset处的位值，就和我们上面添加的获取一样，获取22位=1、21位=0，0位=1
    getbit record 22
    注：以record的key来说，当获取偏移量超过31的话，那么字符串就会假定为一个连续的空间，那些连续的空间都当作0，
        所有我获取偏移量500的话，那么会从31~500都是0，最后我们返回也是0；若当前key不存在，获取一个随机偏移量，那么
        也会从0位往后都被假定为0，返回也是0

语法：bitcount key [start end]
说明：计算字符串中设置位数为1的个数，默认情况下获取字符串中所有字节的统计，指定范围则使用start、end；
    [start end]：
        我们以上面设置的为例：=> 11111111   11100001   11001011   10000010
        存储可以看为字符串数组一样正好对应上面 【0 , 1 , 2 , 3】
    注：start和end可以设置负数，负数代表从后往前
    bitcount record 0 0      代表查询【11111111】=8
    bitcount record 0 2      代表查询【11111111 11100001 11001011】=17
    bitcount record 1 2      代表查询【11100001 11001011】=9
    bitcount record 0 -1     代表查询【11111111 11100001 11001011 10000010】=19
    bitcount record 0 -2     代表查询【11111111 11100001 11001011】=17
    bitcount record -3 3     代表查询【11100001 11001011 10000010】=11
    bitcount record -1 -2    代表查询【】=0
    bitcount record -3 -1    代表查询【10000010 11001011 11100001】=11
    bitcount record -3 -3    代表查询【11100001】=4
    bitcount record -3 -4    代表查询【】=0
    注：如果都是负数偏移则是反过来的[正数从左往右，负数从右往左]，以下面为例
        bitcount record -3 -4     -3代表终止，-4代表起始
        以上面字节可看作：-4 -3 -2 -1    ；-3是终止点，而-4在后面

语法：bitop operation destkey key [key ...]
说明：在多个键中执行位运算，并将结果存储到目标键中
    operation：支持四种按位运算分别是：and、or、xor、not；
        and：多个键中对应的位值都相同时才为1
        or：多个键中对应的位值有1则为1
        xor：多个键中对应的位值有1则为1，都为1则为0
        not：值接收一个键，并取当前键里面位的反转值0变为1，1变为0
    destkey：结果存放的key
    示例：
        setbit bitA 0 1       setbit bitB 0 1
        setbit bitA 1 1       setbit bitB 1 0
        setbit bitA 2 0       setbit bitB 2 1
        setbit bitA 3 1       setbit bitB 3 0
        setbit bitA 4 1       setbit bitB 4 0
        setbit bitA 5 0       setbit bitB 5 0
        setbit bitA 6 0       setbit bitB 6 1
        setbit bitA 7 1       setbit bitB 7 1
        bitop and newBit bitA bitB
            and => newBit内部存储【10000001】=>2
        bitop or newBit bitA bitB
            or => newBit内部存储【11111011】=>7
        bitop xor newBit bitA bitB
            xor => newBit内部存储【01111010】=>5
        bitop not newBit bitA
            not => newBit内部存储【00100110】=>3

语法：bitpos key bit [start [end]]
说明：返回位图中第一次出现1或者0的位置，默认是从位图0位置开始查找，也可指定start、end
    key：要查询的位图
    bit：值只可写0或者1，告知在位图中查询第一次出现的位置
    [start [end]]：范围，可以单写start，或者start和end一起
    举例：record：=> 11111111   11100001   11001011   10000010
        bitpos record 1
            返回0；代表所有字节查询，查询第一次出现位值为1的位置
        bitpos record 0
            返回11；代表所有字节查询，查询第一次出现位值为0的位置（0开始索引）
        bitpos record 0 2 3
            返回18；代表范围查询，查询第一次出现位值为0的位置（0开始索引）
    注：默认情况下，检查位图包含的所有字节，若指定范围则可以使用start和end来定位，start和end的范围
        查询是以字节来说明的，比如start=1，end=2，则查询范围为【11100001 11001011】；还有就是，即使设置
        start和end来指定范围，位位置也始终从0开始；算上start之前的字节＋start~end之间查询到第一次出现的位置
```
