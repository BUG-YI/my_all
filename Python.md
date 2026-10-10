# Python入门

### 环境搭建

### 基本语法规范

### 运算符

##### 算数运算符

> +（加），-（减），*（乘），/（除），%（取余），//（商）

实例：

```python
i=15
j=3
#  +
print(i+j) #打印18

#  -
print(i-j) #打印12

#  *
print(i*j) #打印45

#  /
print(i/j) #打印5

#  %
print(i%2) #打印0

#  //
print(i//j) #打印5
```

##### 比较运算符（bool）

> ==（等于），>（大于），<（小于），>=（大于等于），<=（小于等于），!=（不等于）

实例：

```python
i=10
j=13

#  ==
print(i==j) #打印False

#  >
print(i>j) #打印False

#  <
print(i<j) #打印True

#  >=
print(i>=j) #打印False

#  <=
print(i<=j) #打印True

#  !=
print(i!=j) #打印True
```



赋值运算符

> =（直接赋值），+=（先加再赋值），-=（先减再赋值），......

实例：

```python
#  =
i=10 #给i赋值为10
p=20 #给p赋值为20
j='你好！' #给j赋值 你好！

#  +=
i+=1
print(i) #打印11

#  -=
p-=1
print(p) #打印19
```



##### 逻辑运算符（bool）

> and,or,not

and：左右两边同时成立，即真

or：只要有一个条件成立，就是真

not：非，条件为真返回假，条件为假返回真

> [!TIP]
>
> 若同时出现两个及以上的逻辑运算符，建议将先判断的两个条件加上（），避免出现歧义

实例：

```python
# and
print(True and True) #打印True
print(True and False) #打印False

# or
print(False or False) #打印False
print(True or True) #打印True
print(True or False) #打印True

# not
print(not True) #打印False
print(not False) #打印True
```



##### 成员运算符

> in，not in

in：判断什么在什么当中出现了

not in：判断什么在什么当中没有出现

实例：

```python
#创建列表
lis=[5,2,3,6]

# in
print(3 in lis) #打印True

#not in
print(3 not in lis) #打印False
```











### 输入与输出

> input：输入

input函数接收控制台传入的数据

```python
input()
```



> print：输出

print函数打印括号里想要展示的数据

```python
print("hello world") #这里打印hello world
```



> 占位符

1. %s：字符串占位符      %d：数字占位符

实例：

```python
name="张三"
age=18
print("姓名：%s,年龄：%d岁"%(name,age)) #输出姓名：张三,年龄：18岁
```

2.{}.format

实例：

```python
name="张三"
age=18
print("姓名：{},年龄：{}岁".format(name,age)) #输出姓名：张三,年龄：18岁
```

3. f  {}

实例：

```python
name="张三"
age=18
print(f"姓名：{name},年龄：{age}岁") #输出姓名：张三,年龄：18岁
```



### 数据类型

##### int类型

int类型接收整数，如：i=9

##### float浮点数类型

float接收小数，如：i=5.4

##### complex复数

complex接收以j结尾的复数，如：i=4+4j

##### bool布尔类型

布尔类型只有两个参数，true和false，true记作1，false记作0

##### string字符串类型

string接收任意字符串，需要引号引起来，如："你好~"

> [!NOTE]
>
> 对字符串进行常规操作，不会改变原字符串，都会返回一个新的字符串



> 字符串的切片

能截取字符串一部分字符

1. 变量[开始索引:结束索引] #不包括结束索引字符，如果输入的是负数将从右向左数，最右边的第一位索引是-1

实例：

```python
i="hello，world"
print(i[2:6]) #截取2-5索引的字符，不包括6，打印llo，

print(i[-3:-1]) #打印rl
```

2. 变量[开始索引:结束索引:间隔]，如果是间隔负数截取的就是右边的

实例：

```python
i="hello，world"
print(i[2:6:2]) #打印lo,注意l是2索引的

print(i[-3:-1:-1]) #打印dl
```



> 字符串的索引

能够拿取字符串对应索引字符

实例：

```python
i="hello world"
print(i[0]) #打印h
```

> capitalize：将字符串首字母换成大写

实例：

```python
i="hello,world"
print(i.capitalize()) #Hello,world
```



> title：将每一个单词首字母变成大写

实例：

```python
i="hello,world"
print(i.title()) #打印Hello,World
```



> lower：全变为小写

实例：

```python
i="HELlo,woRld"
print(i.lower()) #打印hello,world
```



> upper：所有字母变为大写

实例：

```py
i="hello,world"
print(i.upper()) #打印HELLO,WOELD
```

> 忽略大小写
>

实例：

```py
#将用户输入的验证码和提示的验证码，都全转为大写或小写
i='Po2e'
user_input=input(f'请输入验证码{i}：')
if user_input.upper()==i.upper():
	print("验证成功")
else:
	print('验证失败')
```

> strip：去掉左右两边的空白符（空格，\t，\n）
>

实例：

```python
i="  fsa  d  "
print(i.strip()) #打印fsa  d
```



> replace：替换

replace(被替换的字符串，替换的字符串)

实例：

```python
i=" sfd f ds "
#将空格全部去掉
print(i.replace(' ','')) #打印sfdfds
```



> split：切割

split(切割的数据)，结果以列表返回

实例：

```py
i='java_python_c++_c#'
print(i.split('_')) #以'_'切割，然后将结果以列表的形式返回
					#打印['java', 'python', 'c++', 'c#']
```

> join：拼接列表

用法：

'用什么拼接'.join(列表)

实例：

```
i=['java', 'python', 'c++', 'c#']
print('_'.join(i)) #打印java_python_c++_c#
```





> find：查找

如果查找到了就返回第一个字的索引，如果没有就返回-1

实例：

```python
i='你好啊，朋友'
print(i.find('朋友')) #打印4
```



> index：也是查找

index与find不同，index没查找到就会报错

实例：

```python
i='你好啊，朋友'
print(i.index('朋友')) #打印4

#如果没有
print(i.index('12')) #会报错
```

> startswith：判断字符串是否以xxx开头

实例：

```py
i='你好啊，朋友'
print(i.startswith("你")) #判断结果为true
```



> len：判断字符串长度

实例：

```py
i="hello,world"
print(len(i)) #打印11
```



### 集合

##### 创建空集合

实例：

```
t=tuple() #元组
l=list() #列表
s=set() #集合
Str=str() #空字符串
```





##### list列表

> [!NOTE]
>
> 也和字符串一样有切片和索引

列表用中括号[]表示，元素以逗号隔开

实例：

```
i=[1,2,4,3]
```

###### 列表的增删改查

> append：增加

实例：

```py
#创建一个列表
i=[]
i.append("薛之谦")
print(i) #打印['薛之谦']
```



> insert：插入

insert(插入索引，元素)

实例：

```python
#创建一个列表
i=[1,2,3,4]
i.insert(1,3)
print(i) #打印[1, 3, 2, 3, 4]
```

> extend：合并两个列表

实例：

```python
i=[1,2,3,4,5]
p=['q','w','er','t','+']
i.extend(p)
print(i) #[1, 2, 3, 4, 5, 'q', 'w', 'er', 't', 'y']
```

> pop：删除

删除列表索引上的元素，返回元素值

实例：

```py
i=[1,2,3,4,5]
print(i.pop(0)) #删除0索引，1
print(i) #打印[2, 3, 4, 5]
```



> remove：删除某个元素

实例：

```py
i=[1,2,3,4,5]
i.remove(4)
print(i) #打印[1, 2, 3, 5]
```



> 修改和查询，直接用索引

实例：

```python
####修改
i=[1,2,3,4,5]
i[3]=9
print(i) #打印[1, 2, 3, 9, 5]
####查询
print(i[1]) #打印2
```



> 列表排序

sort：升序

实例：

```python
i=[5,2,3,1,4,5,9]
i.sort()
print(i) #打印[1, 2, 3, 4, 5, 5, 9]
```

reserve：列表元素反转

降序：先升序再反转

实例：

```python
i=[5,2,3,1,4,5,9]
i.sort()
i.reverse()
print(i) #打印[9, 5, 5, 4, 3, 2, 1]
```



> 列表嵌套

实例：

```py
i=[1,23,['张三','李四'],6,7,8,9]
#拿到张三，要i[2][0]
print(i[2][0]) #内嵌套的列表，在外列表的2索引，内列表的0索引
```





##### tuple元组（不可变列表）

用法：

元组用括号表示

使用场景：固定数据，不允许外界改变时用

> [!CAUTION]
>
> 如果元组里只有一个元素，需要在该元素后面加个逗号,否则python会将其视为字符串
>
> 实例：
>
> ```python
> i=("ni",)
> print(type(i)) #元组
> 
> p=("ni") #（）表示优先级
> print(type(p)) #字符串
> ```
>
> 如果元组里面有列表等可变数组，列表等的元素可以改变，但不能改变列表的地址值
>
> 实例：
>
> ```python
> i=(1,23,4,[9,8,7,6],0,7)
> i[3].append(156)
> print(i) #打印(1, 23, 4, [9, 8, 7, 6, 156], 0, 7)
> ```



##### set集合

set是一个无序列表，可以去重

set集合不能存储列表，存入集合的数据需要进行哈希计算

> [!NOTE]
>
> 可哈希：不可变的数据类型，int，Str，tuple，bool



若只有`i={}`python会将其认为是字典



> add：增加

实例：

```py
i=set()
i.add(12)
print(i) #在集合中增加元素12，打印{12}
```

> pop：删除最后的元素

由于set集合是无序的，pop删除充满随机性，使用remove



> remove：删除元素

实例：

```py
i={1,2,3,4,5,6}
i.remove(2)
print(i) #打印{1, 3, 4, 5, 6}
```



> 修改：由于set集合无序，先删除，再添加



> 查询：只能通过for循环查询



> set的交集，并集，差集

实例：

```python
i={1,2,3,4,5}
p={1,2,9,8,7,6}
#交集
print(i&p) #打印{1, 2}
print(i.intersection(p))

#并集
print(i|p) #打印{1, 2, 3, 4, 5, 6, 7, 8, 9}
print(i.union(p))

#差集
print(i-p) #后面集合有的去除，打印后面没有的{3, 4, 5}
print(i.difference(p))
```





##### dictionary字典

字典是用{}花括号，以键值对的形式进行存储

用法：
{键值：元素}

键值必须是可哈希数据类型

拿取获取元素，用键值

实例：

```python
#创建字典
dic={1:"周星驰",2:'薛之谦',3:'成龙'}
print(dic[2]) #打印薛之谦
```



###### 字典的增删改查

> 增加

实例：

```python
#创建字典
dic={1:"周星驰",2:'薛之谦',3:'成龙'}
dic["新增"]="路飞"
print(dic) #字典变为{1: '周星驰', 2: '薛之谦', 3: '成龙', '新增': '路飞'}
```



> 修改

修改就重新给键值赋值，原来的值将被覆盖

实例：

```python
dic={1:"周星驰",2:'薛之谦',3:'成龙'}
dic[1]="路飞"
print(dic) #字典变为{1: '路飞', 2: '薛之谦', 3: '成龙'}
```



> pop：删除

pop(键值)

实例：

```python
dic={1:"周星驰",2:'薛之谦',3:'成龙'}
dic.pop(1)
print(dic) #删除了1:"周星驰"
```



> 查询

用法：

1. 字典名[键值]

这个用法如果没有这个键值，程序会报错

2. 字典名.get(键值)

如果没有这个键值，会返回none

实例：

```python
dic={1:"周星驰",2:'薛之谦',3:'成龙'}
print(dic[1]) #打印周星驰


print(dic.get(1)) #打印周星驰
```



> keys：拿到所有的键值

实例：

```python
dic={1:"周星驰",2:'薛之谦',3:'成龙'}
print(dic.keys()) #拿到所有键值，并打印dict_keys([1, 2, 3])
```



> values：能够获取所有键值后面的元素

实例：

```python
dic={1:"周星驰",2:'薛之谦',3:'成龙'}
print(dic.values()) #dict_values(['周星驰', '薛之谦', '成龙'])
```



> item：能直接拿到键值和元素

实例：

```python
dic={1:"周星驰",2:'薛之谦',3:'成龙'}
print(dic.items()) #打印dict_items([(1, '周星驰'), (2, '薛之谦'), (3, '成龙')])
```



> for循环能够直接拿到键值和元素

用法：

for 键值，元素 in 字典名.items()

​	print(键值，元素)



实例：

```python
dic={1:"周星驰",2:'薛之谦',3:'成龙'}
for key,value in dic.items():
	print(key,value) #打印  1 周星驰
                     #     2 薛之谦
                     #     3 成龙
```



|        类型        |       描述        |                       说明                       |
| :----------------: | :---------------: | :----------------------------------------------: |
|    列表（list）    |  有序的可变序列   | Python中使用最频繁的数据类型，可有序记录一堆数据 |
|   元组（tuple）    | 有序的不可变序列  |       可有序记录一堆不可变的Python数据集合       |
|    集合（set）     |  无序不重复集合   |       可无序记录一堆不重复的Python数据集合       |
| 字典（dictionary） | 无序Key-Value集合 |    可无序记录一堆Key-Value型的Python数据集合     |

### 算法

##### 条件语句

> if语句

if  条件：

​	需要执行的语句（条件成立执行）

else:

​	需要执行的语句（条件不成立执行）

实例：

```python
s = input("请输入数字")
s2 = input("请输入数字")
if s>s2:
	print(s+"大")
else:
	print(s2+"大")
```



##### 循环语句

> while循环

while  条件：

​	循环体（条件成立执行，若条件不成立则退出循环）

实例：

```python
while True:
	print("你好啊！"); #死循环，一直打印你好啊！
```



> break结束语句

在循环体内使用break能跳出循环

实例：

```python
i=0
while True:
	print(i)
	i+=1
	if i==10:
		break #打印0-9，在10的时候跳出循环，循环了10次
```



> continue语句

停止当前循环，继续进行下次循环

实例：

```python
i=0
while i<10:
    if i==4:
        i+=1  #跳过4，继续后面的循环。如果这里不加i+=1，将陷入死循环，i一直是4
        continue
    print(i)
    i+=1
```

> for循环

range(数字)

range(开始数，结束数) #不包括结束数

range(开始数，结束数，中间间隔) #不包括结束数

实例：

```python
for i in range(10):
    print(i) #从0数到9，循环10次
for j in range(2,10):
    print(j) #从2数到9，循环8次
for q in range(2,10,2):
    print(q) #从2数到9，中间间隔两位，打印2，4，6，8
```

> pass占位符

可以先让代码通过，后续再修改这里







### 文本操作

> open(文件路径,mode='操作模式',encoding='字符编码')

#### 文件路径

1. 绝对路径：从d/c盘开始到该文件
2. 相对路径：当前文件找（建议使用）
3. ../(返回到上一层文件夹)

实例：

```python
#假设有一个文件路径'D:\笔记\计算机导论.md'
#现在我们的程序在'D:\笔记\程序'里面
p=open('../计算机导论.md') #这时就能读取到计算机导论.md文件
p.close()f
```

> [!TIP]
>
> 建议每次open打开使用之后，用close关闭文件

#### mode模式

##### r（read）:读取模式

```python
#假设有一个文件路径'D:\笔记\计算机导论.md'
p=open('笔记/计算机导论.md',mode='r',encoding='utf-8') #文件路径：笔记/计算机导论.md，模式：读取模式，编码:utf-8编码
read = p.read()
print(read) #打印文件内的内容
p.close() #关闭文件
```



> read：读取文件全部内容

实例：

```python
#假设有一个文件路径'D:\笔记\计算机导论.md'
p=open('笔记/计算机导论.md',mode='r',encoding='utf-8')
read = p.read()
print(read) #打印文件内的全部内容
```



> readline：读取文件一行内容

实例：

```python
p=open('笔记/计算机导论.md',mode='r',encoding='utf-8')
read = p.readline()
print(read) #读取第一行

#如果再将其写一遍将打印第二行
read = p.readline()
print(read) #读取第二行
```



> readlines：将文件内的所有文本放入列表中

实例：

```python 
p=open('笔记/计算机导论.md',mode='r',encoding='utf-8')
read = p.readlines()
#如果文件中有这些东西
'''
asdf
asfda
1231
2
3dfsag
'''
print(read) #返回一个列表，['asdf\n', 'asfda\n', '1231\n', '2\n', '3dfsag']
```



> [!IMPORTANT]
>
> > for：python很重要的读取方式
>
> 实例：
>
> ```python
> p=open('笔记/计算机导论.md',mode='r',encoding='utf-8')
> for i in read:
> 	print(i.strip()) #打印以下内容
> 	'''
> asdf
> asfda
> 1231
> 2
> 3dfsag
> 	'''
> ```
>
> 



##### w（write）：写入模式

在w模式下每次打开文件，如果文件里有内容，将被清空

如没有这个文件，会自动创建，然后写入



```python
#假设有一个文件路径'D:\笔记\计算机导论.md'
p=open('笔记\计算机导论.md',mode='w',encoding='utf-8') #文件路径：笔记/计算机导论.md，模式：读取模式，编码:utf-8编码
lis=['1','2','3','4']
p.write(lis[0])
p.write(lis[1])
p.write(lis[2])
p.write(lis[3]) #文件内将写入1234，如果想要其他效果，比如换行可以在后面加一个'\n'

p.close()
```

> for：循环

实例：

```python
p=open('笔记/计算机导论.md',mode='w',encoding='utf-8') #文件路径：笔记/计算机导论.md，模式：读取模式，编码:utf-8编码
lis=['1','2','3','4']
for i in lis:
	p.write(i)
	p.write('\n') #这就实现了换行
p.close()
```



##### a（append）：增加

在原有的文本后面追加

实例：

```python
p=open('笔记/计算机导论.md',mode='a',encoding='utf-8')
p.write('你好') #在原有的文件后面追加你好
p.close()
```



##### b：读写分文本文件

读取非文本文件不写encoding

实例：

```python
#比如说现在有一张美女图片 美女.png
p=open('美女.png',mode='rb')
p.close()
```

##### with：不用手动关闭文本

实例：

```python
with open('笔记/计算机导论.md',mode='a',encoding='utf-8') as p: #as的作用可以看作'='赋值号
	p.write('wenben') #不用手动关闭，python会自动关闭文本，在with以外不能继续编写

```



#### 文件复制

实例：

```python
 #现在有个文件'home\new'和文件'home\old\图片.png'，将文件复制从old到new里面
with open('home/old/图片.png',mode='rb') as old,open('home/new/图片.png',mode='wb') as new:
	new.write(old.read())
```



#### 文件修改

python没有文件直接修改的函数，但是我们可以通过一些巧妙的转换               ；）

{

需要导入***os模块***

将文件遍历一遍，将符合要求的用***replace函数***进行修改，再将修改过的和没修改的写入新文件

这时用os模块中的***remove函数***删除源文件，再修改新文件的名称为源文件的

如果文件不大更改将会是一瞬间，这时我们又可以导入***time模块***，应用time模块中的***sleep函数***可以将程序休眠，让其过段时间后运行,最后使用os中的***rename函数***模块修改名字

}

实例：

```python
import time
import os

#现在有一个r1文件修改里面内容，将姓张的改为姓陈的
#文件内容为
'''
张三
李四
张伟
王五
赵六
'''
with open('r1',mode='r',encoding='utf-8') as p,open('r1_副本',mode='w',encoding='utf-8') as p1:
    for i in p:
        i=i.strip()
        if i.startswith('张'):
            i=i.replace('张','陈')
        p1.write(i)
        p1.write('\n')
time.sleep(5)
os.remove('r1')
time.sleep(5)
os.rename('r1_副本','r1')

```



### def函数

#### 函数定义

对一些特定的代码或者重复的代码进行封装，以后直接调用

用法：

def  函数名():

​	代码块

#在调用的时候直接写函数名()

函数名()



实例：

```python
#定义getname函数
def getname():
	print('张山')
	
#调用
getname() #打印张山
```



#### 参数

顺序：位置>*args>默认值>**kwargs

如果传参只有*args和**kwargs，就没有顺序要求

> 函数实参和形参

函数后面括号里写了接收参数的形参，调用时也必须要有

- 实参

就是有具体值的参数，例如：a=12,这时a就是一个实参

位置参数：按照顺序进行赋值

关键字参数：通过关键字赋值,不用按顺序放

混合参数（不建议使用）：

​	放置顺序：位置参数放前面，关键词参数放后面，不然会报错

​	同种参数不能出现两遍



实例：

```python
def getcs(eathing,drink,play):
	print(eathing,drink,play)

#位置参数
getcs('米饭','果汁','游戏')

#关键字参数
getcs(eathing='米饭',play='游戏',drink='果汁')
															#前三种都打印米饭 果汁 游戏
#混合参数
getcs('米饭','果汁',play='游戏') 

#混合参数，同种参数出现两遍
#getcs('米饭','果汁',drink='饮料') #会报错 
```



- 形参是位置参数

就是函数接收的变量值

在编写函数的时候写了几个形参，在调用的时候也只能接收几个形参，多了少了都会报错

默认参数：在写形参时给该形参赋值

​	顺序：默认参数要放在其他形参后面

例如：

```python
def gety(name,age,gender='女'):
	print(name,age,gender)
	
gety('李四',20) #这里没有给gender赋值默认gender为女
gety('张三',18,'男') #这里默认值将覆盖为男
```





用法：

def 函数名(形参1,形参2,...):

​	代码块

#调用函数

函数名(形参1,形参2,...)



实例：

```python
#定义getname函数带形参
def getname(name):
	print(name)
	
#调用
getname('张山') #打印张山
```



> *元素：动态传参，接收的参数存放在元组里

用法：

def 函数名(*元素):

​	代码块

调用：

函数名（数据1，数据2，...)



实例：

```python
def eat(*food):
    print(food)

eat('龙虾泡面','爆炒小龙虾','蒜蓉小龙虾')  #打印('龙虾泡面', '爆炒小龙虾', '蒜蓉小龙虾')
```



> **元素：将接收到的元素去不转换成字典

用法：

def eat(**元素):

​	代码块

调用：

函数名（数据名=数据1，数据名=数据2，...)

实例：

```python
def eat(**food):
    print(food)

eat(food1='龙虾泡面',food2='爆炒小龙虾')  #打印{'food1': '龙虾泡面', 'food2': '爆炒小龙虾'}
```



> *列表名在参数里，就是将列表转换成位置参数（不常见）

实例：

```python
def cs(*args):
    print(args)

lis=[1,2,3,4,5]
cs(*lis)
```



#### 函数返回值

1. return语句后面的，代码不会执行
2. 写了return，后面不写其他的会返回None
3. return后面有东西会返回一个值，调用函数时可以用变量接收
4. return后面有多个值（值需要用逗号隔开）将会返回一个元组



创建一个函数如果需要函数的结果或需要处理结果，就需要返回值

用法：

def  函数名(元素1，元素2，...):

​	代码块

​	return   返回语句



实例：

```python
def  add(a,b):
	return a+b;

s=add(1,4)  #可以对s进行操作
print(s)  
```



#### 变量的作用域

- 变量顶格写的为全局变量，在定义那个变量后面所有区域都能够调用

- 将变量定义在函数里面的为局部变量，局部变量一般在局部使用



实例：

```python
a=10   #全局变量
def  add(a,b):
    i=20   #局部变量
	return a+b;

#print(i)   #会报错i声明在函数内为局部变量
```



#### 内置函数

> lambda

用法：

lambda  参数：表达式



实例：

```python
add = lambda x, y: x + y

print(add(1, 23))
```









#### 函数嵌套

在函数里面再写一个新函数，新函数为局部函数

def  函数名（）：

​	代码块

​	def  函数名（）：

​		代码块



实例：

```python
def add():
    b=10
    print(123)
    def pad():  #内层函数
        a=20
        print(98)
    pad()  #外界不能直接调用
    
print(add())
```





### 正则表达式

需要导入re

#### 基本符号

“.”：号可以代替除了换行符的任意一字符

“*”：可以表示它前面的一个子表达式（普通字符、另一个或几个正则表达式符号）0次到无限次

“?”：表示它前面的子表达式0次或无限次

“\”：在表达式中不能单独使用，反斜杠可以将普通字符转换成特殊字符，也可以将特殊字符转换成普通字符

“\d”：表示所有数字

“()”：用于后面将括号里的数据提取出来



常见的转义字符

| 转义字符 |     意义     |
| :------: | :----------: |
|    \n    |    换行符    |
|    \t    |    制表符    |
|    \\    | 普通的反斜杠 |
|   \\'    |    单引号    |
|   \\"    |    双引号    |
|    \d    |     数字     |



#### re内置方法

##### findall

能够以列表的方式返回所有满足要求的字符串

若表达式里有多个括号，会将多个括号里的内容装进元组，再放入列表返回

用法：

re.findall(正则表达式，原字符串，特殊功能)

特殊功能，例如忽略大小写，忽略换行符（re.S)等



实例：

```python
import re

str1='翻译：hello，world'
findall = re.findall('翻译：(.*)', str1)
print(findall)  #结果['hello，world']

str2='账号：admin，密码：123'
re_findall = re.findall('账号：(.*)，密码：(.*)', str2)
print(re_findall)  #结果[('admin', '123')]

str3='''账号：admin，密码：
123'''
l = re.findall('账号：(.*)，密码：(.*)', str3, re.S)
print(l)  #[('admin', '\n123')],虽然是忽略了换行符，但是会被打印出来
```



##### search

与findall用法一样，但是只查找第一个符合要求的，找到了就结束

没找到返回None，找到了需要用group获取值

re.search(正则表达式，原字符串，特殊功能)

group用法：group（数字），0表示符合表达式的所有字符，1表示第一个括号里的内容，后面以此类推



实例：

```python
import re
str3='账号：admin，密码：123'
l = re.search('账号：(.*)，密码：(.*)', str3, re.S)
print(l.group(0))  #0打印所有符合规则的数据
print(l.group(1))  #1代表第一个括号里的内容
print(l.group(2))  #2代表第二个括号里的内容
```



##### compile

compile方法可以不需要，findall和search方法里都有调用compile方法，再写compile方法多此一举



> [!NOTE]
>
> “.*”，“.\*?”的区别
>
> .*：获取最长满足要求的字符串（贪婪模式）
>
> 
>
> .\*?：获取最短能满足要求的字符串（非贪婪模式）



?P:分组











#### 技巧

##### 先抓大在抓小



实例：

```python
import re

str1='''
有效姓名
name:张三
name:李四
name:王五
无效姓名
name:悠闲的行僧
name:隐身的大侠
name:会飞的朱
'''
user=re.findall('有效姓名(.*?)无效姓名',str1,re.S)
print(user)  #先抓有效姓名     #['\nname:张三\nname:李四\nname:王五\n']

user1=re.findall('name:(.*?)\n',user[0])
print(user1)  #再整理有效姓名  #['张三', '李四', '王五']
```



##### 括号内和括号外

括号内不是只能写.*?，还可写其他内容



实例：

```python
import re
str1='标准北京时间2025年10月7日，日历、在线闹钟。'

#在括号里
print(re.findall('北京时间(2025.*)', str1))  #['2025年10月7日，日历、在线闹钟。']

#在括号外
print(re.findall('北京时间2025(.*)', str1))  #['年10月7日，日历、在线闹钟。']

#只有.*?
print(re.findall('(.*)', str1))  #['标准北京时间2025年10月7日，日历、在线闹钟。', '']
```



### 爬虫基础

#### 测试网站

测试内容较全：https://scrape.center

较多的爬虫练习：https://www.spiderbuf.cn/



#### requests模块

##### get方式

http://exercise.kingname.info/exercise_requests_get.html

content：获取网页源代码（进制代码）

decode：解码，获得字符串源代码（人能够看得懂的字符），默认utf-8

用法：

requests.get(‘网址’).content.decode(‘源码格式’)



实例：

```python
#导入模块
import requests

html=requests.get('http://exercise.kingname.info/exercise_requests_get.html').content.decode()

print(html)
```



##### post方式

http://exercise.kingname.info/exercise_requests_post



用法：

requests.post(‘网站’，data=‘数据’).content.decode()

requests.post(‘网站’，json=‘数据’).content.decode()



实例：

```python
import requests

data1={'name':'admin','password':'123456'}
html=requests.post('http://exercise.kingname.info/exercise_requests_post',json=data1).content.decode()

print(html)
```



```python
import requests

data1={'name':'admin','password':'123456'}
html=requests.post('http://exercise.kingname.info/exercise_requests_post',data=data1).content.decode()

print(html)
```



#### requests与正则表达式





#### 多线程爬虫

##### 多进程库（multiprocessing）

> dummy模块

能让python的线程使用multiprocessing的各种方法

dummy里的Pool类实现线程池，线程池的map()方法可以让线程池里面的所有线程同时执行一个函数

map（函数，可迭代对象）



实例：

```python
#导入模块
from multiprocessing.dummy import Pool

#算平方
def power(a):
    return a*a

pool=Pool(3)  #3个线程
num=[x for x in range(1,11)]
pool_map = pool.map(power, num)
print(pool_map)
```



##### 多线程爬虫开发

```python
from multiprocessing.dummy import Pool
import time
import requests

def get_html(q):
    requests.get(q)
###单线程
start=time.time()
for i in range(30):
    get_html('http://exercise.kingname.info/exercise_requests_post')

end=time.time()

print(f'单线程消耗时间：{end-start}')

###多线程
start_1=time.time()
lis=[]
for i in range(30):
    lis.append('http://exercise.kingname.info/exercise_requests_post')

pool=Pool(5)              ###得出多线程明显要比单线程快
pool.map(get_html,lis)
end_1=time.time()

print(f'多线程消耗时间|：{end_1-start_1}')
```



#### 爬虫的常见搜索算法

小说网站：http://kanunu8.com/book3/6879

##### 深度优先搜索

##### 广度优先搜索

##### 爬虫搜索算法选择







#### html基础

##### XPath

是一种查询语言，能够在XML和HTML的树状结构中寻找结点，需要安装三方库：lxml

安装命令：

```python
pip install lxml
```



用法：

接收名=lxml.html.fromstring(‘网页源码’)

接收名.xpath(‘Xpath语句’)



> XPath语句格式

语法：

获取文本：

//标签1[@属性1=‘属性值1’]/标签2[@属性2=‘属性值2’]/.../text()

获取属性：

//标签1[@属性1=‘属性值1’]/标签2[@属性2=‘属性值2’]/.../@属性n

其中[@属性=‘属性值’]不是必须的，只是用来找出特殊的标签



//标签[starts-with(@属性名，‘相同的开头部分’)]/...

//标签[contains(@属性名，‘相同的部分’)]/...

> string(.)关键字

能提取标签名下的所有文本数据和相对位置



实例：

```python
import lxml.html

str1='''
<div id="dfa">
'第一句'
<span id="siger">
    '第二句'
    <ul>
            '第三句'
    </ul>
        '第4句'
</span>
    '第5句'
</div>
'''
# xpath = lxml.html.fromstring(str1).xpath('//div[@id="dfa"]/text()')
#for i in xpath:
#    print(i)
#只打印
'''
'第一句'


    '第5句'
'''

xpath = lxml.html.fromstring(str1).xpath('string(.)')
print(xpath)  
#打印结果如下
'''
'第一句'

    '第二句'
    
            '第三句'
    
        '第4句'

    '第5句'

'''
```



##### Beautiful Soup4

为三方库没有的需要安装

安装命令：

```python
pip install beautifulsoup4
```



用来提取html和xml中的数据，bs4在某些方面比XPath易懂，但不如XPath简洁

BeautifulSoup(‘网页源码’，‘解析器’)

解析器可用：html.parser或lxml等



> find()或find_all：查找内容

找到的内容用 .string获取文本

find与find_all参数相同

find(name,attrs,recursive,text,**kwargs)



name：是html标签名，如div，body，ul，li等

attrs：是一个字典

recursive：为True和False。为False时将不搜索子标签

text：可以是正则表达式或者字符串用于搜索标签里的文本信息

**kwargs：是key=value形式的参数



> [!NOTE]
>
> 由于html和python中的class关键字相同，为了不冲突，bs4规定遇到查询class用class_来代替



find与find_all的不同点

find()返回的是BeautifulSoup tag对象，如果有多个html标签符合，返回第一个符合要求的，找不到返回None

find_all()返回的是BeautifulSoup tag对象组成的列表，若没有找到满足要求的返回空列表



#### MySQL数据库

##### 驱动下载

```python
pip install mysql-connector-python
```



##### 连接数据库

```python
#导入模块
import mysql.connector

#创建数据库连接
db=mysql.connector.connect(
	host='localhost',  #mysql服务器地址
    user='username',  #用户名
    password='password',  #密码
    database='mydatabase'  #数据库名
)

#创建游标对象，用于执行sql查询
cursor=db.cursor()
```



> 执行select查询

游标对象. `execute`（“select * from 表名”）

`fetchall`获取所有结果



实例：

```python
#导入模块
import mysql.connector

#创建数据库连接
db=mysql.connector.connect(
	host='localhost',  #mysql服务器地址
    user='username',  #用户名
    password='password',  #密码
    database='mydatabase'  #数据库名
)

#游标对象
cursor=db.cursor()
cursor.execute('select*from aq1')  #aq1 为数据表
#获取结果
results=cursor.fetchall()
for i in results:
    print(i)  #打印结果
```



> insert，update，delete操作

MySQL默认用`%s`占位

操作完用`commit`提交事务

`rowcount`返回数据操作所影响的行数



insert into 表名（字段名1，字段名2，...）values（值1，值2，...)；

update 表名 set 字段名1=值1，字段名2=值2，....[where 条件]；

delete from 表名 [where 条件]



实例：

```python
#导入模块
import mysql.connector

#创建数据库连接
db=mysql.connector.connect(
	host='localhost',  #mysql服务器地址
    user='username',  #用户名
    password='password',  #密码
    database='mydatabase'  #数据库名
)

cursor=db.cursor()
values = ("张三", 25) #需要提交值  #需要传入元组或者列表
cursor.execute("INSERT into aq1 (name, id) VALUES (%s, %s)", values)  #插入数据

#values=('张三',)   #需要传入元组或者列表
#cursor.execute("delete from aq1 where name=%s",values)  #删除符合条件的数据

#values=('zhangs','lis')
#cursor.execute('update aq1 set name=%s where name=%s',values)  #修改数据

db.commit()
print(cursor.rowcount, "条记录插入成功")  #打印操作影响的行数
```



> 关闭连接

```python
cursor.close()
db.close()
print("数据库连接已关闭")
```



#### redis内存数据库



#### 异步加载与请求头

##### 异步加载

> AJAX技术：Asynchronous JavaScript And XML

如何判断一个网页有没有使用AJAX技术？http://exercise.kingname.info/exercise_ajax_1.html

打开网站查看源码，没有网页显示的内容，可得出为AJAX技术



> JSON介绍与应用

json是一种轻量级的数据交换格式



python中要导入json模块，将python中的代码字符串转换成json格式的字符串，然后json格式的字符串被其他语言再次转换

json用法：

转成json数据

json.dumps(‘要转换的数据’，indent=缩进）



实例：

```python
import json  #导入模块

person={
    'basic_info':{
        'name':'zhangs',
        'age':18,
        'chengnian':True
    },
    'work_info':{
        'place':'beijing',
        'work':'tingzhang'
    }
}
print(json.dumps(person))  #打印{"basic_info": {"name": "zhangs", "age": 18, "chengnian": true}, "work_info": {"place": "beijing", "work": "tingzhang"}}
```



json转python数据格式 

json.loads(‘json字符串’)  #如果只是字符串需要用双引号将数据引起来，再嵌套一层单引号，如`‘ “name” ’`



实例：

```python
import json
person='{"basic_info": {"name": "zhangs", "age": 18, "chengnian": true}, "work_info": {"place": "beijing", "work": "tingzhang"}}'
print(type(json.loads(person)))  #打印<class 'dict'>
```



> 异步get与post请求

http://exercise.kingname.info/exercise_ajax_1.html

在网页上用鼠标右键--->检查--->找到网络--->刷新网页

里面有些响应中有我们想要的数据，标头能够查看是post请求还是get请求



post：ajax_1_postbackend

get：ajax_1_backend





实例：

```python
import requests
#get
html_get=requests.get('http://exercise.kingname.info/ajax_1_backend').content.decode('utf-8')
print(html_get)
#post
html_post=requests.post('http://exercise.kingname.info/ajax_1_postbackend',json={'name':'zhangs','age':12}).content.decode('utf-8')  #修改了请求内容，name和age
print(html_post)
```



> 特殊的异步加载

http://exercise.kingname.info/exercise_ajax_2.html



该网站源码下看似没有页面显示的内容,但是源码中有一句`{"code": "\u884c\u52a8\u4ee3\u53f7\uff1a\u5929\u738b\u76d6\u5730\u864e"}`是json格式的代码,尝试用json模块解析



实例：

```python
import json
new_1=json.loads('{"code": "\u884c\u52a8\u4ee3\u53f7\uff1a\u5929\u738b\u76d6\u5730\u864e"}')
print(new_1)  #就会得到网页内容{'code': '行动代号：天王盖地虎'}
```



> [!TIP]
>
> 解决思路：一般用正则表达式提取再解析
>
> 
>
> 实例：
>
> ```python
> import json
> import re
> import requests
> html=requests.get('http://exercise.kingname.info/exercise_ajax_2.html').content.decode('utf-8')
> search = re.search("var secret = '(.*?)'", html, re.S)
> print(json.loads(search.group(1))['code'])  #json.loads(search.group(1)是一个字典，['code']是字典key键，打印value值  #打印行动代号：天王盖地虎
> ```



> 多次请求的异步加载

有些网页需要多次请求，上一次请求成功后才能向下继续请求

http://exercise.kingname.info/exercise_ajax_3.html



检查该网页请求负载下有两个奇怪的参数secret1，secret2，在网页源码中有secret_2参数，从值得出与secret2就是同一个参数，在检查中在axaj_3_backend中找到了code参数，code值与secret1相同



实例：

```python
import json
import re
import requests

html=requests.get('http://exercise.kingname.info/exercise_ajax_3.html').content.decode('utf-8')

secret_2= re.search("secret_2 = '(.*?)'", html, re.S).group(1)

secret_=requests.get('http://exercise.kingname.info/ajax_3_backend').content.decode('utf-8')
secret_1= json.loads(secret_)['code']
axaj_2=requests.post('http://exercise.kingname.info/ajax_3_postbackend',json=({'name': 'zhangs','age':18,'secret1':secret_1,'secret2':secret_2})).content.decode('utf-8')

print(json.loads(axaj_2)['code'])  #打印行动代号：哎哟不错哦
```



> 基于异步加载的简单登录

http://exercise.kingname.info/exercise_ajax_4.html



post方式

实例：

```python
import json
import requests

html=requests.post('https://exercise.kingname.info/ajax_4_backend',json={'username':'kingname','password':'genius'}).content.decode('utf-8')
print(json.loads(html)['code']) 
```



##### 请求头

> headers:伪造请求头

http://exercise.kingname.info/exercise_headers.html



headers参数是一个字典

requests.get(‘网站’，headers=字典).content.decode(‘编码格式’)

requests.get(‘网站’，json=‘json格式字符串’，headers=字典).content.decode(‘编码格式’)



https://exercise.kingname.info/exercise_headers_backend

实例：

```python
import json
import requests

header={
'user-agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/141.0.0.0 Safari/537.36 Edg/141.0.0.0'
}

html=requests.get('https://exercise.kingname.info/exercise_headers_backend',headers=header).content.decode('utf-8')
print(json.loads(html))
```



##### 模拟浏览器

有些网站在发起AJAX请求会带上特殊字符串用于验证身份，这种字符串称为`Token`



https://exercise.kingname.info/exercise_advanced_ajax.html

网页发起AJAX请求时headers会带上参数reqtime，在post参数会有一个sum参数，多次刷新reqtime和sum参数一直在变化，只有reqtime与sum存在一一对应关系，才能获取到网页数据，这种关系算法会写在网页的某一个JavaScript文件里，一般很难发现



> Selenium介绍

在网页源码无法看到异步加载的内容，但在检查的元素选项卡中可以看到，此时显示的是被加载的内容

如果能获得这个被加载的内容，那么就能绕过手动构造reqtime和sum的过程，就可以直接用XPath获取内容。这种情形就需要Selenium操作浏览器来解析javascript，再爬取内容



Selenium是python三方库需要安装

> Selenium使用

webdriver.浏览器驱动       #例如：edge驱动：webdriver.Edge()    #chrome驱动：webdriver.Chrome()等

需要浏览器对应的驱动



实例：

```python
from selenium import webdriver

edge = webdriver.Edge()
edge.get('https://exercise.kingname.info/exercise_advanced_ajax.html')
source = edge.page_source
input()	 #如果不加程序运行完将直接结束
```



> Selenium



```python
from selenium.webdriver.support.ui import WebDriverWait
```

WebDriverWait会阻塞程序运行

用法：

WebDriverWait（‘浏览器驱动’，等待时长）



```python
from selenium.webdriver.common.by import By
```

元素定位方式

用法：

find_element(定位元素，定位值)    #获取第一个符合条件的元素

find_elements(定位元素，定位值)    #获取所有符合条件的元素



By可以指定元素：

By.ID  #元素id属性，定位效率高

By.NAME  #常用于表单元素，如输入框、按钮

By.CLASS_NAME   #class 可能有多个值，需传入单个类名，`不能带空格`

By.TAG_NAME   #通过 HTML 标签名定位，如 div、a、input，易返回多个元素

By.LINK_TEXT   #通过链接的**完整文本**定位，仅适用于 `<a>` 标签

By.PARTIAL_LINK_TEXT   #通过链接的**部分文本**定位（模糊匹配，适用于 `<a>` 标签）

By.CSS_SELECTOR   #通过 CSS 选择器定位（灵活强大，支持复杂定位）

By.XPATH   #通过 XPath 表达式定位（支持复杂层级和属性匹配，几乎可定位所有元素）



```python
from selenium.webdriver.support import expected_conditions 
```

本质是判断页面状态是否符合预期

ec.presence_of_element_located((By.定位方式, 定位值))    #等待**单个元素存在于 DOM 中**（无需可见，只要 DOM 树中有该元素即可）







`until`方法：等待直到括号里面的条件成立，成立返回对应元素对象



实例：

```python
from selenium import webdriver
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.common.by import By
from selenium.webdriver.support import expected_conditions as ec

driver = webdriver.Edge()

try:
    driver.get('https://exercise.kingname.info/exercise_advanced_ajax.html')             WebDriverWait(driver,30).until(ec.presence_of_element_located((By.CLASS_NAME, 'content')))
except ec:
    print('网页加载超时')

print(driver.page_source)
```



实例：

用XPATH获取内容

```python
from selenium import webdriver
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.common.by import By
from selenium.webdriver.support import expected_conditions as ec

driver = webdriver.Edge()

try:
    driver.get('https://exercise.kingname.info/exercise_advanced_ajax.html')
    until = WebDriverWait(driver, 30).until(ec.presence_of_element_located((By.CLASS_NAME, 'content')))
    WebDriverWait(driver, 20).until(lambda driver: until.text.strip() != "" ) # 文本非空才算加载完成
except ec:
    print('网页加载超时')

ele = driver.find_element(By.XPATH, '//div[@class="content"]').text

print(ele)
driver.quit()   #自动化操作完成，彻底关闭浏览器
```



##### 阶段案例

目标网站：http://www.le.com

目标内容：爬取视频评论

涉及知识点：

分析网站的异步加载请求

使用requests请求







#### 模拟登陆与验证码





### 爬虫进阶

#### cookie处理

session对象=requests.session()  #获取session对象

#登录请求

login_data={‘username’=‘user’, ‘password’=‘pw’}

session.post(‘网址’，data=login_data)



> **referer**防盗链

理解为当前请求的网址，他会去找源，找它前面的网址，称为溯源，没有找到不会返回想要的网址内容





#### 代理IP

```python
import requests
#代理IP
proxies={
	"https":"https://ip:端口"
	"http":"http://ip:端口"
}
requests.get('网址',proxies=proxies)
```



#### scrapy框架（必学）

需要下载scrapy模块

```python
pip install Scrapy
```



##### 创建项目框架

在终端输入以下命令创建scrapy项目

```python
scrapy startproject 项目名
```

该路径下会出现scrapy框架

```python
mySpider/
    scrapy.cfg
    mySpider/
        __init__.py
        items.py
        pipelines.py
        settings.py
        spiders/
            __init__.py
            ...
```

- scrapy.cfg: 项目的配置文件。
- mySpider/: 项目的Python模块，将会从这里引用代码。
- mySpider/items.py: 项目的目标文件。
- mySpider/pipelines.py: 项目的管道文件。
- mySpider/settings.py: 项目的设置文件。
- mySpider/spiders/: 存储爬虫代码目录。

> [!CAUTION]
>
> 在settings.py中要关掉`ROBOTSTXT_OBEY`，如果是`Ture`就改为`False`，不然很多网页都爬取不了
>
> 然后再将`DEFAULT_REQUEST_HEADERS`的注释关掉，再写入用户端设备标识user-agent，可以应对一些简单的反爬机制



##### 创建爬虫

scrapy genspider  爬虫名  网址域名



##### 编写爬虫

根据自己需求来



##### 运行爬虫

需要在创建的项目下用终端运行

```python
scrapy crawl  爬虫名
```













### 进度条

#### tqdm

需要下载`tqdm`库

常用参数

| 参数名      | 作用                                   |
| ----------- | -------------------------------------- |
| iterable    | 要跟踪进度的可迭代对象（必填）         |
| total       | 总任务数（必填）                       |
| desc        | 进度条前缀描述（自定义提示文字）       |
| ncols       | 进度条总宽度（适配终端）               |
| unit        | 任务单位（显示在速度统计后）           |
| colour      | 进度条颜色（支持英文/十六进制）        |
| leave       | 任务结束后是否保留进度条（默认为true） |
| mininterval | 进度条最小更新间隔(默认0.1秒）         |





### python代码转网页
