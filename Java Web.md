# Java Web

<!--起：2025.12.15-->

java server page(jsp)以Java为基础开发，所以它沿用Java强大的API。JSP页面中HTML代码用来显示静态内容部分，嵌入到页面中的Java代码与与JSP标记用来生成动态内容部分。



JSP页面元素的组成：

1. 静态部分：HTML标记、CSS样式和普通的静态文本
2. 指令：以`<%@ 指令名`标记开始，以`%>`结束
3. 表达式：<%= java 表达式%>
4. 脚本：<% java代码 %>
5. 声明：<%! 方法或者变量%>
6. 动作：以`<jsp:动作名>`标记开始，以`</jsp:动作名>`结束
7. 注释：<%-- 注释内容 --%>



## 环境搭建

1. 基本的Java jdk安装
2. Tomcat服务器搭建

​	官网上tomcat是一个7个文件压缩包，解压即用



## JSP基础

JSP脚本段（scriptlet）是一个有效的程序段

1. JSP脚本段中只能出现Java代码，不能出现其他模块元素
2. 必须遵循Java语法
3. JSP页面可以有多个脚本段，在两个脚本段间可以嵌入文本、HTML标记和其他JSP元素
4. 多个脚本段可以相互访问，单个脚本段中的Java语句可以不是完整的，但多个脚本段组成的完整代码必须是完整的



### 基础语法

#### JSP声明

```JSP
<%! 声明1;声明2;...; %>
```

1. 可以直接使用`<%@ page%>`中声明的变量和方法
2. 本页的声明只在本页生效，在其他页面使用，可以将他们写成一个独立的文件，让后用<%@ include %>或`<jsp:include>`包含导入

实例：

```JSP
<%! 
    public int count;  <%-- 声明变量   --%>
	public void info(){  <%-- 声明方法   --%>
		out.print("hello!")
}
%>                               <%--  每次刷新页面会自增1  --%>

<% out.println(count++) %>
```



#### JSP表达式

```JSP
<%=变量或表达式 %>
```



实例：

```JSP
<%@ page import="org.apache.jasper.compiler.Node" %>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>实例</title>
</head>
<body>
<%!
    String str="http://www.baidu.com";
%>

<a href="<%=str%>">点击跳转</a>      <%--实现跳转到百度--%>
<form action="<%=str%>">
    <input type="submit" value="点击跳转">
</form>
</body>
</html>
```



#### JSP注释

JSP：`<%--    --%>`

Java：`/   /`或`/*   */`

HTML：`<!--    -->`



### JSP指令标记

#### page页面标记

page指令用于定义与整个JSP页面相关的各种属性

```JSP
<%@page 属性1=“值1” 属性2=“值2” ...%>
```

| 属性         | 解释                                                         | 默认值                     |
| ------------ | ------------------------------------------------------------ | -------------------------- |
| language     | 声明要使用的脚本语言，暂时只能用Java                         | java                       |
| import       | 在程序中导入一个或多个类和包                                 |                            |
| session      | 设定客户是否需要HTTP Session，取值为true/false，若为true，则表示session是有用的 | true                       |
| autoFlash    | 设置缓冲区填满时是否进行缓冲自动刷新                         | true                       |
| isThreadSafe | 设置JSP页面是否支持多线程，值为false时限制每次只能有一个用户访问该页面 | true                       |
| isErrorPage  | 指定当前页面的出错处理页面的url                              |                            |
| contentType  | 指定JSP字符的编码和JSP页面响应的MIME类型，格式为“MIME类型；字符集类型” | “text/html;charset=gb2312” |

实例：

```jsp
<@%page contentType=“text/html;charset=gb2312”%>
<@%page import="java.sql.*"%>
<%@page errorPage="err.jsp"%>
```



#### include静态包含指令标记

引入其他jsp页面，引入后，jsp引擎会将两个jsp页面翻页为一个servlet。

include指令也称为静态引入指令

```jsp
<%@include file="路径"%>
```



> [!NOTE]
>
> 引入的文件不要包含<html></html>,<body></body>等标记



#### taglib指令标记

用于引入jsp页面中需要使用的标签库的定义，以便在页面中使用标签库定义的标签

```jsp
<%@taglib url="标签库URI" prefix="自定义标签的前缀"%>
```



实例：

```jsp
<%@taglib url="http://www.tjdz.net/tags" prefix="public"%>
<public:pool>
...
</public:pool>
```



> [!CAUTION]
>
> 定义标签时，不能用jsp，jspx，java，javax，servlet，sun，sunw作为前缀



### jsp动作标记

#### `<jsp:include>`

可以用来包含其他静态或动态文件

**不带参数**

```jsp
<jsp:include page="相对url" flush="ture|false"/>
```



**带参数**

```jsp
<jsp:include page="相对url" flush="ture|false"/>
<jsp:param name="属性名" value="属性值"/>
<jsp:param...>
</jsp:include>
```



#### `<jsp:forward>`

用于在服务器终端终止当前页面的运行，并重定向到其他指定页面重定向可以是静态的HTML页面，jsp页面，或者是一个程序段



**不带参数**

```jsp
<jsp:forward page="页面url">
```



**带参数**

```jsp
<jsp:forward page="页面url">
<jsp:param name="属性名" value="属性值"/>
...
</jsp:forward>
```



#### `<jsp:param>`

用来传递参数给jsp页面

```jsp
<jsp:param name="属性名" value="{参数值|<%=表达式%>}"/>
```



jsp页面通过**request.getParameter(“属性名”)**来获取参数值

`<jsp:forward>`标记必须搭配`<jsp:include>,<jsp:forward>或<jsp:plugin>`等标记使用



#### `<jsp:plugin>`

用于jsp网页加载Java Applet或JavaBean程序组件，与HTML的`<Applet>与<Object>`标签有类似功能

| 属性           | 解释                                                         |
| -------------- | ------------------------------------------------------------ |
| type           | 加载Java程序的类型，可设置的值有Applet和Bean                 |
| code           | 加载Java程序编译后的类名称，如showpic.class                  |
| codebase       | 编译后Java程序所在的目录，可设置绝对路径或相对路径。若未设置此属性，则以当前执行页面所在的目录为默认值 |
| name           | 用来加载对Java Applet 和JavaBean程序设置一个用以识别的名称   |
| align          | 设置加载的程序在窗口的对齐方式，可设置的有bottom（下对齐），top（上对齐），middle（中对齐），left（左对齐），right（右对齐） |
| height         | 加载的程序在窗口中显示的高度                                 |
| width          | 加载的程序在窗口中显示的宽度                                 |
| hspace         | 加载程序的显示区与网页其他内容的水平间距                     |
| vspace         | 加载程序的显示区与页面其他内容的垂直间距                     |
| `<jsp:params>` | 若要传递参数给加载程序，必须在`<jsp:params>`和`</jsp:params>`的起始标签和结束标签中使用`<jsp:param>`操作元素来设置 |



#### `<jsp:useBean>`

用来加载jsp页面中使用的JavaBean

```jsp
<jsp:useBean id="JavaBean实例名称" scope="pagelrequestlsessionlapplication" class="package.class"></jsp:useBean>
```

id指JavaBean实例变量的名称

scope指该指定该Bean变量的有效范围：page指只在当前jsp页面有效

request指在任何执行相同请求的jsp页面中使用该Bean，直到页面执行完毕

session指从创建该Bean开始，在相同session下的jsp页面中可以使用该Bean

application指从创建该Bean开始，在相同application下的jsp页面可以使用该Bean



实例

```jsp
<jsp:useBean id="clock" scope="page" class="java.util.Date"/>
```



#### `<jsp:setProperty>`

用于设置已经实例化的Bean对象的属性

```jsp
<jsp:setProperty
     name="JavaBean实例名称"{
         property="*"|
         property="属性名"[param="参数"]|
         property="属性名" value="{String|<%=表达式%>}"
                 }
/>
```

`<jsp:setProperty>`中name值必须和`<jsp:useBean>`中的id值相同，且大小写敏感



#### `<jsp:getProperty>`

可获取Bean的属性值，用于在页面显示

```jsp
<jsp:getProperty name="JavaBean实例名称" property="属性名"/>
```

 

### jsp内置对象

| 对象名称    | 衍生类 | 功能简述                       | 对象作用域  |
| ----------- | ------ | ------------------------------ | ----------- |
| request     |        | 取得客户端与系统的信息         | request     |
| response    |        | 响应客户端信息                 | page        |
| application |        | 记录与处理上线者共享的数据     | page        |
| session     |        | 记录与处理上线者的个别数据     | session     |
| out         |        | 控制数据输出的操作             | application |
| config      |        | 取得jsp编译后的Servlet信息     | page        |
| pageContext |        | 存取和处理系统运行时的各种信息 | page        |
| page        |        | 代表目前的这个jsp网页对象      | page        |
| exception   |        | 异常处理机制                   | page        |



#### request常用方法

| 方法                                  | 说明                                               |
| ------------------------------------- | -------------------------------------------------- |
| getAttribute(String name)             | 返回name所指定的属性值                             |
| setAttribute(String name，Object obj) | 设定name所指定的属性值为obj                        |
| removeAttribute(String name)          | 删除name所指定的属性                               |
| getAttributeNames()                   | 返回request对象所有的属性名称集合                  |
| getParameter(String name)             | 从客户端获取name所指定的参数值                     |
| getParameter Names()                  | 从客户端获取所有参数名称                           |
| getParameterValues(Sting name)        | 从客户端获取name所指定参数的所有值                 |
| setCharacterEncoding(String encoding) | 设定请求正文中使用的字符编码（只支持post提交数据） |



#### response常用方法

| 方法                                | 说明                                     |
| ----------------------------------- | ---------------------------------------- |
| setContentType(String type)         | 动态响应contentType属性                  |
| setHeader(String name,String value) | 设置HTTP应答报文的首部字段和值及自动更新 |
| sendRedirect(String redirect)       | 将客户端重定向到指定的url                |
| setStatus(int n)                    | 设置HTTP返回的状态值                     |
| addCookie(Cookie cookie)            | 添加一个Cookie对象                       |



#### out常用方法

| 方法                   | 说明                                                         |
| ---------------------- | ------------------------------------------------------------ |
| clear()                | 清除缓冲区中的数据，如缓冲区已经是空的，则会产生IOException异常 |
| clearBuffer()          | 清除缓冲区中的数据，若缓冲区已经是空的，并不会产生IOException异常 |
| flush()                | 直接将暂存与缓冲区的数据清空并输出到页面                     |
| getBufferSize()        | 返回缓冲区的大小                                             |
| getRemaining()         | 返回缓冲区中剩余空间的大小                                   |
| isAutoFlush()          | 返回布尔值，表示是否自动输出缓存区中的数据                   |
| newline()              | 输出换行                                                     |
| print(datatype data)   | 输出数据类型为datatype的数据data                             |
| println(datatype data) | 输出数据类型为datatype的数据data，并自动换行（下一个输出语句在下以行开始输出） |



#### session常用方法

| 方法                                 | 说明                                                         |
| ------------------------------------ | ------------------------------------------------------------ |
| setAttribute(String name,Object obj) | 在session中设定name所指定的属性值为obj                       |
| getAttribute(String name)            | 返回session中name所指定的属性值                              |
| getAttributeNames()                  | 返回session中所有变量的名称                                  |
| removeAttribute(String name)         | 删除session中name所指定的属性                                |
| invalidate()                         | 销毁与用户关联的session                                      |
| getCreationTime()                    | 返回session建立的时间，返回值为1970.1.1开始算到session建立时的时间，毫秒 |
| getLastAccessedTime()                | 返回客户端对服务器提出请求至处理session中数据的最后处理时间，若新建的session，则返回-1 |
| getMaxInactiveInterval()             | 返回客户端未对session开始停滞到自动消失之间所间隔的时间，返回单位为秒 |
| isNew                                | 返回布尔值，表示是否为新建的session。新建是指程序调用session对象在服务器端建立session，而尚未将此session的信息记录到客户端的Cookie中 |
| setMaxInactiveInterval(int interval) | 设置客户端未对session提出请求而session开始停滞到自动消失之间所间隔的时间为interval，以秒为单位 |



#### application常用方法

| 方法                                 | 说明                                          |
| ------------------------------------ | --------------------------------------------- |
| setAttribute(String name,Object obj) | application中设定name所指定的属性值为obj      |
| getAttribute(String name)            | 返回application中name所指定的属性             |
| getAttributeNames()                  | 返回application中所有变量的名称               |
| removeAttribute(String name)         | 删除application中name所指定的属性             |
| getMajorVersion()                    | 返回服务器解释引擎所支持的最新Servlrt API版本 |
| getMajorVertion()                    | 返回服务器解释引擎所支持的最低Servlrt API版本 |
| getMimeType(String file)             | 返回文件file的文件格式与编码方式              |
| getRealPath(String path)             | 返回虚拟路径path的真实路径                    |
| getServerInfo()                      | 返回服务器解析引擎的信息                      |





### JDBC技术

#### 环境搭建

安装MySQL数据库



#### 连接MySQL数据库

##### 加载jdbc数据库驱动



##### 建立数据库连接

DriverManager类是JDBC的管理层，用于用户和驱动程序之间

**常用方法**

| 方法名                                                       | 功能说明                                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Static connection getConnection(String url,String user,String password) | 用于建立到指定数据库url连接。其中，url为jdbc:subprot6col:subname 形式的数据库 url；user为数据库用户名；password为用户的密码 |
| static Driver getDriver(String url)                          | 用于返回能够打开url指定的数据库的驱动程序                    |

