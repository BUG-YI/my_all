# JavaEE

## servlet

 **Server Applet** 的简称，中文名为**小服务程序**或**服务连接器**。它是用 **Java** 编写的服务器端程序，具有独立于平台和协议的特性，主要功能在于交互式地浏览和生成数据，生成动态 Web 内容。

主要功能包括：

1. **读取客户端发送的数据**：包括网页上的 HTML 表单数据，或者来自 applet 或自定义的 HTTP 客户端程序的表单数据。
2. **处理数据并生成结果**：可能需要访问数据库，执行 RMI 或 CORBA 调用，调用 Web 服务，或者直接计算得出响应。
3. **发送数据到客户端**：包括文本文件（HTML 或 XML）、二进制文件（GIF 图像）、Excel 等。
4. **发送 HTTP 响应到客户端**：包括设置 cookies 和缓存参数。



### 实现

创建JavaEE项目

![image-20260314130921007](C:\Users\25172\AppData\Roaming\Typora\typora-user-images\image-20260314130921007.png)

在项目名称文件夹下创建Java类

继承HTTPServlet类，重写方法

```java
package com.yi.demo1.base;

import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;

import java.io.IOException;

//WebServlet注解
@WebServlet("/api") //浏览器访问路径，在原有的路径下加上api访问
public class servlet extends HttpServlet {
    @Override
    //req请求，resp响应
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException{
        System.out.println("hello");//控制台打印
        resp.getWriter().write("hello1");//访问后浏览器页面输出
    }
}
```



### servlet生命周期

**init**方法，在servlet实例创建之后执行，证明servlet有实例创建，只执行一次

```java
public void init(ServletConfig config) throws ServletException {
    System.out.println("创建了实例")
}
```



**service**方法，每次请求到达某个servlet方法时执行，用于处理请求

```java
protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    System.out.println("调用了服务")
}
```



**destroy**方法，servlet实例销毁时执行

```java
public void destory(){
    System.out.println("实例销毁")
}
```



### HttpServletRequest对象

HttpServletRequest用于接收客户端发送的请求



#### 常用方法

| 方法                 | 介绍                             |
| -------------------- | -------------------------------- |
| getRequestURL()      | 获取客户端发出请求时的完整URL    |
| getRequestURI()      | 获取请求行中的资源名称部分       |
| getQueryString()     | 获取请求行中的参数部分           |
| getMethod()          | 获取客户端请求方式               |
| getProtocol()        | 获取Http版本号                   |
| getContextPath()     | 获取webapp名字                   |
| getParameter()       | 获取指定参数的值，返回字符串     |
| getParameterValues() | 返回指定参数的所有值，字符串数组 |

示例

```java
String contextPath = req.getContextPath();
```



#### 请求乱码问题

Get请求不会，Post请求会乱码

设置编码格式

```java
req.setCharacterEncoding("UTF-8");
```



#### 请求转发

地址栏不变，请求跳转到其他路径

```java
req.getRequestDispatcher("路径").forward(req,resp);
```







### HttpServletrespond对象