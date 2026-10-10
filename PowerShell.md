# PowerShell

```powershell
Start-Process net -Verb RunAs -ArgumentList "start VMnetDHCP"
#start-process 开启新进程
#net 程序net.exe
#-Verb RunAs 临时提权
#-ArgumentList 传递参数
#"start VMnetDHCP" 要启动的服务
```



### 变量

用**$**定义变量，例如$name

查找变量：ls variable:

测试变量是否存在：test-path variable:变量名

删除变量：del variable: 变量名



自动化变量

$?：判断上条命令执行是否成功



### 环境变量

ls env:

$env: name（名称，打印值）



### 条件判断

#### if

```powershell
$num=100
if($num -gt 90){"大于90"}elseif($num -lt 80){"小于80"}else{"false"}
```



#### switch

```powershell
$num=100
switch($num){
	{$_ -lt 50} {"小于50"}
	{$_ -gt 50} {"大于50"}
}
```



### 循环

#### foreach

```powershell
$arr=1..10
foreach($a in $arr){ $a }
```



#### while

```powershell
$num=13
while($num -gt 10){
	$num
	$num--
}
```



#### break/continue

break结束循环

continue跳过当前循环



#### for

```powershell
$sum=0
for($i=1;$i -le 100;$i++){
$sum+=$i
}
$sum
```



### 数组

#### 定义数组

```powershell
$arr=1,2,3,4,5
$arr=1..5
```



空数组

```powershell
$arr=@()
```

一个元素的数组

```powershell
$arr=,1
```



#### 访问数组

```powershell
$arr=1,"hell0",155
$arr[0..2]    #打印下标0-2的值
$arr.count    #输出数组元素个数
```



### 函数

```powershell
function 函数名([参数,...]){}    #定义
函数名  [参数]  #调用
```



#### 返回值

```powershell
function add($num1,$num2){
	$sum=$num1+$num2
	return $sum
}
add 1 3
```



### 定义文本

**`**:转义字符

```powershell
“输出: $(2 * 2)”
```



### 控制台输入

```powershell
$input=read-host "请输入数字"
"输入的数字是$input"
```



### 格式化字符串

```powershell
$name='zhangs'
$age=23
$gender='man'
"我是{0},今年{1}岁，{2}" -f $name,$age,$gender
#同理
"我是$name,今年$age岁，$gender"
```



### String对象方法

```powershell
$str="c:\windows\system32\1.txt"
$str.split("\")
```

