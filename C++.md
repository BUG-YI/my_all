# C++入门



### 注释

> 单行注释

在当行开头输入'//'



实例：

```c++
//注释这一行
```



> 多行注释

'/*    */'代表多行注释，写在其中间的代码无效



实例：

```c++
/*写在中里的代码无效
这里同样无效
*/
```



### 标识符命名规则

1. 不能使用关键字
2. 只能是下划线、数字、字母组成
3. 第一给字符必须为下划线或字母
4. 区分大小写



### 变量

在程序中是可变的值

创建方式：数据类型  变量名=变量初始值；

实例：

```C++
//首先创建一个c++程序
#include <iostream>
using namespace std;

int main(){
    int a=10; //创建了一个变量a并赋值为10
    cout <<a;
}
```



### 常量

在程序中定义了之后不可变

创建方式：

1. 宏常量通常在文件上方定义

​		#define  常量名   常量值；

1. const 数据类型  常量名=常量值；



实例：

```c++
//首先创建一个c++程序
#include <iostream>
using namespace std;

#define b 10;  //创建了一个常量b并赋值为10

int main(){
    const int a=10; //创建了一个常量a并赋值为10
}
```



### 基本数据类型

创建语法：数据类型  变量名  =变量初始值；

数据类型存在的意义：给数据划分空间，减少资源浪费



#### sizeof关键字

可以统计数据类型所占用的内存大小

用法：

sizeof（数据类型/变量）

实例：

```c++
//首先创建一个c++程序
#include <iostream>
using namespace std;

int main(){

    cout <<"int所占用的内存空间："<<sizeof(int);  //打印int所占用的内存空间：4
}
```



#### 整型

创建方式：数据类型  变量名=数据；

| 数据类型  |                          占用空间                          |          取值范围          |
| :-------: | :--------------------------------------------------------: | :------------------------: |
|   short   |                           2字节                            | （-2的15次方~2的15次方-1） |
|    int    |                           4字节                            | （-2的31次方~2的31次方-1） |
|   long    | Windows为4字节，Linux（32位）为4字节，Linux（64位）为8字节 | （-2的31次方~2的31次方-1） |
| long long |                           8字节                            | （-2的63次方~2的63次方-1） |



> int：整形    

实例：

```c++
//首先创建一个c++程序
#include <iostream>
using namespace std;

int main(){
    int a=10;  //创建一个整型a并赋值10
    cout <<a;  //打印10
}
```



> short：短整型

实例：

```c++
//首先创建一个c++程序
#include <iostream>
using namespace std;

int main(){
    short a=10;  //创建一个短整型a并赋值10
    cout <<a;  //打印10
}
```



> long：长整型

实例：

```c++
//首先创建一个c++程序
#include <iostream>
using namespace std;

int main(){
    long a=10;  //创建一个长整型a并赋值10
    cout <<a;  //打印10
}
```



> 长长整型

实例：

```c++
//首先创建一个c++程序
#include <iostream>
using namespace std;

int main(){
    int a=10;  //创建一个长长整型a并赋值10
    cout <<a;  //打印10
}
```



#### 浮点型 

创建方式：数据类型  变量名=数据；



1. float单精度，要在数据后面加 f

2. double双精度



| 数据类型 | 占用空间 |  有效数字范围   |
| :------: | :------: | :-------------: |
|  float   |  4字节   |   7位有效数字   |
|  double  |  8字节   | 15~16位有效数字 |



实例：

```c++
//首先创建一个c++程序
#include <iostream>
using namespace std;

int main(){
	float a=1.7f;  //float类型
	
	double b=1.23;  //double类型
    
}
```





#### 字符型

创建方式：数据类型  变量名=数据；

字符类型只占用一个字节



实例：

```c++
//首先创建一个c++程序
#include <iostream>
using namespace std;

int main(){
	char a='a'; //字符类型
}
```



#### 字符串

两种风格

1. c++风格

​	string  变量名 =字符串；

2. c风格

​	char  变量名 [] =字符串；



实例：

```c++
//首先创建一个c++程序
#include <iostream>
using namespace std;

int main(){
char a[]="你好！"; //字符类型c风格
string b= "你好！"; //字符类型c++风格

}
```



bool类型

有只两个值：true（本质为1）和false（本质为0）

bool  变量名=bool值；





#### 转义字符

常用转义字符：\n（换行），\\\（输出反斜杠\），\t（制表符） 



### 数据输入

> cin：命令行接收数据

用法：

数据类型  变量名=变量值；

cin >>变量名；



实例：

```c++
//首先创建一个c++程序
#include <iostream>
using namespace std;

int main(){
    int a=0;
    cout<<"请输入数字";
    cin >> a ;
}
```



### 运算符

#### 算数运算符

> +（加），-（减），*（乘），/（除），%（取模）

取模可理解为取余



实例：

```c++
//首先创建一个c++程序
#include <iostream>
using namespace std;

int main(){
    int a=10;
    int b=20;

    // +
    cout<<a+b<<endl; //打印30

    // -
    cout<<b-a<<endl;  //打印10

    // *
    cout<<b*a<<endl;  //打印200

    // /
    cout<<b/2<<endl;  //打印10
    
    cout<<b%a<<endl;  //打印0
}
```



> 前置递增与后置递增都是 ++

区别：

前置递增先将数据增加再进行运算

后置递增是先进行运算再增加



实例：

```C++
//首先创建一个c++程序
#include <iostream>
using namespace std;

int main(){
    int a=1;
    int b=1;
    cout <<a++ *10<<endl;  //先运算a++ *10，再给a加1
    cout <<++b *10<<endl;  //先给b加1，再运算b++ *10
}
```



> 前置递减与后置递减都是 --

和上述递增同理



#### 赋值运算符

> 赋值运算  =，+=，-=，*=，/=，%=

实例：

```c++
//首先创建一个c++程序
#include <iostream>
using namespace std;

int main(){
	// =
    int a=1; //直接赋值
    
    // +=
    a+=1; //等同于a=a+1
    
    // -=
    a-=1;  //等同于a=a-1
    
    // *=
    int b=2;
    b*=2;  //等同于b=b*2
    
    // /=
     b/=2;  //等同于b=b/2
    
    // %=
     b%=2;  //等同于b=b%2
}
```



#### 比较运算符

> ==（等于），>（大于），<（小于），>=（大于等于），<=（小于等于），!=（不等于）

实例：

```C++
//首先创建一个c++程序
#include <iostream>
using namespace std;

int main(){
    int a=10;
    int b=9;
    cout << (a==b)<<endl;  //打印0，也就是false
    cout << (a>b)<<endl;  //打印1，也就是true
    cout << (a<b)<<endl;  //打印0，也就是false
    cout << (a>=b)<<endl;  //打印1，也就是true
    cout << (a<=b)<<endl;  //打印0，也就是false
    cout << (a!=b)<<endl;  //打印1，也就是true

}
```



#### 逻辑运算符

> ！（非），||（或），&&（与/和）

&&：左右两边同时成立，即真

||：只要有一个条件成立，就是真

!：非，条件为真返回假，条件为假返回真



实例：

```c++
//首先创建一个c++程序
#include <iostream>
using namespace std;

int main(){
    cout<<(true || false)<<endl;  //打印1，也就是true
    cout<<(true && false)<<endl;  //打印0，也就是false
    cout<<(!false)<<endl;  //打印1，也就是true
}
```



#### 三目运算符（三元运算符）

判断条件？执行语句1：执行语句2；

如果条件为真，执行语句1，如果为假，执行语句2



实例：

```c++
#include <iostream>
using namespace std;

int main(){
   int a=10;
   int b=20;
   
   cout<<(a>b?100:50);  //打印50
}
```





### 流程结构

#### 选择结构

##### if判断语句

满足if条件执行里面的代码块

用法：

1. 单条件if：

if（条件）{代码块}

else{代码块}



2. 多条件if：

if（条件）{代码块}

else if（条件）{代码块}

......

else{代码块}





实例：

```c++
//判断一个数是否大于10
#include <iostream>
using namespace std;

int main(){
    int a=5;
    if (a>10){
    cout<<"a>10";
    }else{
    cout<<"a<10";
    }
    
}
```



##### switch选择语句

> [!IMPORTANT]
>
> 要在每条case的结尾加上break不然，会一直向下执行switch中所有代码
>
> default后面可以选择不加，default就是最后一条



用法：

switch(选择语句){

case 1：执行语句；break；

case 2：执行语句；break；

.......

default：执行语句；

}

实例：

```c++
#include <iostream>
using namespace std;

int main(){
   int a=0;
   cout<<"请输入一个整数（1~3）";
   cin>>a;
   switch(a){
       case 1:cout <<"输入的是1";
           break;
       case 2:cout <<"输入的是2";
           break;
       case 3:cout <<"输入的是3";
           break;
       default:cout <<"输入错误";
           break;
      }
}
```



#### 循环结构

##### for循环

用法（初始变量；条件；末尾语句）{代码块}



实例：

```c++
#include <iostream>
using namespace std;

int main(){
for(int i=0;i<10;i++){
cout <<i<<endl;     //打印0~9
}
}
```



##### while循环

如果while条件一直成立会一直执行while循环体，称之死循环

用法：

while(判断语句){代码块}



实例：

```C++
#include <iostream>
using namespace std;

int main(){
    int a=5;
    while(a<10){   //当a的值为10，while循环结束
    cout<<a<<endl;
    a++;
    }
    
    
}
```



##### do...while循环

先执行do中的代码块，再进行判断

用法：

do{代码块}

while（判断语句）；



实例：

```c++
#include <iostream>
using namespace std;

int main(){
    int a=5;
    do{						//当a的值为10，while循环结束
        cout<<a<<endl;
        a++;
    }
    while(a<10);
}
```

##### 循环嵌套

一个循环中嵌套另一个循环



实例：

```c++
#include <iostream>
using namespace std;

int main(){
    for(int i=0;i<4;i++){
        for(int j=0;j<4;j++){
            cout<<"*  ";
        }
        cout<<endl;
    }
}
/*
//打印一个正方形
*  *  *  *
*  *  *  *
*  *  *  *
*  *  *  *

 */
```



#### 跳转语句

##### break

跳出选择结构或者循环结构



实例：

```c++
//以for循环为例
#include <iostream>
using namespace std;

int main(){
    for(int i=0;i<10;i++){

        if(i==5){
            break;          //从0打印到4，i=5时结束了循环，不再打印后面的数
        }
        cout<<i<<endl;
    }
}
```



##### continue

跳出该次循环，继续后面的循环



实例：

```c++
//以for循环为例
#include <iostream>
using namespace std;

int main(){
    for(int i=0;i<10;i++){

        if(i==5){
            continue;          //从0打印到4，i=5时结束该次循环，继续打印后面的6~9
        }
        cout<<i<<endl;
    }
}
```



##### goto语句（一般情况不建议使用）

代码执行到goto时会跳转到标记位置，如果中间有代码会跳过不执行

用法：

执行语句1；

goto:标记;

执行语句2；

标记：

执行语句3；



实例：

```c++
#include <iostream>
using namespace std;

int main(){
    cout<<1<<endl;
    goto POOL;
    cout<<2<<endl;
    cout<<3<<endl;
    POOL:						//跳过2，3执行4
    cout<<4<<endl;
}
```



### 数组

数组的用途可以查看数组在内存空间中占用了多少  用sizeof函数

直接打印数组可以查看数组的首地址

用&可以查看每一个元素的地址值，例：打印&arr[0]



#### 一维数组

> 创建方式：

1. 数据类型  数组名  [数据长度] ={元素1，元素2，....}；
2. 数据类型  数组名  [数据长度]；  //用于后续放置数据
3. 数据类型  数组名  []={元素1，元素2，....}；

> 查询方式：使用索引,索引从0开始

索引0为数组的第一个元素，以此类推

用法：

数组名  [0]；

> 添加方式：

数组名  [0]=数据；



实例：

```c++
#include <iostream>
using namespace std;

int main(){
    int arr1 []={1,2,3,4};
    string arr2 []={"nihao","zhangs","lishi"};
    double arr3 [2];
    arr3[0]=1.1;     //往arr3中添加元素
    arr3[1]=1.2;
    cout <<arr3[0];  //查询arr3中的第一个元素
}
```



#### 二维数组

二维数组遍历需要用嵌套循环，外层打印行数，内层打印列数

创建方式：（推荐使用前两种）

1. 数据类型  数据名[行数] [列数]；
2. 数据类型  数据名[行数] [列数]={{元素1，元素2}，{元素3，元素4}}；
3. 数据类型  数据名[行数] [列数]={元素1，元素2，元素3}；  //会根据行列顺序填充
4. 数据类型  数据名[]  [列数]={元素1，元素2，元素3}；  //会根据列数计算每一行有多少，超出则多加一行



实例：

```c++
#include <iostream>
using namespace std;

int main(){
    //第一种
    int arr[2][2];  //创建数组
    arr[0][0]=1;  //给数组的每一项添加元素
    arr[0][1]=2;
    arr[1][1]=3;
    arr[1][0]=4;
    //只演示arr数组，其余同理
    for (int i=0;i<sizeof(arr)/sizeof(arr[0][0])/2;i++) {
        for (int j=0;j<sizeof(arr)/sizeof(arr[0][0])/2;j++) {
        cout<<arr[i][j]<<" ";
        }
        cout<<endl;
    }


    //第二种
    int arr1[2][2]={{1,2},{3,4}};

    //第三种
    int arr2[2][2]={1,2,3,4};

    //第四种
    int arr3[][2]={1,2,3,4};

}
```



### 算法

#### 冒泡排序

```c++
#include <iostream>
using namespace std;

int main(){
    int arr1 []={1,435,4,6,2,3,9,8};
    int length=sizeof(arr1)/sizeof(arr1[0]);   //通过数组占用的内存除一个元素占的内存得到数组长度
    for (int i=0;i<length;i++) {
        for (int j = 0; j < length; j++) {
            if (arr1[i]<arr1[j]) {
                int temp=arr1[i];
                arr1[i]=arr1[j];
                arr1[j]=temp;
            }
        }
    }
    for (int i:arr1) {
        cout<<i<<endl;
    }
}
```



### 函数

作用：将重复代码写在一个函数内，用的时候进行调用，使代码更加简洁



在函数创建时括号里定义的参数，为形式上的参数，称之形参

在其他位置的为实际参数，称为实参

创建：   //如果函数不需要返回值，返回值数据类型可以写  void

返回值数据类型  函数名  （数据类型  形参1，数据类型  形参2....）{  

代码块  

return  表达式；//函数不需要返回值时，可以不写}



调用：

函数名（参数）；  //如果创建是定义了参数，才需要传，没有就不写



值传递

实参传递给形参，形参发生改变不影响实参



> [!NOTE]
>
> 函数不能定义在主函数main内



实例：

```c++
#include <iostream>
using namespace std;
//定义一个add函数用于计算两数之和
double add(double a,double b) {
        return a+b;
    }
int main(){
    double c = add(2,44);
    cout <<c;
}

```



#### 函数声明

如果定义的函数写在主函数后面，才需要声明    //一个函数声明只需要写一次

声明方法：
返回值数据类型  函数名  （数据类型  形参1，数据类型  形参2....）；



实例：

```c++
#include <iostream>
using namespace std;
//定义一个add函数用于计算两数之和
double add(double a,double b);
int main(){
    double c = add(2,44);
    cout <<c;
}
double add(double a,double b) {
        return a+b;
    }
```



#### 分文件编写

可以创建一个头文件来声明函数

头文件后缀为.h

用法：
在头文件中写

#include <iostream>
using namespace std;  //声明

返回值数据类型  函数名  （数据类型  形参1，数据类型  形参2....）；  //声明函数



在源文件中写

#include  "头文件名.h"

实例：

头文件

```c++
#include <iostream>
using namespace std;

double add(double a,double b);
```

源文件

```c++
#include "head.h"
//定义一个add函数用于计算两数之和
int main(){
    double c = add(90,44);
    cout <<c;
}
double add(double a,double b) {
    return a+b;
}
```



### 指针

指针的作用：可以通过指针间接访问内存

可以通过指针访问变量

通过修改指针变量，会修改原始变量的值



创建指针：

数据类型  *指针变量；

指针变量=&变量名；  //用&提取变量名的地址值，并赋值给指针变量

*指针变量  //可以访问变量

实例：

```C++
#include <iostream>
using namespace std;

int main(){
    //创建变量
    int a=9;
    int *p;
    p=&a;
    cout<<p<<endl;  //打印a的地址值
   
    cout<<*p<<endl;  //打印a的值  //解引用
    *p=10;  //这里改变了*p,a的值也随之改变
}
```



指针所占用的空间

在32位操作系统中所有数据类型都为4位

在64位操作系统中所有数据类型都为8位



实例

```c++
#include <iostream>
using namespace std;

int main(){
    //32位
    //只列举int类型
    cout<<sizeof(int *)<<endl;  //32位中占4位

    //64位
    cout<<sizeof(int *)<<endl;  //32位中占8位
}
```



#### 空指针和野指针

> 空指针：指针指向内存空间编号为0的空间

用途：初始化指针变量

> [!WARNING]
>
> 空指针指向的内存是不可访问的，0~255为系统占用内存



实例：

```c++
#include <iostream>
using namespace std;

int main(){
   int * p=NULL;  //创建了空指针
  // *p=100;  //会报错，空指针不允许访问，
   
}
```



> 野指针：指针变量指向非法的内存空间，没有申请的空间	



实例：

```c++
#include <iostream>
using namespace std;

int main(){
    int * p=(int *)0x1111;  //创建了野指针
    cout<<*p;
}
```



#### const修饰指针

> const修饰指针——常量指针

用法：const  数据类型  *指针名=地址值

指针的指向可以修改，但指针指向的值不可以修改



实例：

```C++
#include <iostream>
using namespace std;

int main() {
    int a = 10;
    int b = 10;
    const int *p = &a;
    p = &b;  //指针的指向可以修改
    //*p=23;  //指针指向的值不可以修改
}

```



> const修饰常量——指针常量

用法：数据类型  * const  指针名=地址值

指针指向的值可以修改，但指针的指向不可以修改



实例：

```c++
#include <iostream>
using namespace std;

int main() {
    int a = 10;
    int b = 10;
    int *const p = &a;
    //p = &b;  //指针的指向不可以修改
    *p = 23; //指针指向的值可以修改
}
```



> const即修饰常量又修饰指针

指针的指向和指针指向的值都不可以修改



实例：

```c++
#include <iostream>
using namespace std;

int main() {
    int a = 10;
    int b = 10;
    const int *const p = &a;
    //p = &b; //指针的指向不可以修改
    //*p = 23; //指针指向的值也不可以修改
}

```



#### 指针和数组



实例：

```c++
#include <iostream>
using namespace std;

int main() {
    int arr[]={1,2,3,4,5,6};
    cout<<"第一个元素为"<< arr[0]<<endl;
    int *p=arr;
    cout<<"第一个元素为"<< *p<<endl;
    
    p++;  //指针p向后偏移了4个字节
    cout<<"第二个元素为"<< *p<<endl;
}
```

> 用指针遍历数组



实例：

```c++
#include <iostream>
using namespace std;

int main() {
    int arr[]={1,2,3,4,5,6};
    int *p=arr;
    for(int i=0;i<sizeof(arr)/sizeof(arr[0]);i++){
        //cout<<arr[i]<<" ";  //这里是使用原来的for循环
        
        //下面用指针遍历数组
        cout<<*p<<" ";
        p++;
    }
}
```



#### 指针和函数

地址传递会改变实参的数据



实例：

```c++
#include <iostream>
using namespace std;

//写一个用于交换两个变量地址的函数
void jh(int *a,int *b){
	int temp=*a;
	*a=*b;
	*b=temp;
	cout <<*a<<endl;
	cout <<*b;
}
int main() {
	int a=10;
	int b=20;
    jh(&a,&b);  //地址传递会改变实参的数据
}
```



#### 函数传递数组

创建函数时传输数组时用指针传递

数据类型 函数名（数据类型  *数组名，....){函数体}



返回数组的方式：

实例:

```c++
#include <iostream>
using namespace std;

//写一个用于交换两个变量的函数
int *jh(int *arr, int len) {
    for (int i = 0; i < len; i++) {
        for (int j = 0; j < len; j++) {
            if (arr[i] < arr[j]) {
                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }
    }
    for (int i = 0; i < len; i++) {
        cout << arr[i] << " ";
    }
    return arr;
}

int main() {
    int arr[] = {1, 23, 4, 5, 6};
    int len = sizeof(arr) / sizeof(arr[0]);
    jh(arr, len);
}

```



### 结构体

结构体是用户自定义的数据类型，运行用户储存同的数据类型



#### 结构体的定义和使用

> [!NOTE]
>
> 如果结构体里用了string，需要导入#include<string> ,不然有点时候会报错

用法：struct  结构体名{数据类型   变量名1，数据类型   变量名2，......}；

创建方式：

-  结构体名  变量名
-  结构体名  变量名 = {变量名1，变量名2，......}
- 定义结构体时顺便创建变量

在主函数中调用：

> 第一种：

创建实例对象：结构体名 对象名；

对象名.变量名=数据；



实例：

```c++
#include <iostream>
using namespace std;
#include<string>

struct student {
    string name;			//有字符串name，要加上#include<string>
    int age;
};

int main() {
     student stu; 
    stu.age=19;
    stu.name="zhangs";
    cout<<stu.name<<" "<<stu.age;
}
```



> 第二种：需要按顺序传参

创建实例对象：结构体名 对象名={"数据1","数据2","数据3"，...}；



实例：

```c++
#include <iostream>
using namespace std;
#include<string>

struct student {
    string name;
    int age;
};

int main() {
    student stu{"zhangs",18};
    cout<<stu.name<<" "<<stu.age;
}
```



> 第三种

struct  结构体名{数据类型   变量名1，数据类型   变量名2，......}实例对象；



实例：

```c++
#include <iostream>
using namespace std;
#include<string>

struct student {
    string name;
    int age;
}stu;        //这里直接创建了实例对象

int main() {
    stu.age=19;
    stu.name="zhangs";
    cout<<stu.name<<" "<<stu.age;
}
```



#### 结构体数组

将定义的结构体放在数组中方便维护



创建结构体

调用：

struct  结构体名  数组名[元素个数]={{数据1}，{数据2}，.....};     //struct可以省略

修改可以用  数组名.变量名=数据；



实例：

```c++
#include <iostream>
using namespace std;
#include<string>

struct student {
    string name;
    int age;
}stu;        //这里直接创建了实例对象

int main() {
    student arr[2]={
        {"zhangs",18},
        {"lisi",19}
    };
    arr[1].name="wangwu";    //修改名字和年龄
    arr[1].age=20;
    
    for (int i=0;i<sizeof(arr)/sizeof(arr[0]);i++) {
        cout<<arr[i].name<<" "<<arr[i].age<<endl;
    }
}
```



#### 结构体指针

作用：可以通过结构体指针访问结构体成员

需要用`->`访问结构体中的属性



实例：

```c++
#include <iostream>
using namespace std;
#include<string>

struct student {
    string name;
    int age;
};        //这里直接创建了实例对象

int main() {
    student stu={"zhangs",12};
    student *p=&stu;
    cout<<"name:"<<p->name<<",age："<<p->age;
}
```

