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

