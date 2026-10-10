# PHP入门

php社区：https://learnku.com/php/wikis

### 环境搭建

### php标记符

> ##### 标准标记
>

标准标记以<?php开始，以?>结束

```php
实例：
<?php
	echo "hello world";
?>
```

> ##### 简短标记
>

以<?开始，以?>结束

```php
实例：
<?
	echo 'hello world';
?>
```

### php注释

> ##### 单行注释
>
> 在“//”后面的不会被输出，php将直接跳过
>

实例：

```php
<?php
	echo 'hello world';//输出字符串
?>
```

> ##### 多行注释
>



```php
实例：
<?php
	echo 'hello world';
	/*
	这里面的内容php不会执行
	*/
```

> ##### Shell风格的注释
>

以"#"开头

#相较于//，//更加流行。

```php
实例：
<?php
	echo 'hello world';#输出字符串
?>
```

> ### php语句块和语句块
>

语句块用于多条语句之间有联系的情况，放于"{}"之间。

语句块一般不会单独使用，会和条件判断语句、循环语句、函数一起使用。

```php
实例：
<?php
	echo 'hello world';
	echo '<br>';
	echo 'hi,php';	
?>
```

> ### php标识符
>

在php程序开发中需要定义变量、













### 变量和常量

> 命名规则

变量名前面需要加‘$’，列如：“$变量名=赋值”

> echo：打印

echo $变量名;

echo '字符串';

echo打印可以用'.'连接

实例：

```php
<?php
//先要给一个变量赋值
$name='张三';
//用'.'
echo '大家好我是'.$name;
?>
```



##### 全局变量

> global关键字和$GLOBAL

用法：global $变量名

​		$GLOBAL['变量名']

实例：

```php
//全局变量
<?php
$name='zhangs';
//定义函数
function foo(){
    global $name;
    echo $name;  
}

function foo1(){
    echo "{$GLOBALS['name']}";  
}

foo();  //打印全局变量zhangs

foo1();  //打印超全局变量zhangs
```



##### 局部变量

局部变量定义在函数内部，只在内部生效，超出将失效

实例：

```php
<?php
//创建函数
function foo(){
    $num=1;
    echo $num;
}

foo();  //第一次调用打印1
foo();  //第一次调用打印1
//echo $name;   这里打印不生效，报错
```



##### 静态变量

用法：

static $变量名



实例：

```php
<?php
//创建函数
function foo(){
   static $num=1;
   
    echo $num;
}

foo();  //第一次调用打印1
foo();  //第一次调用打印2
```



##### 弱类型语言

支持两数据之间进行隐式转换

实例：

```php
<?php
$var=123;
var_dump($var);  //int类型123

$var='dsf';
var_dump($var);  //string类型'dsf'
```



##### 变量命名

- **变量名的开始**：PHP变量名以美元符号（*$*）开始，后跟变量的名称。
- **字符类型**：变量名可以包含字母、数字和下划线（*_*），但不能以数字开头。
- **大小写敏感性**：PHP变量名是大小写敏感的，这意味着*$Variable*和*$variable*是两个不同的变量。
- **中文变量名**：虽然PHP允许使用中文作为变量名，但这并不推荐，因为它可能会影响代码的可读性和兼容性。

- **静态变量**：通常以小写的*s_*开头，例如*$s_user_count*。
- **局部变量**：通常以*_*开头，例如*$_temp_data*。
- **全局变量**：通常以*g_*开头，以表明它们的全局作用域，例如*$g_config*。
- **全局常量**：通常全部使用大写字母，并用下划线分隔单词，例如*BASE_URL*。
- **Session变量**：通常以大写的*S_*开头，并用下划线分隔单词，例如*$S_USER_PROFILE*。



##### 可变变量

用法：

$$变量名



实例：

```php
//创建一个变量
$var='hello';

//在$var前面加一个$变成可变变量
$$var='world';  //这时$hello等价于$$var
				//hello替换$var，$$var=$hello
```



##### 变量引用赋值

> 普通赋值

实例：

```php
<?php
$bar=10;

echo '$bar = ' . $bar;

$foo=$bar; //直接将值赋给$foo

```



> 引用赋值：&

将第一个变量引用赋值给第二个变量，第二个变量的值发生改变，第一个变量的值也会发生改变



实例：

```php
<?php
$var=12;
$bee=&$var;  //将var引用赋值给bee
echo $var.'<br>'.$bee;

$bee=20;
echo $var.'<br>'.$bee; //var和bee的值同时发生改变
```



##### 常量的定义和使用

常量前面没有$符号

> define函数

用法：

define('常量名',常量值,布尔值);

布尔值不写默认为false

布尔值代表大小写是否敏感，false代表敏感，true代表不敏感

实例：

```php
<?php
define('bee','something');

```



> const关键字

用法：

const 常量名=常量值;



实例：

```php
<?php
const bee=12;
```



##### 常量与变量的区别

1. 变量存储的值可以随时改变，常量存储的值不可以改变的。
2. 变量都用 $ 符开头，然后跟上变量名，常量不用 $ 符开头。



变量可以通过 unset () 销毁，常量不能被销毁。

变量的作用域根据定义范围分为局部变量和全局变量，常量无论在哪里定义都可以直接调用，没有作用域。

变量的值可以是 PHP 所有的数据类型，常量的值只能是标量（如整型，浮点型，布尔型，null，字符串等，不能是数组，对象，资源）。

常量只能用 define() 或 const 来定义常量，不能通过赋值语句。



### 打印语句

#### echo

echo可以打印一个或多个变量或语句，需要用‘.’或‘,’连接

实例：

```php
<?php
$name='zhangs';
$age=19;

echo $name.'<br>';  //打印zhangs
echo $name,' ',$age;  //打印zhangs 19
```



#### print



实例：

```php
<?php
$name='zhangs';
print($name);
print('nihao'.$name);
```



#### var_dump语句

函数显示关于一个或多个表达式的结构信息，包括表达式的类型与值。数组将递归展开值，通过缩进显示结构

返回：

数据类型（数据长度） 数据值



实例：

```php
<?php
$str='hello world';
var_dump($str);  //输出string(11) "hello world"
```



#### print_r

用法：

bool  print_r(mixed  $变量名 [,bool $return])  //中括号中表示可选项



实例：

```php
<?php
$str=array('a'=>'app','b'=>'bule','c'=>array('x','y','z'));
print_r($str);  //打印Array ( [a] => app [b] => bule [c] => Array ( [0] => x [1] => y [2] => z ) )
echo '<br>';
$ru=print_r($str,true);  //用$ru接收返回值
echo $ru;
```



### 数据类型

#### integer：整形

支持二进制，八进制，十进制，十六进制,使用二进制前面要加0b，八进制加0，十六进制加0x

在integer前面加-或+表示正负

> [!NOTE]
>
> 与整形有关的常量
>
> > PHP_INT_MAX：最大值，PHP_INT_SIZE：字长，PHP_INT_MIN：最小值
>
> 实例：
>
> ```php
> <?php
> $int_max=PHP_INT_MAX;  //9223372036854775807
> $int_min=PHP_INT_MIN;  //-9223372036854775808
> $int_SIZE=PHP_INT_SIZE;  //8
> ```



#### string：字符串

表示：可以用‘数据’或“数据”表示



#### boolean类型

只有两个值，true和false



#### float：小数类型

可以接收存储小数，列如$num=9.33;



#### array数组

php5.4起  自动分配id键



实例：

```php
<?php
$arr=array('ff','dd');
print_r($arr);  //调试
//Array
//(
//    [0] => ff
//    [1] => dd
//)
```















#### 数据类型强制转换

用法：

(数据类型)数据



实例：

```php
//将float强制转换为int
<?php
var_dump((int)9.99);  //输出打印int(9)  //int为数据类型  （）里为强制转换的结果
```









### 正则表达式

















### 函数

创建函数											//参数并不是一定要写

function 函数名（$形参1，$形参2，....）{代码块}    //如果函数需要返回值，在代码块后面加return  语句；

默认参数：在形参后面直接赋值，在传参时没有赋值，就会使用默认值，传参时赋值了就会覆盖默认值

函数调用：

函数名(参数1，参数2，...)；



实例：

```php
<?php
function num($a,$b){
	echo $a+$b;
	//return $a+$b;
}
//调用
num(1,2); 
```



#### 内置函数

> strlen()：能够返回字符串长度



实例：

```php
<?php
$str_1='qwerty';
echo strlen($str_1);  //打印6
```



#### 递归函数

递归函数必须要有一个出口，否则是一个是循环



实例：

```php
<?php
//阶乘函数
function num($a){
    if($a==1){
        return 1;
    }
    else {
        return $a*num($a-1);
    }
}
$ab=num(4);
echo $ab;
```



### 面向对象

#### 类和对象

类：将数据以及这些数据上的操作封装在一起，是一种抽象的数据类型

对象：具有类类型的变量，是类的实例体现



创建类：

class  类名{ 类成员 }



类的实例化：

new  类名（）；



#### 类成员：属性和方法

> 属性

类的成员变量叫属性，可初始化属性值，也可不初始化，但初始化值只能是常量

使用关键字`public`，`protected`或`private`声明属性



实例：

```php
class Person{
    public $name;
    public $age=18;
}
new Person();  //实例化对象
```



`常量属性`：用`::`调用

用法：

类名::常量属性



实例：

```php
<?php
class Person{
const PI=3.14;
}
echo Person::PI;
```

> [!NOTE]
>
> 常量值不可修改



> 方法

是一个类所具备的具体功能，能被类和对象调用。方法之前必须添加访问修饰符，例如 `public` `protected` `private`。

用->调用方法



实例：

```php
<?php
class Person{
public function say(){
echo 'hello';
}
}
$new_p=new Person();
$new_p->say();  //打印hello
```



#### $this 访问类成员

this指向当前对象指针，是伪变量，调用本类的属性和方法



实例：

```php
<?php
class Person{
    public $name='zhangs';
    public $age=18;
    public function say(){
        echo '我是'.$this->$name.'今年'.$this->$age.'岁';
    }
}
$new_p=new Person();
$new_p->say();
```

> [!NOTE]
>
> 类里面的属性和方法必须要用`$this`才能访问



#### __construc构造方法

具有构造方法的类会在每次创建对象时先调用该方法

用法：

访问修饰符 function __construct（[参数，...]）{代码块}



实例：

```php
<?php
    class Person{
    public function __construct(){
        echo '调用了构造方法';
    }
}
$new_p=new Person();  //打印调用了构造方法
```



#### __destruct析构方法

某个对象的所有引用都被删除或者对象被显式销毁时执行

**析构函数的主要作用：**

1. **资源管理**：自动释放数据库连接、文件句柄、网络连接等
2. **数据一致性**：确保事务正确处理（提交或回滚）
3. **清理工作**：删除临时文件、释放锁、保存会话等
4. **调试辅助**：内存监控、性能分析等
5. **对象生命周期管理**：对象池、引用计数等



实例：

```php
<?php
class Person{
    public function __construct(){
        echo '调用了构造方法'.'<br>';
    }
    public $name='zahngs';
    public $age=20;
    public function say()
    {
        echo $this->name.'age:'.$this->age.'<br>';
    }
    public function say1()
    {
        echo $this->name.'age:'.$this->age.'<br>';
    }
    public function __destruct()
    {
        echo '调用析构函数';
    }
}
$new_p=new Person();  //打印调用了构造方法
$new_p->say();   //zahngsage:20
$new_p->say1();  //zahngsage:20  调用析构函数
//$new_p=null;      //销毁对象
//$new_p->say1();   //这里调用将会报错
```



#### public封装









### 连接数据库

使用扩展mysqli_connect()函数链接数据库

```
<?php
	$con=mysqli_connect("localhost","wrong_user","my_passwd","my_db");
	if(!$con){
		die("连接错误：".mysqli_connect_error());
	}
```



mysqli_connect(“host”,“username”,“password”,“dbname”,“port”,“socket”)

| 参数     | 描述                                    |
| -------- | --------------------------------------- |
| host     | 可选，规定主机名或IP地址                |
| username | 可选，规定MySQL用户名                   |
| password | 可选，规定MySQL密码                     |
| dbname   | 可选，规定默认使用的数据库              |
| port     | 可选，规定尝试连接到MySQL服务器的端口号 |
| socket   | 可选，规定socket或要使用的已命名pipe    |

> [!CAUTION]
>
> mysqli_connect()函数是mysql::__construct()函数名，所使用对象mysqli()也可实现数据库连接



> 面向过程写法

```php
<?php
	$host='localhost';
	$username='root';
	$password='';
	$dbname='test';
	$port='3306';
	$link=@mysqli_connect($host,$username,$password,$dbname,$post);
	if($link){
		mysqli_set_charset($link,'utf-8');
		$sql='select * from user';
		$result=mysql_query($link,$sql);
		$data=mysql_fetch_all($result);
		$mysqli_close($link);
	}else{
		die('数据库连接失败');
	}
	echo '<pre>';
	print_r($data);
```



> 面向对象写法

```php
<?php
	$host='localhost';
	$username='root';
	$password='';
	$dbname='test';
	$mysql=new Mysql($host,$username,$password,$dbname);
	if($mysql->connect_errno){
        die('数据库连接失败：'.$mysql->connect_eerno);
    }else{
        $mysql->set_charset('utf-8');
        $sql='select *from user';
        $result=$mysql->query($sql);
        $data=$result->fetch_all();
        $mysql->close();
    }
	echo '<pre>';
	print_r($data);

```





### DG图像处理库

