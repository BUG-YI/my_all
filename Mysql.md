# Mysql

## 基础

### 数据库基础

#### DLL

##### DDL-数据库操作

[]内的是可选内容，不是必须的

> 创建数据库

create database[IF NOT EXISTS] 数据库名 [DEFAULT CHARSET 字符集] [COLLATE 排序规则]；

IF NOT EXISTS：判断是否有该数据库，没有则创建

> 删除数据库

drop database [IF EXISTS] 数据库名；



> 使用数据库

use 数据库名；



> 查询当前数据库

select database（）；



##### DDL-表查询

> 查询当前数据库所有表

show tables;



> 查询表结构

desc 表名；



> 查询指定表的建表语句

show create table 表名；



##### DDL-表结构 -创建

create table 表名（

字段1  字段1类型[COMMENT  字段1注释]，

字段2  字段2类型[COMMENT  字段2注释]，

......

字段n  字段n类型[COMMENT  字段n注释]

)[COMMENT  表注释]；



##### DDL-表操作-修改

> 修改数据类型

alter table 表名 add 字段名 类型（长度）[COMMENT 注释] [约束];



> 修改字段名和字段类型

alter table 表名  change 旧字段名  新字段名 类型（长度）[comment 注释] [约束]；



> 删除字段

alter table 表名 drop 字段名；



> 修改表名

alter table 表名 rename to 新表名；



##### DDL-表操作-删除

> 删除表

drop table [IF EXISTS] 表名；



> 删除指定表，并创建该表（简单理解就是清空数据）

truncate table 表名；



#### DML

##### insert ：添加数据

> 给指定字段添加数据

insert into 表名（字段名1，字段名2，...）values（值1，值2，...)；



> 给所有字段添加数据

insert into 表名 values（值1，值2，...);



> 批量添加

insert into 表名（字段名1，字段名2，...）values（值1，值2，...)，（值1，值2，...)，....；

insert into 表名 values（值1，值2，...)，（值1，值2，...)，....；



> [!CAUTION]
>
> 添加数据时，字段和值需要一一对应
>
> 字符串和日期数据应该用引号引起来
>
> 插入的数据大小要在规定的范围内



##### update：修改数据

update 表名 set 字段名1=值1，字段名2=值2，....[where 条件]；

> [!CAUTION]
>
> 建议写上where 条件
>
> 不写将修改表内`所有`该字段的值
>
> 写上将匹配符合条件的修改



##### delete：删除数据

delete from 表名 [where 条件]





#### DQL

##### 编写顺序

select

​	字段列表

from

​	表名列表

where

​	条件列表

group by 

​	分段字段列表

having

​	分组后条件列表

order by 

​	排序字段列表

limit

​	分页参数



##### 执行顺序

from

​	表名列表

where

​	条件列表

group by 

​	分段字段列表

having

​	分组后条件列表

select

​	字段列表

order by 

​	排序字段列表

limit

​	分页参数



##### select查询



> 多字段查询

select 字段1，字段2...  from 表名；

select * from 表名；



> 设置别名

select 字段1[AS 别名1]，字段2[AS 别名2]...  from 表名；



> 去除重复记录

select distinct  字段列表  from 表名；



##### 条件查询

select 字段列表 from 表名 where 条件列表；

条件

| 比较运算符       | 功能                                      |
| ---------------- | ----------------------------------------- |
| >                |                                           |
| >=               |                                           |
| <                |                                           |
| <=               |                                           |
| =                |                                           |
| <>或!=           | 不等于                                    |
| between...and... | 在这个范围之内（含最大，最小）            |
| in(...)          | 在in之后的列表中的值，多选一              |
| like 占位符      | 模糊匹配（匹配单个字符，%匹配任意个字符） |
| is null          | 是null                                    |

| 逻辑运算符 | 功能                         |
| ---------- | ---------------------------- |
| and或&&    | 并且（多个条件同时成立）     |
| or或\|\|   | 或者（多个条件任意一个成立） |
| not或！    | 并非，不是                   |

 

##### 聚合函数

select 函数（字段列表） from 表名；



| 函数  | 功能     |
| ----- | -------- |
| count | 统计数量 |
| max   | 最大值   |
| min   | 最小值   |
| avg   | 平均值   |
| sun   | 求和     |



##### 分组查询

select 字段列表 from 表名 [where 条件] group by 分组字段名 [having 分组后过滤条件]；

> [!NOTE]
>
> where与having的区别
>
> 执行时机不同：where是分组前进行过滤，不满足where条件不参加分组；having是分组之后对结果进行过滤
>
> 判断条件不同：where不能对聚合函数进行判断，而having可以

> [!CAUTION]
>
> 执行顺序：where>聚合函数>having
>
> 分组之后，查询的字段一般为聚合函数和分段字段，查询其他字段无任何意义



##### 排序查询

select 字段列表 from 表名 order by 字段1  排序方式1，字段2  排序方式2；



排序方式：

asc：升序（默认值）

desc：降序



> [!CAUTION]
>
> 如果是多个字段排序，当第一个字段相同时，才会根据第二个字段进行排序



##### 分页查询

select 字段列表 from 表名 limit 起始索引，查询记录数；



> [!CAUTION]
>
> 起始索引从0开始，起始索引=（查询页面-1）* 每页显示记录数
>
> 分页查询是数据库的方言，不同的数据库有不同的实现，MySQL中是limit
>
> 如果查询的是第一页数据，起始索引可以省略，直接简写为limit  10

 

#### DCL

##### 用户管理

> 查询用户

use mysql;

select *from user;



> 创建用户

create user ‘用户名’@‘主机名’  identified by ‘密码’；



> 修改用户密码

alter user ‘用户名’@‘主机名’  identified with mysql_native_password   by ‘新密码’;



> 删除用户

drop user ‘用户名’@‘主机名’；



> [!CAUTION]
>
> 主机名可以使用%通配
>
> 这类sql开发人员操作的比较少，主要是DBA（数据库管理员）使用



##### 权限控制

| 权限               | 说明     |
| ------------------ | -------- |
| all,all privileges | 所有权限 |
| select             |          |
| insert             |          |
| update             |          |
| delete             |          |
| alter              |          |
| drop               |          |
| create             |          |



> 查询权限

show grants ‘用户名’@‘主机名’；



> 授予权限

grant  权限列表  on 数据库名 .表名 to ‘用户名’@‘主机名’；



> 撤销权限

revoke 权限列表 on 数据库名.表名 from ‘用户名’@‘主机名’；



> [!CAUTION]
>
> 多个权限之间，使用逗号分隔
>
> 授权时，数据库名和表名可以使用*进行通配，代表所有





### 数据类型

#### 数值类型

|   类型    |                   大小                   |                     范围（有符号）SIGNED                     |                    范围（无符号）UNSIGNED                    |      用途       |
| :-------: | :--------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :-------------: |
|  TINYINT  |                  1bytes                  |                         (-128，127)                          |                           (0，255)                           |    小整数值     |
| SMALLINT  |                  2bytes                  |                      (-32 768，32 767)                       |                         (0，65 535)                          |    大整数值     |
| MEDIUMINT |                  3bytes                  |                   (-8 388 608，8 388 607)                    |                       (0，16 777 215)                        |    大整数值     |
|    INT    |                  4bytes                  |               (-2 147 483 648，2 147 483 647)                |                      (0，4 294 967 295)                      |    大整数值     |
|  BIGINT   |                  8bytes                  |   (-9,223,372,036,854,775,808，9 223 372 036 854 775 807)    |               (0，18 446 744 073 709 551 615)                |   极大整数值    |
|   FLOAT   |                  4bytes                  | (-3.402 823 466 E+38，-1.175 494 351 E-38)，0，(1.175 494 351 E-38，3.402 823 466 351 E+38) |         0，(1.175 494 351 E-38，3.402 823 466 E+38)          | 单精度 浮点数值 |
|  DOUBLE   |                  8bytes                  | (-1.797 693 134 862 315 7 E+308，-2.225 073 858 507 201 4 E-308)，0，(2.225 073 858 507 201 4 E-308，1.797 693 134 862 315 7 E+308) | 0，(2.225 073 858 507 201 4 E-308，1.797 693 134 862 315 7 E+308) | 双精度 浮点数值 |
|  DECIMAL  | 对DECIMAL(M,D) ，如果M>D，为M+2否则为D+2 |                        依赖于M和D的值                        |                        依赖于M和D的值                        |     小数值      |



#### 字符串类型

|    类型    |         大小          |              用途               |
| :--------: | :-------------------: | :-----------------------------: |
|    CHAR    |      0-255 bytes      |           定长字符串            |
|  VARCHAR   |     0-65535 bytes     |           变长字符串            |
|  TINYBLOB  |      0-255 bytes      | 不超过 255 个字符的二进制字符串 |
|  TINYTEXT  |      0-255 bytes      |          短文本字符串           |
|    BLOB    |    0-65 535 bytes     |     二进制形式的长文本数据      |
|    TEXT    |    0-65 535 bytes     |           长文本数据            |
| MEDIUMBLOB |  0-16 777 215 bytes   |  二进制形式的中等长度文本数据   |
| MEDIUMTEXT |  0-16 777 215 bytes   |        中等长度文本数据         |
|  LONGBLOB  | 0-4 294 967 295 bytes |    二进制形式的极大文本数据     |
|  LONGTEXT  | 0-4 294 967 295 bytes |          极大文本数据           |



#### 日期和时间类

|   类型    | 大小 ( bytes) |                             范围                             |        格式         |           用途           |
| :-------: | :-----------: | :----------------------------------------------------------: | :-----------------: | :----------------------: |
|   DATE    |       3       |                    1000-01-01/9999-12-31                     |     YYYY-MM-DD      |          日期值          |
|   TIME    |       3       |                   '-838:59:59'/'838:59:59'                   |      HH:MM:SS       |     时间值或持续时间     |
|   YEAR    |       1       |                          1901/2155                           |        YYYY         |          年份值          |
| DATETIME  |       8       |        '1000-01-01 00:00:00' 到 '9999-12-31 23:59:59'        | YYYY-MM-DD hh:mm:ss |     混合日期和时间值     |
| TIMESTAMP |       4       | '1970-01-01 00:00:01' UTC 到 '2038-01-19 03:14:07' UTC结束时间是第 **2147483647** 秒，北京时间 **2038-1-19 11:14:07**，格林尼治时间 2038年1月19日 凌晨 03:14:07 | YYYY-MM-DD hh:mm:ss | 混合日期和时间值，时间戳 |





[约束]: 







### 函数

#### 字符串函数

| 函数                     | 功能                                                      |
| ------------------------ | --------------------------------------------------------- |
| concat（s1,s2,...）      | 字符串拼接，将括号里的拼接为一个字符串                    |
| lower（str）             | 将字符串str全部转为小写                                   |
| upper(str)               | 将字符串str全部转换为大写                                 |
| lpad(str,n,pad)          | 左填充，用字符串pad对str的左边进行填充，达到n个字符串长度 |
| rpad(str,n,pad)          | 右填充，用字符串pad对str的右边进行填充，达到n个字符串长度 |
| trim(str)                | 去掉字符串头部和尾部的空格                                |
| substring(str,start,len) | 返回从字符串str从start位置起的len个长度的字符串           |



#### 数字函数

| 函数        | 功能                   |
| ----------- | ---------------------- |
| CEIL(x)     | 向上取整               |
| FLOOR(x, y) | 向下quzheng            |
| MOD(x, y)   | 返回x/y的模            |
| RAND()      | 返回0~1内的随机数      |
| ROUND(x, y) | 四舍五入x，保留y位小数 |



#### 日期函数

| 函数                               | 功能                                                |
| ---------------------------------- | --------------------------------------------------- |
| CURDATE()                          | 返回当前日期                                        |
| CURTIME()                          | 返回当前日期                                        |
| NOW()                              | 返回当前时间，日期                                  |
| YEAR(date)                         | 返回指定date年份                                    |
| MONTH(date)                        | 返回指定date月份                                    |
| DAT(date)                          | 返回指定date天数                                    |
| DATE_ADD(date, INTERVAL expr type) | 返回上一个日期/时间值加上一个时间间隔expr后的时间值 |
| DATE_DIFF(date1, date2)            | 返回起始时间date1，date2之间的天数                  |



#### 流程函数

| 函数                                                         | 功能                                              |
| ------------------------------------------------------------ | ------------------------------------------------- |
| IF(value, t, f)                                              | 如果value为true，返回t，否则返回f                 |
| IFNULL(value, t, f)                                          | 如果value不为空，返回t，否则返回f                 |
| CASE WHERE [ val1 ] THEN [ res1 ] ... ELSE [ default ] END   | 如果val1为true，返回res1，否则返回默认值default   |
| CASE [ expr ] WHERE [ val1 ] THEN [ res1 ] ...ELSE [ default] END | 如果expr等于val1，返回res1，否则返回default默认值 |



###  约束

| 约束                       | 描述                                             | 关键字      |
| -------------------------- | ------------------------------------------------ | ----------- |
| 非空约束                   | 限制该字段值不能为空                             | NOT NULL    |
| 唯一约束                   | 确保字段数据唯一，不能重复                       | UNIQUE      |
| 主键约束                   | 主键是一行数据的唯一标识，要求非空唯一           | PRIMARY KEY |
| 默认约束                   | 保存数据时，该字段没有数据，设置默认值           | DEFAULT     |
| 检查约束(8.0.16版本后)     | 保证字段满足一定条件                             | CHECK       |
| 外键约束(阿里规范，不使用) | 用来让两张表数据建立联系，保证数据一致性、完整性 | FOREIGN KEY |



> 案例

| 字段名 | 字段含义   | 字段类型    | 约束                 |
| ------ | ---------- | ----------- | -------------------- |
| id     | id唯一标识 | int         | 主键，自增           |
| name   | 姓名       | varcher(10) | 不为空，唯一         |
| age    | 年龄       | int         | 大于0，且小于等于120 |
| status | 状态       | char(1)     | 默认1                |
| gender | 性别       | char(1)     | 无                   |

```mysql
create table index(
    id int auto_increment primary key,
    name varchar(10) not null unique,
    age int check(age > 0 && age <= 120),
    status cahr(1) default 1,
    gender char(1)
);
```



### 多表查询(需要用到外键)

#### 多表查询关系

##### 一对多

在多的一方建立外键



##### 多对多

需要建立一张表专门存储外键



##### 一对一

在任意一方建立外键，关联另一方的主键，并设置唯一约束



#### 笛卡尔积

**理解**：两张表不加连接条件直接查，行数 = 两表行数相乘

多表查询中笛卡尔积需要消除



#### 内连接

##### 隐式内连接

SELECT 字段 FROM 表1，表2 WHERE 条件 ...;



##### 显示内连接

SELECT 字段列表 FROM 表1 [ INNER ] JOIN 表2 ON 连接条件 ...;



#### 外连接

##### 左连接

查询表1（左表）的所有数据包含表1，表2交集部分的数据



SELECT 字段列表 FROM 表1 LEFT [ OUTER ] JOIN 表2 ON 条件...;



##### 右连接

查询表2（右表）的所有数据包含表1，表2交集部分的数据



SELECT 字段列表 FROM 表1 RIGHT [ OUTER ] JOIN 表2 ON 条件...;



#### 自连接

自连接可以是内连接，也可以是外连接

给一张表起两别名，当两张表



SELECT 字段列表 FROM 表1 JOIN 表2 ON 条件...;



> 案例

表名user，u_id为领导者id

| id   | name   | u_id |
| ---- | ------ | ---- |
| 1    | zhangs | null |
| 2    | lis    | 1    |
| 3    | wangw  | 1    |
| 4    | zhaol  | 3    |



```mysql
select a.name a_name, b.name b_name from user a, user b where a.id = b.u_id;
```

结果

| a.name | b.name |
| ------ | ------ |
| zhangs | lis    |
| zhangs | wangw  |
| wangw  | zhaol  |



#### 联合查询( union, union all)

> [!caution]
>
> 联合查询的多张表的列数、字段类型必须保持一致
>
> union all会将两次查询直接拼接，可能会出现重复
>
> union会去重



SELECT 字段列表 FROM 表1 ...

UNION [ ALL ]

SELECT 字段列表 FROM 表2 ...;



#### 子查询(嵌套查询)

子查询位置：WHERE之后，FROM之后，SELECT之后



SELECT * FROM 表1 WHERE column1 = (SELECT column1 FROM 表2);



##### 标量子查询

子查询结果为单个值

常用操作符：=, <>(不等于), <, >, <=, =>



SELECT * FROM 表1 WHERE column1 **`>`** (SELECT column1 FROM 表2);



##### 列子查询

子查询结果为一列，可以是多行

常用操作符：

| 操作符 | 描述                                     |
| ------ | ---------------------------------------- |
| IN     | 在指定的集合范围之内，多选一             |
| NOT IN | 不在指定的集合范围之内                   |
| ANY    | 子查询返回列表中，有任意一个满足要求即可 |
| SOME   | 与ANY等同，使用SOME的地方都可以使用ANY   |
| ALL    | 子查询返回列表的所有值都必须满足         |



SELECT * FROM 表1 WHERE column1 > **`IN`**(SELECT column1 FROM 表2);



##### 行子查询

子查询结果为一行，可以是多列

=, <>, IN, NOT IN, 



##### 表子查询

子查询结果为多行多列

常用操作符：IN



SELECT 字段列表 FROM 表1 WHERE （字段列表）IN  (SELECT 字段列表 FROM 表1 WHERE ...) 



### 事务

事务是一组操作的集合它是一个不可分割的工作单位，事务会把所有操作作为一个整体一起向系统提交或撤销操作请求，即这些操作要么**同时成功**要么**同时失败**

MySQL的事务**默认**自动提交，当执行一条DML语句，MySQL会立即**隐式**提交事务



> 方式1

查看/设置事务提交方式(1：自动提交，0：手动提交)

SELECT @@autocommit;

SET @@autocommit = 0; 



提交事务

COMMIT



回滚

ROLLBACK



> 方式2

开始事务

START TRANSACTION 或 BEGIN



提交事务

COMMIT



回滚

ROLLBACK



#### 四大特性(ACID)

1. 原子性（Atomicity）：事务是不可分割的最小操作单元，要么全部成功，要么全部失败
2. 一致性（Consistency）：事务完成时，必须所有的数据都保持一致状态
3. 隔离性（Isolation）：数据库系统提供的隔离机制，保证事务在不受外部并发操作影响的独立环境下运行
4. 持久性：（Durability）：事务一旦提交回滚，它对数据库中的数据的改变就是永久的



#### 并发事务问题

| 问题       | 描述                                                         |
| ---------- | ------------------------------------------------------------ |
| 脏读       | 一个事务读到另一个事务还没提交的数据                         |
| 不可重复读 | 一个事务先后读取同一条记录，但两次读取的数据不同，称之为不可重复读 |
| 幻读       | 一个事务按照条件查询数据时，没有对应的数据行，但是在插入数据时，又发现这行数据已存在，好像出现了幻影 |



#### 事务隔离级别

查看/设置事务隔离级别

SELECT @@TRANSATION_ISOLATION;

SET [ SESSION | GLOBAL ] TRANSATION ISOLATION LEVEL { READ UNCOMMITTED | READ COMMITTED | REPEATABLE READ | SERIZALIZABLE }

| 隔离级别              | 脏读 | 不可重复读 | 幻读 |
| --------------------- | ---- | ---------- | ---- |
| Read uncommitted      | √    | √          | √    |
| Read committed        | ×    | √          | √    |
| Repeatable Read(默认) | ×    | ×          | √    |
| Serizalizable         | ×    | ×          | ×    |

> [!caution]
>
> Serizalizable等级最高，事务级别越高，数据越安全，性能越低



## 进阶

### 存储引擎

#### MySQL体系结构

MySQL 整体分四层：**连接层 → 服务层 → 存储引擎层 → 文件系统层**。



#### 存储引擎介绍

查询表结构：show create table 表1 ;

查看当前数据库支持的存储引擎：show engines;

默认引擎为InnoDB



创建表时指定引擎

create table 表1 (

​	字段 类型 [comment “字段注释”]

​	...

)ENGINE = INNODB [comment “表注释”];



#### 存储引擎特点

> InnoDB

**介绍**：是一种兼顾高可靠性和高性能的通用存储引擎，在MySQL 5.5之后，成为默认存储引擎

**特点**

1. DML操作遵循ACID模型，支持事务
2. 行级锁，提高并发访问性能
3. 支持外键 FOREIGN KEY约束，保证数据的完整性和正确性

**文件后缀**

.ibd



> MyISAM

**介绍**：MyISAM是MySQL早期的默认 存储 引擎

**特点**

1. 不支持事务，不支持外键
2. 支持表锁，不支持行锁
3. 访问速度快

**文件后缀**

.sdi：存储表数据信息

.MYD：存储数据

.MYI：存储索引



> Memory

**介绍**：Memory引擎的表数据时存储在内存中的，由于受到硬件问题、或断电问题的影响，只能将这些表作为临时表或缓存使用

**特点**：

1. 内存存放
2. hash索引（默认）

**文件**

.sdi：存储表结构



特点

| 特点         | InnoDB              | MyISAM | mory |
| ------------ | ------------------- | ------ | ---- |
| 存储限制     | 64TB                | 有     | 有   |
| 事务安全     | 支持                | -      | -    |
| 锁机制       | 行锁                | 表锁   | 表锁 |
| B+tree索引   | 支持                | 支持   | 支持 |
| Hash索引     | -                   | -      | 支持 |
| 全文索引     | 支持（5.6版本之后） | 支持   | -    |
| 空间使用     | 高                  | 低     | N/A  |
| 内存使用     | 高                  | 低     | 中等 |
| 批量插入速度 | 低                  | 高     | 高   |
| 支持外键     | 支持                | -      | -    |



#### 存储引擎选择

InnoDB：支持事务、外键。应用对事务完整性有比较高的要求，在并发条件下要求数据的一致性，数据操作除了插入和查询之外，还包含很多的跟新、删除操作

MyISAM：如果应用以读取操作和插入操作为主，只有很少的更新和删除操作，并且对事物的完整性、并发性要求不是很高

MEMORY：将所有数据保存在内存中，访问速度快，通常用于临时表及缓存。缺陷就是对表的大小有限制，太大的表无法缓存在内存中，而且无法保障数据的安全性



### 安装Linux版MySQL

可以用虚拟机、dockers、云服务机搭建



### 索引

索引是帮助MySQL高效获取数据的数据结构（有序）。在数据之外，数据库系统还维护 者满足特定查找算法的数据结构，这些数据结构以某种方式引用（指向）数据，这样就可以在这些数据结构上实现 高级查找算法



**数据可视化**网站：https://algo.hufeifei.cn/



#### 优缺点

| 优点                                                        | 缺点                                                         |
| ----------------------------------------------------------- | ------------------------------------------------------------ |
| 提高数据检索的效率，降低数据库的IO成本                      | 索引列也是要占空间的                                         |
| 通过索引列对数据进行排序，降低数据排序的成本，降低CPU的消耗 | 索引大大提高了查询效率，同时却也降低更新表的速度，如对表 进行INSERT、UPDATE、DELETE时效率降低 |



#### 索引结构

| 索引结构             | 描述                                                         | InnoDB          | MyISAM | Memory |
| -------------------- | ------------------------------------------------------------ | --------------- | ------ | ------ |
| B+tree索引           | 常见的索引类型 ，大部分引擎都支持 B+数索引                   | 支持            | 支持   | 支持   |
| Hash索引             | 底层数据结构是用哈希表实现的，只有精确匹配索引列的查询才有效，不支持范围查询 | 不支持          | 不支持 | 支持   |
| R-tree（空间索引）   | 空间索引是MyISAM引擎的一个特殊索引类型，主要用于地理空间数据类型，通常使用较少 | 不支持          | 支持   | 不支持 |
| Full-text（全文索引) | 是一种通过建立倒排索引，快速匹配文档的方式，类似于Lucene，Solr，ES | 5.6版本之后支持 | 支持   | 不支持 |



##### 二叉树

缺点：顺序插入时会形成一个链表，查询性能大大降低，大量数据情况下，层级较深，检索速度慢



##### B-Tree(多路平衡查找树)

中间数向上分裂

> 5阶案例，Max. Degree = 5

每子节点数据超过四个取中间值向上分

![image-20260918213200903](C:\Users\25172\AppData\Roaming\Typora\typora-user-images\image-20260918213200903.png)



##### B+Tree

1. 所有数据都会出现在叶子节点
2. 叶子节点形成单向列表



> 5阶案例，Max. Degree = 5

![image-20260918213809086](C:\Users\25172\AppData\Roaming\Typora\typora-user-images\image-20260918213809086.png)



> [!note]
>
> MySQL索引数据结构对原B+Tree进行优化，增加了一个指向相邻叶子节点的链表指针，就形成了带有顺序指针的B+Tree，提高区间访问的性能



##### Hash

哈希索引采用一定的hash算法，将键值换算成新的hash值，映射到对应的槽位上，然后存储在hash表中

如果两个（或多个）键值，映射到一个相同槽位上，它们就会产生冲突（称hash碰撞），可以通过链表解决



特点

1. Hash索引只能用于 对等比较（=，in），不支持范围查询（between，<，>，...）
2. 无法利用索引完成排序操作
3. 查询效率高，通常只需要一次检索就可以，效率通常高于B+tree



#### 索引分类

| 分类     | 含义                                                 | 特点                      | 关键字   |
| -------- | ---------------------------------------------------- | ------------------------- | -------- |
| 主键索引 | 针对于表中主键创建的索引                             | 默认自动创建 ，只能有一个 | PRIMARY  |
| 唯一索引 | 避免同一个表中某数据列中的值重复                     | 可以有多个                | UNIQUE   |
| 常规索引 | 快速定位特定数据                                     | 可以有多个                |          |
| 全文索引 | 全文索引查找的是文件中的关键词，而不是比较索引中的值 | 可以有多个                | FULLTEXT |



##### InnoDB

索引存储形式，可以分为两种

| 分类                        | 含义                                                       | 特点                 |
| --------------------------- | ---------------------------------------------------------- | -------------------- |
| 聚焦索引（Clustered Index） | 将数据存储与索引放到一块，索引结构的叶子节点 保存了行数据  | 必须有，而且只有一个 |
| 二级索引（Secondary Index） | 将数据与索引分开存储，索引结构的叶子节点关联的是对应的主键 | 可以存在多个         |



聚焦索引选取规则：

1. 如果存在主键，主键索引就是聚焦索引
2. 如果不存在主键，将使用的第一个唯一（UNIQUE）索引作为聚焦索引
3. 如果表没有 主键，或没有合适的唯一索引，则InnoDB会自动生成一个rowid作为 隐藏的聚焦索引



聚集索引叶子节点下面挂的是一行的数据

二级索引挂的是对应的id

**回表查询**：如果查询的是二级索引，查询到的id再向聚焦索引下查找最终数据



#### 索引语法

##### 创建索引

写多字段为联合索引

CREATE [ UNIQUE | FULLTEXT ] INDEX 索引名 ON 表1 (index_col_name, ...);



##### 查看索引

SHOW INDEX FROM 表1；



##### 删除索引

DROP INDEX 索引名 ON 表1；



#### SQL性能分析

##### SQL执行频率

下划线为单匹配字符

SHOW [ GLOBAL | SESSION ] STATUS LIKE `“Com_______”`



##### 慢查询日志

查看慢查询日志是否开启：show variables like ‘slow_query_log’;



慢查询日志记录了所有执行时间超过 指定参数（long_query_time，单位：秒，默认10秒）的所有SQL语句日志

MySQL的慢查询日志默认没有开启，需要在MySQL（Linux版）的配置文件（/etc/my.cnf）中配置如下信息：

```
#日志位置：/var/lib/mysql/localhost-slow.log
#开启慢日志查询
slow_query_log=1

#设置慢日志时间，SQL语句执行时间超过设定时间，则视为慢查询，记录慢查询日志
long_query_time=11
```



##### profile详情

show profiles能够在做SQL优化时帮助我们了解时间都消耗到哪里去了，通过have_profiling参数，能够看到当前MySQL是否支持profile操作：

SELECT @@have_profiling;

默认是关闭的，可以通过set语句在session/global级别开启profile：

SELECT @@profiling;

SET profiling=1;



查看耗时情况

show profiles;

查询指定 query_id的SQL语句在各个阶段的耗时情况

show profile for query query_id;

查看指定query_id的SQL语句CPU的使用情况

show profile cpu for query  query_id;



##### explain执行计划

explain或者desc命令获取MySQL如何执行select语句的信息，包括在select语句执行过程中表如何连接的顺序

EXPLAIN SELECT 字段列表 FROM 表1 WHERE 条件;



**执行计划各字段含义**

id：select查询的序列号，表示查询中执行select子句或者是操作表的顺序（id相同，执行顺序从上到下；id不同，值越大，越先执行）

select_type：表示select的类型，常见的取值有simple（简单表 ，即使不使用表连接或子查询）、primary（主查询，即外层的查询）、union（union中的第二或者后面的查询语句）、subquery（select/where之后包含了子查询）等

type：表示连接类型，性能由好到差的连接类型为NULL、system、const、eq_ref、ref、range、index、all

possible_key：显示可能应用在这张表的索引，一个或多个

key：实际使用的索引，如果为NULL，则没有使用索引

key_len：表示索引中使用的字节数，该值为索引字段最大可能长度，并非实际使用长度，在不损失精确性的前提下，长度越短越好

rows：MySQL认为必须要执行查询的 行数，在innodb引擎的表中，是一个估计值，可能并不总是准确的

filtered：表示返回结果的行数占读取行数的百分比，filtered的值越大越好



#### 索引使用

在未建立索引时查询耗时

select * from 表1 where 字段=“” ；

创建索引

create index 索引名 on 表1(字段)；

创建完再次查询耗时



> [!note]
>
> 需要很大的数据表，小数据表不是很明显



##### 最左前缀法则

如果索引多列（联合索引），要遵守最左前缀法则：与查询时条件书写顺序无关，查询从最左侧开始并且不跳过索引中的列

如果跳过某一列，该索引后面的索引将失效



> 案例

```mysql
-- user表中创建了一个联合索引为
create index idx_id_tel_age on \`user`(id, tel, age);
-- 遵循最左前缀法则
select * from user where id = 1 and tel = '123' and age = 12;
select * from user where id = 1 and tel = '123';
select * from user where id = 1;

-- 错误案例，不走索引
select * from user where age = 12;
select * from user where tel = '123' and age = 12;
-- 只走id索引，age不走
select * from user where id = 1 and age = 12;
```



##### 规则

**索引列运算**：不要在索引上进行运算，否则索引失效

**字符串不加引号**：字符串类型字段使用时，不加引号，索引失效

**模糊查询**：如果只是尾部进行模糊查询索引不会失效，如：select * from 表1 where name link ‘zhang%’，头部模糊查询才会失效，如：select * from 表1 where name link ‘%san’

**or连接的条件**：用or分割的条件，如果or前的条件中的列有索引，而后面的列中没有索引，那么涉及的索引都不会备用到

**数据分布影响**：如果MySQL评估使用索引比全表扫描慢，则不用索引

**SQL提示**：是数据库的一个重要手段，简单来说，就是在sql语句中加入一些人为的提示来达到优化操作的目的

- 建议索引

​	explain select * from 表1 use index(索引名) where 条件;

- 忽略索引

​	explain select * from 表1 ignore  index(索引名) where 条件;

- 强制索引

​	explain select * from 表1 force index(索引名) where 条件;

**覆盖索引**：尽量使用覆盖索引（查询使用索引，并且需要返回的列，在该索引中已经全部能够找到），减少select*

覆盖索引不需要回表查询，如果条件写的为辅助索引，如果需要返回的字段超过辅助索引所能返回的字段信息就不能使用覆盖索引，将进行回表查询，去获取超出字段的值

**前缀索引**：当字段类型为字符串（varchar，text）时，有时需要索引很长的字符串，这会让索引变得很大，查询时浪费大量的磁盘IO，影响查询效率，此时可以将字符串的一部分前缀，建立索引，这样可以大大节约索引空间，从而 提高索引效率

- 语法

​	create index 索引名 on 表1(字段名(取多少位))

- 前缀长度：可以根据索引的选择性来决定，而选择性是指不重复的索引值（基数）和数据表的记录总数的比值，索引选择性越高查询效率越高，唯一索引的选择性是1，这是最好的索引选择性，性能也是最好的

select count(distinct 字段1)/count(*) from user;

结果越接近1重复性越小，越接近0重复性越高

**distinct**去重

**单列索引与联合索引**：在业务场景中，如果在多个查询条件，考虑针对查询字段建立索引时，建议建立联合索引，而非单列索引

**单列索引**在查询多字段时会回表查询，例：

现在user表中分别给name，tel两字段创建单列索引，

select name,tel from user where name=‘zhangs’ and tel=‘1234’;

此时会回表



#### 索引设计原则

1. 数据量较大，且查询比较麻烦的表建立索引
2. 常作为查询条件（where）、排序（order by）、分组（group by）操作的字段建立索引
3. 尽量选择区分度高的列作为索引，尽量建立唯一索引，区分度越高，使用索引的效率越高
4. 如果是字符串类型的字段，字段的长度较长，可以针对字段的特点，建立前缀索引
5. 尽量使用联合索引，减少单列索引，查询时，联合索引很多时候可以覆盖索引，节约空间，避免回表，提高查询效率
6. 要控制索引的数量，索引并不是多多益善，索引越多，维护索引结构的代价就越大，会影响增删改的效率
7. 如果索引列不能存储NULL值，请在创建表时使用NOT NULL约束它。当优化器知道每列含NULL值时，它可以更好地确定哪个索引最有效的用于查询



### SQL优化

#### 插入数据

1. 批量插入

2. 手动提交事务

3. 主键顺序插入

4. 大批量插入数据

   如果一次性需要插入大批量数据，使用insert语句插入性能较低，此时可以使用MySQL提供的load指令进行插入

   ```mysql
   -- 客户端连接服务器时，加上参数 --local-infile
   mysql --local-infile -u 用户 -p
   
   -- 查询是否开启
   select @@local_infile;
   
   -- 设置全局参数local_infile为1，开启从本地加载文件导入数据的开关
   set global local_infile=1;
   
   -- 执行load指令将准备好的数据，加载到表结构中
   -- 
   load data local infile '数据文件路径' into table `表1` fields terminated by '分隔符' lines terminated by '换行符';
   ```

   

#### 主键优化

1. 数据组织方式

   在InnoDB存储引擎中，数据都是根据主键顺序存放的，这种存储发方式的表 称为 索引组织表**IOT**（index organized table）

2. 页分列

   页可以为空，也可以填充一半，也可以填充100%，每个也包含了2-N行数据（如果一行数据多大 ，会行溢出），根据主键排列

3. 页合并

   当删除一行数据时，实际上记录并没有被物理删除，只是被标记（flaged）为 删除并且它的空间变得被允许其他记录声明使用

   当页 中删除的记录达到MERGE_THRESHOLD(默认为页的50%)，InnoDB会开始寻找最近的页（前或后）看看是否可以 将两页合并以优化空间 使用



**主键设置原则**

1. 满足业务需求的情况下，尽量降低主键的长度
2. 插入数据时 ，尽量选择顺序插入，选择使用AUTO_INCREMENT自增 主键
3. 尽量不要使用 UUID做主键或者是其他自然主键，如身份证号
4. 业务操作时，避免对主键的修改



#### order by优化

1. Using filesort：通过表的索引或全表扫描，读取满足条件的数据行，然后在排序缓存区sort buffer中完成排序操作，所以不是通过索引直接返回排序结果的排序都叫FileSort排序
2. Using index：通过有序索引顺序扫描直接返回有序数据，这种情况即为using index，不需要额外排序，操作效率高



创建索引时可以写上升序/降序，默认升序 

create index 索引名 on 表1(字段1 [ asc/desc ], 字段2 [ asc/desc ], ...)



**原则**

1. 根据排序字段建立合适的索引，多 字段排序时，也遵循最左前缀法则
2. 尽量使用覆盖索引
3. 多字段排序，一个 升序一个降序，此时需要注意联合索引在创建时的规则（ASC/DESC）
4. 如果不可避免的出现filesort，大量数据排序时 ，可以适当增大排序缓冲器大小sort_buffer_size(默认256k)



#### group by优化

1. 在分组操作时，可以通过索引来提高效率
2. 在分组操作时，索引的使用也是满足最左前缀法则



#### limit优化

官方推荐：覆盖索引+子查询

select s.* from 表1 s, (select id from 表1 order by id limit 20,10) a where s.id = a.id;



#### count优化

MyISAM：引擎把一个表的总行数存在磁盘上，因此执行count（*）的时候会直接 返回，效率高

InnoDB引擎：需要将数据一行行读取出来，然后累计

优化思路：自己计数



count几种用法

1. count()是一个聚合函数，对于返回的结果集，一行行的判断，如果count函数的参数不是NULL，就加1，否则不加，最后返回累计值

2. 用法：

   - count(*)

     InnoDB引擎并不会把全部字段取出来，而是专门做了优化，不取值，服务层直接按行进行累加

   - count(主键)

     InnoDB引擎会遍历整张表，把每一行的主键id值取出来，返回给服务层，服务层拿到主键后，直接进行累加（主键不可能为null）

   - count(字段)

     - 没有not null约束：InnoDB引擎会遍历整张表把每行字段都取出来，返回给服务层判断是否为null，不为null累加
     - 有not null 约束：InnoDB引擎会遍历  整张表把每行字段都取出来，返回给服务层，直接累加

   - count(1)

     InnoDB引擎遍历整张表，单不会把全部字段取出来，而是专门做了优化，不取值，服务层直接累加

   > [!note]
   >
   > 按照 效率排序：count(*)≈count(1)>count(主键 id)>count(字段)，建议使用count(\*)

   

#### update优化(避免行锁升级为表锁)

**update**更新数据要用索引更新，索引跟新为行锁，用没有索引的字段更新行锁会进化成表锁，降低并发效率

InnoDB的行锁是针对索引加锁，不是针对数据加锁，并且索引不能失效，否则行锁会进化成表锁



### 视图

视图是一种虚拟表

视图只保存了查询的sql逻辑，不保存查询结果，所以我们在创建视图的时候，主要的工作落在创建这条sql查询语句上



**创建**

CREATE [ OR REPLACE ] VIEW 视图名[(列名列表)] AS SELECT语句 [ WITH [ CASCADED | LOCAL ] CHECK OPTIO]

**查询**

查看创建视图：

SHOW CREATE VIEW 视图名;

查看视图数据：

SELECT * FROM 视图名 条件...;



**修改**

1. CREATE [ OR REPELACE ] VIEW 视图名[(列名列表)] AS SELECT语句 [ WITH  [ CASCASED | LOCAL ] CHECK OPTION ]
2. ALTER VIEW 视图名[(列名列表)] AS SELECT语句 [ WITH  [ CASCASED | LOCAL ] CHECK OPTION ]

**删除**

DROP VIEW [ IF EXISTS ] 视图名 [, 视图名 ]...



#### 视图的检测选项

当使用WITH CHECK OPTION 子句创建视图时，MySQL会通过视图检查正在更改的每行，如插入、更新、删除，以使其符合视图的定义。MySQL允许基于另一个视图创建视图，它还会检查依赖视图中的规则以保持一致。为确定检查范围，MySQL提供两个选项：cascaded和local，默认为cascaded



表user，字段id，name

CASCADED：

```mysql
-- 1、创建v_user视图，条件id<=23
create view v_user as select id, name from user where id<=23;

-- 2、创建v_user1视图，条件id>=10，添加检测选项，因为v_user1依赖于v_user，所以在v_user2插入数据会检查v_user的条件
create view v_user1 as select id, name from v_user where id >=10 with cascaded check option;

-- 3、创建v_user2视图，条件id<=18
create view v_user2 as select id, name from v_user1 where id <=18;

-- 在v_user2中插入数据19，因没添加检测跳过3，2中写了检测，就会检测1、2的条件，满足1、2条件插入数据，但v_user2中没有数据，会出现在满足条件的视图中
insert into v_user2 values (19,'zhangs');

-- 在v_user2中插入数据19，因没添加检测跳过3，2中写了检测，就会检测1、2的条件，不满足1条件报错
insert into v_user2 values (25,'zhangs');
```



LOCAL：

local只检查自己视图定义的where条件，没定义不检查



#### 视图更新

##### 原则

要视图可更新，视图中的行与基础表中的行之间必须存在一对一的关系，如果视图包含以下任意一项，则不可更新：

1. 聚合函数或窗口函数（SUM(), MUN(), MAX(), COUNT()等）
2. DISTINCT
3. GROUP BY
4. HAVING
5. UNION或者 UNION ALL



##### 作用

1. 简单：视图不仅可以简化用户对数据的理解，也可以简化他们的操作，哪些经常使用的查询可以被定义为视图，从而使得用户不必为以后的操作每次指定全部条件
2. 安全：数据库可以授权，但不能授权到数据库特定行和特定的列上，通过视图用户只能查询和修改他们能够见到的数据
3. 数据独立：视图可以帮助用户屏蔽真实表结构变化的影响



### 存储过程

存储过程是事先经过编译并存储在数据库中的一段SQL语句的集合，调用存储过程可以简化应用开发的很多工作，减少数据在数据库和应用服务器之间的传输，提高数据处理的效率

存储过程思想，就是将数据库SQL语句表层的代码封装重用



**特点：**封装，复用，可以接收参数，也可以返回数据减少网络交互，提升效率



#### 语法

**创建**

```mysql
-- 创建完成出现在routines文件夹下
CREATE PROCEDURE 存储过程名([ 参数列表 ])
BEGIN
	SQL语句
END;
```



**调用**

```mysql
CALL 名称 ([ 参数 ]);
```



**查看**

```mysql
-- 方式1
SELECT * FROM INFORMATION_SCHEMA.ROUTINES WHERE ROUTINE_SCHEMA='数据库名';

-- 方式 2
SHOW CREATE PROCEDURE 存储过程名;
```



**删除**

```mysql
DROP PROCEDURE [IF EXISTS] 存储过程名;
```



> [!caution]
>
> 在命令行中，执行创建存储过程的SQL时，需要通过关键字delimiter指定SQL语句的结束符



#### 变量

系统变量是MySQL服务器提供，不是用户自定义的，属于服务器层面，分为全局变量（GLOBAL）、会话变量（SESSION）



##### 系统变量

**查看系统变量**

1. 查看所有

   SHOW [ SESSION | GLOBAL ] VARIABLES;

2. 模糊匹配查找

   SHOW [  SESSION | GLOBAL ] VARIBLES LIKE “...”;

3. 查看指定变量

   SELECT  @@[ SESSION | GLOBAL.]系统变量名;

> [!note]
>
> 不指定SESSION/GLOBAL默认SESSION
>
> 用@@指定要注意SESSION/GLOBAL后加`.`



**设置系统变量**

1. SET [ SESSION | GLOBAL ] 系统变量名 = 值;
2. SET @@[ SESSION | GLOBAL ] 系统变量名 = 值;



> [!caution]
>
> global设置的全局变量在数据库重启时会还原，永久设置需要改配置文件



##### 用户变量

用户变量是用户根据需要 自己 定义的变量，用户变量不用提前声明，在用的时候直接@变量名使用就可以，***作用域***为当前连接



**赋值**

SET @变量名 = expr [, @变量名 = expr]...;

SET @变量名 := expr [, @变量名 := expr]...;

SELECT @@变量名 := expr [, @变量名 := expr]...;

SELECT 字段名 INTO @变量名 FROM 表名;

> [!note]
>
> 建议使用`:=`命名变量，`=`可以做比较，也可以赋值，会有歧义



**使用**

SELECT@var_name;



##### 局部变量

局部变量是根据需要定义在局部生效的变量，访问之前，需要DECLARE声明，可以存储过程内的局部变量和输入参数，局部变量的范围在BEGIN...END中



**声明**

DECLARE 变量名 变量类型 [ DEFAULT ...];

变量类型就是数据库字段类型：INT、BIGINT、CHAR、VARCHAR、DATE、TIME等



**赋值**

SET 变量名=值;

SET 变量名:=值;

SELECT 字段名 INTO变量 FROM 表名...;



#### if判断

```mysql
if 条件1 then

-- 可选
elseif 条件2 then

-- 可选
else

end if;
```



#### 参数

```mysql
CREATE PROCEDURE 存储过程名([ IN/OUT/INOUT 参数名 参数类型 ])
BEGIN
	SQL语句
END;
```

| 类型  | 含义                       | 备注 |
| ----- | -------------------------- | ---- |
| IN    | 作为输入，调用时传入值     | 默认 |
| OUT   | 作为输出，该参数作为返回值 |      |
| INOUT | 可以作为输入/输出值        |      |



```mysql
CREATE PROCEDURE p1(IN a int, out b int)
BEGIN
	if a >10 then
	set b := 30;
	else 
	set b := 40;
	end if;
END;

CALL p1(2, @value);
```



#### case选择

```mysql
-- 语法1
CASE case_val:
	WHEN case_val1 THEN 
		SQL;
    [WHEN case_val2 THEN
    	SQL;]...
    [ELSE 
    	SQL;]
    	
END CASE;

-- 语法2
CASE 
	WHEN case_val1 THEN 
		SQL;
    [WHEN case_val2 THEN
    	SQL;]...
    [ELSE 
    	SQL;]
    	
END CASE;
```



#### while循环

```mysql
WHILE 条件 DO
	SQL;
END WHILE;
```



#### repeat循环

是有条件的循环语句，满足条件退出

```mysql
-- 先执行逻辑，然后判断逻辑是否满足，满足退出，不满足继续下次循环

REPEAT 
	SQL;
	
-- 退出条件
UNTIL 条件
END REPEAT;
```



#### loop循环

loop实现简单循环，如果不在sql逻辑中增加退出的条件，可以用来实现简单的死循环，loop可以配合以下两个语句使用：

1. LEAVE：配合循环使用，退出循环
2. ITERATE：必须在循环中，作用是跳过当前循环，进入下一次循环

```mysql
[begin_label:]LOOP
	SQL;
END LOOP [end_label];

-- 退出循环
LEAVE label;

-- 直接进入下个循环
ITERATE label;
```



#### 游标(CURSOR)

游标是用来存储查询结果集的数据类型，在存储过程和函数中可以使用游标对结果集进行循环处理，游标的使用包括声明、OPEN、FETCH和CLOSE

**声明游标**

DECLARE 游标名 CURSOR FOR 查询语句;

**打开游标**

OPEN 游标名;

**获取游标记录**

FETCH 游标名 INTO 变量[, 变量];

**关闭游标**

CLOSE 游标名;



> [!note]
>
> 需要先声明变量再声明游标



**为什么需要游标**

SQL 是**面向集合**的，一条 `SELECT` 返回一批行。但有些逻辑**必须逐行处理**：

1. 对每一行做不同判断、调用不同逻辑。
2. 逐行插入/更新到别的表。
3. 逐行拼接字符串、累加计算。



#### 条件处理程序

可以用来定义在流程控制结构执行过程中遇到问题时相应的处理步骤

```mysql
DECLARE handler_action HANDLER FOR 条件值[,条件值] SQL;
```

handler_action

1. ​	CONTINUE: 继续执行当前程序
2. ​	EXIT: 退出当前程序


条件值

1. ​	SQLSTATE sqlstate_value: 状态码，如 02000
2. ​	SQLWARING: 所有以01开头的SQLSTATE代码简写
3. ​	NOT FOUND: 所有以02开头的SQLSTATE代码简写
4. ​	SQLEXCEPTION: 所有没有被SQLWARNING或NOT FOUND捕获的SQLSTATE代码简写



### 存储函数

**用的少**

存储函数是有返回值的存储过程，存储函数的参数只能是`IN`类型

```mysql
CREATE FUNCTION 存储函数名([参数列表])
-- type 是返回数据类型
RETURNS type [characteristic...]
BEGIN
	SQL;
	RETURN ...;
END;
```

characteristic说明：

1. DETERMINSTIC：相同的输入参数总是产生相同的结果
2. NO SQL：不包括SQL语句
3. READS SQL DATA：包含读取数据的语句，但不能包含写入数据的语句



### 触发器

触发器是与表有关的数据库对象，指在insert/update/delete之前或之后，触发并执行触发器中定义的SQL语句集合，触发器的这种特性可以协助应用在数据库端确保数据的完整性，日志记录，数据校验等操作

使用别名OLD和NEW来引用触发器中发生变化的记录内容，这样其他的数据库是相似的，现在触发器还只支持行级触发，不支持语句级触发

| 触发器类型 | NEW和OLD                                             |
| ---------- | ---------------------------------------------------- |
| INSERT型   | NEW表示将要或者已经新增的数据                        |
| UPDATE型   | OLD表示修改之前的数据，NEW表示将要或已经修改后的数据 |
| DELETE型   | OLD表示将要或者已经删除的数据                        |

**创建**

```mysql
CREATE TRIGGER trigger_name
BEFORE/AFTER INSERT/UPDATE/DELETE
-- 行级触发器
ON tbl_name FOR EACH ROW 
BEGIN 
	trigger_stmt;
	
END;
```

**查看**

```mysql
SHOW TRIGGERS;
```



**删除**

```mysql
-- 如果没有指定schema_name,默认为当前数据库
DROP TRIGGER [schema_name.]trigger_name;
```



例子：

```mysql
create trigger new_trigger
-- 在movie中插入数据后触发
after insert on movie for each row
begin 
	insert into movie1(id, name, email, old_info) values (null, new.name, new.email, '');
end;
```



```mysql
create trigger new_trigger
-- 在movie中更新数据后触发
after update on movie for each row
begin 
	insert into movie1(id, name, email, old_info) values (null, new.name, new.email, concat("old_data", old.name, "和", old.email));
end;
```



### 锁

锁是计算机协调多个进程或线程并发访问某一资源的机制，在数据库中，传统的计算资源（CPU，RAM，I/O）的争用以外，数据也是一种供许多用户共享的资源，如何保证数据并发访问的一致性、有效性是所有数据库必须解决的一个问题，锁冲突也是影响数据库并发访问性能的一个重要因素，从这个角度来说，锁对数据库尤为重要，也更加复杂



分类

MySQL的锁，按照锁的颗粒度分，分为3类

1. 全局锁：锁定数据库中的所有表
2. 表级锁：每次操作锁定整张表
3. 行级锁：每次操作锁住对应的行数据



#### 全局锁

就是对整个数据库实例加锁，加锁之后整个实例处于只读状态，后续的DML的语句，DDL语句，已经更新操作的事务提交语句都将阻塞

典型使用场景是做全库的逻辑备份，对所有的表进行锁定，从而获取一致性视图，保证数据的完整性



```mysql
-- 给数据库添加全局锁
flush tables with read lock;

-- 备份数据
mysqldump -u用户名 -p密码 数据库 >	导出文件名;
mysqldump -uroot -p1234 mydb > mydb.sql;

-- 取消全局锁
unlock tables;
```



**特点**：

数据库中加全局锁，是一个比较重的操作，存在以下问题：

1. 如果 在主数据库上备份，那么在备份期间都不能执行更新，业务基本上停摆
2. 如果在从库上备份，那么在备份期间从库不能执行主库同步过来的二进制日志，导致主从延迟



在InnoDB引擎中，可以在备份时加上参数`--single-transction`参数来完成不加锁的一致性数据备份

```mysql
-- 备份数据
mysqldump --single-transation -u用户名 -p密码 数据库 >	导出文件名;
```



#### 表级锁

每次操作锁住整张表，锁定粒度大，发生锁冲突的概率最高，并发度最低，应用在MyISAM、InnoDB、BDB等引擎

表级锁主要分为三类：表锁、元数据锁、意向锁



##### 表锁

分为两类：

1. 表共享读锁
2. 表独占写锁



语法：

1. 加锁

   ```mysql
   lock tables 表1... read/write;
   ```

2. 释放锁：

   ```mysql
   unlock tables;  -- 或者直接断开客户端连接
   ```



> [!note]
>
> 一客户端给数据表加读锁，都能读数据但不能写入数据
>
> 一客户端给数据库加写锁，该客户端能读写，其他不能读写



##### 元数据锁

MDL加锁过程是系统自动控制，无需显示使用，在访问一张表的时候会自动加上。MDL锁主要作用是维护表元数据一致性，在表上有活动事务的时候，不可以对元数据进行写入操作。**为了避免DML与DDL冲突，保证读写的正确性**

在MySQL5.5中引入了MDL，当对一张表进行增删改查时，加MDL读锁（共享）；当对表结构进行变更操作时，加MDL写锁

| 对应SQL                                       | 所类型                                | 说明                                         |
| --------------------------------------------- | ------------------------------------- | -------------------------------------------- |
| lock tables xxx read/wirte                    | SHARED_READ_ONLY/SHARED_ON_READ_WIRTE |                                              |
| select、select ... lock in share mode         | SHARED_READ                           | 与SHARED_READ、SHARED_WIRTE兼容，与EXCLUSIVE |
| insert、update、delete、select ... for update | SHARED_WRITE                          | 与SHARED_READ、SHARED_WIRTE兼容，与EXCLUSIVE |
| alter table ...                               | EXCLUSIVE                             | 与其他DML相互排斥                            |



**查看元数据锁**

```mysql
select object_type, object_schema, object_name, lock_type, loack_duration from performance_schema.metadata_locks;
```



##### 意向锁

为了避免DML在执行时，加的行锁与表锁冲突，在InnoDB中引入了意向锁，使得表锁不用检查每行数据是否加锁，使用意向锁来减少锁检查

1. 意向共享锁（IS）：由语句select ... lock in share mode添加

   与表锁共享锁（read）兼容，与表锁排他锁（write）互斥

2. 意向排他锁（IX）：由insert、update、delete、select ... for update添加

   与表锁共享锁和排他锁都互斥。意向锁之间不互相拍照

```mysql
select object_schema, object_name, index_name, lock_type, lock_mode, lock_data from performance_schema.data_locks;
```



#### 行级锁

行级锁，每次操作锁住对应的行数据，锁定颗粒度最小，发生锁冲突的概率最低 ，并发度最高，应用在InnoDB存储引擎中 

InnoDB的数据是基于索引组织的，行锁是通过对索引上的索引项加锁来实现的，而不是对记录加锁。对于行级锁，主要分为以下三类：

1. 行锁 ：锁定单个行记录的锁，防止其他事务对此行进行update和delete，在RC、RR隔离级别下都支持
2. 间隙锁：锁定索引记录 间隙（不含该记录 ），确保 索引记录间隙不变，防止其他事物在这个 间隙 进行insert，产生幻读。在RR隔离级别下都支持
3. 临建锁：行锁和间隙锁组合，同时锁住数据，并锁住数据前的间隙Gap，在RR隔离级别下支持



InnoDB实现了以下 两种形式的行锁：

1. 共享锁（S）：允许一个事务去读一行 ，阻止其他事务获取相同数据集的排他锁
2. 排他锁（X）：允许获取排他锁的事务更新 数据，阻止其他事务获取相同数据集的共享锁和排他锁

|            | 请求锁类型 | S 共享锁 | X 排他锁 |
| ---------- | ---------- | -------- | -------- |
| 当前锁类型 |            |          |          |
| S 共享锁   |            | 兼容     | 冲突     |
| X 排他锁   |            | 冲突     | 冲突     |

| SQL                           | 行锁类型   | 说明                                    |
| ----------------------------- | ---------- | --------------------------------------- |
| INSERT ...                    | 排他锁     | 自动加锁                                |
| UPDATE ...                    | 排他锁     | 自动加锁                                |
| DELETE ...                    | 排他锁     | 自动加锁                                |
| SELECT (正常)                 | 不加任何锁 |                                         |
| SELECT ... LOCK IN SHARE MODE | 共享锁     | 需要手动在SELEC之后加LOCK IN SHARE MODE |
| SELECT ... FOR UPDATE         | 排他锁     | 需要手动在SELECT之后加 FOR UPDATE       |



**行锁**

默认情况下，InnoDB在REPEATABLE READ事务 隔离级别 运行，InnoDB使用next-key锁进行搜索和索引扫描 ，防止 幻读

1. 针对唯一索引进行检索时，对已存在的记录进行等值匹配时，将会自动优化为行锁
2. InnoDB的行锁是针对索引加的锁 ，不通过索引条件检索数据，那么InnoDB将对表中所有 记录加锁，此时就会升级为表锁



**间隙锁/临键锁**

默认情况下 ，InnoBD在REPEATABLE READ事务 隔离级别 运行，InnoDB使用next-key锁进行搜索和索引扫描 ，防止 幻读

1. 索引上的等值查询（唯一索引），给不存在的记录加锁时，优化为间隙锁
2. 索引上的等值查询（普通索引），向右遍历时最后一个值不满足查询需求时，next-key lock  退化为间隙锁
3. 索引上的范围查询（唯一索引），会访问到不满足他条件的唯一值为止

> [!caution]
>
> 间隙锁唯一目的是防止其他事务插入间隙，间隙锁可以共存，一个事务 采用的间隙锁不会阻止另一个事务在同一间隙上采用间隙锁



