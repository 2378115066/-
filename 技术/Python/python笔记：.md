# python笔记：

## 一：计算机基础及python运算符：

### 1.1编码：

* ASCII编码：只能表示英文字符，数字及特殊的英文字符。用1个字节表示。
* Unicode编码：能表示世界上所有的字符，用4个字节表示。
* UTF-8编码：Unicode的压缩版，能表示世界上所有的字符，用1~4个字节表示，中文占3个字节。
* GBK编码：国际码，中文占2个字节。

### 1.2python2和python3的区别：

|                                  | python2                                                      | python3                             | 注备                                                         |
| -------------------------------- | ------------------------------------------------------------ | ----------------------------------- | ------------------------------------------------------------ |
| str不同                          | 有unicode类型 v = u'李杰'　　str类型　v='李杰'               | 有str类型　　byte类型 　v = b'李杰' | py2中的str等价于py3中的byte，py2的unicode类型等价于py3的str类型 |
| 编译器编码                       | ASCII                                                        | UTF-8                               | # _ * _  coding:utf-8 _ * _ 可以指定编译器的编码             |
| 整数                             | int具有范围，超出后自动转换成long                            | 无范围                              |                                                              |
| 两个整数相除                     | 只保留整数部分                                               | 保留全部                            | from __future__ import division可解决python2中2个整数相除只保留整数部分 |
| 输入                             | raw_input()                                                  | input()                             |                                                              |
| 输出                             | print  关键字                                                | print() 函数                        |                                                              |
| 随机数                           | xrange()　生成一个可迭代对象         range()  生成的是一个列表 | range()直接生成一个可迭代对象       |                                                              |
| 文件和包                         | 包里面必须有```__init__.py```                                | 可有可无                            |                                                              |
| 字典items,keys,values map/filter | 直接生成列表                                                 | 返回迭代器                          |                                                              |

### 1.3python运算符的优先级

![img](https://pythonav.com/media/uploads/2019/03/29/%E8%BF%90%E7%AE%97%E7%AC%A6%E4%BC%98%E5%85%88%E7%BA%A7.png)

## 二:数据类型:

### 2.1.1整形(int)

在python2中:

* 在32位机器上,整数的位数为32位,取值范围为-2*  * 31~2 * * 31-1
* 在64位机器上,整数的位数为64位,取值范围为-2*  * 63~2 * * 63-1
* 超出范围之后自动转换为long

在python3中:

* 只有int类型,没有long

注意:在ptrhon2中2个整数相除只会保留整数位,如果想要保留全部需要导入模块:form  __ future  __  import divsision



### 2.1.2布尔值(bool)

可与转换成False的有:

* 0,'',{},(,),[],set(),None



### 2.1.3.字符串(str)

#### 独有功能:

* 大小写转换:upper()/lower
* 判断是否可以转换为数字:isdecimal()
* 去两端空格:strip()
* 替换:replace()
* 分割:split()
* 判断开头和结尾:startswith()/endswith()
* 连接:join()
* 格式化:format()
* 编码:encode()
* 查找:find()/index() 

​       区别:find()找不到返回-1,index()找不到会报错

#### 通用功能:

* len/索引/切片/步长/for循环



### 2.1.4.列表:

#### 独有功能:

* 添加:

  append(元素)    在末尾追加元素     

  insert(索引值,元素)	在指定位置添加

  extent()			追加用于for循环的每一个元素

* 删除:

  remove(元素)	删除指定元素

  pop(索引值)		删除指定位置的元素,不写索引值默认删除最后一个

  clear() 清空列表中的所有元素

* 查找:

  reverse()	翻转列表中的元素

* 排序:

  sort(reverse=True/False)	从大到小/从小到大排序,默认False

#### 通用功能:

* len/索引/切片/步长/for循环/删除/更新 

#### 列表表达式:

* [变量名 for 变量名 in  可迭代对象   条件 ]

```python
print([i for i in range(10)])
#结果:[0,1,2,3,4,5,6,7,8,9]

print([i for i in range(10) if i > 5])
#结果:[6,7,8,9]

```



### 2.1.5.元祖:

#### 独有功能:

* 无

#### 通用功能:

* len/索引/切片/步长/for循环 



### 2.1.6.字典

#### 独有功能:

* 获取键,值,键值对	keys()/values()/items()
* 获取值     get()
* 删除键值对    pop(key)
* 增加键值对    update()

#### 通用功能:

* len/索引/for循环/修改/删除

### 2.1.7.集合

#### 独有功能:

* 增加

  add()  

  update()  

* 删除         discard()

* 交并差:instersection()/union()/difference()

#### 通用功能:

* len/for循环



### 2.2.可变类型和不可变类型:

* 可变类型:列表,字典,集合
* 不可变类型:数字,字符串,元祖,布尔值



### 2.3.深浅拷贝

* 深拷贝:

  拷贝嵌套层次中的所有可变类型

* 浅拷贝:

  只能拷贝第一层的内容



### 2.4.is 和 == 的区别:

* is是判断内存是否相等
* == 是判断值是否相等



## 三:文件操作

大文件的内容读取:

```
#方法1:
str = ""
with open("data.txt", mode="r", encoding="utf-8") as f:
	for data in f:
		str += data  # 按行读取

#方法2:
str = ""
with open("data.txt", mode="r", encoding="utf-8") as f:
    while True:
        data = f.readline()
        if data != "":
            str += data
        else:
            break
print(str)
```

移动光标:seek() 

* 移动到开头seek(0,0)
* 移动到结尾seek(0,2)) seek的第二个参数表示的是从哪个位置进行偏移,默认是0,表示开头,1表示当前位置,2表示结尾
* seek(6)如果是单数而且不是0是按照**字节**来移动



获取光标的位置:tell()



## 四:函数相关

函数的默认返回值为None

函数式编程：增加代码的可读性和重用性

### 4.1传参的分类:

* (1)位置传参:只能参数一一对应
* (2)关键字传参:关键字参数只能放在位置传参的后面.
* (3)默认参数传参:可以接受参数,不传参数将使用默认值,
  * 注意:默认关键字如果是不可变类型,可以随便玩,如果是可变类型,需要注意有一个坑.
  * 如果默认参数设置成可变类型为空，改可变类型会创建在函数中，不会被释放，因此在下次调用时还会继续使用上次一创建的可变类型中的数据．

```python
def func(data, value=[]):  # 不推荐　
    value.append(data)
    return value


print(func(11))  # ［１１］
print(func(1, [11, 22, 33]))  # [11,22,33,1]
print(func(22))  # [11,22]


def fun1(data, value=None):  # 推荐
    if not value:
        value = []
    value.append(data)
    return value

print(fun1(11))  # ［１１］
print(fun1(1, [11, 22, 33]))  # [11,22,33,1]
print(fun1(22))  # [22]

```



* (4)万能传参:可以接受n个参数

```python
#实例1:*args 只能接受位置传参
def fun1(*args):
	print(args)

fun1((11,22,33,44))  # 结果((11,22,33,44))
fun1(*(11,22,33,44))  # 结果(11,22,33,44)

#实例2:**kwargs 只能接受关键字传参
def fun2(**kwargs)
	print(kwargs)

fun2(k1=11,k2=22)  # 结果{k1:11,k2:22}
fun3(k1=11,**{k2:22,k3:33})  # 结果{k1:11,k2:22,k3:33}

```

### 4.2函数的作用域

* 一个函数就是一个作用域.
* 作用于查找数据的规则:优先在自己的作用域中查找数据,自己没有就去上一级去找,
* 子作用域只能找到父级中的值,默认无法重写赋值

```python
a = [11,22]
def fun():
    a.appen(33)

print(a)  # 结果[11,22,33]

a = "aaa"
def fun1():
    a = "bbb"

print(a) # 结果"bbb"

```

* _如果非要修改上一级或者全局变量需要添加关键字global或者nonlocal关键字_

* 如果非要去修改则可以使用global 或 nonlocal关键字

  globla:直接声明为全局变量

  nonlocal:声明为上一级变量,不一定是全局变量大

* 全局变量的命名采用全部大写,局部变量采用小写

### 4.3函数小高级

#### 4.3.1函数可以赋值

```python
def func():
    print(123)

list = [func,func,func]  # func为函数的地址
for i in list:
    i()  #　运行函数
```

#### 4.3.２函数做参数

```python
def fun(arg):
    arg()

def show():
    print(111)

fun(show)  # 输出１１１

```

#### 4.3.３函数做字典的值

```python
#应用:
def fun1():
    print("fun1")
def fun2():
    print("fun2")  
def fun3():
    print("fun3")
def fun4():
    print("fun4")
def fun5():
    print("fun5")
    
fun_dict ={"f1":fun1,"f2":fun2,"f3":fun3,"f4":fun4,"f5":fun5,}
chooice = input("请选择功能：")
find_fun = fun_dict.get(chooice)
if find_fun:
    find_fun()
else:
    print("请检查输入内容后在重新运行！")
    
```

### 4.4lambda表达式及三元运算符

#### 4.4.1三元运算符：

* 为了解决简单的ｉｆ　ｅｌｓｅ情况

```python
#普通写法：
max = None
if a > b:
    max = a
else:
    max = b

#三元运算符写法
max = a if a>b else b
```

#### 4.4.2lambda表达式：为了解决简单的函数

```python
#普通写法：
def func(a.b)
	return a+b

#lambda表达式：
func = lambda a, b: a + b
```

### 4.5内置函数：

* 数据类型转换相关：

  * int	转换为整形

  * float　转换为浮点型

  * bool　转换为布尔型

  * chr　转换为字符型

  * ord    将一个unicode编码中的一个字符转换成１０进制数

    ```python
    #实例：验证码生成器
    import random
    
    
    def get_yzm(longth=6):
        yzm = []
        for x in range(6):
            v = random.randint(65,90)
            yzm.append(chr(v))
        return "".join(yzm)
    
    
    print(get_yzm())
    ```

    

  * str　转换为字符串类型

  * list　转换为列表

  * dict　转换为字典

  * tuple　转换为元祖

  * set　转换为集合

* 数学相关：

  * abs　取绝对值

  * max　取最大值

  * min　取最小值

  * sum　求和

  * divmod　求商和余数

    ```pyt
    # 实例：分页
    def show_pige(data, pige_num, show_num=10):
        pige, a = divmod(len(data),show_num)
        max_page =pige + 1 if a > 0 else pige
        if pige_num < 0 or pige_num > max_page:
            print("输入的值超出范围0~%s" %max_page)
        else:
            start_pige_num = show_num*(pige_num - 1)
            end_pige_num = start_pige_num + show_num
            for i in range(start_pige_num,end_pige_num+1):
                print(data[i])
    
    if __name__ == '__main__':
        list = []
        for i in range(0, 856):
            list.append("data%s" %i)
        pige_num = int(input("请输入要查看的页数:"))
        show_pige(list, pige_num, 20)
    
    
    ```

* 进制转换：

  * bin　将１０进制转换为２进制
  * oct　将１０进制转换为８进制
  * int　将其他进制转换为１０进制
  * hex　将１０进制转换为１６进制

```python
#1十进制转换二，八，十六进制
num = 100

print(bin(num))
print(oct(num))
print(hex(num))

#2 其他进制转换成１０进制
num_0b = "0b1100100"
num_0o = "0o144"
num_0x = "64"

print(int(num_0b,base=2))
print(int(num_0o,base=8))
print(int(num_0x,base=16))
```

* 其他：map/filter/reduce第一个参数必须是一个函数，第二个参数是一个可以迭代的类型

  * map()    遍历序列，对序列中每个元素进行操作，最终获取新的序列。![img](https://images2015.cnblogs.com/blog/425762/201511/425762-20151114164016869-1553913346.png)

    ```python
    #1.map函数应用：
    #需求：每个元素增加１００
    li = [11,22,33,44,55,66,77,88,99]
    new_list = map(lambda x:x+100, li)
    print(list(new_list))
    ```

    * filter()    对于序列中的元素进行筛选，最终获取符合条件的序列![img](https://images2015.cnblogs.com/blog/425762/201511/425762-20151114164107884-344713622.png)

    

    ```python
    #2.获取列表中大于12的所有元素集合
    new_set = filter(lambda x : x > 12 ,li)
    print(list(new_set))
    ```

    

    

  * reduce()    对序列内的所有元素进行累计操作![img](https://images2015.cnblogs.com/blog/425762/201511/425762-20151114164122962-1616737731.png)

    ```python
    #3.获取列表中所有元素的和
    import functools
    new_list = functools.reduce(lambda x, y : x+y, li)
    print(new_list)
    ```

    

* 面试题：ｉｐ地址转换

```python
#需求将一个ｉｐ地址转换成一个３２位的二进制数，并将其转换成一个１０进制数输出.

ip = "192.168.9.71"
list_ip = []
for i in ip.split('.'):
    i_num = bin(int(i))
    i_num = "{:0>8}".format(i_num[2:])
    list_ip.append(i_num)

str_ip = "".join(list_ip)
print(str_ip)
print(int(str_ip,base=2))

```

### 4.6闭包：

#### 4.6.1闭包的概念：

为函数创建一快区域并将其维护自己数据，以后执行是方便调用

#### 4.6.2应用场景：

装饰器，SQL ALchemy源码

### 4.7装饰器:

#### 4.7.1装饰器的目的

* 在不改变原函数内部代码的基础上,在函数执行之前和之后自动执行某个功能.

#### 4.7.2普通装饰器的编写格式:

```python

def 外层函数(参数):
    def 内层函数(*args, **kwargs):
        #执行函数之前的内容
        return 参数(*args, **kwargs)
    	#执行函数之后的内容
    return 内层函数
```

#### 4.7.3普通装饰器应用格式:

```python
@外层函数名
# 第一步:执行外层函数并将下面的函数参数传递,相当于:外层函数名(index)
#第二部:将fun的返回值从新赋值给下面的函数名,相当于index = 外层函数名(index)
def index():
    pass
index()
```

#### 4.7.4普通装饰器的应用:

```python
#1.计算多个函数的运行时间:(普通写法)
import time
def fun1():
    time.sleep(1)
    pass

def fun2():
    time.sleep(1)
    pass

def fun3():
    time.sleep(1)
    pass

if __name__ == '__main__':
    start_time = time.time()
    fun1()
    end_time = time.time()
    run_time = end_time - start_time
    
    start_time = time.time()
    fun2()
    end_time = time.time()
    run_time = end_time - start_time
    
    start_time = time.time()
    fun2()
    end_time = time.time()
    run_time = end_time - start_time
   

#采用装饰器写法:
import time

def run_time(arg):
    def index(*args,**kwargs):
        start_time = time.time()
        arg()
		end_time = time.time()
        run_time = end_time - start_time
        print('运行时间为:%s' % run_time)
    return index
        
@run_time       
def fun1():
    time.sleep(1)
    pass
@run_time  
def fun2():
    time.sleep(1)
    pass
@run_time  
def fun3():
    time.sleep(1)
    pass

if __name__ == "__main__":
    fun1()
    fun2()
    fun3()
```

#### 4.7.5带参数的装饰器的编写格式：

```python
def outer(data):
    def wraper(func):
        def inner(*args, **kwargs):
            data = func(*args, **kwargs)
            return data
        return inner
    return wraper

```

#### 4.7.6带参数的装饰器的应用格式：

```python
@outer(data)
# 1执行　v1 = outer(data)
# 2执行　ret = v1(func)
# 3执行　func = ret
def func(*args, **kwargs):
    pass
```

#### 4.7.7带参数装饰器的应用：

```python
# 1需求通过装饰器传参，使某个函数运行多次
NUM = 1

def run_time(num):
    def wrapper(arg):
        def inner(*args, **kwargs):
            for i in range(num):
                arg()
        return inner
    return wrapper


@run_time(5)
def func():
    global NUM
    print(NUM)
    NUM += 1



func()
```



### ４.８递归

* 递归效率低．默认的递归最大次数为１０００,查看方法如下：

```python
import sys
result = sys.getrecursionlimit()
print(result)
```

* 递归的应用

```python
#计算ｎ的阶乘
def a(n):
    if n == 1:
        return 1
    else:
        n = n * a(n - 1)
    return n


print(a(10))
```



## 五.模块

### 5.1hashlib：

#### 5.1.1md5加密

```python
＃md5加密
import hashlib
obj = hashlib.md5('醋'.encode('utf-8'))  # 加盐
obj.update('xx'.encode('utf-8'))
result = obj.hexdigest()
print(result)
```

### 5.2getpass

#### ５.2.1密码不显示

pycharm中能够显示，只能在终端中才能不显示．

```python
＃密码不显示
import getpass
pwd = getpass.getpass("请输入密码：")
print(pwd)
```

### 5.3random:

#### 5.3.1随机生成整数：

```python
import random
print(random.randint(0,10))
```

### 5.4 os

#### 5.4.1判断路径是否存在

```python
import os
print(os.path.exists('路径地址'))　　# 找到返回Ｔｒｕｅ，找不到返回Ｆａｌｓｅ　
```

#### 5.4.2获取文件的大小

```python
import os

path = '/home/dell/Desktop/成套资料C&C08数字程控交换系统-(V610R105M90,128模，V9.00)/31161761-操作手册 特殊业务和范例分册 (V9.01)/11-附录A 特殊业务命令列表_irm.doc'
print(os.stat(path).st_size)
```

#### 5.4.3 获取文件的决定路径

```python
import os

print(os.path.abspath('./data_html.py')) # /home/dell/Desktop/老男孩python学习笔记/python开发基础/day_14/data_html.py
```

#### 5.4.4 获取路径的上级目录

```python
import os

print(os.path.dirname('/home/dell/Desktop/老男孩python学习笔记/python开发基础/day_14/data_html.py')) # /home/dell/Desktop/老男孩python学习笔记/python开发基础/day_14
```

#### 5.4.5目录的拼接(重点)

```python
import os

print(os.path.join('/home/dell/Desktop','老男孩python学习笔记/python开发基础/day_14/data_html.py'))
# /home/dell/Desktop/老男孩python学习笔记/python开发基础/day_14/data_html.py
```

#### 5.4.6 获取一个目录下的所有文件(只有一层)

```python
import os

print(os.listdir('/home/dell/Desktop/老男孩python学习笔记')) # ['.git', 'python笔记：.md', 'python开发基础', '.idea']
```

#### 5.4.7 获取一个目录下的所有文件(重点＋面试题)

```python
import os

for a,b,c in os.walk('/home/dell/Desktop/老男孩python学习笔记/python开发基础/day_14'):
    for item in c:
        path = os.path.join(a,item)
        print(path)
```

#### 5.4.8 创建目录

```python
import os

file_path = '/home/dell/Desktop/老男孩python学习笔记/python开发基础/day_15'
file_name = '123'
path = os.path.join(file_path,file_name)
if not os.path.exists(path):
    os.mkdir('123')  # 只能创建一层目录
  	os.makedirs('123/456')  # 创建多层目录
```

#### 5.4.9 重命名

```python
import os
os.rename(old_name,new_name)
```



### 5.5sys：

#### ５.5.1 sys.argv 获取传参

```python
import sys

print(sys.argv) # ['/home/dell/Desktop/老男孩python学习笔记/python开发基础/day_14/day_14_03ｓｙｓ模块.py']

```

#### ５.5.2  sys.getrefcount 获取内存变量的调用次数

```python
import sys

a = [11,22]
print(a)
print(sys.getrefcount(a))  # 2
```

#### 5.5.3 sys.getrecursionlimit 获取递归的最大值

```python
import sys

print(sys.getrecursionlimit())
```

#### 5.5.4 sys.path 编译器环境变量(重点)

```python
import sys
sys.path  # 获取编译器的环境变量
sys.path.append()  # 添加环境变量
```

#### 5.5.5 sys.exit 退出程序

```python
import sys
sys.exit()
```



### 5.6 shutil

#### 5.6.1 删除目录

```python
import shutil

shutil.rmtree(path)
```

#### 5.6.2 重命名

```python
import shutil
shutil.move('haha','hahaha')
```

5.6.3 压缩文件

```python
import shutil
file_name = 'hahaha'
format = 'zip'
shutil.make_archive(file_name, format=format)
```

5.6.4解压文件

```python
import shutil
file_path = 'hahaha.zip'
shutil.unpack_archive(file_path,format=format,extract_dir='hahaha')
```

#### 5.6.5 练习题

```python
# 练习题：
# 压缩hahaha文件夹　放到code文件夹中(默认不存在)　并将文件解压到桌面code文件中
import os
import shutil

if not os.path.exists('code'):
    os.mkdir('code')

shutil.make_archive(base_name='./code/hahaha',format='zip',root_dir='hahaha')
shutil.unpack_archive(filename='./code/hahaha.zip',format='zip',extract_dir='/home/dell/Desktop/code/')

```



### 5.7 json

#### 5.7.1 json基础知识

* json 是一个特殊的字符串，字符串最外层必须是列表或字典，
* 字符串中的字符串必须用双引号
* 布尔值全部为小写否则报错

![](/home/dell/Desktop/老男孩python学习笔记/python开发基础/day_15/深度截图_选择区域_20191128174508.png)

* json中不能出现集合

#### 5.7.2 序列化

```python
import json

stra = [123,{1:456},"hha",[445,5,3],True]
a  = json.dumps(stra)  # 将python数据转换为json数据，如果存在中文，或变成unicode编码的字节

# 序列化保留中文,需要传入一个关键字参数ensure_ascii=False
a = json.dumps(stra,ensure_ascii=False)
print(a)
```



#### 5.7.3反序列化

```
import json

stra = '[123,{"1":456},"hha",[445,5,3],true]'
b  = json.loads(stra)  # 将json数据转换为python数据
print(b)

```

### 5.8 pickle模块

#### 5.8.1 pickle与json的区别

* pickle 和 json 都是做序列化
* json：优：所有的语言通用，缺点：只能序列化基本的数据类型
* pickle：优：python中的所有的东西都可以被序列化(套接字对象除外),缺点：序列化的内容只有python能够识别．

#### 5.8.2 序列化和反序列化

```python
import pickle
def run():
    print('hello word!')

# 序列化
v = pickle.dumps(run)
print(v)

# 反序列化
y  = pickle.loads(v)
y()
```

5.9 datetime模块

```python
import time
from datetime import datetime
from datetime import timedelta
from datetime import timezone


# 获取当前时间
time1 = datetime.now().strftime('%Y-%m-%d %H:%M:%S')
print(time1)

# 获取UTC时间
time2 = datetime.utcnow().strftime('%Y-%m-%d %H:%M:%S')
print(time2)

# 获取某个时区的时间
t = timezone(timedelta(hours=7)) # 东是正　西是负
time3 = datetime.now(t).strftime('%Y-%m-%d %H:%M:%S')
print(time3)

# 将datetime.datetime装换成字符串
time4 = datetime.now()
print(type(time4))
time5 = time4.strftime('%Y-%m-%d %H:%M:%S')
print(time5)

# 将str装换成datetime.datetime类型
str1 = '2019-11-30 14:52:33'
time6 = datetime.strptime(str1,'%Y-%m-%d %H:%M:%S')
print(time6,type(time6))

# datetime的加减
time7 = datetime.now()
time8 = time7 + timedelta(days=50)
print(time8)

# 时间戳转换datetime
time_t1 = time.time()
time9 = datetime.fromtimestamp(time_t1)
print(time9)

# datetime转换时间戳
time_t2 = time9.timestamp()
print(time_t2)
```

### 5.自定义模块及包的知识：

#### 1.自定义模块

* 定义模块时可以把一个py文件或一个文件夹(也叫作包)当作一个模块，以方便以后其他的py文件的调用

```python
# 假设有一个包名称为haha　里面有一个hello.py文件  并且haha所在的路径已经添加到sys.path中
# 导入hello的方法１：
form haha import hello
#引用方法：
hello.xxx

# 方法2:
import haha.hello
#引用方法：
haha.hello.xxx
```

* 注意：在导入模块或者包的时候，模块或包中所有的值都会被导入到内存中．

#### 2.包的定义

* py2中：文件夹里面必须有_ _ init _ _.py
* py3中：不需要_ _ init _ _ .py，但推荐加上
* _ _ file _ _变量可以直接获取到python运行时的文件路径参数

导入实例：

![深度截图_选择区域_20191129133220](/home/dell/Desktop/老男孩python学习笔记/python开发基础/day_16/深度截图_选择区域_20191129133220.png)

#### 3.包的安装方法：

* 1. pip包管理工具
  2. 源码安装
     * 1. 下载源码包，是一个压缩文件
       2. 解压文件
       3. 终端进入解压的路径
       4. 执行python setup.py build
       5. 执行python setup.py install

#### ４.导入包：

```python
# 假设存在一个包名称为xxx，里面包含jd.py....
import xxx
from xxx import *
# 以上２种导入全部都是导入的包里面的__init__.py文件，并不能去导入其他的模块
import xxx.jd
from xxx import jd
# 这样可以导入包里面的某一个模块
```



## 六.异常处理及多任务相关内容

### 1.异常处理的基本写法

```python
try:
    v = 12 + "str"
except Exception as e:
    print('异常处理')
```

### ２.迭代器

* 迭代器帮助你对某种对象中的元素进行逐一获取

#### 2.1创建迭代器

```python
list1 = [11,22,33,44]
# 方法１
list2 = list1.__iter__()

# 方法2
list3 = iter(lits1)

```

#### 2.2调用迭代器的值

```python
v = [11,22,33,44].__iter__()
# 方法１
v.__next__()　# 取值时取完最后一个再去取值时则会报错
# 方法２ 
for i in v:
    pass
```

#### 2.3可迭代对象

* 具有```__intr__```和```__next__```或者能够能够语用于for循环

### 3.生成器

#### 3.1创建生成器

```python
# 如果一个函数中出现了yield关键字，该函数就是一个生成器的模板
def fun():
    yield 1
 
v = fun() # 创建生成器
```

#### 3.2调用生成器的值

```python
def fun():
    a = yield 1
    
def fun1()：
	yield 2
    yield 3
    yield from fun() # py3.3之后，从一个生成器跳到另一个生成器．
    yield 5
 
v = fun() # 创建生成器    

# 方法１
v.__next__()　# 取值时取完最后一个再去取值时则会报错

# 方法２ 
for i in v:
    pass
# 方法３
v.send(参数) # 可以在断点传入一个附加的数据　

# 方法四
```

#### 3.3调用生成器的值并获取return的结果

```python
def fun():
    a = yield 1
    b = yield 2
    c = yield 3
    return a,b,c

v = fun()
i = 1
while True:
    try:
        result = v.send(i)
        print(result)
        i += 1
    except Exception as e:
        print(e.value)
        break
```

#### 3.4生成器推导式

```python
v1 = [lambda i for i in range(10)] # 列表推导式
v2 = (lambda i for i in range(10)) #　生成器推导式，不会立即执行，等待迭代时才会被执行．
for i in v1:
    i()  # 生成１０个９
for i in v2:
    i()  # 生成１，２，３，．．．．９
 
```

## 七.面向对象

1 类和对象的基本定义