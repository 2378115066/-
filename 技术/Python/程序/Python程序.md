## 项目1 踏上Python之旅

```python
print("*********浣溪沙·夜饮*********")
print("***********宋·苏轼***********")
print("佳酿飘香自蜀南，且邀明月醉花间。")
print("三杯未尽兴尤酣，夜露清凉搀乐去。")
print("青山微薄桂枝寒，凝眸迷恋玉壶间。")
```

## 项目2 夯实Python语言基础

```python
#-*- coding:utf-8 -*-
'''
@功能:中国白酒度数分类描述
@author:翔子
@create:2020-04-01
'''
#===============程序开始=============#
#按酒精含量分高度酒、中度酒、低度酒
vol = int(input("请输入酒的度数:"))  #定义一个变量，变量名为vol，用来保存输入酒的度数
if vol >= 40:  #酒精度是否大于40
    print("该酒是高度酒! ")  #大于40，输出该酒是高度酒
elif 20 <= vol <= 40:  #酒精度是否在20到40之间
    print("该酒是中度酒!")  #20到40之间，输出该酒是中度酒")
else:  #判断是否符合条件，即输入小于20的值
    print("该酒是低度酒!")  #小于20，输出该酒是低度酒
#================程序结束=============#
```

2.2  保留字与标识符

**2.2.1** **保留字**

import keyword

keyword.kwlist

 

if = "今朝有酒今朝醉，明日愁来明日愁"

print(if)

 

**2.2.2** **标识符**

USERID

name

model2

user_age

 

4word          #以数字开头

try          #Python中的保留字

$money         #不能使用特殊字符$

2.3  变量

**2.3.2** **变量的定义与使用**

number=1314      #创建变量number并赋值为1314，该变量为数值型

nickname=“沧海一笑” # 非字符串类型的变量

 

**任务****2-2** **计算中国各省市白酒产量值**

01 print("2019年1-4月中国各省市白酒产量排行榜前五名分别是：")

02 print("四川 湖北 北京 河南 安徽")

03 output_sc = float(input ("请输入第一名四川省的白酒产量:"))  #定义一个变量output_sc，用来保存输入的四川省白酒产量

04 output_hb = float(input ("请输入第二名湖北省的白酒产量:"))  #定义一个变量output_hb，用来保存输入的湖北省白酒产量

05 output_bj = float(input ("请输入第三名北京市的白酒产量:"))  #定义一个变量output_bj，用来保存输入的北京市白酒产量

06 output_hn = float(input ("请输入第四名河南省的白酒产量:"))  #定义一个变量output_hn，用来保存输入的河南省白酒产量

07 output_ah = float(input ("请输入第五名安徽省的白酒产量:")) #定义一个变量output_hn，用来保存输入的安徽省白酒产量

08 print("2019年1-4月中国各省市白酒产量排行榜前五名的省份和对应的白酒产量如下：")

09 print("四川: " + str(output_sc) + "亿升")   #将output_sc转换为字符串

10 print("湖北: " + str(output_hb) + "亿升")   #将output_hb转换为字符串

11 print("北京: " + str(output_bj) + "亿升")   #将output_bj转换为字符串

12 print("河南: " + str(output_hn) + "亿升")   #将output_hn转换为字符串

13 print("安徽: " + str(output_ah) + "亿升")   #将output_ah转换为字符串

14 output_av = (output_sc + output_hb + output_bj + output_hn

 \+ output_ah)/5 #定义变量output_av，保存前5名产量计算平均值结果

15 print("排行榜前五名省市平均白酒产量为："+format(output_av,'.3f')) #输出平均白酒产量，保留3位小数点

 

2.4  基本数据类型

**2.4.1** **数字类型**

**1****．整数**

3141592485278771713

8888888888888888888888888888888888888888888888888888888888888888

-2020

0

**实例****01****：根据身高、体重计算****BMI****指数**

\# -*- coding:utf-8 -*-

'''

  @ 功能：根据身高、体重计算BMI指数

  @ author:闰土

  @ create:2020-4-10

'''

01 height = 1.75   # 保存身高的变量，单位：米

02 print("您的身高：" + str(height))

03 weight = 68.5   # 保存体重的变量，单位：千克

04 print("您的体重：" + str(weight))

05 bmi=weight/(height*height)   # 用于计算BMI指数，公式为“体重/身高的平方”

06 print("您的BMI指数为："+str(bmi)) #输出BMI指数

\# 判断身材是否合理

07 if bmi<18.5:

08   print("您的体重过轻，请加强营养！")

09 if bmi>=18.5 and bmi<24.9:

10   print("您的体重在正常范围，请注意保持！")

11 if bmi>=24.9 and bmi<29.9:

12   print("您的体重属于超重，请加强锻炼！")

13 if bmi>=29.9:

14   print("您的体重属于肥胖，请抓紧减肥！")

 

**2.4.2** **字符串类型**

01 title = '我喜欢的经典诗句'    #使用单引号，字符串内容必须在一行

02 verse_cn = "天生我才必有用，千百金散尽还复来。" #使用双引号，字符串内容必须在一行

\#使用三引号，字符串内容可以分布在多行

03 verse_en = '''Everyone will be useful if they are born.

04 thousands of gold can be swept away, but it can still be earned.'''

05 print (title)

06 print(verse_cn)

07 print(verse_en)

 

**实例****02****：输出****1573****号坦克**

\# -*- coding:utf-8 -*-

'''

  @ 功能：输出字符画

  @ author:毛台

  @ create:2020-04-10

'''

01 print('''

​            ▶ 前进！前进！前进！

​            |          

​        __\--__|_ 

II=======OOOOO[/ ★1573___|      

​     _____\______|/-----. 

​    /___**************___|       

​     \◎◎◎◎◎◎◎◎⊙/ 

​      \~~~~~~~~~~~~~~~~

02 ''')

 

**实例****03****：模拟泸州沃尔玛超市抹零结账行为**

\# -*- coding:utf-8 -*-

'''

  @ 功能：模拟超市抹零结账行为

  @ author:翔子

  @ create:2020-4-10

'''

01 money_all = 56.66 + 72.99 + 88.88 + 26.99 + 68.00 # 累加总计金额

02 money_all_str = str(money_all)        # 转换为字符串

03 print("商品总金额为：" + money_all_str)

04 money_real = int(money_all)          # 进行抹零处理

05 money_real_str = str(money_real)       # 转换为字符串

06 print("实收金额为：" + money_real_str)

 

2.5  运算符

**实例****04****：计算泸职院软件技术专业学生成绩的分差及平均分**

\# -*- coding:utf-8 -*-

'''

  @ 功能：计算学生成绩的分差及平均分

  @ author:米线儿

  @ create:2020-04-10

'''

01 java = 92         # 定义变量，存储Java语言程序设计的分数

02 structure = 78       # 定义变量，存储数据结构的分数

03 linux = 95         # 定义变量，存储Linux操作系统的分数

04 network = 89        # 定义变量，存储计算机网络的分数

05 sub = java - structure   # 计算Java语言程序设计课程和数据结构课程的分数差

06 avg = (java + structure + linux + network) / 4 # 计算平均成绩

07 print("Java语言程序设计课程和数据结构课程的分数差： " + str(sub) + " 分\n")

08 print("4门课的平均分： " + str(avg) + " 分")

 

**实例****05****：使用比较运算符比较大小关系**

01 java = 92      # 定义变量，存储Java语言程序设计的分数

02 structure = 78    # 定义变量，存储数据结构的分数

03 linux = 95      # 定义变量，存储Linux操作系统的分数

04 network = 89     # 定义变量，存储计算机网络的分数

\# 输出4个变量的值

05 print("java = " + str(java) + " structure = " +str(structure) + 

" linux = " +str(linux) + " network = " +str(network) + "\n")

06 print("java < structure的结果：" + str(java < structure)) #小于操作

07 print("java > structure的结果：" + str(java > structure)) #大于操作

08 print("java == structure的结果：" + str(java == structure))#等于操作

09 print("java != structure的结果：" + str(java != structure)) #不等于操作

10 print("java <= structure的结果：" + str(java <= structure)) #小于等于操作

11 print("java >= structure的结果：" + str(java >= structure)) #大于等于操作

 

**实例****06****：参加郎酒专卖店的打折活动**

01 print("\n金秋十月，郎酒专卖店（北方路店）打折促销活动火热进行中\n") # 输出提示信息

02 strWeek = input("请输入中文星期（如星期一）：") #输入星期

03 intTime = int(input("请输入时间中的小时（范围：0~23）：")) # 输入时间，由于input()方法返回的结果为字符串类型，所以需要进行类型转换

\# 判断是否满足活动参与条件（使用了if条件语句)

04 if (strWeek == "星期一" and (intTime >= 10 and intTime <= 11)) or (strWeek == "星期二" and (intTime >= 14 and intTime <= 15)) or (strWeek == "星期三" and (intTime >= 9 and intTime <= 10)) or (strWeek == "星期四" and (intTime >= 15 and intTime <= 16)) or (strWeek == "星期五" and (intTime >= 11 and intTime <= 12)) or (strWeek == "星期六" and (intTime >= 13 and intTime <= 15)) or (strWeek == "星期日" and (intTime >= 9 and intTime <= 12)):

05   print("恭喜您！可以享受8折优惠，快快选购吧！") # 输出提示信息

06 else:

07   print("对不起，您今天来晚一步！不能享受折扣优惠！") # 输出提示信息

 

**2.5.5** **位运算符**

01 print("12&8 ="+str(12&8))    #位与计算整数的结果

02 print("4|8 = "+str(4|8))    #位或计算整数的结果

03 print("31^22 = "+str(31^22))  #位异或计算整数的结果

04 print("~123 = "+str(~123))   #位取反计算整数的结果

2.6  基本输入和输出

**2.6.1** **使用****input()****函数输入**

tip = input("请输入文字："）

age = int(input("请输入数字："))

 

**实例****07****：根据身高、体重计算****BMI****指数（改进版）**

01 height = float(input("请输入您的身高（单位为米）：")) # 输入身高，单位：米

02 weight = float(input("请输入您的体重（单位为千克)：")) # 输入体重，单位：千克

03 bmi=weight/(height*height) # 用于计算BMI指数，公式为“体重/身高的平方”

04 print("您的BMI指数为："+str(bmi)) # 输出BMI指数

\# 判断身材是否合理

05 if bmi<18.5:

06   print("您的体重过轻，请加强营养！")

07 if bmi>=18.5 and bmi<24.9:

08   print("您的体重在正常范围，请注意保持！")

09 if bmi>=24.9 and bmi<29.9:

10   print("您的体重属于超重，请加强锻炼！")

11 if bmi>=29.9:

12   print("您的体重属于肥胖，请抓紧减肥！")

 

**2.6.2** **使用****print()****函数输出**

print(输出内容）

 

a=10                  #变量a,值为10 

b=6                  #变量b,值为6

print(6)                #输出数字6

print(a*b)               #输出变量a*b的结果60

print(a if a>b else b)         #输出条件表达式的结果10

print("今朝有酒今朝醉,明日愁来明日愁。") #输出字符串“今朝有酒今朝醉,明日愁来明日愁。”

 

项目3 学习流程控制语句 

**任务****3-1** **泸州老窖特曲销售人员业绩提成分档设计**

01 sale = 6000 #为销售金额变量sale赋值

02 if sale <= 5000: #判断sale值是否小于等于5000

03   print("无提成")

04 elif sale <= 10000: #判断sale值是否小于等于10000

05   print("最高提成10%")

06 elif sale <= 50000: #判断sale值是否小于等于50000

07   print("最高提成20%")

08 else: # sale值大于50000

09  print("最高提成30%")

 

**实例****01****：判断输入的是不是令狐冲所说酒坛数量**

01 print("今有美酒若干坛，然不知其数，三三数之剩二，五五数之剩三，七七数之剩二，问几何？ \n")

02 number = int(input("请输入您认为符合条件的数："))   #输入一个数

03 if number%3 == 2 and number%5 == 3 and number%7 == 2: #判断是否符合条件

04   print(number,"符合令狐大侠所说条件！")

 

number = 5 

if number == 5 

  print ("number的值为5")

number = 5 

if number == 5:

  print ("number 的值为5")

if bmi<18.5:

  print(“您的BMI指数为：”+str(bmi))  #输出BMI指数

  print (“您的体重过轻！”)

if bmi<18.5:

  print(“您的BMI指数为:”+str(bmi))  #输出BMI指数

print(“您的体重过轻！”)

 

**3.2.2  if…else****语句**

a = -9 

if a > 0: 

  b = a

else:

  b = -a 

print(b)

 

a = -9

b = a if a>0 else -a

print(b)

 

**实例****02****：验证您给出的答案是否满足令狐冲要求**

01 print("今有美酒若干坛，然不知其数，三三数之剩二，五五数之剩三，七七数之剩二，问几何？ \n")

02 number = int(input("请输入您认为符合条件的数："))   #输入一个数

03 if number%3 == 2 and number%5 == 3 and number%7 == 2: #判断是否符合条件

04   print(number,"符合令狐大侠所说条件！")

05 else:

06   print(number, "不符合令狐大侠所说条件！")

 

else:

  print(number, "不符合令狐大侠所说条件！")

02 if a >= 0:

03   if a > 0:

04     print("a大于0")

05   else:

06     print("a等于0")

01 a = -1

02 if a >= 0:

03   if a > 0:

04     print("a大于0")

05 else:

06    print("a小于0")

 

**实例****03****：输出玫瑰花语**

01 print("在古希腊神话中，玫瑰花集爱情与美丽于一身，所以人们常用玫瑰来表达爱情。\n")

02 print("但是你知道吗？不同朵数的玫瑰花代表的含义是不同的。\n")

\#获取用户输入的朵数，并转换为整型

03 number = int(input("输入你想送几朵玫瑰花，小泸会告诉您含义："))

04 if number == 1:      #如果输入的是1，代表1朵

05   print("1朵：一见钟情！") 

06 elif number == 2:     #输入2

07   print("2朵：这世界只有我俩！")

08 elif number == 4:     #输入4

09   print("4朵：至死不渝！")

10 elif number == 10:    #输入10

11   print("10朵：十全十美！")

12 elif number == 99:    #输入99

13  print("99朵：天长地久！")

14 elif number == 100:    #输入100

15   print("100朵：百分之百的爱！")

16 elif number == 108:    #输入108

17   print("108朵：求婚！")

18 else:           #输入其他数字 

19   print("无论送她多少朵，都代表你满满的爱意！")

 

3.3 语句的嵌套

**实例****04****：泸州交警判断司机是否酒后驾车**

01 print("\n 中国酒城·醉美泸州 四川省泸州市欢迎您! \n")

02 print("美酒虽好，请不要贪杯哦！为了您和他人的安全，严禁酒后驾车！\n")

\#获取驾驶员输入的酒精含量，并转换为整型

03 proof = int(input("请输入驾驶员每100mL血液的酒精含量："))

04 if proof < 20:  #酒精含量小于20mg，不构成饮酒行为

05   print("\n您还不构成饮酒行为，可以开车，但要注意安全！")

06 else:  #酒精含量大于或等于20mg，已经构成饮酒驾车行为

07   if 80 > proof >= 20: #酒精含量大于或等于20mg且小于80mg，达到饮酒驾驶标准

08     print("\n已经达到酒后驾车标准，请不要开车！")

09   else:  #酒精含量大于或等于80mg，已经达到醉酒驾驶标准

10     print("\n已经达到醉酒驾车标准，千万不要开车！")

 

3.4  条件表达式

a = 10

b = 6

if a > b:

  r = a

else:

r = b

 

a = 10

b = 6

r = a if a > b else b

 

**任务****3-2** **计算郎酒销售人员近****3****个月的平均销售金额**

01 print("\n四川古蔺郎酒销售有限公司试用期销售人员平均销售业绩考核")

02 end = 'y'

03 while end == 'y' or end == 'Y':

04   print("请输入要考核的销售人员姓名：",end = "")

05   name = input() #录入销售人员姓名

06   sum = 0

07   for i in range(1,4):

08     print("请输入" + name + "第" + str(i) + "个月的销售金额：",end = "")

09     score = input() #录入销售金额

10     sum += int(score) #计算销售金额总和

11   avg = '%.2f'%(sum/3)  #计算平均销售金额，结果保留2位小数

12   print(name + "试用期间月平均销售金额是：" + str(avg))

13   print("继续输入吗(y/n)?",end="")

14  end = input()  #输入结束字符

15 print("所有销售人员该项考核结束！")

 

3.5  循环语句

**实例****05****：破解令狐大侠难题解法①****while****循环**

01 print("今有美酒若干坛，然不知其数，三三数之剩二，五五数之剩三，七七数之剩二，问几何？ \n")

02 none = True     #作为循环条件的变量

03 number = 0     #计数的变量

04 while none:

05   number += 1     #计数加1

06   if number%3 == 2 and number%5 == 3 and number%7 == 2:  #判断是否符合条件

07     print("答曰：这个数是",number)  #输出符合条件的数

08     none = False    #将循环条件的变量赋值为否

 

**实例****06****：破解令狐大侠难题解法②****for****循环**

01 print("今有美酒若干坛，然不知其数，三三数之剩二，五五数之剩三，七七数之剩二，问几何？ \n")

02 for number in range(100):

03   if number%3 == 2 and number%5 == 3 and number%7 == 2:  #判断是否符合条件

04     print("答曰：这个数是",number)  #输出符合条件的数

 

01 for number in range(100)

02   print(number)

 

**实例****07****：打印九九乘法表**

01 for i in range(1,11):    #输出10行

02   for j in range(1,i+1): #输出与行数相等的列

03     print(str(j) + "x" + str(i) + "=" + str(i * j) + "\t",end = '')

04   print("")       #换行

 

**任务****3-3** **模拟五粮液集团财务系统录入员工薪资**

01 print("\n 五粮液集团有限公司财务系统录入员工薪资系统 \n")

02 empNum = 1      #计数的变量

03 salarySum = 0

\#公司员工姓名列表

04 sName = ['闰土','大美','球球','猪小明','毛台','冷檬','蘑菇头','米线儿','小美']

05 salarys = []  #薪资列表

06 inputName = [] #已录入薪资的员工姓名列表

07 while True:

08   s = input("请输入第{0}位员工{1}的薪资（按 Q 或 q 结 束）:".format(empNum,sName[empNum-1])) #从键盘输入员工薪资数值

09   if s.upper() == 'Q': #循环退出条件，如果输入Q或q，循环结束

10     print("录入完成!")

11     break      #使用break跳出while大循环

12   if float(s) < 0:  #终止本次循环条件，如果输入薪资值为负数，则终止本次循环

13     continue     #使用continue终止本次循环并提前进入到下一次循环中

14   inputName.append(sName[empNum - 1]) 

15   salarys.append(float(s)) 

16   salarySum += float(s)

17   empNum += 1

18 print("录入员工数量为：{0}".format(empNum-1)) 

19 print("录入的员工姓名分别为：", inputName) #输出录入员工姓名

20 print("录入的员工对应的薪资为：", salarys) #输出录入员工对应的薪资

21 print("平均薪资为：{0}".format('%.2f'%(salarySum/(empNum-1)))) #计算出员工平均薪资

3.6  跳转语句

**实例****08****：破解令狐大侠难题解法③：****for****循环改进**

01 print("今有美酒若干坛，然不知其数，三三数之剩二，五五数之剩三，七七数之剩二，问几何？ \n")

02 for number in range(100):

03   if number%3 == 2 and number%5 == 3 and number%7 == 2: #判断是否符合条件

04     print("答曰：这个数是",number)  #输出符合条件的数

05     break              #跳出for循环

 

**实例****09****：逢七拍腿员工拓展小游戏**

01 total = 99          #记录拍腿次数的变量

02 for number in range(1,100): #创建一个从1到100（不包括）的循环

03   if number % 7 == 0:   #判断是否为7的倍数

04     continue       #继续下一次循环

05   else:

06     string = str(number)   #将数值转换为字符串

07     if string.endswith('7'): #判断是否以数字7结尾 

08       continue

09   total -= 1             #可拍腿次数-1

10 print("本次游戏中，所有参与员工从1数到99共拍腿",total,"次。") #显示拍腿次数

3.7  pass空语句

01 for i in range(1,10):

02   if i%2 == 0:      #判断是否为偶数

03     print(i,end = ' ') 

04   else:          #不是偶数

05     pass        #占位符，不做任何事情

 

 

项目4 掌握常见的数据结构

**任务****4-1** **中国十大酱香型白酒榜单更新管理**

01 print("\n=====中国十大酱香型白酒榜单更新管理====")

\#初始化列表，charts列表首次存储2017年排行榜10个元素

02 charts = ['茅台','郎酒','习酒','金沙窖','武陵','钓鱼台','国台','仙潭','珍酒','云门陈酿']

03 print("2017年中国十大酱香型白酒排行榜：")

04 for index,item in enumerate(charts): #遍历列表操作，按行打印出2017年排行榜

05   print(index + 1,item)

06 print("2018年中国十大酱香型白酒排行榜发生变化！")

07 print("具体变化内容如下：")

08 charts[2] = '钓鱼台'

09 charts[4] = '习酒'

10 charts[5] = '武陵'

11 charts[7] = '云门陈酿'

12 charts[9] = '领军酒'

13 print("第3名：习酒 ——> 钓鱼台") #打印出2018年排行榜具体变化情况

14 print("第5名：武陵 ——> 习酒")

15 print("第6名：钓鱼台 ——> 武陵")

16 print("第8名：仙潭 ——> 云门陈酿")

17 print("第10名：云门陈酿 ——> 领军酒（新进榜单）")

18 print("2018年中国十大酱香型白酒排行榜：")

19 print(charts)   #打印出2018年排行榜

20 print("2019年中国十大酱香型白酒排行榜发生变化！")

21 print("具体变化内容如下：")

22 del charts[-1]   #删除列表最后一个元素

23 del charts[-2]   #删除列表倒数第二个元素

24 charts.append('君寿酒')

25 charts.append('仙潭')

\#打印出2019年排行榜具体变化情况

26 print("第9名：珍酒 ——> 君寿酒（新进榜单）")

27 print("第10名：领军酒 ——> 仙潭（新进榜单）")

28 print("2019年中国十大酱香型白酒排行榜：")

29 print(charts)   #打印出2019年排行榜

30 print("荣获2019年中国十大酱香型白酒排行榜前三甲的是：")

\#遍历列表前3个元素，输出2019年榜单前三甲元素

31 for item in charts[0:3]:

32   print(item)

4.1 序列

**4.1.1**  **索引**

verse = ["花间一壶酒","独酌无相亲","举杯邀明月","对影成三人"]

print(verse[2])   #输出第3个元素

print(verse[-1])  #输出最后1个元素

**4.1.2**  **切片**

nba = ["迈克尔·乔丹","比尔·拉塞尔","卡里姆·阿布杜尔·贾巴尔","威尔特·张伯伦","埃尔文·约翰逊","科比·布莱恩特","蒂姆·邓背","勒布朗·詹姆斯","拉里·伯德","沙奎尔·奥尼尔"]

print(nba[1:5])    #获取第2个到第5个元素

print(nba[0:5:2])   #获取第1个、第3个和第5个元素

**4.1.3**  **序列相加**

nba1 = ["德怀特·霍华德","德维恩·书德","凯里·欧文","保罗·加索尔"]

nba2 = ["迈克尔·乔丹","比尔·拉塞尔","卡里姆·阿布杜尔·贾巴尔","威尔特·张伯伦","埃尔文·约翰逊","科比·布菜恩特","蒂姆·邓肯","勒布朗·詹姆斯",]

print(nba1+nba2)

 

num =[7,14,21,28,35,42,49,56,63]

print(num +"输出的数是7的倍数")

**4.1.4**  **乘法**

Alcohol = ["泸州老窖1573","青花郎"]

print(Alcohol*3)

**4.1.5**  **计算序列的长度、最大值和最小值**

num = [7,14,21,28,35,42,49,56,63]

print("序列num的长度为", len(num))

 

num = [7,14,21, 28,35,42,49,56,63]

print("序列",num, "中的最大值为" , max(num))

 

num = [7,14,21,28,35,42,49,56,63]

print("序列" ,num,"中的最小值为",min(num))

4.2  列表

**4.2.1**  **列表的创建和删除**

**1****．使用赋值运算符直接创建列表**

listname = [element 1,element 2,element 3,-,element n]

 

num = [7,14, 21,28,35,42,49,56, 63]

verse = ["明月几时有？" ,"把酒问青天","不知天上宫阙","今夕是何年"]

untitle = ['泸州老窖',1573,"贵州茅台",["江阳古城","醉美泸州","欢迎您","来做客"]]

python = ['郎酒',"青花郎","红花郎"]

**2****．创建空列表**

emtylist = []

**3****．创建数值列表**

list(data)

list(range(10,20,2))

**4****．删除列表**

del listname

 

Alcohol = ["泸州老窖","贵州茅台","宜宾五粮液","山西汾酒"]

del Alcohol

 

**4.2.2**  **访问列表元素**

untitle = ['泸州老窖', 1573,"贵州茅台", ["江阳古城","醉美泸州","欢迎您","来做客"]]

print(untitle )

 

untitle = ['泸州老窖', 1573,"贵州茅台", ["江阳古城","醉美泸州","欢迎您","来做客"]]

print(untitle)

 

**实例****01****：每天向深爱的人说一句“土情话”**

01 import datetime               # 导入日期时间类

\# 定义一个列表

02 mot = ["今天星期一：\n你知道我喜欢吃什么吗？痴痴的望着你。",

​    "今天星期二：\n我有一个超能力，超喜欢你。",

​    "今天星期三：\n你今天怪怪的。怎么了？怪好看的。",

​    "今天星期四：\n你最爱上谁的课？爱上你的每一刻。",

​    "今天星期五：\n你的脸上有点东西，有什么？有点漂亮。",

​    "今天星期六：\n你知道我喜欢喝什么吗？ 呵护你。",

​    "今天星期日：\n你会弹吉他吗？为什么拨动了我的心弦。"]

03 day=datetime.datetime.now().weekday()   # 获取当前星期

04 print(mot[day])  

 

**4.2.3**  **遍历列表**

**1****．直接使用****for****循环实现**

print("四川2019年各市GDP总量排名前十: ")

city = ["成都市","绵阳市","宜宾市","德阳市","南充市","泸州市" ,

"达州市","乐山市","凉山州","内江市"]

for item in city:

  print(item)

**2****．使用****for****循环和****enumerate()****函数实现**

print("四川2019年各市GDP总量排名前十: ")

city = ["成都市","绵阳市","宜宾市","德阳市","南充市","泸州市",

"达州市","乐山市","凉山州","内江市"]

for index,item in enumerate(city) :

  print(index + 1,item)

 

**实例****02****：分两列显示四川****2019****年各市****GDP****总量前十名的城市**

01 print("四川2019年各市GDP总量排名前十: ")

02 city = ["成都市","绵阳市","宜宾市","德阳市","南充市","泸州市",

03 "达州市","乐山市","凉山州","内江市"]

04 for index,item in enumerate(city):

05   if index%2 == 0:     # 判断是否为偶数，为偶数时不换行

06     print(item +"\t\t", end='')

07   else:

08     print(item + "\n")  # 换行输出

 

**4.2.4**  **添加、修改和删除列表元素**

**1****．添加元素**

Alcohol = ["泸州老窖1573","古蔺郎酒","宜宾五粮液","贵州茅台"]

len(Alcohol)  #获取列表的长度

Alcohol. append("山西汾酒")

len(Alcohol)  #获取列表的长度

print(Alcohol)

 

**实例****03****：向泸州市三级医院列表中追加****2018****年新增的医院**

\#泸州市原有三级医院列表

01 old3hospital = ["西南医科大附属医院","西南医科大附属中医医院","西南医科大附属口腔医院和","泸州市中医医院","合江县人民医院"] 

\# 新增人员列表

02 newlist = ["泸州市人民医院","泸县人民医院","叙永县人民医"]

03 old3hospital.extend(newlist)  # 追加新增三级医院

04 print(old3hospital)  # 显示泸州市新的三级医院列表

**2****．修改元素**

verse =["人有悲欢离合","月有阴晴圆缺","此事古难全"]

print(verse)

verse[2] = "千里共婵娟"  #修改列表的第3个元素

print(verse)

**3****．删除元素**

verse =["人有悲欢离合","月有阴晴圆缺","此事古难全"]

del verse[-1]

print(verse)

 

city = ["成都市","绵阳市","宜宾市","德阳市","南充市","泸州市",

"达州市","乐山市","凉山州","内江市"]

city.remove("雅安市")

 

city = ["成都市","绵阳市","宜宾市","德阳市","南充市","泸州市",

"达州市","乐山市","凉山州","内江市"]

value = "雅安市"       #指定要移除的元素

if city.count(value)>0:   #判断要删除的元素是否存在

  city.remove(value)   #移除指定的元素

print(city)

 

**4.2.5**  **对列表进行统计和计算**

**1****．获取指定元素出现的次数**

song = ["我们不一样","武汉呀","往事随风","成都","我们不一样","凉凉","一剪梅","北京欢迎你"]

num = song.count("我们不一样")

print(num)

**2****．获取指定元素首次出现的下标**

song = ["我们不一样","武汉呀","往事随风","成都","新贵妃醉酒","凉凉","一剪梅","北京欢迎你"]

position = song.index("新贵妃醉酒")

print(position)

**3****．统计数值列表的元素和**

grade = [80, 77, 88,90,86,96,94, 89 ,95, 78] # 10名学生的物理成绩列表

total = sum(grade)#计算总成绩

print("物理总成绩为: ", total)

 

**4.2.6**  **对列表进行排序**

**1****．使用列表对象的****sort()****方法**

grade = [80, 77, 88,90,86,96,94, 89,95,78] # 10名学生的物理成绩列表

print("原列表: ",grade)

grade.sort()         #进行升序排列

print("升序: " ,grade)

grade.sort( reverse = True)  #进行降序排列

print("降序:" ,grade)

 

char = ['cat', 'Dog', 'Chicken', 'cattle', 'Sheep']

char.sort()            #默认区分字母大小写

print("区分字母大小写: " , char)

char.sort(key=str.lower)    #不区分字母大小写

print("不区分字母大小写: " , char)

 

**2****．使用内置的****sorted()****函数实现**

grade = [80, 77, 88,90,86,96,94, 89,95,78]# 10名学生的物理成绩列表

grade_as = sorted(grade)           #进行升序排列

print('升序:',grade_as)

grade_des = sorted(grade, reverse = True)   #进行降序排列

print("降序:", grade_des)

print("原序列:",grade)

 

**4.2.7**  **二维列表的使用**

**1****．直接定义二维列表**

verse = [['滚', '滚', '长', '江', '东', '逝', '水'],

['浪', '花', '淘', '尽', '英', '雄'],

['是', '非', '成', '败', '转', '空', '头']]

print(verse)

**2****．使用嵌套的****for****循环创建**

arr = []

for i in range(4):

  arr.append([])

  for j in range(5):

​    arr[i].append(j)

print(arr)

**实例****04****：使用二维列表输出不同版式的李白《月下独酌》古诗**

01 str1 = "花间一壶酒 独酌无相亲"

02 str2 = "举杯邀明月 对影成三人"

03 str3 = "月既不解饮 影徒随我身"

04 str4 = "暂伴月将影 行乐须及春"

05 str5 = "我歌月徘徊 我舞影零乱"

06 str6 = "醒时相交欢 醉后各分散"

07 str7 = "永结无情游 相期邈云汉"

08 verse = [list(str1), list(str2), list(str3), list(str4),

  list(str5), list(str6), list(str7)] # 定义一个二维列表

09 print("\n------- 横版 -------\n")

10 for i in range(7): # 循环古诗的每一行

11   for j in range(11): # 循环每一行的每个字（列）

12     if j == 10: # 如果是一行中的最后一个字

13       print(verse[i][j]) # 换行输出

14     else:

15       print(verse[i][j], end="") # 不换行输出

16 verse.reverse() # 对列表进行逆序排列

17 print("\n------- 竖版 -------\n")

18 for i in range(11): # 循环每一行的每个字（列）

19   for j in range(7): # 循环新逆序排列后的第一行

20     if j == 6: # 如果是最后一行

21       print(verse[j][i]) # 换行输出

22     else:

23       print(verse[j][i], end="") # 不换行输出

 

**任务****4-2 2019****年四川省各市（州）****GDP****数据查询**

01 print("\n2019年四川省各市（州）GDP数据查询系统")

\#初始化元组，存储四川省各市（州）GDP总量前十的城市信息

02 SC_city = ("第一名：成都市 2019年GDP总量：17012.65（亿元） 2018年GDP总量：15698.94（亿元） 增量：1313.71（亿元） 实际增长率：7.80%",

​    "第二名：绵阳市  2019年GDP总量：2856.20（亿元） 2018年GDP总量：2613.30（亿元） 增量：242.90（亿元）  实际增长率：8.10%",

​    "第三名：宜宾市  2019年GDP总量：2601.89（亿元） 2018年GDP总量：2349.31（亿元） 增量：252.58（亿元）  实际增长率：8.80%",

​    "第四名：德阳市  2019年GDP总量：2335.90（亿元） 2018年GDP总量：2148.39（亿元） 增量：187.51（亿元）  实际增长率：7.20%",

​    "第五名：南充市  2019年GDP总量：2322 22（亿元） 2018年GDP总量：2115.73（亿元） 增量：206.49（亿元）  实际增长率：8.00%",

​    "第六名：泸州市  2019年GDP总量：2081.30（亿元） 2018年GDP总量：1895.55（亿元） 增量：185.75（亿元）  实际增长率：8.00%",

​    "第七名：达州市  2019年GDP总量：2041.50（亿元） 2018年GDP总量：1879.53（亿元） 增量：161.97（亿元）  实际增长率：7.70%",

​    "第八名：乐山市  2019年GDP总量：1863.31（亿元） 2018年GDP总量：1709.81（亿元） 增量：153.50（亿元）  实际增长率：7.60%",

​    "第八名：乐山市  2019年GDP总量：1863.31（亿元） 2018年GDP总量：1709.81（亿元） 增量：153.50（亿元）  实际增长率：7.60%",

​    "第九名：凉山州  2019年GDP总量：1676.30（亿元） 2018年GDP总量：1556.48（亿元） 增量：119.82（亿元）  实际增长率：5.60%",

​    "第十名：内江市  2019年GDP总量：1433.30（亿元） 2018年GDP总量：1318.83（亿元） 增量：114.47（亿元）  实际增长率：7.80%")

03 end = 'y'

04 while end == 'y' or end == 'Y':

05   print("请输入要查询市（州）的GDP排名序号：", end="")

06   cityNum = input()     # 录入要查询市（州）的GDP排名序号

07   print("您查询的城市信息2019年GDP如下：")

08   print(SC_city[int(cityNum)-1])   #访问元组操作

09   print("继续输入吗(y/n)?",end="")

10   end = input()  #输入结束字符

11 print("查询结束！")

4.3  元 组

**4.3.1**  **元组的创建和删除**

**1****．使用赋值运算符直接创建元组**

num = (7,14,21,28,35,42,49,56,63)     #数字

song = ("北京欢迎你" ,"新贵妃醉酒","懂你","一次就好")  #歌曲

AdLanguage = ('泸州老窖', 1573,("喝百世窖酒", "交一生朋友"), ["窖","传百世" ,"酒" , "香天下"])  #广告语

Brandname = ('长相思','渔歌子','苏幕遮','虞美人','采桑子')  #词牌名

song = "北京欢迎你" ,"新贵妃醉酒","懂你","一次就好"

print(song)

 

verse1 = ("众人皆醉我独醒",)

print(verse1)

verse2 = ("众人皆醉我独醒")

print(verse2)

**2****．创建空元组**

emptytuple = ()

**3****．创建数值元组**

import random   #导入random标准库

randomnumber = (random.randint(10,100) for i in range(10))

randomnumber = tuple (randomnumber)   #转换为元组

print("转换后: ", randomnumber)

**4****．删除元组**

verse = ("对酒当歌","人生几何？","譬如朝露","去日苦多","何以解忧","唯有杜康")

del verse

 

**实例****05****：使用元组保存苏格酒吧里提供的饮品名称**

\# 定义元组

01 Alcoholname = ('洋酒','白兰地','啤酒','白酒','红酒','鸡尾酒') 

02 print(Alcoholname)          # 输出元组

 

**4.3.2**  **访问元组元素**

untitle = ('泸州老窖', 1573,("喝百世窖酒", "交一生朋友"), ["窖","传百世" ,"酒" , "香天下"]) 

print(untitle )

 

print(untitle[0])

 

print(untitle[:3])

 

**实例****06****：使用****for****循环列出苏格酒吧里的酒类饮品名称**

\# 定义元组

01 Alcoholname = ('洋酒','白兰地','啤酒','白酒','红酒','鸡尾酒')  

02 print("您好，欢迎光临 ~ 苏格酒吧 ~\n本酒吧提供6种酒类饮品供您选择：")

03 for name in Alcoholname:      #遍历元组

04   print(name, end = " ")

 

**实例****07****：分两列显示四川****2019****年各市****GDP****总量前十名的城市**

01 print("四川2019年各市GDP总量排名前十: ")

02 city = ("成都市","绵阳市","宜宾市","德阳市","南充市","泸州市",

"达州市","乐山市","凉山州","内江市")

03 for index,item in enumerate(city):

04   if index%2 == 0:       # 判断是否为偶数，为偶数时不换行

05     print(item +"\t\t", end='')

06   else:

07     print(item + "\n")    # 换行输出

 

**实例****08****：将白兰地替换为威士忌**

01 Alcoholname = ('洋酒','白兰地','啤酒','白酒','红酒','鸡尾酒') # 定义元组

02 Alcoholname[1] = '威士忌'  # 将“白兰地”替换为“威士忌”

03 print(Alcoholname)

 

 \# 定义元组

01 Alcoholname = ('洋酒','白兰地','啤酒','白酒','红酒','鸡尾酒') 

\# 对元组进行重新赋值

02 Alcoholname = ('洋酒','威士忌','啤酒','白酒','红酒','鸡尾酒')  

03 print("新元组为：",Alcoholname)

 

Alcoholname = ('洋酒','白兰地','啤酒','白酒')

Alcoholname = Alcoholname + ['红酒','鸡尾酒']

 

Alcoholname = ('洋酒','白兰地','啤酒','白酒')

Alcoholname = Alcoholname + ('红酒')

 

**任务****4-3** **四川泸天化股份有限公司员工信息管理**

01 print("\n===四川泸天化股份有限公司研发部员工信息管理===")

02 print("操作指令：i 增加 r 删除  c 修改  s 查找")

\#初始化字典，存储四川泸天化股份有限公司研发部员工信息管理

03 staff = {'Y20180053':'猪小明，男，27岁，大学本科学历',

​     'Y20180089':'毛台，男，45岁，大学专科学历',

​     'Y20190020':'球球,女，25岁，大学本科学历',

​     'Y20170078': '冷檬，女，22岁，大学专科学历',

​     'Y20120023': '闰土，男，38岁，大学本科学历',

​     'Y20110090':'陈翔，男，32岁，硕士研究生学历',

​     'Y20080120':'米线儿，女，22岁，大学专科学历',

​     'Y20100003':'小美，女，26岁，大学本科学历'

​     }

04 end = 'y'

05 operC = 'n'

06 while end == 'y' or end == 'Y':

07   print("请输入相关操作：", end="")

08   operC = input()

09   if str(operC) == 'i': #选择增加员工操作

10     print("请输入新增加员工工号：", end="")

11     iNo = input()   #保存输入的新增员工工号

12     if str(iNo) in staff:  # 新增员工工号如果存在字典中

13       print("该工号已存在，添加失败！")  # 输出添加失败信息

14     else:           #新增员工工号不存在字典中

15       print("请输入新增加员工信息：", end="")

16       iInfo = input()    #保存输入的新增员工信息

17          staff[str(iNo)] = str(iInfo)  #执行字典增加元素操作

18       print("添加成功！")       #输出添加成功

19       print("新添加的员工信息如下：")

20       print("工号：" + str(iNo) + "    员工信息：

" + staff[str(iNo)]) #输出新增记录信息

21    elif operC == 'r':  #选择删除员工操作

22     print("请输入要删除的员工工号：", end="")

23     iNo = input()   #保存输入的要删除员工工号

24     if str(iNo) in staff: # 要删除员工工号如果存在字典中

25       del staff[str(iNo) ]  #执行字典删除元素操作

26       print("删除成功！")

27     else:           #要删除员工工号如果不存在字典中

28       print("该工号不存在，删除失败！")  #输出删除失败

29   elif operC == 'c':  #选择更改员工操作

30     print("请输入要更改信息的员工工号：", end="")

31     iNo = input()   #保存要更改信息的员工工号

32     if str(iNo) in staff: # 要修改员工工号如果存在字典中

33       print("请输入最新的员工信息：", end="")

34       iInfo = input()   #保存要更改信息的员工的信息内容

35       staff[str(iNo) ] = str(iInfo)#执行字典修改元素操作 

36       print("修改成功！修改后该员工信息如下：")#输出修改成功

37       print("工号：" + str(iNo) + "    员工信息："+staff[str(iNo)])  #输出修改后的员工信息

38     else:

39       print("该工号不存在，修改失败！")  #输出修改失败

40   elif operC == 's':  #选择查找员工操作

41     print("请输入要查找的员工工号：", end="")  

42     iNo = input()    #保存要查找的员工工号 

43     if str(iNo) in staff: # 要查找的员工工号如果存在字典中

44       print("查找成功！") #输出查找成功

45       print("查找到的该员工信息如下：")

46       print("工号：" + str(iNo) + "    员工信息：" + staff[str(iNo)])   #输出查找到的员工信息

47     else:

48       print("该工号不存在，查找失败！") #输出查找失败

49   else:

50     operC == 'n'

51   print("继续相关操作吗(y/n)?",end="")

52   end = input()  #输入结束字符

53 print("操作结束！")

4.4  字典

**4.4.1**  **字典的创建和删除**

dictionary = {'猪小明':'18384978921','球球':'13864532670','米线儿':'17726567780'}

print(dictionary)

**实例****09****：创建一个保存泸职院学霸星座的字典**

01 name = ['球球','冷檬','米线儿','小美']   #作为键的列表

02 sign = ['白羊座','射手座','双鱼座','双子座']  #作为值的列表

03 dictionary = dict(zip(name,sign))      #转换为字典

04 print(dictionary)  

**2****．通过给定的“键****-****值对”创建字典**

01 name = ['球球','冷檬','米线儿','小美']   #作为键的列表

02 sign = ['白羊座','射手座','双鱼座','双子座']  #作为值的列表

03 dictionary = dict(zip(name,sign))      #转换为字典

04 print(dictionary)  

 

name = ['球球','冷檬','米线儿','小美']   #作为键的列表

dictionary = dict.fromkeys(name)

print(dictionary) 

 

name_tuple = ('球球','冷檬','米线儿','小美')   #作为键的元组

sign = ['白羊座','射手座','双鱼座','双子座']  #作为值的列表

dict1 = {name_tuple:sign}

print(dict1) 

 

name_list = ['球球','冷檬','米线儿','小美']   #作为键的列表

sign = ['白羊座','射手座','双鱼座','双子座']  #作为值的列表

dict1 = {name_list:sign}

print(dict1) 

del dictionary

dictionary.clear()

 

**实例****10****：根据星座测试性格特点**

01 name = ['球球','冷檬','米线儿','小美']    # 作为键的列表

02 sign_person = ['白羊座','射手座','双鱼座','双子座']#作为值的列表

03 person_dict = dict(zip(name,sign_person))  # 转换为个人字典

04 sign_all =['白羊座','金牛座','双子座','巨蟹座','狮子座','处女座','天秤座','天蝎座','射手座','摩羯座','水瓶座','双鱼座']

05 nature = ['有一种让人看见就觉得开心的感觉，阳光、乐观、坚强，性格直来直去，就是有点小脾气。',

​     '很保守，喜欢稳定，性格比较慢热，是个理财高手。',

​     '喜欢追求新鲜感，有点小聪明，耐心不够，因你的可爱性格会让很多人喜欢和你做朋友。',

​     '情绪容易敏感，缺乏安全感，为人重情重义，对朋友和家人特别忠实。',

​     '有着远大的理想，总是期待被仰慕被崇拜的感觉。',

​     '坚持追求自己的完美主义者。',

​     '追求平等、和谐，交际能力强。最大的缺点就是面对选择总是犹豫不决。',

​     '精力旺盛，占有欲强，对于生活很有目标，不达目的誓不罢休，复仇心重。',

​     '崇尚自由，勇敢、果断，身上有一股勇往直前的劲儿，只要想做，就能做。',

​     '是最有耐心的，做事最小心。做事脚踏实地，比较固执，不达目的不罢休。',

​     '人很聪明，追求独一无二的生活，个人主义色彩很浓重的星座。',

​     '集所有星座的优缺点于一身。最大的优点是有一颗善良的心，愿意帮助别人。']

06 sign_dict = dict(zip(sign_all,nature))   # 转换为星座字典

07 print("球球的星座是:",person_dict.get("球球"))  # 输出星座

08 print("她的性格特点是：\n",sign_dict.get(person_dict.get("球球"))) # 输出性格特点

09 print("小美的星座是:",person_dict.get("小美"))   # 输出星座

10 print("她的性格特点是：\n",sign_dict.get(person_dict.get("小美"))) # 输出性格特点

 

**4.4.3**  **遍历字典**

dictionary = {'猪小明':'18384978921','球球':'13864532670','米线儿':'17726567780'}

for item in dictionary.items():

  print(item)

 

dictionary = {'猪小明':'18384978921','球球':'13864532670','米线儿':'17726567780'}

for key,value in dictionary.items():

  print(key,"的手机号是",value)

 

**4.4.4**  **添加、修改和删除字典元素**

dictionary =dict((('球球', '白羊座'),('冷檬','射手座'),('米线儿','双鱼座'),('小美','双子座')))

dictionary["婷婷"] = "巨蟹座"   #添加一个元素

print(dictionary)

 

dictionary =dict((('球球', '白羊座'),('冷檬','射手座'),('米线儿','双鱼座'),('小美','双子座')))

dictionary["冷檬"] = "水瓶座"   #添加一个元素，当元素存在时，则相当于修改功能

print(dictionary)

 

dictionary =dict((('球球', '白羊座'),('冷檬','射手座'),('米线儿','双鱼座'),('小美','双子座')))

del dictionary["冷檬"]   #删除一个元素

print(dictionary)

 

**4.4.5** **字典推导式**

import random   #导入random标准库

randomdict = {i:random.randint(10,100) for i in range(1,5)}

print("生成的字典为: ", randomdict)

 

**实例****11****：应用字典推导式实现根据名字和星座创建一个字典**

01 name = ['球球','冷檬','米线儿' ,'小美']  #作为键的列表

02 sign = ['白羊','射手','双鱼','双子']  #作为值的列表

03 dictionary = {i:j+'座' for i,j in zip(name,sign)}  #使用列表推导式生成字典

04 print(dictionary)  #输出转换后字典

 

 

 

**任务****4-4** **白酒专卖店经销商和白酒品牌的故事**

01 print("\n===白酒专卖店经销商和白酒品牌的故事===")

02 lzlj_set = {'球球','毛台','猪小明','小泸','米线儿'}

03 wly_set = {'翔子','吴妈','冷檬','闰土'}

04 jnc_set = {'妹爷','米线儿','小野','闰土'}

05 print("泸州老窖在河北授权的白酒专卖店经销商名单：")

06 print(lzlj_set)

07 print("五粮液在河北授权的白酒专卖店经销商名单：")

08 print(wly_set)

09 print("剑南春在河北授权的白酒专卖店经销商名单：")

10 print(jnc_set)

11 print('同时获得泸州老窖和五粮液两个白酒品牌的专卖店经销商有：',lzlj_set & wly_set)

12 print('同时获得泸州老窖和剑南春两个白酒品牌的专卖店经销商有：',lzlj_set & jnc_set)

13 print('同时获得五粮液和剑南春两个白酒品牌的专卖店经销商有：',wly_set & jnc_set)

\#泸州老窖品牌在河北新增授权一家专卖店经销商王炸

14 wly_set.add('王炸')

15 print("河北现有五粮液授权的白酒专卖店经销商名单：")

16 print(wly_set)

17 jnc_set.remove('妹爷') #剑南春品牌在河北解除一家专卖店经销商妹爷的授权资质

18 print("河北现有剑南春授权的白酒专卖店经销商名单：")

19 print(jnc_set)

4.5  集 合

**4.5.1** **集合的创建**

**实例****12****：创建保存学生选课信息的集合**

01 python = {'球球','猪小明','闰土','冷檬'}   # 保存选择Python语言的学生姓名

02 print('选择Python语言的学生有：',python,'\n')# 输出选择Python语言的学生姓名

03 c = {'米线儿','毛台','婷婷','小美'} # 保存选择C语言的学生姓名

04 print('选择C语言的学生有：',c)    # 输出选择C语言的学生姓名

**2****．使用****set()****函数创建**

set1 = set("雪花飘飘,北风萧萧,天地一片苍茫")

set2 = set([1.414,1.732,3.14159,2.236])

set3 = set(('醉美泸州','欢迎您的到来！'))

 

**4.5.2**  **集合的添加和删除**

**1****．向集合中添加元素**

mr = set(['泸州老窖','贵州茅台' ,'古井贡酒','衡水老白干','五粮液'])

mr.add('剑南春')    #添加一个元素

print(mr)

 

**2****．从集合中删除元素**

mr = set(['泸州老窖','贵州茅台' ,'古井贡酒','衡水老白干','五粮液','剑南春'])

mr.remove('古井贡酒')    #移除指定元素

print('使用remove()方法移除指定元素后: ',mr)

mr.pop()           #删除一个元素

print('使用pop( )方法移除一个元素后: ',mr)

mr.clear()          #清空集合

print('使用clear( )方法清空集合后: ',mr)

 

**实例****13****：学生更改选学课程**

01 python = set(['球球','猪小明','闰土','冷檬'])  # 保存选择Python语言的学生姓名

02 python.add('婷婷')             # 添加一个元素

03 print('选择Python语言的学生有：',python,'\n')  # 输出选择Python语言的学生姓名

04 c = set(['米线儿','毛台','婷婷','小美'])# 保存选择C语言的学生姓名

05 c.remove('婷婷')           # 删除指定元素

06 print('选择C语言的学生有：',c)    # 输出选择C语言的学生姓名

 

01 python = set(['球球','猪小明','婷婷','闰土','冷檬']) # 保存选择Python语言的学生姓名

02 c = set(['米线儿','猪小明','毛台','婷婷','小美']) # 保存选择C语言的学生姓名

03 print('选择Python语言的学生有：',python)    # 输出选择Python语言的学生姓名

04 print('选择C语言的学生有：',c)   # 输出选择C语言的学生姓名

05 print('交集运算：',python & c) # 输出既选择了Python语言又选择C语言的学生姓名

06 print('并集运算：',python | c)   # 输出参与选课的全部学生姓名

07 print('差集运算：',python - c)# 输出选择Python语言但没有选择C语言的学生姓名

项目5 玩转字符串操作

**任务****5-1** **输出完整的中国知名白酒品牌经典广告语**

01 list_new = []  #定义拼接后新的广告列表

02 list_ad = []  #广告列表

03 list_name = ['泸州老窖：','五粮液：','茅台：','郎酒：','剑南春：','西凤酒：','汾酒：','衡水老白干：','劲酒：']  #白酒品牌名称列表

04 Ad_allsentence = '中国白酒经典广告语大全(1)@中国荣耀泸州老窖。(2)@中国的五粮液，世界的五粮液。(3)@国酒茅台，玉液之冠。(4)@神采飞扬，中国郎。(5)@唐时宫廷酒，今日剑南春。(6)@三千年不间断传承，国脉凤香西凤酒。(7)@开启尊贵生活，中国酒魂。(8)@衡水老白干，喝出男人味。(9)@劲酒虽好，可不要贪杯哦。'    #原字符串

05 subBTstr = Ad_allsentence[:11]  #从左边开始，截取长字符串前11个字符，获取标题

06 print("\n=====中国知名白酒品牌经典广告语=====")

07 print("原字符串:"+ Ad_allsentence)

08 substr = Ad_allsentence[11:] #从第12个字符开始截取，获取除标题外的所有广告长串

09 list_adS = substr.split('。') #采用。号进行分割，得到初始广告列表

10 for item in list_adS:     #遍历list_adS，只截取广告语文字

11   list_ad.append(item[4:]) #每条广告语从第5个字符开始截取

\# 实现list_name和list_ad两个列表拼接

12 for i in range(0, len(list_name)):

13   list_new.append(list_name[i] + list_ad[i])

14 print("经过截取、分割、拼接等字符串操作，得到按行输出的中国知名白酒品牌经典广告语如下\n")

15 for item in list_new:

16   item = item + '。' #给每条广告语加上。号

17   print(item)  #输出每条白酒品牌+完整广告语

5.1  字符串常用操作

**5.1.1**  **拼接**

sen_en = 'If you donnot like something, please change it. If you cannot change it, change your attitude. Donnot complain.'

sen_cn ='如果你不喜欢某件事，就请去改变它。如果你不能改变它，就改变你的态度。不要抱怨。'

print(sen_en + '——' + sen_cn)

 

str1 ='泸州老窖'  #定义字符串

num = 1573   #定义一个整数

str2 = '好喝的不得了'  #定义字符串

print(str1 + num + str2)  #对字符串和整数进行拼接

 

str1 ='泸州老窖'  #定义字符串

num = 1573   #定义一个整数

str2 = '好喝的不得了'  #定义字符串

print(str1 + str(num) + str2)  #对字符串和整数进行拼接

**实例****01****：使用字符串拼接输出一个关于程序员的笑话**

01 programmer_1 = '程序员猪小明：搞代码太辛苦了，我想换行，怎么办' # 程序员猪小明说的话

02 programmer_2 = '程序员闰土：敲一下回车键'  # 程序员闰土说的话

03 print(programmer_1 + '\n\n' + programmer_2)    # 拼接后输出

**5.1.2**  **计算字符串的长度**

str1 = '中国名酒郎酒，始于1898年。'  #定义字符串

length = len(str1)      #计算字符串的长度

print(length)

 

str1 = '中国名酒郎酒，始于1898年。'  #定义字符串

length = len(str1)      #计算字符串的长度

print(length)

 

str1 = '中国名酒郎酒，始于1898年。'  #定义字符串

length = len(str1.encode('gbk'))  #计算UTF-8编码的字符串的长度

print(length)

 

**5.1.3** **截取字符串**

str1 = '中国名酒郎酒，始于1898年。'  #定义字符串

substr1 = str1[1]   #截取第2个字符

substr2 = str1[5:]   #从第6个字符截取

substr3 = str1[:5]   #从左边开始截取5个字符

substr4 = str1[2:5]  #截取第3个到第5个字符

print('原字符串:',str1)

print(substr1 + '\n' + substr2 + '\n' + substr3 + '\n' + substr4)

 

str1 = '中国名酒郎酒，始于1898年。'  #定义字符申

try:

  substr1 = str1[20]   #截取第20个字符

except IndexError:

  print('指定的索引不存在')

 

**实例****02****：截取球球身份证号码中的出生日期**

01 programer_1 = '球球，能告诉我你的生日吗？'  # 闰土问球球

02 print('闰土说：',programer_1)     # 输出闰土的话

03 programer_2 = '人家不好意思说嘛！'  # 球球回答

04 print('球球说：',programer_2)     # 输出球球的回答

05 programer_3 = '那能告诉我身份证号码吗？以后可以帮忙订票一起回家！' # 闰土问球球

06 print('闰土说：',programer_3)     # 输出闰土的话

07 idcard = '511531199006277890'  # 定义保存身份证号码的字符串

08 print('球球说：','OK，我身份证号码是'+ idcard) # 输出球球的回答

09 birthday = idcard[6:10] + '年' + idcard[10:12] + '月' + idcard[12:14] + '日'          # 截取生日

10 print('闰土说：','球球，我知道了！你是' + birthday + '出生的，所以你的生日是' + birthday[5:])    # 闰土说出球球的生日

11 programer_4 = '等着我给你的惊喜哦！' 

12 print('闰土说：',programer_4) # 输出闰土的话

 

**5.1.4**  **分割、合并字符串**

**1****．分割字符串**

str1 ='泸州老窖官网 >>> www.lzlj.com'

print('原字符串:', str1)

list1 = str1.split()  #采用默认分隔符进行分割

list2 = str1.split('>>>')  #采用多个字符进行分割

list3 = str1.split('.' )  #采用.号进行分割

list4 = str1.split(' ',4)  #采用空格进行分割，并且只分割前4个

print(str(list1) + '\n' + str(list2) + '\n' + str(list3) 

\+ '\n' + str(list4) )

list5 = str1.split('>')  #采用>进行分割

print(list5)

 

**实例****03****：输出被****@****的好友名称**

01 str1 = '@泸州老窖 @郎酒 @五粮液'

02 list1 = str1.split(' ') # 用空格分割字符串

03 print('您@的好友有：')

04 for item in list1:

05   print(item[1:])   # 输出每个好友名时，去掉@符号

 

**实例****04****：通过好友列表生成全部被****@****的好友**

01 list_friend = ['泸州老窖','郎酒','五粮液','剑南春','茅台'] # 好友列表

02 str_friend = ' @'.join(list_friend) # 用空格+@符号进行连接

03 at = '@'+str_friend # 由于使用join()方法合并时，第一个元素前不加分隔符，所以需要在前面加上@符号

04 print('\n您要@的好友：',at)

 

**5.1.5**  **检索字符串**

**1****．****count()****方法**

str1 ='@泸州老窖@郎酒@五粮液'

print('字符串“',str1,'”中包括', str1.count('@'),'个@符号')

**2****．****find()****方法**

str1 ='@泸州老窖 @郎酒 @五粮液'

print('字符串“',str1,'”中@符号首次出现的位置索引为: ', str1.find('@'))

 

str1 ='@泸州老窖 @郎酒 @五粮液'

print('字符串“',str1,'”中*符号首次出现的位置索引为: ', str1.find('*'))

**3****．****index()****方法**

str1 = '@泸州老窖 @郎酒 @五粮液'

print('字符串“',str1,'”中@符号首次出现的位置索引为: ',str1.index('@'))

 

str1 = '@泸州老窖 @郎酒 @五粮液'

print('字符串“',str1,'“中*符号首次出现的位置索引为: ',str1.index(*'))

**4****．****startswith()****方法**

str1 = '@泸州老窖 @郎酒 @五粮液'

print('字符串“',str1,'”中@符号首次出现的位置索引为: ',str1.index('@'))

 

**任务****5-2** **复原诗仙李白的《将进酒》**

01 list_verseS = []  #存储分割切片后的诗句

02 list_verseN = []  #存储修复后的诗句

03 verse_S = '@君不见，黄河之 水天上   来，奔流到 海 不复回$$$$。，高堂明镜  悲白发，朝如青丝暮成雪@。@人生得意须尽欢，莫使金樽空对月。，千金散 尽还 复来。*烹羊宰牛且为乐，会须一饮三百杯*。岑夫子，丹丘生，将进酒，杯莫停。与君歌一曲@@@@，请君为我倾耳听。钟鼓馔玉 不足贵，但  愿 长 醉不复醒&&。*&古来圣贤  皆寂寞，惟有 饮 者 留其名@。'  

04 print('球球搜索到的残缺诗原文：')

05 print(verse_S)

06 list_verseS = verse_S.split('。') #采用。号进行分割，得到list_verseS

07 for item in list_verseS:

08   mid_item = item.strip('@*&$')+'。'    #去除每句诗首尾的特殊符号@ . * & $

09  mid_item = mid_item.replace(" ", "")  #去除每句诗首尾的空格

10   mid_item = mid_item.replace("\t", "") #去除每句诗首尾的制表符

11   list_verseN.append(mid_item) #将处理后的诗句添加到list_verseN

12 list_verseN[6] = list_verseS[6][:5] + list_verseS[6][9:] + '。'  #截取、拼接字符串，去除第7行诗中的符号@@@

13 list_verseN[1] = '君不见' + list_verseN[1]  #拼接字符串，补全第2句诗

14 list_verseN[3] = '天生我材必有用' + list_verseN[3] #拼接字符串，补全第4句诗

\#向list_verseN添加3个新元素，补全整首诗

15 list_verseN.append('陈王昔时宴平乐，斗酒十千恣欢谑。')  #拼接字符串，补全第4句诗

16 list_verseN.append('主人何为言少钱，径须沽取对君酌。')

17 list_verseN.append('五花马，千金裘，呼儿将出换美酒，与尔同销万古愁。')

18 del list_verseN[9] #删除多余行

19 print('\n你已完成整首诗的修复工作！给力！整首诗全文如下：\n')

20 print('\n   《将进酒》  ——李白\n')   #输出整首完整诗

21 for item in list_verseN:

22   print(item)

5.2  字符串其它操作

**5.2.1**  **字母的大小写转换**

**1****．****lower()****方法**

str1 = 'www.lzlj.com'

print('原字符串:', str1)

print('新字符串:',str1.lower()) #全部转换为小写字母输出

**2****．****upper()****方法**

str1 = 'www.lzlj.com'

print('原字符串:', str1)

print('新字符串:',str1.upper()) #全部转换为大写字母输出

 

**实例****05****：不区分大小写验证会员名是否唯一**

01 username_1 = '|MaoTai|mt|mixianer|ZXM|ChenXiang|'  # 假设已经注册的会员名称保存在一个字符串中，以｜进行分隔

02 username_2 =username_1.lower() # 将会员名称字符串转换为全部小写

03 regname_1 = input('输入要注册的会员名称：')

04 regname_2 = '|' + regname_1.lower() + '|'# 将要注册的会员名称也转换为全部小写

05 if regname_2 in username_2:  # 判断输入的会员名称是否存在

06   print('会员名',regname_1,'已经存在！请更换用户名重新注册！')

07 else:

08   print('会员名',regname_1,'可以注册！')

 

**5.2.2**  **去除字符串中的空格和特殊字符**

**1****．****strip()****方法**

01 str1 = 'http://www.lzlj.com \t\n\r'

02 print('原字符串str1：' + str1 + '。')

03 print('字符串:'+ str1.strip() + '。') #去除字符串首尾的空格和特殊字符

04 str2 = '@泸州老窖.@.'

05 print('原字符串str2:' + str2 + '。')

06 print('字符串: ' + str2.strip('@.') +'。') #去除字符串首尾的“@”“."

**2****．****lstrip()****方法**

str1 = '\t http://www.lzlj.com'

print('原字符串str1：' + str1 +'。')

print('字符串: ' + str1.lstrip() + '。')#去除字符串左侧的空格和制表符

str2 = '@泸州老窖'

print('原字符串str2: ' + str2 + '。')

print('字符串: ' + str2.lstrip('@') +'。')  #去除字符串左侧的@

**3****．****rstrip()****方法**

01 str1 = 'http://www.lzlj.com\t'

02 print('\n原字符串str1：' + str1 +'。')

03 print('字符串: ' + str1.rstrip() + '。')#去除字符串右侧的空格和制表符

04 str2 = '泸州老窖，'

05 print('原字符串str2: ' + str2 + '。')

06 print('字符串: ' + str2.rstrip('，') +'。') #去除字符串右侧的逗号

 

**5.2.3**  **格式化字符串**

**1****．使用“％”操作符**

template = '编号: %09d\t公司名称: %s \t管网: http://www.%s.com'#定义模板

context1 = (1, '泸州老窖股份有限公司', 'lzlj')  #定义要转换的内容1

context2 = (2, '贵州茅台集团' ,'china-moutai' ) #定义要转换的内容2

print(template%context1)           #格式化输出

print(template%context2)           #格式化输出

**2****．使用字符串对象的****format()****方法**

template = '编号: {:0>9s}\t公司名称: {:s} \t官网: http://www.{:s}.com'#定义模板

context1 = template.format('1','泸州老窖' ,'lzlj') #转换内容1

context2 = template.format('2','贵州茅台','china-moutai')#转换内容2

print(context1)      #输出格式化后的字符串

print(context2)      #输出格式化后的字符串

 

**实例****06****：格式化不同的数值类型数据**

01 import math # 导入Python的数学模块

02 print('1251+3950的结果是（以货币形式显示）：￥{:,.2f}元'.format(1251+3950)) # 以货币形式显示

03 print('{0:.1f}用科学计数法表示：{0:E}'.format(120000.1)) # 用科学计数法表示

04 print('π取5位小数：{:.5f}'.format(math.pi)) # 输出小数点后五位

05 print('{0:d}的16进制结果是：{0:#x}'.format(100)) # 输出十六进制数

06 print('天才是由 {:.0%} 的灵感，加上 {:.0%} 的汗水 。'.format(0.01,0.99)) # 输出百分比，并且不带小数

 

**任务****5-3** **模拟顾客登录酒仙网功能**

01 import re # 导入Python的re模块

02 qq_pattern = r"(^\d{5,10}@qq\.com$)" #模式字符串，正确qq邮箱正则表达式

03 alc_pattern = r'(假酒)|(假货)|(假)|(劣质酒)|(勾兑)|(勾兑酒)' # 模式字符串，

04 print("\n========欢迎光临酒仙网========")

05 print("  操作指令：A 注册 B 购物 ")

06 end='y'

07 operC='n'

08 flag_l = 0   #是否注册过标志位，0表示未注册，1表示已完成注册

09 while end == 'y' or end == 'Y':

10   print("请您输入相关操作：", end="")

11   operC = input()

12   if str(operC) == 'A':   #选择进行注册操作

13     print("请输入你注册使用的qq邮箱：")

14     iInfo = input() # 保存输入的qq邮箱

15     match = re.match(qq_pattern, str(iInfo), re.I)  # 匹配字符串，不区分大小写

16     if match == None:  #不符合模式字符串，输入的qq邮箱不满足正则表达式

17       print("您输入的邮箱不符合qq邮箱注册要求！请重新申请注册！")

18       flag_l = 0  #未注册成功，标志位置为0

19     else:     #符合模式字符串，输入的qq邮箱满足正则表达式

20       flag_l = 1  #注册成功，标志位置为1

21        print("注册成功！")

22   elif str(operC) == 'B':  #选择进行购物操作

23    if flag_l == 0:  #标志位置为0，表示未完成注册

24       print("请您先完成新用户注册！")

25     elif flag_l == 1:  #标志位置为1，表示已完成注册

26       print("您已注册，可以开始购物！")

27       print("请输入您要搜索的商品关键字")

28       key_info = input() # 保存输入的关键字

29       match = re.search(alc_pattern, str(key_info))  #进行模式匹配

30       if match == None:  #匹配失败，不用输出温馨提示

31         print('显示出搜索的商品')

32       else:        #匹配成功，输出温馨提示

33         print('买真酒就上酒仙网！我们承诺假一赔十，请顾客放心购买！')

34   else:

35     print("无效指令")

36   print("继续相关操作吗(y/n)?",end="")

37   end = input()  #输入结束字符

38 print("操作结束!")

5.5  使用re模块实现正则表达式操作

**5.5.1**  **匹配字符串**

**1****．使用****match()****方法进行匹配**

import re

pattern = r'mr_\w+'        #模式字符串

string = 'MR_SHOP mr_shop'   #要匹配的字符串.

match = re.match(pattern,string,re.I) #匹配字符串，不区分大小写

print(match)             #输出匹配结果

string = '项目名称MR_SHOP mr_ shop'

match = re.match(pattern,string,re.I)  #匹配字符串，不区分大小写

print(match)   #输出匹配结果

 

import re

pattern = r'mr_\w+'           #模式字符串

string = 'MR_SHOP mr_shop'       #要匹配的字符串

match = re.match(pattern,string,re.I)  #匹配字符串，不区分大小写

print('匹配值的起始位置: ' , match.start())

print('匹配值的结束位置: ' , match.end())

print('匹配位置的元组: ', match.span())

print('要匹配的字符串:', match.string)

 

**实例****07****：验证输入的手机号码是否为中国移动的号码**

01 import re # 导入Python的re模块

02 pattern = r'(13[4-9]\d{8})|(15[01289]\d{8})$'

03 mobile = '13834222652'

04 match = re.match(pattern, mobile) # 进行模式匹配

05 if match == None: # 判断是否为None,为真表示匹配失败

06   print(mobile, '不是有效的中国移动手机号码。')

07 else:

08   print(mobile, '是有效的中国移动手机号码。')

09 mobile = '13334987690'

10 match = re.match(pattern, mobile) # 进行模式匹配

11 if match == None: # 判断是否为None,为真表示匹配失败

12   print(mobile, '不是有效的中国移动手机号码。')

13 else:

14   print(mobile, '是有效的中国移动手机号码。')

 

**2****．使用****search()****方法进行匹配**

import re

pattern = r'mr_\w+'  #模式字符串

string = 'MR_SHOP mr_shop' #要匹配的字符串

match = re.search(pattern,string,re.I) #搜索字符串，不区分大小写

print(match) #输出匹配结果

 

**实例****08****：验证是否出现危险字符**

01 import re # 导入Python的re模块

02 pattern = r'(黑客)|(网络攻击)|(监听)|(木马)|(病毒)|(僵尸)' # 模式字符串

03 about = '闰土是名技术宅男，空闲时间喜欢研究黑客技术，也会偶尔编写木马程序。'

04 match = re.search(pattern, about) # 进行模式匹配

05 if match == None: # 判断是否为None,为真表示匹配失败

06   print(about, '@ 安全！')

07 else:

08   print(about, '@ 出现了危险词汇！')

09 about = '球球是一名时尚美女，周末喜欢逛街购物、旅游出行。'

10 match = re.match(pattern, about) # 进行模式匹配

11 if match == None: # 判断是否为None,为真表示匹配失败

12   print(about, '@ 安全！')

13 else:

14   print(about, '@ 出现了危险词汇！')

 

**3****．使用****findall()****方法进行匹配**

import re

pattern = r'mr_\w+'  #模式字符串

string ='MR_SHOP mr_shop'  #要匹配的字符串

match = re.findall(pattern,string,re.I)  #搜索字符串，不区分大小写

print(match)  #输出匹配结果

string = '项目名称MR_SHOP mr_shop'

match = re.findall(pattern, string)  #搜索字符串，区分大小写

print(match)  #输出匹配结果

 

import re

pattern = r'[1-9]{1,3}(\.[0-9]{1,3}){3}'  #模式字符串

str1 = '127.0.0.1 192.168.2.66'  #要配置的字符串.

match = re.findall(pattern,str1)  #进行模式匹配

print(match)

 

import re

pattern = r'([1-9]{1,3}(\.[0-9]{1,3}){3})'  #模式字符串

str1 = '127.0.0.1 192.168.2.66'  #要配置的字符串

match = re.findall(pattern,str1) #进行模式匹配

for item in match:

  print(item[0])

 

**实例****09****：替换出现的危险字符**

01 import re # 导入Python的re模块

02 pattern = r'(黑客)|(网络攻击)|(监听)|(木马)|(病毒)|(僵尸)' # 模式字符串

03 about = '闰土是名技术宅男，空闲时间喜欢研究黑客技术，也会偶尔编写木马程序。\n'

04 sub = re.sub(pattern, '@_@', about) # 进行模式替换

05 print(sub)

06 about = '球球是一名时尚美女，周末喜欢逛街购物、旅游出行。'

07 sub = re.sub(pattern, '@_@', about) # 进行模式替换

08 print(sub)

 

 

**5.5.3**  **使用正则表达式分割字符串**

import re

pattern = r'[?|&]'  #定义分割符

url = 'https://www.lzlj.com/login.jsp?username="xm" &pwd="12789"'

result = re.split(pattern,url) #分割字符串

print(result)

 

**实例****10****：输出被****@****的好友名称（应用正则表达式）**

01 import re

02 str1 = '@泸州老窖 @贵州茅台 @五粮液 @剑南春 @衡水老白干'

03 pattern = r'\s*@'

04 list1 = re.split(pattern,str1) # 用空格和@或单独的@分割字符串

05 print('\n您@的好友有：')

06 for item in list1:

07   if item != "":   # 输出不为空的元素

08     print("\n",item)   # 输出每个好友名

 

项目6 实用的函数学习

**任务****6-1** **泸州老窖销售人员工资计算**

01 def salary(work_age, performance):

02   basic = 1000

03   work_age_salary = 100*work_age

04   tatal_salary = basic + work_age_salary + performance

05   return tatal_salary

07 ######################################

08 print("你的工资是：", salary(19, 5000)) ##调用函数

 

6.1 函数的创建和调用

**6.1.1** **创建一个函数**

01 def fn(*nums):

   '''

   函数的作用： 计算任意数值的总和

   函数的参数： *nums 会接受所有传进来的值，保存到一个元组中（装包）

   '''

02   print(nums,type(nums))   

03   result = 0  #定义一个变量，用来保存总和

04   for n in nums:

05     result += n

06     return result

07 help(fn)

 

01 def fn(*nums):

  '''

  函数的作用： 计算任意数值的总和

  函数的参数： *nums 会接受所有传进来的值，保存到一个元组中（装包）

  '''

02   print(nums,type(nums))

  \#定义一个变量，用来保存总和

03   result = 0

04   for n in nums:

05    result += n

06   print(result)

 

**6.1.2** **调用函数**

fn(1,2,3,4)

 

**任务****6-2** **酒价格计算**

01 laojiao1573 = 1000

02 maotai = 300

03 laojiao = 200

04 def price(person, x, y, z): #person代表购买人；x,y,z分别代表老窖1573，茅台，泸州老窖的瓶数

05   total = laojiao1573*x+maotai*y+laojiao*z

06   print(person,"您买的酒总价格为：",total)

07 price("李先生",10,20,30)

 

6.2 参数传递

**6.2.1** **了解形式参数和实际参数**

**1****．通过作用理解**

01 a = [1, 2, 3]

02 b = 1

\##############值传递###########

03 def changer_list(list1):

04   list1[0] += 1

05   return list1

06 print(changer_list(a))  

07 print(a)     #值传递a改变

\#############参数传递##########

08 def changer_integer(num):

09   num += 1

10   return num

11 print(changer_integer(b))

12 print(b)  # 参数传递b不变

 

**6.2.2** **位置参数**

**1****．数量必须与定义时一致**

price("李先生",10,20)

**2****．位置必须与定义时一致**

price(10, "李先生",20,30)

price("李先生",20,10,30)

 

**6.2.3** **关键字参数**

price(z=30,y=20,x=10,person="李先生")

 

**6.2.4** **为参数设置默认值**

01 laojiao1573 = 1000

02 maotai = 300

03 laojiao = 200

04 def price(x, y, z,person="客人"): #person代表购买人；x,y,z分别代表老窖1573，茅台，泸州老窖的瓶数

05 total = laojiao1573*x+maotai*y+laojiao*z

06 print(person,"您买的酒总价格为：",total)

price(10,20,30)  

 

def demo(obj=[]):

  print("obj的值：",obj)

  obj.append(1)

demo()

 

def demo(obj=None):

  if obj==None:

​    obj=[]

  print("obj的值：",obj)

  obj.append(1)

 

**6.2.5** **可变参数**

**1****．*****parameter**

def favorite_wine(*wine):

  print('我喜欢的酒有：')

  for i in wine:

​    print(i)

 

favorite_wine('泸州老窖','茅台','五粮液')

favorite_wine('泸州老窖','茅台')

favorite_wine('泸州老窖')

 

wine = ['泸州老窖','茅台','五粮液']

favorite_wine(*wine)

 

**任务****6-3** **多客户酒价格计算**

01 laojiao1573 = 1000

02 maotai = 300

03 laojiao = 200

04 def price_upgrade(*customer_imfo_list):

05   '''输入的数据为一个列表如[("李先生",10,20,30),("王小姐",2,2,2),("刘总",1,2,3)]

06   每个列表中可以有多个tuple,tuple中第一个位置代表客户名字，其他三个数字分别代表购买

07   老窖1573，茅台，泸州老窖的数量，输出每个客户买酒的总价格'''

08   for i in customer_imfo_list:

09     for j in i:

10       print("="*10+j[0]+"="*10)

11       total = laojiao1573*j[1]+maotai*j[2]+laojiao*j[3]

12       print(j[0],"您买酒的总价格为:",total)

13

14 #*****************************调用函数*****************************#

15 customers_info = [("李先生",10,20,30),("王小姐",2,2,2),("刘总",1,2,3)]

16 price_upgrade(customers_info)

 

def printinfo(**pram):

  print()

  for key, value in pram.items():

​    print("["+key+"]喜欢喝"+value)

printinfo(杜甫="茅台",李白="啤酒")

printinfo(李诞="泸州老窖",池子="哇哈哈",小美="果汁")

 

dict1 = {"李诞":"泸州老窖","池子":"哇哈哈","小美":"果汁"}

printinfo(**dict1)

6.3  返回值

return [value]

**任务****6-4** **多客户酒价格计算**

01 def settle_accounts(money):

02   '''功能：计算白酒总价并打折，输出应付金额

03   money是一个列表，里面包含购买的各种酒的价格'''

04   total = sum(money)

05   if 0<=total<500:

06     should_pay = total

07   elif 500<=total<1000:

08     should_pay = total*0.9

09   elif 1000<=total<2000:

10     should_pay = total*0.8

11   elif 2000<=total<3000:

12     should_pay = total*0.7

13   elif 3000<=total:

14     should_pay = total*0.6

15   should_pay = '{:.2f}'.format(should_pay) #保留两位小数

16   return total,should_pay

17 #****************调用函数*****************#

18 print('\n开始结算......')

19 money_list = []

20 while True:

21   input_money = float(input("输入商品金额（输入0表示输入完毕）："))

22   if int(input_money)==0:

23     break

24   else:

25     money_list.append(input_money)

26 money = settle_accounts(money_list)

27 print("合计金额:",money[0],"实付金额",money[1])

6.4  变量的作用域

**6.4.1** **局部变量**

def demo():

  message = "我喜欢喝泸州老窖"

  print("局部变量",message)

demo()

print(massage)

 

**6.4.2** **全局变量**

message = "我喜欢喝泸州老窖"

def demo():

  print("函数体内输出全局变量：",message)

demo()

print("函数体外输出全局变量：",message)

 

**任务****6-5** **一个酒鬼的梦**

01 reality = "喝二锅头配咸菜"

02 def dream():

03   elusion = "喝泸州老窖1573配烤鸭"

04   print("开始做梦...")

05   print(elusion)

06   print()

07   print("梦醒了")

08 dream()

09 print("现实是：",reality)

 

msg = "这是一个全局变量" #定义一个全局变量

print("函数体外：",msg)

def demo():

  msg = "这是一个局部变量" #定义一个局部变量

  print("函数体内：",msg)

 

demo()

print("函数体外：",msg)

 

glb = "这是一个全局变量" #定义一个全局变量

print("函数体外：",glb)

def change_global():

  global glb      #global关键字能够用在函数内改变全局变量

  glb = "这是一个全局变量，在函数中改变了" 

  print("函数体内：",glb)

change_global()

print("函数体外：",glb)

6.5  匿名函数

import math

def circlearea(r):

  result = math.pi*r*r   #pi为圆周率

  return result

r = 10

print("半径为",r,"的圆的面积为：",circlearea(r))

 

import math

r = 10

result = lambda r:math.pi*r*r #math.pi为圆周率

print("半径为",r,"的圆的面积为：",result(r))

 

项目7 掌握代码模块化方法

**任务****7-1** **计算白酒的重量模块设计**

01 def spiritMass(degree, vol):  #定义一个计算酒质量的函数，需要输入度数和体积

02 degree = degree/100 #degree为白酒度数，例如50表示白酒度数为50

03 print("此酒质为： "+str(0.8*degree*vol + 1*(1degree)*vol)) #vol代表体积单位默认为ml

04 spiritMass(65, 100)       #调用函数

 

**任务****7-2** **导入两个包括同名函数的白酒模块**

01 def thirty_eight():

02 # 返回泸州老窖3年38度酒的价格

03   return "泸州老窖3年38度酒的价格为200"

04 def fifty_two():

05 # 返回泸州老窖3年52度酒的价格

06   return "泸州老窖3年52度酒的价格为300"

07 if __name__ == '__main__':

08   thirty_eight = thirty_eight()

09   print(thirty_eight)

 

01 def thirty_eight():

02 # 返回茅台3年38度酒的价格

03  return "茅台3年38度酒的价格为100"

04 def fifty_two(degree):

05 # 返回泸州老窖3年52度酒的价格

06  if degree == 3:

07    return "茅台3年52度酒的价格为150"

08  if degree == 5:

09    return "茅台5年52度酒的价格为250"

10  else:

11    return ("请输入正确的酒藏年限，我们只有三年酒和五年酒")

12 if __name__ == '__main__':

13   price = fifty_two(4)

14   print(price)

7.2  自定义模块

**7.2.2** **使用****import****语句导入模块**

import spirit

spirit.spiritMass(65, 100) 

 

**7.2.3** **使用****from****…****import****语句导入模块**

from spirit import spiritMass

from spirit import spiritMass, water

from spirit import *

 

01 from laojiao import *

02 from maotai import *

03 if __name__ == '__main__':

04   print(fifty_two(3))

05   print(fifty_two())

 

01 import laojiao as L

02 import maotai as M 

03 if __name__ == '__main__':

04   print(M.fifty_two(3))

05   print(L.fifty_two()

 

**7.2.4** **模块搜索目录**

import sys

print(sys.path)   #打印出模块路径

**1****．临时添加**

import sys

sys.path.append("D:\code\python")

7.3  以主程序的形式执行

01 def thirty_eight():

02 # 返回泸州老窖3年38度酒的价格

03   return "泸州老窖3年38度酒的价格为200"

04 def fifty_two():

05 # 返回泸州老窖3年52度酒的价格

06   return "泸州老窖3年52度酒的价格为300"

07 print(thirty_eight())

08 print(fifty_two())

 

 import laojiao as L

 print(L.fifity_two())

import laojiao as L 

if __name__ == '__main__':

   print(L.fifty_two()

7.4  Python中的包

**2****．使用包**

import setting.size

width = 300     #宽度

height = 1000    #高度

import settings.size

if __name__ == '__main__':

  print("宽度: ", settings.size.width)

  print("高度: ", settings.size.height)

 

from settings import size

from settings import size

if __name__ == '__main__':

  print("宽度: ", size.width)

  print("高度: ", size.height)

 

from settings.size import width,height

from settings.size import width,height

if __name__ == '__main__':

  print("宽度: ", width)

  print("高度: ", height)

 

01 spirit = "泸州老窖"

02 beverage = "咖啡"

03 def change(s, b):

04   global spirit

05   spirit = s

06   global beverage

07   beverage = b 

08 def get_spirit():

09   global spirit

10   return spirit

11 def get_beverage():

12   global beverage

13   return beverage

 

01 from settings.drink import *

02

03 if __name__ == '__main__':

04 change("茅台","牛奶")

05 print(get_spirit())

 

**任务****7-3** **实时酒商抽奖**

01 import random

02 lottery_pool = ["泸州老窖","茅台","五粮液","国窖1573","郎酒"] #奖池

03 if __name__ == '__main__':

04   lottery = random.choice(lottery_pool)    #随机挑选一份奖励

05   print(lottery)

7.5  引用其它模块

**7.5.1** **导入和使用标准模块**

import random

 

import random

print(random.randint(0,10))

 

**7.5.2** **第三方模块的下载与安装**

pip <command> [modulename]

pip install numpy

项目8 异常处理及程序调试

**任务****8-1** **模拟幼儿园分苹果**

01 def division():

02   '''功能：分苹果'''

03   print("\n================分苹果=================\n")

04   apple = int(input("请输入苹果数量："))

05   children = int(input("请输入小朋友个数；"))

06   result = apple/children

07   remain = apple - result*children

08   if remain>0:

09     print(apple,"个苹果，平均分给",children,"个小朋友，每人分",

10     result,"个，剩下",remain,"个")

11   else:

12     print(apple,"个苹果，平均分给",children,"个小朋友，每人分",

13     result,"个")

14 if __name__ == "__main__":

15   division()

**任务****8-2** **模拟幼儿园分苹果（除数不为****0****）**

01 def division():

02   '''功能：分苹果'''

03   print("\n================分苹果=================\n")

04   apple = int(input("请输入苹果数量："))

05   children = int(input("请输入小朋友个数；"))

06   result = apple/children

07   remain = apple - result*children

08   if remain>0:

09     print(apple,"个苹果，平均分给",children,"个小朋友，每人分",

10     result,"个，剩下",remain,"个")

11   else:

12     print(apple,"个苹果，平均分给",children,"个小朋友，每人分",

13     result,"个")

14 if __name__ == "__main__":

15   try:

16     division()

17   except ZeroDivisionError:

18     print("\n出错!!!!!苹果不能够被0个小朋友分！")

8.2  异常处理语句

**8.2.1 try…except****语句**

try:

block1

except [exceptionname [as alias]]:

  block2

 

01 def division():

02   '''功能：分苹果'''

03   print("\n================分苹果=================\n")

04   apple = int(input("请输入苹果数量："))

05   children = int(input("请输入小朋友个数；"))

06   result = apple/children

07   remain = apple - result*children

08   if remain>0:

09     print(apple,"个苹果，平均分给",children,"个小朋友，每人分",

10     result,"个，剩下",remain,"个")

11   else:

12     print(apple,"个苹果，平均分给",children,"个小朋友，每人分",

13     result,"个")

14 if __name__ == "__main__":

15   try:

16     division()

17   except ZeroDivisionError:

18     print("\n出错!!!!!苹果不能够被0个小朋友分！")

19   except ValueError as e:

20     print("输入错误",e)

 

try:

  division()

except (ZeroDivisionError, ValueError) as e:

  print("输入错误",e)

 

**8.2.2 try…except…else****语句**

01 def division():

02   '''功能：分苹果'''

03   print("\n================分苹果=================\n")

04   apple = int(input("请输入苹果数量："))

05   children = int(input("请输入小朋友个数；"))

06   result = apple//children

07   remain = apple - result*children

08   if remain>0:

09     print(apple,"个苹果，平均分给",children,"个小朋友，每人分",

10     result,"个，剩下",remain,"个")

11   else:

12     print(apple,"个苹果，平均分给",children,"个小朋友，每人分",

13     result,"个")

14 if __name__ == "__main__":

15   try:

16     division()

17   except ZeroDivisionError:

18     print("\n出错!!!!!苹果不能够被0个小朋友分！")

19   except ValueError as e:

20     print("输入错误",e)

21   else:

22     print("分苹果完成！！")

 

**8.2.3  try…except…finally****语句**

try:

block1

except [exceptionname [as alias]]:

block2

finally:

  block3

 

01 def division():

02   '''功能：分苹果'''

03   print("\n================分苹果=================\n")

04   apple = int(input("请输入苹果数量："))

05   children = int(input("请输入小朋友个数；"))

06   result = apple//children

07   remain = apple - result*children

08   if remain>0:

09     print(apple,"个苹果，平均分给",children,"个小朋友，每人分",

10     result,"个，剩下",remain,"个")

11   else:

12     print(apple,"个苹果，平均分给",children,"个小朋友，每人分",

13     result,"个")

14 if __name__ == "__main__":

15   try:

16     division()

17   except ZeroDivisionError:

18     print("\n出错!!!!!苹果不能够被0个小朋友分！")

19   except ValueError as e:

20     print("输入错误",e)

21   else:

22     print("分苹果完成！！")

23   finally:

24     print("进行了一次分苹果操作")

 

**8.2.4** **使用****raise****语句抛出异常**

raise [ExceptionName[(reason)]]

 

**任务****8-3** **模拟幼儿园分苹果（使用****raise****抛出异常）**

01 def division():

02   '''功能：分苹果'''

03   print("\n================分苹果=================\n")

04   apple = int(input("请输入苹果数量："))

05   children = int(input("请输入小朋友个数；"))

06   if apple < children:

07     raise ValueError("苹果太少，不够分！！")

08   result = apple//children

09   remain = apple - result*children

10   if remain>0:

11     print(apple,"个苹果，平均分给",children,"个小朋友，每人分",

12     result,"个，剩下",remain,"个")

13   else:

14     print(apple,"个苹果，平均分给",children,"个小朋友，每人分",

15     result,"个")

16 if __name__ == "__main__":

17   try:

18     division()

19   except ZeroDivisionError:

20     print("\n出错!!!!!苹果不能够被0个小朋友分！")

21   except ValueError as e:

22     print("出错了",e)

8.3  程序调试

**8.3.2** **使用****assert****语句调试程序**

assert expression [,reason]

 

**任务****9-1** **为泸州驰援湖北的****89****名白衣勇士点赞**

01 import os    #导入os模块

02 import random  #导入随机模块

03 import string  #导入string模块

\#定义4个变量，存储用户点赞留言信息txt文件的本地路径

04 path1 = r'C:\output\ekdfs.txt'

05 path2 = r'C:\output\ekdzyy.txt'

06 path3 = r'C:\output\fybj.txt'

07 path4 = r'C:\output\qita.txt'

\#存储西南医科大学附属医院援鄂医护人员名单列表

08 西南医科大学附属医院 = ['兰四友','李 多','邹永胜','李 强','吕朝霞', '姜 敏' ,'邱少平' ,'兰黎艳','邢 婷', '王 倩', '钟起燕' ,'黄桂芳',

'杨 梅' ,'周 凯' ,'高晓岚', '梅松涛','邹林帆' ,'冯 磊', '伍 松', '温远淇','邓 俊' ,'刘 勇', '赵丽娜', '方蘅雯','潘永建' ,'刘西焱' ,'刘孝元' ,'贺 茜','曹 鑫' ,'牟清梦', '陈菊屏', '刘 英','徐 陶', '尹德锋' ,'李玉娟', '黄 敏','曾晓春', '郑 丽', '何雪梅' ,'张春梅','周虹羽' ,'吴宇超' ,'敬 宏' ,'李 舒','炜赵越' ,'刘春丽' ,'石春霞' ,'张 佳','熊 宣', '喻 敏']

\#存储西南医科大学附属中医医院援鄂医护人员名单列表

09 西南医科大学附属中医医院 = ['雷 波', '刘 操' ,'林 玲' ,'许志刚','罗 英' ,'高婧臻' ,'魏光蓉' ,'魏梦穗','蓝晓维' ,'郑雪梅' ,'周春梅', '李 婧','梁 敏' ,'涂连洁', '袁茂思', '胡 蓉','罗 婷' ,'李晓娟' ,'曾 理']

\#存储泸州市妇幼保健院医护人员名单列表

10 泸州市妇幼保健院 = ['何先夜' ,'王德明', '陈小兰' ,'李冬梅']

\#存储泸州市其它医院医护人员名单列表

11 古蔺县人民医院 = ['杨云满','余 倩']

12 古蔺县中医医院 = ['刘 铭','杨 莉']

13 叙永县人民医院 = ['刘 路', '龚太康']

14 叙永县中医医院 = ['余 洪', '杨 梅']

15 泸县中医医院 = ['胡 波', '胡 馨']

16 泸县第二人民医院 = ['何 春', '李国华']

17 合江县人民医院 = ['赵 艳', '吴中华']

18 合江县中医医院 = ['黄 胜', '汤 霞']

19 def OutputNameList(list): #定义函数，功能：输出列表对应的援鄂医院人员名单，参数：list

20   j = 0

21   for i in range(len(list)): # 遍历医护人员列表列表

22     print(list[i], end=' ')

23     j += 1

24     if j % 5 == 0: # 每行输出5个名字

25       print("\n")

26 def OutputQtNameList():  #定义函数，功能：打印输出泸州市其它区县医院驰援武汉白衣勇士全部名单，参数：无

27   print("泸州市其它区县医院驰援武汉医护人员共计16人。具体名单如下：")

28   print("古蔺县人民医院 ：杨云满 余 倩 共2人")

29   print("古蔺县中医医院：刘 铭 杨 莉 共2人")

30   print("叙永县人民医院：刘 路 龚太康 共2人")

31   print("叙永县中医医院：余 洪 杨 梅 共2人")

32   print("泸县中医医院：胡 波 胡 馨  共2人")

33   print("泸县第二人民医院：何 春 李国华 共2人")

34   print("合江县人民医院：赵 艳 吴中华 共2人")

35   print("合江县中医医院：黄 胜 汤 霞 共2人")

36 def SavaMessage(path,message): #定义函数，功能：将用户点赞留言写入到对应文件中，参数：path,message

37     file = open(path, "a") # 以追加模式打开文件

38     file.write("用户" + ran_strUserName + "的点赞留言：" + message + "\n") # 写入一条动态信息

39     file.close() # 关闭文件对象

40 if __name__ == '__main__':

41   print("========= 向泸州援鄂白衣勇士们致敬！！！！ ========\n")

42   print("  (*￣︶￣)春风十里，最美是战“役”的你(*￣︶￣)  ")

43   print("    欢迎您为泸州援鄂医护人员点赞留言  \n")

44   print("******没有从天而降的英雄，只有挺身而出的凡人*******\n")

45   ran_strUserName = ''.join(random.sample(string.ascii_letters + string.digits, 5)) # 为用户生成随机用户名

46   end = 'y'

47   operC = 'n'

48   while end == 'y' or end == 'Y':

49     print("医院序号")

50     print("1 西南医科大学附属医院 ")

51     print("2 西南医科大学附属中医医院 ")

52     print("3 泸州市妇幼保健院 ")

53     print("4 泸州市其它区县医院 ")

54     print("\n请输入您要点赞的医院序号：", end="")

55     operC = input()

56     if str(operC) == '1': # 选择1 西南医科大学附属医院

57       print("西南医科大学附属医院驰援湖北医护人员共计" + str(len(西南医科大学附属医院)) + "人。具体名单如下：")

58       OutputNameList(西南医科大学附属医院)

59       print("\n请输入您要点赞的留言：", end="")

60       message = input() # 保存用户输入的点赞留言

61       SavaMessage(path1, message)

62       print("您的留言已被记录在：" + "C:\output\ekdfs.txt") # 打印出用户点赞留言保存的本地路径

63       print("\n谢谢您为西南医科大学附属医院援鄂医护人员点赞！\n")

64     elif operC == '2': # 选择2 西南医科大学附属中医医院

65       print("西南医科大学附属中医医院驰援武汉医护人员共计" + str(len(西南医科大学附属中医医院)) + "人。具体名单如下：")

66       OutputNameList(西南医科大学附属中医医院)

67       print("\n请输入您要点赞的留言：", end="")

68       message = input() # 保存用户输入的点赞留言

69       SavaMessage(path2, message)

70       print("您的留言已被记录在：" + "C:\output\ekdzyy.txt") # 打印出用户点赞留言保存的本地路径

71       print("\n谢谢您为西南医科大学附属中医医院医护人员点赞！\n")

72     elif operC == '3': # 选择3 泸州市妇幼保健院

73       print("泸州市妇幼保健院驰援武汉医护人员共计" + str(len(泸州市妇幼保健院)) + "人。具体名单如下：")

74       OutputNameList(泸州市妇幼保健院)

75       print("\n请输入您要点赞的留言：", end="")

76       message = input() # 保存用户输入的点赞留言

77       SavaMessage(path3, message)

78       print("您的留言已被记录在：" + "C:\output\\fybj.txt") # 打印出用户点赞留言保存的本地路径

79       print("\n谢谢您为泸州市妇幼保健院援鄂医护人员点赞！\n")

80     elif operC == '4': # 选择4 泸州市其它区县医院

81       OutputQtNameList()

82       print("\n请输入您要点赞的留言：", end="")

83       message = input() # 保存输入的点赞留言

84       SavaMessage(path4, message)

85       print("您的留言已被记录在：" + "C:\output\qita.txt") # 打印出用户点赞留言保存的本地路径

86       print("\n谢谢您为泸州市其它区县医院援鄂医护人员点赞！\n")

87     print("继续相关操作吗(y/n)?", end="")

88     end = input() # 输入结束字符

89   print("操作结束！")

9.1 基本文件操作

**9.1.1** **创建和打开文件**

file = open(filename[,mode[,buffering]])

 

**实例****01****：创建并打开酒城新报最新动态栏目的文件**

01 print("\n","**********","酒城新报","**********")

02 file = open('message.txt','w')  # 创建或打开保存酒城新报最新动态信息的文件

03 print("\n 新闻……\n")

**2****．以二进制形式打开文件**

file = open( 'Alcohol.png','rb')  #以二进制方式打开图片文件

print(file)  #输出创建的对象

 

**9.1.2** **关闭文件**

file.close()  #关闭文件对象

 

**9.1.3** **打开文件时使用****with****语句**

print("\n","**********","酒城新报","**********")

with open('message.txt','w') as file: # 创建或打开保存酒城新报最新动态信息的文件

  pass

print("\n 新闻……\n")

 

**实例****02****：向酒城新报的最新动态文件写入一条信息**

01 print("\n","**********","酒城新报","**********")

02 file = open('message.txt','w')  # 创建或打开保存酒城新报最新动态信息的文件

\# 写入一条动态信息

03 file.write("泸州援助湖北的89名白衣勇士全部平安归来。\n")

04 print("\n 写入了一条新动态……\n")

05 file.close()  # 关闭文件对象

 

01 print("\n","**********","酒城新报","**********")

02 file = open('message.txt','a')  # 创建或打开保存酒城新报最新动态信息的文件

\# 追加一条动态信息

03 file.write("四川首家酒类产业计量测试中心在泸州市成立。\n")

04 print("\n 追加了一条动态……\n")

05 file.close()  # 关闭文件对象

 

 

**9.1.5** **读取文件**

**1****．读取指定字符**

with open('message.txt','r') as file:  #打开文件

  string = file. read(10) #读取前10个字符

  print(string)

 

with open('message.txt' ,'r') as file:  #打开文件

  file. seek(14)   #移动文件指针到新的位置

  string = file.read(13) #读取13个字符

  print(string)

 

**实例****03****：显示酒城新报最新动态栏目内容**

01 print("\n","="*20,"酒城新报最新动态栏目内容","="*20,"\n")

02 with open('message.txt','r') as file:  # 打开保存酒城新报最新动态栏目内容的文件

03   message = file.read()  # 读取全部动态信息

04   print(message)      # 输出动态信息

05   print("\n","="*28,"over","="*28,"\n")

**实例****04****：逐行显示酒城新报最新动态栏目的内容**

01 print("\n","="*20,"酒城新报最新动态栏目内容","="*20,"\n")

02 with open('message.txt','r') as file: # 打开保存酒城新报最新动态栏目内容的文件

03   number = 0  # 记录行号

04   while True:

05     number += 1

06     line = file.readline()

07     if line =='':

08       break  # 跳出循环

09     print(number,line,end= "\n") # 输出一行内容

10 print("\n","="*28,"over","="*28,"\n")

**3****．读取全部行**

01 print("\n","="*20,"酒城新报最新动态栏目内容","="*20,"\n")

02 with open('message.txt','r') as file: # 打开保存酒城新报最新动态栏目内容的文件

03   message = file.readlines()#读取全部动态信息

04   print(message) # 输出动态信息

05   print("\n","="*28,"over","="*28,"\n")

 

01 print("\n","="*20,"酒城新报最新动态栏目内容","="*20,"\n")

02 with open('message.txt','r') as file: # 打开保存酒城新报最新动态栏目内容的文件

03   messageall = file.readlines()

04   for message in messageall:

05     print(message)

06 print("\n","="*28,"over","="*28,"\n")

 

**任务****9-2** **实现白酒资料分类整理功能**

01 import os,shutil  #导入os模块和shutil模块

02 def goThroughFiles(path):  #遍历目录函数 参数: path为原始路径

03   print("【", path, "】 目录下包括的文件和目录：")

04   for root, dirs, files in os.walk(path, topdown=True): # 遍历指定目录

05     for name in dirs: # 循环输出遍历到的子目录

06       print("●", os.path.join(root, name))

07     for name in files: # 循环输出遍历到的文件

08       print("◎", os.path.join(root, name))

09 def crateFiles(path):   #创建目录函数 参数: path为要创建目录路径

10   if not os.path.exists(path): # 判断目录是否存在

11     os.mkdir(path) # 创建目录

12     print("目录创建成功! ")

13     print("新创建的目录路径为：" + path)

14   else:

15     print("该目录已经存在! ")

16 def moveFiles(path, new_path,dir_type): # 移动文件函数 参数: path为原始路径，new_path是移动到的目标目录，dir_type为数据类型

17   for root, dirs, files in os.walk(path):  #取得该文件夹下的所有文件

18     for i in range(len(files)):

19       if dir_type == 'Pic' : #数据类型为图片

20         if (files[i][-3:] == 'jpg') or (files[i][-3:] == 'png') or (files[i][-3:] == 'JPG'):

21           file_path = root + '/' + files[i]

22           new_file_path = new_path + '/' + files[i]

23           shutil.move(file_path, new_file_path)  #将每张图片依次移动到新目录下

24       elif dir_type == 'Word':  #数据类型为文档

25         if(files[i][-3:] == 'doc') or (files[i][-4:] == 'docx') or (files[i][-3:] == 'wps'):

26           file_path = root + '/' + files[i]

27           new_file_path = new_path + '/' + files[i]

28           shutil.move(file_path, new_file_path) #将每个文档依次移动到新目录下

29 if __name__ == '__main__':  #主函数

30   print("====白酒资料分类整理====")

31   path = 'D:\\Alcohol'

32   print("遍历目录：")

33   goThroughFiles(path) #遍历目录

34   Pic_path = 'D:\\Alcohol\\Pic'

35   Word_path = 'D:\\Alcohol\\Word'

36   print("分别创建两个分类子目录 —— Pic和Word：")

37   crateFiles(Pic_path)  #创建新目录

38   crateFiles(Word_path) #创建新目录

39   print("将所有图片移动到子目录Pic文件夹中：")

40   moveFiles('D:\\Alcohol', Pic_path,'Pic')  #移动图片

41   print("successful! 已完成移动！")

42   print("将所有文档移动到子目录Word文件夹中：")

43   moveFiles('D:\\Alcohol', Word_path,'Word') #移动文档

44   print("successful! 已完成移动！")

45   print("整理结束后，再次遍历目录：")

46   goThroughFiles(path)  #遍历目录

9.2 目录操作

**9.2.1 os****和****os.path****语句**

import os

 

**9.2.2** **路径**

**1****．相对路径**

import os

print(os. getcwd())  #输出当前目录

 

with open("demo/message.txt" ) as file:  #通过相对路径打开文件

pass

**2****．绝对路径**

import os

print(os.path.abspath(r"demo\message.txt"))  #获取绝对路径

**3****．拼接路径**

import os

print(os.path.join("E:\example" ,"demo\message.txt" ))#拼接字符串

 

**9.2.3** **判断目录是否存在**

import os

print(os.path.exists("C:\\demo")) #判断目录是否存在

 

 

 

**9.2.4** **创建目录**

**1****．创建一级目录**

import os

print(os.mkdir("C:\\demo")) #创建C:\demo目录

 

import os

path = "C:\\demo"  #指定要创建的目录

if not os.path. exists(path):  #判断目录是否存在

  os. mkdir(path)  #创建目录

  print("目录创建成功! ")

else:

print("该目录已经存在! ")

 

import os  #导入标准模块os

def mkdir(path):  #定义递归创建目录的函数

  if not os. path. isdir(path):  #判断是否为有效路径

​    mkdir(os. path. split(path)[0])  #递归调用

  else:  #如果目录存在，直接返回

​    return

  os.mkdir(path) #创建目录

mkdir("D:/mr/test/demo" )  #调用mkdir递归函数

**2****．创建多级目录**

import os

os.makedirs("C:\\demo\\test\\dir\\mr")#创建C:\demo\test\dir\mr目录

 

**9.2.5** **删除目录**

import os

os.rmdir("C:\\demo\\test\\dir\\mr") #删除C:\demo\test\dir\mr目录

 

import os

path = "C:\\demo\\test\\dir\\mr"  #指定要创建的目录

if os. path. exists (path):  #判断目录是否存在

  os.rmdir("C:\\demo\\test\\dir\\mr")  #删除目录

  print("目录删除成功! ")

else:

print("该目录不存在! ")

 

import shutil

shutil.rmtree( "C:\\demo\\test" )  #删除C:\demo目录下的test子目录及其内容

**9.2.6** **遍历目录**

import os  #导入os模块

tuples = os.walk("E:\\example")#遍历"E:\example"目 录

for tup1e1 in tuples :  #通过for循环输出遍历结果

  print(tup1e1 ,"\n")  #输出每一级目录的元组

 

**实例****05****：遍历指定目录**

01 import os  # 导入os模块

02 path = "E:\\example"    # 指定要遍历的根目录

03 print("【",path,"】 目录下包括的文件和目录：")

04 for root, dirs, files in os.walk(path, topdown=True):#遍历指定目录

05   for name in dirs:      # 循环输出遍历到的子目录

06     print("●",os.path.join(root, name))

07   for name in files:      # 循环输出遍历到的文件

08     print("◎",os.path.join(root, name))

9.3 高级文件操作

**9.3.1** **删除文件**

import os  #导入os模块

os.remove('test.txt' )  #删除当前工作目录下的test.txt文件

 

import os  #导入os模块

path = "test.txt"  #要删除的文件

if os.path.exists(path): #判断文件是否存在

  os.remove(path)   #删除文件

  print("文件删除完毕! ")

else:

print("文件不存在！")

 

**9.3.2** **重命名文件和目录**

import os  #导入os模块

src = r'C:\output\dir\test.txt' #要重命名的文件

dst = r'C:\output\dir\message.txt' #重命名后的文件

if os.path.exists(src):  #判断文件是否存在

  os.rename(src, dst)  #重命名文件

  print("文件重命名完毕! ")

else:

  print("文件不存在! ")

 

import os   #导入os模块

src = "demo"  #重命名的当前目录下的demo

dst = "test"  #重命名为test

if os.path.exists(src):  #判断目录是否存在

  os. rename(src,dst)  #重命名目录

  print("目录重命名完毕! ")

else:

  print("目录不存在! ")

 

import os   #导入os模块

src = r"C:\output\dir\demo"  #重命名的demo上一级目录dir

dst = r"C:\output\test\demo"  #重命名为test

if os.path.exists(src):  #判断目录是否存在

  os. rename(src,dst)  #重命名目录

  print("目录重命名完毕! ")

else:

print("目录不存在! ")

 

**实例****06****：获取文件基本信息**

01 import os  # 导入os模块

02 fileinfo = os.stat("message.txt") # 获取文件的基本信息

03 print("文件完整路径：", os.path.abspath("message.txt")) # 获取文件的完整数路径

\# 输出文件的基本信息

04 print("索引号：",fileinfo.st_ino)

05 print("设备名：",fileinfo.st_dev)

06 print("文件大小：",fileinfo.st_size," 字节")

07 print("最后一次访问时间：",fileinfo.st_atime)

08 print("最后一次修改时间：",fileinfo.st_mtime)

09 print("最后一次状态变化时间：",fileinfo.st_ctime)

 

01 import os  # 导入os模块

02 def formatTime(longtime):

  '''格式化日期时间的函数

​    longtime：要格式化的时间

  '''

03   import time # 导入时间模块

04   return time.strftime('%Y-%m-%d %H:%M:%S',time.localtime(longtime))

05 def formatByte(number):

  '''格式化日期时间的函数

​    number：要格式化的字节数

  '''

06   for (scale,label) in [(1024*1024*1024,"GB"),(1024*1024,"MB"),(1024,"KB")]:

07     if number>= scale:  # 如果文件大小大于等于1KB

08       return "%.2f %s" %(number*1.0/scale,label)

09     elif number == 1: # 如果文件大小为1字节

10       return "1 字节"

11     else:  # 处理小于1KB的情况

12       byte = "%.2f" % (number or 0)

13   return (byte[:-3] if byte.endswith('.00') else byte)+" 字节" # 去掉结尾的.00，并且加上单位“字节”

14 if __name__ == '__main__':

15   fileinfo = os.stat("message.txt") # 获取文件的基本信息

16   print("文件完整路径：", os.path.abspath("message.txt")) # 获取文件的完整数路径

  \# 输出文件的基本信息

17   print("索引号：",fileinfo.st_ino)

18   print("设备名：",fileinfo.st_dev)

19   print("文件大小：",formatByte(fileinfo.st_size))

20   print("最后一次访问时间：",formatTime(fileinfo.st_atime))

21   print("最后一次修改时间：",formatTime(fileinfo.st_mtime))

22   print("最后一次状态变化时间：",formatTime(fileinfo.st_ctime))