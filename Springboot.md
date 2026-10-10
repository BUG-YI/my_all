# Springboot

### yaml配置语法

#### 普通值

key:空格（必要value

```yaml
name: zhangs
```



#### 对象

```yaml
student:
	name: zhangs
	age: 3
```



#### 行内写法

```yaml
student: {name: zhangs,age: 18}
```



#### 数组

```yaml
pets:
 	- cat
	- dog
	- pig
	
pets: [cat,dog,pig]
```



### 邮件

xml配置

```xml
<!--添加配置-->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-mail</artifactId>
</dependency>
```



yml配置

```yaml
spring:
	mail:
		username: 发送者邮箱
		password: 邮箱授权码
		host: smtp.qq.com
		port: 465
		default-encodeing: utf-8
		properties: 
			mail:
				smtp: 
					auth: true
					ssl:
						enable: true
						required: true
                transport:
                	protocol: smtp
```



创建类

```java
package com.yi.hello.component;

import org.springframework.beans.factory.annotation.Value;
import org.springframework.mail.MailException;
import org.springframework.mail.SimpleMailMessage;
import org.springframework.mail.javamail.JavaMailSender;
import org.springframework.stereotype.Component;
    
@Component
public class EmailUtils{
    private final JavaMailSender mailSender;
    public EmailUtils(JavaMailSender mailSender){
        this.mailSender=mailSender;
    }
    @Value("${spring.mail.username}")
    private String fromEmail;
    public void sendeVerity(String toEmail,String code){
        SimpleMailMessage smm = new SimpleMailMessage();
        smm.setFrom(fromEmail);
        smm.setTo(toEmail);
        smm.setSubject("邮件title");
        smm.setText("邮件内容");
        try{
            mailSender.send(smm);
        }catch(MailException){
            throw new RuntimeExceptionn(e.getMessage());
        }
    }
}
```



```java
package com.yi.hello.Controller;

import com.yi.hello.component.EmailUtils;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.*;
import java.util.Random;

@RestController
@RequsetMapping("/api")
@CrossOrigin("*")
public class EmailVerity{
    private final EmailUtils emailUtils;
    public EmailVerity(EmailUtils emailUtils){
        this emailUtils = emailUtils;
    }
    //生成随机验证码
    private String getVerityCode(){
        Random r = new Random();
        StringBuilder code = new StringBuilder();
        for(int i=0;i<6;i++){
            code.append(r.nextInt(0,10));
        }
        return code.toString();
    }
    @GetMapping("/sendVerity")
    public ResponseEntity<?> sendr(@RequestParam String email){
        try{
            emailUtils.sendVerity(email,getVerityCode());
            return ResponseEntity.ok().body("verity send success!");
        }catch(Exception e){
            return ResponseEntity.badRequest().body("e.getMessage()");
        }
    }
}    
```



html

```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>test</title>
</head>
<body>
    邮箱 <input type="text" id="mail">
    <button onclick="sendV()">submit</button>
<script>

    async function sendV(){
        const mail = document.getElementById('mail').value;
        const res = await fetch(`http://localhost:8080/api/sendVerity?email=${mail}`,{
            method:'get'
        })
        if (res.ok){
            alert(await res.text())
        }else { alert(await res.text())}
    }
</script>
</body>
</html>
```



## redis配置

```xml
<dependency>
    <groupId>org.springframework.data</groupId>
    <artifactId>spring-data-redis</artifactId>
</dependency>
<dependency>
    <groupId>redis.clients</groupId>
    <artifactId>jedis</artifactId>
</dependency>
```



```yaml
```



redis配置类

```java
package com.yi.springbootproject.Configuraton;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.data.redis.connection.RedisClusterConfiguration;
import org.springframework.data.redis.connection.RedisConnectionFactory;
import org.springframework.data.redis.connection.RedisStandaloneConfiguration;
import org.springframework.data.redis.connection.jedis.JedisClientConfiguration;
import org.springframework.data.redis.connection.jedis.JedisConnectionFactory;
import org.springframework.data.redis.core.RedisTemplate;
import org.springframework.data.redis.serializer.StringRedisSerializer;
import redis.clients.jedis.Jedis;
import redis.clients.jedis.JedisPoolConfig;

import java.time.Duration;


@Configuration
public class RedisConfig {
    @Bean
    public RedisConnectionFactory redisConnectionFactory(){
        //设置单机远程配置地址
        RedisStandaloneConfiguration standaloneConfiguration = new RedisStandaloneConfiguration("127.0.0.1",6379);

        //集群redis服务器配置(括号中配置个IP地址)
//        RedisClusterConfiguration clusterConfiguration=new RedisClusterConfiguration();


//      连接池相关配置
        JedisPoolConfig jedisPoolConfig=new JedisPoolConfig();
        //最大连接数
        jedisPoolConfig.setMaxTotal(8);
        //最大空闲数
        jedisPoolConfig.setMaxIdle(8);
        //最小空闲
        jedisPoolConfig.setMinIdle(1);
        //最长等待时间,2分30秒
        Duration d5 = Duration.parse("PT2M30S");
        jedisPoolConfig.setMaxWait(d5);

        //使用连接池
        JedisClientConfiguration clientConfiguration=
                JedisClientConfiguration.builder()
                        .usePooling()
                        .poolConfig(jedisPoolConfig)
                        .build();

        return new JedisConnectionFactory(standaloneConfiguration,clientConfiguration);
    }
    @Bean
    public RedisTemplate<String,Object> redisTemplate(RedisConnectionFactory redisConnectionFactory){
        RedisTemplate<String,Object> redisTemplate=new RedisTemplate<>();
        redisTemplate.setConnectionFactory(redisConnectionFactory);

        //序列化
//        redisTemplate.setDefaultSerializer(new StringRedisSerializer());

        return redisTemplate;
    }
}
```



简单使用

```java
public class A{
    private final RedisTemplate<String,Object> redisTemplate;
    public UserController(RedisTemplate<String, Object> redisTemplate) {
        this.redisTemplate = redisTemplate;
    }
    
    
    public 
}
```



## QR二维码

Maven配置

```xml
<dependency>
    <groupId>com.google.zxing</groupId>
    <artifactId>core</artifactId>
    <version>3.5.2</version>
</dependency>
<dependency>
    <groupId>com.google.zxing</groupId>
    <artifactId>javase</artifactId>
    <version>3.5.2</version>
</dependency>
```



实例

```java
import com.google.zxing.EncodeHintType;
import jakarta.servlet.http.HttpServletResponse;
import org.springframework.http.MediaType;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

import com.google.zxing.BarcodeFormat;
import com.google.zxing.client.j2se.MatrixToImageWriter;
import com.google.zxing.common.BitMatrix;
import com.google.zxing.qrcode.QRCodeWriter;

import java.io.OutputStream;
import java.util.HashMap;
import java.util.Map;

@RestController
@RequestMapping("/api")
public class QRC {
    /**
     * @param content 文本内容，连接等
     * @param width height 二维码宽，高
     * @param resp 响应
     * @throws Exception 抛出异常
     */
    
    // produces 返回内容类型
    @GetMapping(value = "/createQRC",produces = MediaType.IMAGE_PNG_VALUE)
    public void cQRC(
            @RequestParam(defaultValue = "https://www.baidu.com") String content,
            @RequestParam(defaultValue = "200")int width,
            @RequestParam(defaultValue = "200")int height,
            HttpServletResponse resp)throws Exception{
        QRCodeWriter QRCw=new QRCodeWriter();
        Map<EncodeHintType,Object> hints =new HashMap<>();
        hints.put(EncodeHintType.CHARACTER_SET,"utf-8");

        BitMatrix bitMatrix=QRCw.encode(
                content,
                BarcodeFormat.QR_CODE,
                width,
                height,
                hints
        );
        resp.setContentType(MediaType.IMAGE_PNG_VALUE);
        OutputStream out=resp.getOutputStream();
        MatrixToImageWriter.writeToStream(bitMatrix,"PNG",out);
        out.close();
     }
}
```





## Token生成

JWT Token生成

xml配置

```xml
        <dependency>
            <groupId>io.jsonwebtoken</groupId>
            <artifactId>jjwt-api</artifactId>
            <version>0.11.5</version>
        </dependency>
        <dependency>
            <groupId>io.jsonwebtoken</groupId>
            <artifactId>jjwt-impl</artifactId>
            <version>0.11.5</version>
        </dependency>
        <dependency>
            <groupId>io.jsonwebtoken</groupId>
            <artifactId>jjwt-jackson</artifactId>
            <version>0.11.5</version>
            <scope>runtime</scope>
        </dependency>
```

appliaction.yml配置

```yml
spring:
 jwt:
  secret: "asdg"	#自己随意配置，尽量大于30位，且复杂
  expriation: 600	#token存在时长，秒
  token-header: "Authorization"
  token-prefix: "Bearer "
```

token配置类,导入yml配置

```java
package com.yi.springbootproject.Configuraton;

import lombok.Data;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.boot.context.properties.ConfigurationProperties;
import org.springframework.stereotype.Component;

@Data
@Component
@ConfigurationProperties(prefix = "jwt")

public class TokenConfig {
    @Value("${spring.jwt.secret}")
    private String secret;
    @Value("${spring.jwt.expiration}")
    private long expiration;
    @Value("${spring.jwt.token-header}")
    private String tokenHeader;
    @Value("${spring.jwt.token-prefix}")
    private String tokenPrefix;
}
```

tokenUtil工具类

```java
package com.yi.springbootproject.Component.Utils;

import com.yi.springbootproject.Configuraton.TokenConfig;
import io.jsonwebtoken.Claims;
import io.jsonwebtoken.Jws;
import io.jsonwebtoken.Jwts;
import io.jsonwebtoken.SignatureAlgorithm;
import io.jsonwebtoken.security.Keys;
import org.springframework.stereotype.Component;

import javax.crypto.SecretKey;
import java.util.Date;
import java.util.Map;

@Component
public class Token {
    /**
     * 导入配置类
     */
    private final TokenConfig tokenConfig;

    public Token(TokenConfig tokenConfig) {
        this.tokenConfig = tokenConfig;
    }

    /**
     * 获取密钥
     * @return 密钥签名
     */
    private SecretKey getSecretKey(){
        return Keys.hmacShaKeyFor(tokenConfig.getSecret().getBytes());
    }

    /**
     * 生成
     * @param claims 自定义数据，载荷
     * @param subject 主题，通常为用户名或id
     * @return token
     */
    public String generateToken(Map<String,Object>claims,String subject){
        return Jwts.builder()
                .setClaims(claims)
                .setSubject(subject)
                .setIssuedAt(new Date())
                .setExpiration(new Date(System.currentTimeMillis()+tokenConfig.getExpiration()*1000))
                .signWith(getSecretKey(), SignatureAlgorithm.HS256)
                .compact();
    }

    /**
     * 获取claims
     * @param token 生成的token
     * @return Claims
     */
    private Claims getClaimsFromToken(String token){
        return Jwts.parserBuilder()
                .setSigningKey(getSecretKey())
                .build()
                .parseClaimsJws(token)
                .getBody();
    }


    /**
     * 解析用户名
     * @param token token
     * @return 主题
     */
    public String getUsernameFromToken(String token){
        return getClaimsFromToken(token).getSubject();
    }

    //验证

    /**
     * 
     * @param token token
     * @return Boolean
     * 主要验证登录状态
     */
    public Boolean validateToken(String token){
        System.out.println(token);
        try{
            if (token.startsWith("Bearer ")) {
                token= token.substring(7);
            }
            Jws<Claims> claimsJws = Jwts.parserBuilder()
                    .setSigningKey(getSecretKey())
                    .build()
                    .parseClaimsJws(token);
            if (!claimsJws.getBody().get("isLogin", Boolean.class))return false;
            System.out.println(claimsJws.getSignature());
            if (claimsJws.getSignature()==null||claimsJws.getSignature().isEmpty())return false;


            return true;
        }catch (Exception e){
            e.printStackTrace();
            return false;
        }
    }
}
```



## Encryption加密

xml配置

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-security</artifactId>
    <version>3.5.11</version>
    <scope>compile</scope>
</dependency>
```

encryptionUtil工具类

```java
package com.yi.springbootproject.Component.Utils;

import org.springframework.security.crypto.bcrypt.BCrypt;
import org.springframework.security.crypto.bcrypt.BCryptPasswordEncoder;
import org.springframework.stereotype.Component;

@Component
public class Encryption {

    private static final BCryptPasswordEncoder encode=new BCryptPasswordEncoder();

    /**
     * 密码加密
     * @param str 用户输入密码
     * @return 加密后的
     */
    public String encryption(String str){
        if (str==null||str.isEmpty())return "-1";

        return encode.encode(str);
    }

    /**
     * 加密验证
     * @param inputPw 用户输入的密码
     * @param hashedPw 数据库中获取的加密密码
     * @return 验证是否成功
     */
    public Boolean checkuserP(String inputPw,String hashedPw){
        return BCrypt.checkpw(inputPw, hashedPw);
    }
}
```



## 拦截器









## GraalVM

GraalVM 是 Oracle 开发的一个**高性能 JDK（Java Development Kit）**，它最大的特点就是能把 Java 程序**提前编译（AOT，Ahead-Of-Time Compilation）**成独立的**本地可执行文件（native executable）**。

