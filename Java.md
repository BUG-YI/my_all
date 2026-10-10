# Java入门

### 权限修饰符（常用private和public）

|    访问包位置    | 类修饰符 |           |        |
| :--------------: | -------- | --------- | ------ |
|                  | private  | protected | public |
|       本类       | 可见     | 可见      | 可见   |
| 同包其它类或子类 | 不可见   | 可见      | 可见   |
| 其他包的类或子类 | 不可见   | 可见      | 可见   |



### 基本数据类型和引用数据类型

#### 基本数据类型

#### 引用数据类型

##### *String类*



### StringBuffer和StringBuilder类

##### *StringBuffer*

用法：

```java
StringBuffer 对象名=new StringBUffer();
```

###### StringBuffer方法：

> ***append***：在创建的对象继续增加字符串。

实例：

```java
//先创建一个StringBuffer类的对象
StringBuffer sb=new StringBUffer();
sb.append();//在括号内添加
```

> ***setcharAt***：能够查找指定索引的字符

实例：

```java
//先创建一个StringBuffer类的对象
StringBuffer sb=new StringBUffer("asdf");
sb.setcharAt(0,'A');//将0索引上的字符替换成A
```

> ***insert***:插入字符

实例：

```java
//先创建一个StringBuffer类的对象
StringBuffer sb=new StringBUffer("asdf");
sb.insert(3,"F");//将F插入3索引
```

> ***reverse***:将字符串反序输出

实例：

```java
//先创建一个StringBuffer类的对象
StringBuffer sb=new StringBUffer("asdf");
sb.reverse();//输出"fdsa"
```

> ***delete***:删除索引上的字符
>
> delete(start,end)//删除下标从start到end-1的字符

实例：

```java
//先创建一个StringBuffer类的对象
StringBuffer sb=new StringBUffer("asdf");
sb.delete(1,2);//删除“sd”
```

> ***toString***:将StringBuffer对象转换为字符串

实例：

```java
//先创建一个StringBuffer类的对象
StringBuffer sb=new StringBUffer("asdf");
sb.toString();//将sb容器里的值转换成字符串
```

> 其他放与String类相似

##### *StringBuilder*

用法：

```java
StringBuilder 对象名=new StringBuilder();
```

> 其方法与StringBuffer相同

##### StringBuffer与StringBuilder不同之处

|           类名           |   String   | StringBuilder | StringBuffer |
| :----------------------: | :--------: | :-----------: | :----------: |
|         对象类型         | 字符串常量 |  字符串变量   |  字符串变量  |
|        线程安全性        |   不安全   |    不安全     |     安全     |
| 执行效率（大部分情况下） |     低     |      高       |      中      |

根据表中内容，可以总结这些类的适用场景：

1. 操作少，数据少，用String。
2. 单线程，操作多，用StringBuilder。
3. 多线程，操作多，用StringBuffer。

### 数组

##### 一维数组

​	一维数组分为：整型数组、小数数组、字符数组、字符串数组。

> 创建一维数组方法：

1. 直接给数组赋值

```Java
数据类型 [] 数组名={};//在{}中写数据
```

实例：

```Java
int [] arr={1,2,3,4};//创建整数数组arr，数组内容：1，2，3，4
```

2. 给数组指定长度

```java
数据类型 [] 数组名=new 数据类型 [];//方括号里写数组长度
```

实例：

```java
int [] arr=new int [5];//指定数组长度为5
```

##### **数组方法：**

> ***length***：获取数组长度

实例：

```java
//先创建一维数组
int [] arr={0,1,2,3};
arr.length;//获取数组长度为4
```

- charAt：提取

------

需要导入java.util.Arrays包

> ***Arrays.fill***：数组填充

> [!CAUTION]
>
> 调用此方法数组不应该有值，有值也会被覆盖

1. Arrays.fill(数组，填充值)

实例：

```Java
//先创建数组
int [] arr =new int [3];
Arrays.fill(arr,13);//arr数组中变成{13，13，13}


//如果原本有值，将被覆盖
int [] arr2={1,2,3};
Arrays.fill(arr2,13);//原数组{1,2,3}，将被覆盖成{13，13，13}
```

2. Arrays.fill(数组，开始索引，结束索引-1，填充值)

实例：

```Java
//创建数组
int [] arr={1,2,3};
Arrays.fill(arr,0,2,13);//原数组索引0~1的值变成13
```



> ***Arrays.sort***：数组排序（升序：小到大）

Arrays.sort(数组)

实例：

```
//创建数组
int [] arr ={8,9,4,1,3,7};
Arrays.sort(arr);//结果：{1，3，4，7，8，9}
```



> ***Arrays.copyOf***：复制数组

1. 新数组 = Arrays.copyOf(老数组，新数组长度)

实例：

```java
//原数组
int [] arr={1,2,3,4};

int [] newArr=Arrays.copyOf(arr,5);//newArr={1,2,3,4,0},不足的将由数据类型的默认值填充
```



2. 新数组=Arrays.copyOfRange(老数组，开始索引位置，结束索引位置-1)

实例：

```
//原数组
int [] arr={1,2,3,4};
int [] newArr=Arrays.OfRange(arr,1,3);//结果：{2，3}
```



------



> 一维数组遍历（for循环）

实例：

```java
//先创建一个一维数组，以int类型为例
int [] arr ={1,2,3,4,5,6};//创建数组，组内元素为1,2,3,4,5,6
for (int i=0;i<arr.length;i++){
	System.out.print(arr[i]);//打印0~arr.length-1索引的所有元素
}
```



##### 二维数组

二维数组也分为：整型数组、小数数组、字符数组、字符串数组。

> 创建二维数组方法

1. 直接赋值

```java
数据类型 [][] 数组名={};// 在{}中写数据
```

实例：

```Java
//创建二维数组
int [][] arr={{0,1,2,3},{4,5,6,7}};
arr[1][2]=36;//将arr二维数组中的
```

2. 指定长度

```Java
数据类型 [][] 数组名=new 数据类型 [][];//在方括号内指定数组长度
```

实例：

```java
//创建二维数组
int [][] arr = new int [2][3]; 
```

> [!CAUTION]
>
> 二维数组左边的[]表示行，右边的[]表示列

> 二维数组与一维数组的方法相同

> ##### **二维数组遍历**（for循环）

> [!NOTE]
>
> 二维数组使用循环嵌套

```Java
实例：
//先创建一个二维数组，以int类型为例
int [][] arr={{1,2,3},{4,5,6}};
for(int i=0; i<arr.length;i++){
    for(int j=0;j<arr[i].length;j++){
        System.out.println(arr[i][j]);
    }
}
```



### 算法

------

##### 排序

> 冒泡排序

升序：拿着一位与后面的对比，如果后一位比前一位小，则交换位置，比前一位大，则反之。

降序：反之。

升序实例：

```java
//现有一组数据很乱的数组
int [] arr ={2,3,9,5,4,7,1,6,8};
for(int i=0;i<arr.length;i++){
	for(int j=0;j<arr.length;j++){
		if(arr[i]<arr[j]){
			int temp=arr[i];
			arr[i]=arr[j];
			arr[j]=temp;
		}
	}
}
```

> 快速排序

实例：

```java
   int [] arr ={2,3,9,5,4,7,1,6,8};
        for(int i=1;i<arr.length;i++){
            int index=0;
            for(int j=1;j<=arr.length-i;j++){
                if(arr[index]<arr[j]){
                   index=j;
                }
            }
            int temp =arr[arr.length-i];
            arr[arr.length-i]=arr[index];
            arr[index]=temp;
        }
```

### 面向对象

##### 类

> 成员变量

成员变量是类的属性。

实例：

```java
//创建一个类
public static Bird{
	String wing;//翅膀
	String claw;//爪子
	String feather;羽毛
}
```



> 成员方法

成员方法是类的行为。

成员方法要有返回值，void除外。

实例：

```Java
public class Animals{
	public void eat(String meat){
	//动物吃东西
	}
	public void sleep(){
	//睡觉
	}
}
```



> 局部变量

局部变量是在成员方法中定义的变量

实例：

```Java
public class Test{
	int j=10;//成员变量
	public int number(){
		int i=20; //局部变量
		return i+this.j;//结果：30
	}
}
```

> [!NOTE]
>
> 局部变量只在定义它的方法内有效；
>
> 局部变量和成员变量可以重名，但是局部或成员中不能命名两个相同的变量名。
>
> 实例：
>
> ```java
> public class Test{
> 	String name="张三";
> 	public void getName(){
> 		String name="李四";//这里的两个name可以重名
> 		System.out.print(name+this.name);
> 	}
> ```
>
> 

> this关键字：this后面的变量是成员变量

在类中this表示类本身的对象

实例：

```java
public class Test{
	String name="张三";
	public void getName(){
		String name="李四";
		System.out.print(name+this.name);
	}
	public static void main(String [] args){
	    Test t=new Test();
	    t.getName();//打印李四张三
	}
}
```

> [!NOTE]
>
> 类的方法追寻就近原则。
>
> 实例：
>
> ```java
> public class Test{
> 	String name="张三";
> 	public void getName(){
> 		String name="李四";
> 		System.out.print(name);//这里就会打印李四
> 	}
> ```
>
> ```Java
> public class Test{
> 	String name="张三";
> 	public void getName(){
> 		System.out.print(name);//这里就会打印张三
> 	}
> ```
>
> 

##### 构造方法

1. 无参构造方法

定义一个没有参数的构造方法，如果自己不定义无参构造，编译器也会自动创建无参构造，除非定义了有参构造

实例：

```Java
public class Test{
	public Test(){}//无参构造
}
```

2. 有参构造

创建构造方法就是在无参构造后面的括号里，写入想要获取的参数

实例：

```Java
public class Test{
	public Test(int i,String){//构造方法获取数字和字符串
	}
}
```

3. 构造方法里的this关键字

可以调用类中的构造方法、成员变量、成员方法。

实例：

```java
public class Test{
	int i=6;
	public Test(){
	this(9);//调用Test的有参构造方法
    this.getNum();//调用成员方法
	}
    public void getNum(){}
	public Test(int i){
    System.out.print(this.i);//调用成员变量
    System.out.print(i);//调用局部变量
	}
}
```

4. 私有构造方法

私有构造方法外部类不能访问，只供本类访问，但可以创建静态方法提供访问

实例：

```Java
public class Test{
	private Test(){
	}
	public static newTest(){
	return new	Test();//创建Test对象
	}
	public static void main(String [] args){
		Test t=Test.newTest();
	}
}
```



> static关键字















### lambda表达式

```java
()->{}
```

()对应着方法的形参

->固定格式

{}对应方法的方法体

> [!CAUTION]
>
> lambda表达式可以用来简化匿名内部类的书写
>
> lambda表达式只能简化函数式的匿名内部类的写法
>
> 函数式接口：有且仅有一个抽象方法的接口叫做函数式接口，接口上方可以加@FunctionalInterface注解

