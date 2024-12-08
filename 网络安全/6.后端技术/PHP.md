我们来个登录页面，简单感受一下前后端的交互。

```php
 <!DOCTYPE html> 
<html>
	<head>
		<meta charset="UTF-8">
		<title>论坛</title>
 	</head>
 	<body>
 		<?php 
            $uname = $_GET['username'];
            $pwd = $_GET['password'];
                if ($uname == 'jaden'){
                 echo "<h1>欢迎 $uname 回来</h1>";
                 echo "<h2>您的密码为: $pwd</h2>";
                }else{
                     echo "<h1>sorry,用户名或者密码不正确！</h1>";
                };
             ?>
 		</body>
 </html>
```

ogin.html

```html
 <!DOCTYPE html> 
<html>
	<head>
         <meta charset="UTF-8">
         <title>jaden小站</title>
    </head>
    <body>
 		<form action='checklogin.php' method='get'>
                用户名： <input type='text' name='username'>
                密码： <input type='password' name='password'>
                <input type='submit'>
 		</form>
 	</body>
</html>
```

# 1、php简介

后端编程语言有很多，前端语言基本就是：html、css、js，js还能算是个编程语言。 

很多网站后端都是php开发的，比如百度，51cto学堂等等 

PHP:   Hypertext Preprocessor  (超文本预处理器) 

php的作用就是生成动态的html文档

# 2.php版本

```
php 1.0  1995
php 2.0  1995
php 3.0   ~  免杀
php 4.0  2000
php 5.0  2004    5.0-5.6
php 7.0  2015   7.0-7.4
php 8.0  2020

市面上主流的还是5.x和7.x。
```

# 3、安装php的运行环境

```
phpstudy的安装，关闭windows更新功能和防病毒功能。
```

![image-20240530215534209](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240530215534209.png)

# 4、php基础语法

```php
<?php 
echo "Hello guy!<br>";  //echo 在html中输出内容用的
echo "I miss you!";
?>
```

#  5、php的变量和常量

变量：可变化的值   

常量：不变的值  圆周率：3.1415  

```
#PHP 中的变量用一个美元符号后面跟变量名来表示。变量名是区分大小写的。 
#定义一个变量，前面不加$符号，那么就是普通字符
$num = 3.1415;
$a = 5;
$b = 6;
echo $a + $b;
$hello world

# 定义常量：
# 常量的名一般都是大写字母
方式1：define('常量名', '常量值');  例如：define('WebSite', 'php中文网');
方式2：const 常量名 = 常量值;  例如：const FOO = 'BAR';
方式2不能用在if判断中。
```

### 变量的命名规则

```
					$中 = 100 
1.一个有效的变量名由字母或者下划线开头，后面跟上任意数量的字母，数字，或者下划线。 
2.变量名不能以数字开头 
3.变量名不要出现中文
4.变量名不要出现非下划线的其他特殊符号  
5.变量名建议使用小写字母
```

#### 不带符号，单引号，双引号的区别

```php
<?php
 header("Content-Type: text/html; charset=utf-8");  // 在响应头中添加了content-type: utf-8，header()是php提供的加工响应头键值对的
// header("jaden: 666"); 

 $name = 'kobe';
 echo $name;
 echo '最喜欢的NBA球星是'.$name.'<br>';  //变量不加符号，遇到字符串拼接，需要加.连接
 echo '最喜欢的NBA球星是$name<br>';      //单引号，不解析变量，原样输出
echo "最喜欢的NBA球星是$name<br>";		//双引号，解析变量
?>
```

#### 小练习：使用前后端交互实现的计算器

#### 后端：

```html
<!DOCTYPE html> 
<html>
	<head>	
        <meta charset="UTF-8">
        <title>jaden小站</title>
	</head>
	<body>
		<div>
            <?php 
                $num1 = $_GET['num1'];
                $num2 = $_GET['num2'];
                $add = $num1 + $num2;
                $jian = $num1 - $num2;
                echo "加法计算结果：$add"."<br>";
                echo "减法计算结果：$jian"."<br>";
            ?>
 		</div>
 	</body>
 </html>
```

#### 前端：

```html
<!DOCTYPE html> 
<html>
	<head>
        <meta charset="UTF-8">
        <title>jaden小站</title>
	</head>
	<body>
		<div>
			<div>欢迎使用计算器</div>
			<form action='calc.php' method='get'>
                    数字1:<input type='text' name='num1'>
                    数字2:<input type='text' name='num2'>
				  <input type='submit'>
			</form>
		</div>
	</body>
</html>
```

#  6、php的数据类型

```php
布尔类型 0 非0 |false true  # 判断条件的结果都是布尔值 

整型   整数 -99999 +99999

浮点型 小数 -1.9 3.25 3.00005

字符串 'hello'  "hello"

数组  array，  例如：$d = array('a', 1,'c',array(1,2,3)); #数组是容器类型的数据，可以
存放各种类型的基础数据
        $d = array('a', 1,'c',array(1,2,3));
        echo $d; //会报错，因为echo是用来输出字符串类型数据的。
        echo $d[0];  # 数组类型是可以通过索引取值的，索引是从0开始的。

对象  object  # 这个需要学到类之后才能看到

资源类型 Resource  # 文件等资源数据

NULL  空  # $a = null; 提前定义，但是不想赋值的时候就可以这样用

    
   						查看变量对应值的类型：
1.使用“gettype(传入一个变量var)”来显示变量var的类型;  只会显示类型
2.使用“var_dump(传入一个变量var)”来显示变量var的类型;  会显示具体内容
						打印array：
$a = array(1,2,3);
print_r($a);
```

#  7、php的运算符

## 算数运算符

![image-20240530220825902](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240530220825902.png)

存在优先级  （乘除 > 加减），提升优先级就加括号。

### 示例

```php
<?php 
    $x=10; 
    $y=6;
    echo ($x + $y); // 输出16
    echo '<br>';  // 换行
    
    echo ($x - $y); // 输出4
    echo '<br>';  // 换行
    
    echo ($x * $y); // 输出60
    echo '<br>';  // 换行
    
    echo ($x / $y); // 输出1.6666666666667
    echo '<br>';  // 换行
    
    echo ($x % $y); // 输出4
    echo '<br>';  // 换行-2
    
    echo -$x;
    echo $x.$y //输出106
?>
```

## 自增自减

![image-20240530221015181](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240530221015181.png)

### 示例

```php
<?php
$x=10; 
echo ++$x; // 输出11  先加1，再执行输出逻辑
 
$y=10; 
echo $y++; // 输出10  先执行输出逻辑，再加1
echo $y;

$z=5;
echo --$z; // 输出4
 
$i=5;
echo $i--; // 输出5
 ?>
```

## 比较运算符

![image-20240530221159645](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240530221159645.png)

 **==    ===的区别**

```php
<?php
    $a = '10'; // 一个等号是赋值的意思
    $b = 10;
    if ($a === $b){ // 强等于，比较数据类型
    // if ($a == $b){  // 弱等于，不比较数据类型
    	echo '这俩人相等';
    	}else{
    		echo '不相等' ;
    	};
?>
```

### 示例

```php
<?php
    $x=100; 
    $y="100";

    var_dump($x == $y);  //输出bool true
    echo "<br>";
    var_dump($x === $y);  //输出bool false
    echo "<br>";
    var_dump($x != $y);  //输出bool false
    echo "<br>";
    var_dump($x !== $y);  //输出bool true
    echo "<br>";

    $a=50;
    $b=90;

    var_dump($a > $b);  //输出bool false
    echo "<br>";
    var_dump($a < $b);  //输出bool true
?>
```

## 赋值运算符

![image-20240530221529823](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240530221529823.png)

### 示例

```php
<?php 
    $x=10; 
    echo $x; // 输出10
    
    $y=20; 
    $y +=100; // $y=$y+100
    echo $y; // 输出120
    
    $z=50;
    $z -= 25; //$z=$z-25
    echo $z; // 输出25
    
    $i=5;
    $i *= 6;
    echo $i; // 输出30
    
    $j=10;
    $j /= 5;
    echo $j; // 输出2
    
    $k=15;
    $k %= 4;
    echo $k; // 输出3
    
    $a = 10;
    $b = 3;
    $c = $a.$b;
    echo $c.'<br>'; // 103
    echo var_dump($c); // string
?>

```



## 逻辑运算符

![image-20240530221713759](C:/Users/ling/AppData/Roaming/Typora/typora-user-images/image-20240530221713759.png)

### 示例

```php
 <?php
    $x = true;
    $y = false;
    //逻辑与（并且），要求两个都为true才执行真区间，所以代码中执行假区间
    if($x && $y){
     		echo '执行了真区间';
        }else{
     		echo '执行了假区间';
        }
?>
```

## 三元运算

也叫做三目运算

**语法**：

```
判断条件?真的处理：假的处理

判断如果为true，那么执行真处理，也就是:冒号前面的代码会执行，否则:冒号后面的执行，和if..else差不多，不过更简洁一些，但是不能执行多条件判断
```

### 示例：

```php
<?php
     $x = true;
     $x ? $y = 5 : $y = 6;
     //输出5
     echo  $y;
 ?>
```

#  8、php的流程控制

## if

```php
if()
{

}
```



```php
<?php
     header("Content-Type: text/html; charset=utf-8");
     $a=rand(1,10);
     
     if ($a >5){
     	echo "随机点数比较大";
     }
     echo "<br>";
     echo "当前的点数是".$a;
 ?>
```

## else

```
if()
{

}
else{

}
```



```php
<?php
     header("Content-Type: text/html; charset=utf-8");
     $user = $_POST["username"];
     $pass = $_POST["password"];
     if ($user =='admin' and $pass =='123456' ){
     	echo "登录成功";
     }else {
     	echo "登录失败";
     }
 ?>
```

## elseif/else if

```php
if()
{
    
}
elseif{
    
}
elseif{
    
}
```

```php
<?php
    // A B C 其他
    $jixiao='F';

    if ($jixiao == 'A'){
    	echo "发放1.2倍薪资";
    } elseif ( $jixiao =='B'){
    	echo "正常发放薪资";
    }else if($jixiao == 'C'){
    	echo "发放90%薪资";
    }else {
    	echo "发放80%薪资";
     }
 ?>
```

## while

条件不成立，**一次都不执行**

```php
while()
{

}
```

```php
<?php
     $i = 1;
     while ($i <= 10) {
    	 $i++;
     	echo '哈哈'.$i.'次'; 
    }
 ?>
```

## do-while

条件不成立，**也会执行一次**

```php
do{
    
}while()
```

```php
<?php
     $i = 0;
     do {
     	echo $i;
     } while ($i > 0);
 ?> 
```

## for

**有限循环**

```php
for(初始值;条件;自增或自减)
{

}
```

```php
#$i=1初始值，$i<=10 条件，$i++每次加1
for ($i = 1; $i <= 10; $i++) {
	echo $i;
}
```

## foreach

**遍历数组**

```php
# 属组的索引默认是从0开始的数字，也可以自行指定索引
$cars=array("特等奖"=>"布加迪","一等奖"=>"捷豹" ,"二等奖"=>"法拉利" ,"三等奖"=>"玛莎拉蒂");
foreach ($cars as $key => $value) {
	echo "<tr><td>$key</td><td>$value</td></tr>";
 }
```

##  break 打断

**打断循环；结束循环**

```php
$cars=array("特等奖"=>"布加迪","一等奖"=>"捷豹" ,"二等奖"=>"法拉利" ,"三等奖"=>"玛莎拉蒂" ,"四等奖"=>"迈凯伦");
 foreach ($cars as $key => $value) {
 if ( $key == '三等奖' ){
 		break;
 } else {
 		echo $key."是".$value."<br>";
 	}
}
```

## continue 继续

**跳出本轮，开始下一轮**

```php
$cars=array("特等奖"=>"布加迪","一等奖"=>"捷豹" ,"二等奖"=>"法拉利" ,"三等奖"=>"玛莎拉蒂" ,"四等奖"=>"迈凯伦");
foreach ($cars as $key => $value) {
    if ( $key == '三等奖' ){
    	continue;
    } else {
    	echo $key."是".$value."<br>";
    }
}
```

##  switch

```php
switch()
{
    case 变量n:执行语句n;break;
    case 变量n:执行语句n;break;
    case 变量n:执行语句n;break;
    default:执行语句;break;
}
```

```php
$a=5;
$b=10; $c=4;  
switch ($c) {
    case 1:echo "$a + $b = ".($a+$b)."<br>";break;
    case 2:echo "$a - $b = ".($a-$b)."<br>";break;
    case 3:echo "$a * $b = ".($a*$b)."<br>";break;
    case 4:echo "$a / $b = ".($a/$b)."<br>";break;
    default: // 条件都不成立时执行
            echo '原来啥也不是';
            break; 
}
```

#  9、php的函数

### 1).函数的介绍

```
函数的英文叫作：function，而function的解释项中有另外一个含义：功能，函数就是功能，比如我们发微信，可能发微信这个后台代码逻辑就是一个函数，将整体的发微信的逻辑代码封装到了函数中，调用并执行这个函数，就能够实现发微信的动作。
```

### 2).语法

```php
//不支持传参的函数
function welcom(){
	echo "欢迎光临!";
}

//调用函数
welcom();

<?php
header("Content-Type: text/html; charset=utf-8");  // 在响应头中添加了content-type: utf-8，header()是php提供的加工响应头键值对的

echo '做一下加法计算！'.'<br>';
// 函数声明，提前定义了两个形式参数：$a, $b
function add($a, $b){
     //$a = 2;
     //$b = 3;
     $c = $a + $b;
 	echo '加法计算结果为：'.$c.'<br>';
 }

// 函数调用：  3，4实际参数
add(3,4);

echo '计算结束..'.'<br>';
?>

//返回值
// 函数声明，提前定义了两个形式参数：$a, $b
function add($a, $b){
    //$a = 2;
    //$b = 3;
    $c = $a + $b;
    // echo '加法计算结果为：'.$c.'<br>';
    return $c;
}

// 函数调用：  3，4实际参数
$ret = add(3,4);
echo $ret.'<br>';

echo '计算结束..'.'<br>';	
```

### 3).内置函数

#### 										文件包含的函数

![image-20240530223755329](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240530223755329.png)

#### 										数学常用函数

我们简单学几个即可：abs()、ceil()、floor()、round()、max()、min()、rand()。

![image-20240530223911385](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240530223911385.png)

![image-20240530223931102](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240530223931102.png)

#### 字符串常用函数

```
echo  __FILE__; 打印当前文件的绝对路径。下面函数大家学习一下我标着*** 的即可。
```

![image-20240530224048152](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240530224048152.png)

![image-20240530224107845](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240530224107845.png)

![image-20240530224124220](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240530224124220.png)

![image-20240530224140244](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240530224140244.png)

![image-20240530224152314](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240530224152314.png)

![image-20240530224222553](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240530224222553.png)

![image-20240530224250034](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240530224250034.png)

![image-20240530224301935](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240530224301935.png)

#### 时间日期函数

```
中国的时区在东八区。时间相关函数：date()、getdate()、time()，我们就说一下这三个吧。
```

```php
// 时区的报错，修改php.ini，date.timezone = Asia/Shanghai
$d = date('Ymd H:i:s');  # 格式化时间日期的。
$d = date('Ymd H:i:s', 1661910865); # 通过某个时间戳来格式化时间
$t = time();  # 当前时间戳

<?php 
    $mytime = getdate(); // 得到当前时间日期的一个属组
    // $mytime = getdate(1661910865);
    echo "年 :".$mytime['year']."<br>";
    echo "月 :".$mytime['mon']."<br>";
    echo "日 :".$mytime['mday']."<br>";
    echo "时 :".$mytime['hours']."<br>";
    echo "分 :".$mytime['minutes']."<br>";
    echo "秒 :".$mytime['seconds']."<br>";
    echo "一个小时中的第几钟 :".$mytime['minutes']."<br>";
    echo "这是一分钟的第几秒 :".$mytime['seconds']."<br>";
    echo "星期名称 :".$mytime['weekday']."<br>";
    echo "月份名称 :".$mytime['month']."<br>";
    echo "时间戳   :".$mytime[0]."<br>";
 ?>
```

#### 数组常用函数

主要是数组元素的增删改查操作

```php
<?php
     header("Content-Type: text/html; charset=utf-8");  // 在响应头中添加了content-type: utf-8，header()是php提供的加工响应头键值对的

    $a = array('aa', 'bb', 33, 55);
    echo $a[0].'<br>';
    echo var_dump($a).'<br>';

    $a[5] = 'kk';
    echo var_dump($a).'<br>';

    $a[1] = 'cc';
    echo var_dump($a).'<br>';

    //unset()删除
    unset($a[1]);
    echo var_dump($a).'<br>';
?>
```

#### 其他数组常用函数

![image-20240531155730982](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240531155730982.png)

![image-20240531155801451](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240531155801451.png)

##### php文件和目录操作

```php
readfile()  //读取文件内容，并返回文件的长度，这个没啥用

file_get_contents('文件路径')  //读取文件，支持本地文件和远程文件url

file_put_contents('文件路径', '内容')  //保存文件

// readfile会自动打印文件内容，
$a = readfile('1.txt');
echo '<br>';
echo $a; //文件长度

// 写入数据    
$a = 'aabbkkdd';
file_put_contents('1.txt', $a); // 没有文件会自动创建
$b = 'ooooo';
file_put_contents('1.txt', $b); // 每次写入新数据都会先清空原文件数据

//读取文件内容
$a = file_get_contents('1.txt');
$a =file_get_contents('http://www.baidu.com/img/flexible/logo/pc/result.png'); 

//直接请求https的网址会报错，休要修改配置，1.windows下的PHP，只需要到php.ini中把extension=php_openssl.dll前面的;删掉，重启服务就可以了。2.linux下的PHP，就必须安装openssl模块，安装好了以后就可以访问了。
// file_put_contents('1.txt', $a)  # 直接将读取的文件输入写入到本地文件中

echo $a;
# 注意：文件读写的内容都是字符串数据格式。
```

##### fopen

```
fopen、fread、fwrite、fclose操作读取文件
。
resource fopen ( string $文件名, string 模式)

string fread ( resource $操作资源(也就是文件路径), int 读取长度)

bool fclose ( resource $操作资源 )

注：resource 、string、bool表示的是方法的返回值 。
```

fopen的模式有下面几个，我们来讲一下fopen的模式： 带+号的先pass

```php
r
只读方式打开，将文件指针指向文件头。 重点

r+
读写方式打开，将文件指针指向文件头。

w
写入方式打开，将文件指针指向文件头并将文件大小截为零。如果文件不存在则尝试创建。重点

w+
读写方式打开，将文件指针指向文件头并将文件大小截为零。如果文件不存在则尝试创建

a
写入方式打开，将文件指针指向文件末尾。如果文件不存在则尝试创建 ，称之为追加。 重点

a+
读写方式打开，将文件指针指向文件末尾。如果文件不存在则尝试创建之

x
创建并以写入方式打开，将文件指针指向文件头。如果文件已存在，则 fopen() 调用失败并返回 FALSE，并生成一条 E_WARNING 级别的错误信息。如果文件不存在则尝试创建 。 重点

x+
创建并以读写方式打开，将文件指针指向文件头。如果文件已存在，则 fopen() 调用失败并返回 FALSE，并生成一条 E_WARNING 级别的错误信息。如果文件不存在则尝试创建
```

**示例**

```php
$a = fopen('1.txt', 'r')
#$b = fread($a,18);

$b = fgets($a);
echo $b."<br>";

while(!feof($a)){  // !feof($a)表示如果读到文件最后了。
        $b = fgets($a);
        echo $b."<br>";
 } 
 
$b = fwrite($a, 'aaaaa'); //失败返回false，成功就返回写入的字符个数
echo $b."<br>";
 if ($b == false){  // r模式打开的文件不能写入,r+模式可以写，但是会从文件内容开头覆盖原有内容
	echo '写入失败';
 }

#fclose($a);
```

####  PHP目录处理函数

**处理文件夹的基本思想如下：**

```
1.读取某个路径的时候判断是否是文件夹
2.是文件夹的话，打开指定文件夹，返回文件目录的资源变量
3.使用readdir读取一次目录中的文件，目录指针向后偏移一次
4.使用readdir读取到最后，没有可读的文件返回false
5.关闭文件目录
```

![image-20240531160354908](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240531160354908.png)

例如：列举当前目录列表

```
$a = dirname(__FILE__);  // php多行注释/* 注释内容 */
 echo '<br>';
 $b = scandir($a);
 var_dump($b);
 foreach ($b as $key=>$filename){
 if ($filename == '.' or $filename == '..' ){
continue;
    }
 echo $filename."<br>";
 }
 # 判断类型
filetype($a.'\wp');
 filetype($a.'\1.txt');
```

示例:查看D盘下的文件和文件夹，并输出他们的类型

```
<?php
 //设置打开的目录是D盘
$dir = "C:/phpStudy/PHPTutorial/WWW";
 //判断是否是文件夹，是文件夹
if (is_dir($dir)) {
 if ($dh = opendir($dir)) {
       }
    }
 ?>
 //读取到最后返回false，停止循环
// while中的条件表示：将readdir每次读取的数据赋值给$file,然后比较$file是否等于
false，如果等false，那么while循环结束
while (($file = readdir($dh)) !== false) {
 echo "文件名为: $file : 文件的类型是: " . filetype($dir ."/". $file) 
. "<br />";
           }
 closedir($dh);

```

####  PHP创建临时文件

我们之前创建的文件都是永久文件。 

而创建临时文件在我们平时的项目开发中也非常有用。创建临时文件的几个好处：用完后即删除，不需 要去维护这个文件的删除状态

```
<?php
    //创建了一个临时文件
    $handle = tmpfile();
    //向里面写入了数据
    $numbytes = fwrite($handle, '写入临时文件');
    // sleep(60);
    //关闭临时文件，文件即被删除
	fclose($handle);

	echo  '向临时文件中写入了'.$numbytes . '个字节';
?>
//windows存储在C:\Users\用户名\AppData\Local\Temp目录中
```

#### PHP移动、拷贝和删除文件

**重命名**

我们日常在处理文件的时候，可以删除文件、重命名文件也可以也可复制文件。 

我们先来说重命名，重命名的函数是： bool rename($旧名,$新名);方法的返回结果是布尔值。 

这个函数返回一个bool值，将旧的名字改为新的名字。

```php
<?php
    //旧文件名
    $filename = 'test.txt';

    //新文件名
    $filename2 = $filename . '.xx';

    //修改文件名称
    rename($filename, $filename2);

    //移动文件，比如移动到xx目录下
    rename($filename, '\\xx\\'.$filename2);
?>
```

**复制文件**

复制文件，就相当于是克隆技术，将一个原来的东西再克隆成一个新的东西。

两个长得一模一样。 

copy(源文件,目标文件) 

功能：将指定路径的源文件，复制一份到目标文件的位置。 我们来通过实验和代码来玩玩：

```php
<?php
    //旧文件名
    $filename = 'copy.txt';

    //新文件名
    $filename2 = $filename . '_new';

    //修改名字。
    copy($filename, $filename2);
?>
```

你会通过上面的例子，发现多出来了一个文件

**删除文件**

删除文件就是将指定路径的一个文件删除，不过这个删除是直接删除。使用的是windows电脑，你在回收站看不到这个文件。你只会发现，这个文件消失了。  bool unlink(指定路径的文件)

```php
<?php
 $filename = 'test2.txt';
 if (unlink($filename)) {
 			echo  "删除文件成功 $filename!\n";
   } else {
 			echo "删除 $filename 失败!\n";
   }
 ?>
```

**检测文件属性**

比如，检测一下xx.txt文件是否存在

```php
<?php
         if(file_exists('文件路径')){
                 echo '文件已存在';
                 exit;
    }
 ?>
```

**常用文件属性函数**

```php
bool file_exists ( $指定文件名或者文件路径)
功能：文件是否存在。

bool is_readable ( $指定文件名或者文件路径)
功能：文件是否可读

bool is_writeable ( $指定文件名或者文件路径)
功能：文件是否可写

bool is_executable ( $指定文件名或者文件路径)
功能：文件是否可执行

bool is_file ( $指定文件名或者文件路径)
功能：是否是文件

bool is_dir ( $指定文件名或者文件路径)
功能：是否是目录

void clearstatcache ( void )   pass它
功能：清除文件的状态缓存
```

##### PHP文件权限设置

chmod 主要是修改文件的的权限。主要是针对linux系统的，这个我们前面学过，就不多说了

```php
<?php
    //修改linux  系统/var/wwwroot/某文件权限为755
    chmod("/var/wwwroot/index.html", 755);  
    chmod("/var/wwwroot/index.html", "u+rwx,go+rx"); 
    chmod("/somedir/somefile", 0755); 
?>
```

权限说明（r-读，w-写，x执行，d-表示文件夹，u-当前用户，g-当前用户所在组，o-其他用户）

![image-20240531161331614](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240531161331614.png)

##### PHP文件路径函数

我们经常会遇到处理文件路径的情况。

```
例如：
  1.文件后缀需要取出来
  2.路径需要取出名字不取目录
  3.只需要取出路径名中的目录路径
  4.或者把网址中的各个部份进行解析取得独立值
  5.甚至是自己组成一个url出来
  ... ....
```

很多地方都需要用路径处理类的函数。 

我们把常用的路径处理函数为大家做了标注，大家对着这个路径处理函数进行处理即可：

![image-20240531161411508](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240531161411508.png)

示例，记住示例中的几个即可

```php
 <?php
     $path_parts = pathinfo('d:/www/index.inc.php');

     echo '文件目录名：'.$path_parts['dirname']."<br />";
     echo '文件全名：'.$path_parts['basename']."<br />";
     echo '文件扩展名：'.$path_parts['extension']."<br />";
     echo '不包含扩展的文件名：'.$path_parts['filename']."<br />"; 
 ?>
```

##### PHP文件上传

在web常见漏洞中有一个文件上传的漏洞，后面我们会讲到。 在我们日常使用中经常会遇到很多种这样的情况：

```
QQ空间里面上传图片呀
微信朋友圈上传图片
发邮件里面上传邮件资料附件
认证的时候要求上传照片或身份证
```

文件上传需要注意php.ini这个配置文件

```php
只有file_uploads = on 时，php才能支持上传文件
```

phpinfo()函数，也可以看到这些配置信息

![image-20240531161553600](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240531161553600.png)

建议尺寸： file_size(文件大小) < upload_max_filesize < post_max_size < memory_limit 

另外，需要注意的是脚本执行时间，max_execution_time配置，这个参数的单位为秒。它是设定脚本的 最大执行时间。也可以根据需求做适当的改变。通常不需要来修改，系统默认值即可。超大文件上传的 时候，可能会涉及到这一项参数的修改。上传时间太长了，会超时。如果你将此项参数设为0，则是不限 制超时时间，不建议使用，文件太大了，想别的方式处理，一般会分块传输 。 

完成了php.ini的相关配置，我们就可以开始试着完成第一次文件上传了。别忘了重启服务。

通过php获取webserver相关配置信息的代码

```php
<?php
    header("Content-Type: text/html; charset=utf-8");  // 在响应头中添加了content-type: 
    utf-8，header()是php提供的加工响应头键值对的
    $a = $_SERVER['HTTP_HOST'];
    $b = $_SERVER['HTTP_USER_AGENT'];
    echo $a.'<br>';
    echo $b.'<br>';
?>
```

##### 上传文件步骤

1.系统返回的错误码详解

![image-20240531161658258](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240531161658258.png)

**注：错误码中没有5。**

2.自定义判断是否超出文件大小范围

在开发上传功能时。我们作为开发人员，除了php.ini中规定的上传的最大值外。我们通常还会设定一个 值，是业务规定的上传大小限制。

例如：

```
新浪微博或者QQ空间只准单张头像图片2M。而在上传图册的时候又可以超过2M来上传。
所以说，它的系统是支持更大文件上传的。
此处的判断文件大小，我们用于限制实际业务中我们想要规定的上传的文件大小。
```

3.判断后缀名和mime类型是否符合

在网络世界里面也有坏人。他们会把图片插入病毒，在附件中上传病毒，他们会在网页中插入病毒或者 黄色图片。

 我们需要对于上传的文件后缀和mime类型都要进行判断才可以

```
百度解释：MIME(Multipurpose Internet Mail Extensions)是多用途互联网邮件扩展类型。是设定某种扩展名的文件用一种应用程序来打开的方式类型，当该扩展名文件被访问的时候，浏览器会自动使用指定应用程序来打开。多用于指定一些客户端自定义的文件名，以及一些媒体文件打开方式。

通俗解释：  有兴趣看一看
    其实MIME更像是一种协议。
    首先，我们要了解浏览器是如何处理内容的。在浏览器中显示的内容有 HTML、有 XML、有 GIF、还有 Flash ……那么，浏览器是如何区分它们，决定什么内容用什么形式来显示呢？答案是 MIME Type，也就是该资源的媒体类型。
    媒体类型通常是通过 HTTP 协议，由 Web 服务器告知浏览器的，更准确地说，是通过 Content-Type 来表示的，例如:
    Content-Type: text/HTML
	表示内容是 text/HTML 类型，也就是超文本文件。为什么是“text/HTML”而不是“HTML/text”或者别的什么？MIME Type 不是个人指定的，是经过 ietf 组织协商，以 RFC 的形式作为建议的标准发布在网上的，大多数的 Web 服务器和用户代理都会支持这个规范 (顺便说一句，Email 附件的类型也是通过MIME Type 指定的)。
通常只有一些在互联网上获得广泛应用的格式才会获得一个 MIME Type，如果是某个客户端自己定义的
格式，一般只能以 application/x- 开头。
    XHTML 正是一个获得广泛应用的格式，因此，在 RFC 3236 中，说明了 XHTML 格式文件的 MIME Type 应该是 application/xHTML+XML。
当然，处理本地的文件，在没有人告诉浏览器某个文件的 MIME Type 的情况下，浏览器也会做一些默认的处理，这可能和你在操作系统中给文件配置的 MIME Type 有关。比如在 Windows 下，打开注册表的“HKEY_LOCAL_MACHINESOFTWAREClassesMIMEDatabaseContent Type”主键，你可以看到所有 MIME Type 的配置信息。
在把输出结果传送到浏览器上的时候，浏览器必须启动适当的应用程序来处理这个输出文档。这可以通过多种类型MIME（多功能网际邮件扩充协议）来完成。在HTTP中，MIME类型被定义在Content-Type header中。

例如，假设你要传送一个Microsoft Excel文件到客户端。那么这时的MIME类型就是
“application/vnd.ms-excel”。在大多数实际情况中，这个文件然后将传送给Execl来处理（假设我们设定Execl为处理特殊MIME类型的应用程序）。在ASP中，设定MIME类型的方法是通过Response对象的ContentType属性。

多媒体文件格式MIME
    最早的HTTP协议中，并没有附加的数据类型信息，所有传送的数据都被客户程序解释为超文本标记语言HTML 文档，而为了支持多媒体数据类型，HTTP协议中就使用了附加在文档之前的MIME数据类型信息来标识数据类型。
    MIME意为多目Internet邮件扩展，它设计的最初目的是为了在发送电子邮件时附加多媒体数据，让邮件客户程序能根据其类型进行处理。然而当它被HTTP协议支持之后，它的意义就更为显著了。它使得HTTP传输的不仅是普通的文本，而变得丰富多彩。
    每个MIME类型由两部分组成，前面是数据的大类别，例如声音audio、图象image等，后面定义具体的种类。
    
常见的MIME类型
    超文本标记语言文本 .html,.html text/html
    普通文本 .txt text/plain
    RTF文本 .rtf application/rtf
    GIF图形 .gif image/gif
    JPEG图形 .ipeg,.jpg image/jpeg
    au声音文件 .au audio/basic
    MIDI音乐文件 mid,.midi audio/midi,audio/x-midi
    RealAudio音乐文件 .ra, .ram audio/x-pn-realaudio
    MPEG文件 .mpg,.mpeg video/mpeg
    AVI文件 .avi video/x-msvideo
    GZIP文件 .gz application/x-gzip
    TAR文件 .tar application/x-tar

Internet中有一个专门组织IANA来确认标准的MIME类型，但Internet发展的太快，很多应用程序等不及IANA来确认他们使用的MIME类型为标准类型。因此他们使用在类别中以x-开头的方法标识这个类别还没有成为标准，例如：x-gzip，x-tar等。事实上这些类型运用的很广泛，已经成为了事实标准。只要客户机和服务器共同承认这个MIME类型，即使它是不标准的类型也没有关系，客户程序就能根据MIME类型，采用具体的处理手段来处理数据。而Web服务器和浏览器（包括操作系统）中，缺省都设置了标准的和常见的MIME类型，只有对于不常见的 MIME类型，才需要同时设置服务器和客户浏览器，以进行识别。

由于MIME类型与文档的后缀相关，因此服务器使用文档的后缀来区分不同文件的MIME类型，服务器中必须定义文档后缀和MIME类型之间的对应关系。而客户程序从服务器上接收数据的时候，它只是从服务器接受数据流，并不了解文档的名字，因此服务器必须使用附加信息来告诉客户程序数据的MIME类型。服务器在发送真正的数据之前，就要先发送标志数据的MIME类型的信息，这个信息使用Content-type关键字进行定义，例如对于HTML文档，服务器将首先发送以下两行MIME标识信息,这个标识并不是真正的数据文件的一部分。
    Content-type: text/html
注意，第二行为一个空行，这是必须的，使用这个空行的目的是将MIME信息与真正的数据内容分隔开。
    MIME (Multipurpose Internet Mail Extensions) 是描述消息内容类型的因特网标准。
    MIME 消息能包含文本、图像、音频、视频以及其他应用程序专用的数据。
官方的 MIME 信息是由 Internet Engineering Task Force (IETF) 在下面的文档中提供的：
    RFC-822 Standard for ARPA Internet text messages
    
    RFC-2045 MIME Part 1: Format of Internet Message Bodies
    
    RFC-2046 MIME Part 2: Media Types
    
    RFC-2047 MIME Part 3: Header Extensions for Non-ASCII Text
    
    RFC-2048 MIME Part 4: Registration Procedures
    
    RFC-2049 MIME Part 5: Conformance Criteria and Examples
    
不同的应用程序支持不同的 MIME 类型
```

```
在判断后缀和MIME类型的时候，我们会用到PHP的一个函数in_array(),该函数传入两个参数。 
    第一个参数是要判断的值； 
    第二个参数是范围数组。
我们用这个函数来判断文件的后缀名和mime类型是否在允许的范围内。
```

4.生成文件名

```
我们的文件上传成功了，不会让它保存原名。因为，有些人在原名中有敏感关键词会违反我国的相关法律和法规。我们可以采用date()、mt_rand()或者unique()生成随机的文件名。
```

5.判断是否是上传文件

```
文件上传成功时，系统会将上传的临时文件上传到系统的临时目录中。产生一个临时文件。同时会产生临时文件名。我们需要做的事情是将临时文件移动到系统的指定目录中。而移动前不能瞎移动，或者移动错了都是不科学的。移动前我们需要使用相关函数判断上传的文件是不是通过 HTTP POST 上传的，is_uploaded_file()传入一个参数($_FILES中的缓存文件名)，is_uploaded_file() 函数检查指定的文件是否是通过 HTTP POST 上传的，如果文件是通过 HTTP POST 上传的，该函数返回 TRUE。
```

6.移动临时文件到指定位置

```
临时文件是真实的临时文件，我们需要将其移动到我们的网站目录下面了。让我们网站目录的数据，其他人可以访问到，我们使用：move_uploaded_file() 。这个函数是将上传文件移动到指定位置，并命名。
需要传入两个参数：
    第一个参数是指定移动的上传文件；
    第二个参数是指定的文件夹和名称拼接的字符串。
```

大致步骤

![image-20240531161916608](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240531161916608.png)

**php文件上传表单注意事项**

创建index.html文件，内容如下

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
	 <h1>上传文件</h1>
    <form action="chuli.php" method="post" enctype="multipart/form-data">
    请选择文件：<input type="file" name="file" /><input type="submit" value="上传"/>
    </from>
</body>
</html>
```

注意事项：

```
1.form 表单中的参数method 必须为post。若为get是无法进行文件上传的
2.enctype须为multipart/form-data
```

再创建一个php文件，比如叫做chuli.php

```php
<?php
//取文件信息
$arr = $_FILES["file"];
//var_dump($arr);
// 获取文件扩展名，可以用到pathinfo()函数
//加限制条件
//1.文件类型
//2.文件大小
//3.保存的文件名不重复
if (($arr["type"] == "image/jpeg" || $arr["type"] == "image/png") &&
    $arr["size"] < 10241000) {
    //临时文件的路径
    $arr["tmp_name"];
    //上传的文件存放的位置
    //避免文件重复: 
    //加时间戳.time()加用户名.$uid或者加.date('YmdHis')
    $filename = "./images/" . date('YmdHis') . $arr["name"]; //注意：要在当前代码文
    件所在目录下先去创建一个名为images的文件夹
        //保存之前判断该文件是否存在
          if (file_exists($filename)) {
              echo "该文件已存在";
          } else {
              //中文名的文件出现问题，所以需要转换编码格式
              $filename = iconv("UTF-8", "gb2312", $filename);
              //移动临时文件到上传的文件存放的位置（核心代码）
              //括号里：1.临时文件的路径, 2.存放的路径
              move_uploaded_file($arr["tmp_name"], $filename);
              echo "文件上传成功";
          }
        } else {
    echo "上传的文件大小或类型不符";
}
?>
```

#### php执行系统命令函数

```php
system('指令')
exec('指令')，这个指令的结果回显不太好，但是指令执行是没问题的。
```

# 10、php的错误处理

很多时候，代码如果写的不太好，那么很容易报错。那么如果遇到了错误，我们应该想办法捕获到这个 错误并记录下来，而且最好不要用户看到，不然太尴尬了，而且容易暴漏自己服务端的一些敏感信息， 方便我们后续修改，并且尽量不要让整个程序因为一点小错误而崩溃。

## 配置项管理

```
在php.ini配置文件中。我们可以控制php的错误显示状态。php.ini中有一个专门的配置项： display_errors  

这个选项设置是否将错误信息输出到网页，或者对用户隐藏而不显示。在生产上必须要关闭显示错误， 开发的时候可以打开方便调试。 

这个值的状态为on 或者 off，也可以设值为1 或者0。  

display_errors的值设为0或者off则不在页面中显示错误，如果设为1或者on则显示错误信息。  

问题：如果没有修改服务器php.ini的状态权限怎么办？ 

那么可以在每个代码文件中使用ini_set方法来进行设置，其实php.ini中的各种配置都可以在代码中进行 动态控制。
```

```php
<?php
    ini_set('display_errors', 0);
    //$a = $GET['xxxx']; 这个错误就不显示了。
?>
```

上面的代码也相当于修改了php.ini中display_errors的值。不过，仅仅在当前php代码中生效。

**问题：想取得php.ini的配置项状态怎么办？**

可以使用ini_get(参数项) 得到参数的值。

演示例子：

```php
<?php
	echo '服务器中display_errors的状态为' . ini_get('display_errors');
?>
```

注：如果我们修改完php.ini文件中的配置，想让配置生效的话，需要在修改完php.ini文件后重启服务器。

## 错误级别

[掌握级别的错误类型] ，可以控制哪些级别的错误可以显示或者记录日志，哪些级别的错误不可以显 示或者不记录日志。

![image-20240531162945921](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240531162945921.png)

我们介绍一下其中几种：

```
error最严重，必须要解决。不然程序无法继续向下执行

warning也很重要。但也必须要解决。如果明确的、故意的可以不用处理。

notice 你可以不用管。但是在有些公司，项目标准特别高。在高标准要求的项目中也必须要解决。因为，notice会影响到PHP的执行效率。通常发生在函数未定义等。

parse错误，是指语法错写错了，必须要解决，代表全部类型的所有错误。
```

```
1、 在php.ini中error_reporting参数。如若error_reporting参数设置为0。整个PHP引擎发错误均不会 显示、输出、记录。在后面要讲的日志记录中，也不会记录。 
    如果我们想显示所有错误可以写上：  
        error_reporting = E_ALL  
    想要显示所有错误但排除提示，可以将这个参数写为：  
        error_reporting = E_ALL & ~ E_NOTICE  
    显示所有错误，但排除提示、兼容性和未来兼容性。可写为：  
        error_reporting ＝ E_ALL & ~E_NOTICE & ~E_STRICT & ~E_DEPRECATED 



2、在有些情况下我们无权限操作php.ini文件，又想要控制error_reporting怎么办呢？在运行的 xxxx.php文件中开始处，我们可以使用error_reporting()函数达到目标。  
```

演示代码如下：

```php
<?php
    //关闭了所有的错误显示
    error_reporting(0);
    
    //显示所有错误
    //error_reporting(E_ALL);
    
    //显示所有错误，但不显示提示
    //error_reporting(E_ALL & ~ E_NOTICE);
?>
```

## 错误记录日志

在一些公司里面，有专门的日志收集系统。日志收集系统会在背后默默的帮你收集错误、警告、提示。 也有些公司没有专门的日志收集系统，通过文件来服务器当中的运行日志。 

其中：PHP的错误，警告这些是必须要收信的。那么问题来了------不让用户看到，设置好错误报告级别 好，如何将错误收集到日志系统中呢？ 

这里有需要使用到php.ini的相关配置项。这两个配置项为：

![image-20240531163417697](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240531163417697.png)

说明：

```
1.在表格中的log_errors和log_errors_max_len非常好理解。

2.而error_log 指定将错误存在什么路径上。配置项中的syslog可能有点不太好理解。syslog是指系统来
记录。windows系统在电脑的事件查看器--应用程序日志。里面。linux默认在：  /etc/syslog.conf
 
[扩展] 了解知识点。若Linux系统启动或修改了日志收集。可能存储在第三方专用的日志收集服务器中。

此外，PHP还为我们专门准备了一个自定义的错误日志函数：
bool error_log ( string $错误消息 [, int $错误消息类型 = 0 [, string $存储目标]] )这个函数可以把错误信息发送到web服务器的错误日志，或者到一个文件里。
```

常用的错误消息类型

![image-20240531183045247](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240531183045247.png)

**示例**

```php
<?php
    //无法连接到数据库服务器，直接记录到php.ini 中的error_log指定位置
    error_log("无法连接到数据库服务器服务器");
    //可以发送邮件，但是php.ini必须配置过邮件系统
    error_log('可以用邮件报告错误，让运维人员半夜起床干活', 1, 'pig@php.cn');
    //记录在指定的位置
    error_log("我是一个错误哟", 3, "d:/test/my-errors.log");
?>
```

web服务应用程序都有自己的日志文件，比如apache的，在phpstudy的安装路径中可以看到。

![image-20240531183207713](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240531183207713.png)

**一般我们手动搭建的apache的默认日志路径是在，重点昂**

```
linux: /etc/httpd/logs/access_log
windows: /Apache/logs/access_log
```

# 11、PHP中的正则表达式

正则表达示我们其实之前经常看到，它主要用在以下一些地方：匹配邮箱、手机号码、验证码、替换敏 感的关键词。例如：涉及政治和骂人的话。

## 定界符

PHP的正则表达示定界符的规定如下： 

​	定界符，不能用a-zA-Z0-9\ 其他的都可以用。必须成对出现，有开始就有结束

![image-20240531183304891](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240531183304891.png)

**注：\ 是转义字符，如果在以后正则表达示里面需要匹配/，需要把定界符里面的/ 用转义字符转义一 下，写成 / \/ / ，如果你觉得麻烦，遇到这种需要转义的字符的时候可以把两个正斜线（/ /）定界， 改为其他的定界符（# #）。**

## 正则表达式的使用

```
preg_match ( string $正则 , string $字符串 [, array &$结果] )
```

**功能**：

```
根据定界符，比如$正则变量，匹配$字符串变量。如果存在则返回匹配的个数，把匹配到的结果 放到$结果变量里。如果没有匹配到结果返回0。
```

```php
<?php
    $zz = '/wq/';  //正则表达式写在中间，'/正则表达式/'

    $string = 'ssssswqaaawqaaa';

    if (preg_match($zz, $string, $matches)) {
        echo '匹配到了，结果为：';
        var_dump($matches);
    } else {
        echo '没有匹配到';
    }
?>
$a = 'hello jaden';
$b = preg_replace('/jaden/', 'wulaoban', $a);
echo $b;  // hello wulaoban
```

我们常用的正则函数有

![image-20240531183438301](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240531183438301.png)

# 12、反序列化函数

## 面向对象编程(类)

```php
<?php
header("Content-Type: text/html; charset=utf-8");  // 在响应头中添加了content-type: 
utf - 8，header()是php提供的加工响应头键值对的
class Fruit
{
    var $name1 = 'apple';  // 定义  属性
    var $name2 = 'orange';

    function chi()
    {  //定义  方法
        echo '吃水果' . '<br>';
        echo $this->name1 . '<br>';
        //...
    }

    function bo()
    {
        echo '剥皮' . '<br>';
    }

    // 特殊方法，魔法\魔术方法,  当某个时机到来时，自动执行
    function __destruct()
    {  //对象销毁时自动执行的方法  __construct 对象创建时自动触发
		echo '对象被销毁了' . '<br>';
 	}
}

$f = new Fruit();
//echo $f->name1.'<br>';  // apple
$f->chi();
 
echo '哈哈' . '<br>';

 /*  
function add(){
     $f = new Fruit();
    $f->chi();
 }
 add();
 */
 ?>
```

## 序列化和反序列化

```php
//序列化,将其他的数据转换成字符串
$a = array('one', 33, 'two');
	var_dump($a); // array(3) { [0]=> string(3) "one" [1]=> int(33) [2]=> string(3)
"two" }
echo "<br>";
$b = serialize($a);
var_dump($b);  // string(43) "a:3:{i:0;s:3:"one";i:1;i:33;i:2;s:3:"two";}"
//反序列化 将序列化的字符串还原成原来的数据类型
$c=unserialize($b);
var_dump($c);

//类的序列化
class S{
    var $name = "jaden";
    function __destruct(){
    echo $this->name;
    //system('ipconfig');
    //echo '
    <script>alert(123);</script>';
}

function chi(){
	echo 'xxxxx';
	}
}

$a = new S();
echo $a->name.'aaaa<br>';
echo $a->chi().'<br>';

$b = serialize($a); // O:1:"S":1:{s:4:"name";s:5:"jaden";}
$c = unserialize($b);
```

# 13、php操作mysql

## 创建表

```mysql
# phpstudy的mysql在：C:\phpStudy\PHPTutorial\MySQL\bin
# 注意下面插入数据的时候，不要插入中文数据！！！，因为php连接mysql的编码没有设置，容易乱码。
create database jaden charset utf8mb4; 
create table  user(id int  NOT NULL AUTO_INCREMENT,username char(20),password 
char(32),reg_time char(36),PRIMARY KEY (`ID`));

insert user(username,password,reg_time) 
values('admin','123456',CURRENT_TIMESTAMP());

insert user(username,password,reg_time) 
values('wulaoban','123456',CURRENT_TIMESTAMP());
```

## 查询

```php
//连接数据库
$db=mysqli_connect('localhost','root','root','jaden', 3306);  # 默认端口如果就是3306，那么其实不用写3306

$sql="select * from user where username='wulaoban'";
//$u = 'wulaoban';
//$sql="select * from user where username='$u'";

//执行sql语句
$a=mysqli_query($db,$sql); 
//遍历数据库的查询结果，
while ($row = mysqli_fetch_assoc($a)) {
     //var_dump($row);
     echo "用户名:".$row['username'].",密码:".$row['password'];
     echo "<br>";
 }
 mysqli_close($db);
```

![image-20240531183906786](D:/%E6%96%87%E6%A1%A3/%E7%AC%94%E8%AE%B0/image-20240531183906786.png)

## 插入数据

```php
$db=mysqli_connect('localhost','root','root','jaden');

 $sql="insert user(username,password) values('laowang2','111111')";
 $a=mysqli_query($db,$sql);
 //echo $a.'<br>';
 if (!$a){
 	echo "sql语句语法问题";
 }else {
	 echo "sql语句执行成功!";
 }
 mysqli_close($db);
```

删除数据，更新数据和插入数据步骤类似

# 14、cookie和session

登录认证。

只使用cookie

```php
 location.href='login.php';
 #设置cookie
 setcookie('user','admin');
 #读取cookie
 $_COOKIE['user'];
```

火狐浏览器有个Cookie-Editor插件。

cookie结合session

```php
验证的地方：
session_start();
isset($_SESSION['user'])
     
登录成功设置：
session_start();
 $_SESSION['user']=$u;
 $_SESSION['login_time']=time();
 $_SESSION['d']='123';
 $_SESSION['login_status']=1;
 // session存放位置：在php.ini配置文件中可以找到，session.save_path
```

