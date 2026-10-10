# SpringBoot AI

### 快速开始

拉取项目：[springboot](https://start.springboot.io)

JDK17，MAVEN

> [!TIP]
>
> 建议用springboot 4.x.x 版本
>
> 3.x.x 拉取项目依赖可能会出现问题



#### 项目依赖

pom.xml

必要依赖

web

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```



pom提供版本项目集中管理

```xml
<dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>org.springframework.ai</groupId>
            <artifactId>spring-ai-bom</artifactId>
            <version>2.0.0</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>
    </dependencies>
</dependencyManagement>
```



ai接口依赖以deepseek为例

```xml
<dependency>
    <groupId>org.springframework.ai</groupId>
    <artifactId>spring-ai-starter-model-deepseek</artifactId>
</dependency>
```



### BigModel AI 模型

现在以bigmodel为例，deepseek没token😅



#### 申请账号/获取API KEY

[bigmodel官方 Java SDK - 智谱AI开放文档](https://docs.bigmodel.cn/cn/guide/develop/java/introduction)

1. [注册账号](https://www.bigmodel.cn/invite?icode=nqwkRJBnF6LuPB%2FFuW15V7C%2Fk7jQAKmT1mpEiZXXnFw%3D)（新用户会送限时token）
2. [获取api key](https://bigmodel.cn/apikey/platform)

> [!TIP]
>
> 建议将获取到的api key写入环境变量，上传的git就不会携带你独有的key



修改ai依赖就行

```xml
<dependency>
    <groupId>ai.z.openapi</groupId>
    <artifactId>zai-sdk</artifactId>
    <version>0.3.5</version>
</dependency>
```





#### 流式对话

```java

```



