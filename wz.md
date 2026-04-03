springboot+vue3

### vue

src/ 

├── api/          # 接口请求封装（Axios） 

├── assets/       # 静态资源（图片/样式） 

├── components/   # 通用组件（按钮/表单/分页）+ 业务组件（商品卡片/订单列表） 

├── router/       # 路由配置（Vue Router）+ 路由守卫（权限控制） 

├── stores/       # 状态管理（Pinia，替代 Vuex） 

├── views/        # 页面组件（登录页/商品列表页） 

├── utils/        # 工具函数（时间格式化/加密/本地存储） 

├── App.vue       # 根组件 

└── main.js       # 入口文件



### springboot

src/main/java/com/xxx/ 

├── controller/   # 接口层（接收前端请求，返回响应） 

├── service/      # 业务逻辑层（接口+实现类，核心业务写这里） 

├── mapper/       # 数据访问层（MyBatis/MyBatis-Plus 操作数据库） 

├── entity/       # 实体类（对应数据库表） 

├── dto/          # 数据传输对象（前端请求/响应的参数封装） 

├── vo/           # 视图对象（给前端返回的结构化数据） 

├── config/       # 配置类（跨域/拦截器/Swagger/JWT） 

├── exception/    # 全局异常处理 

├── utils/        # 工具类（加密/日期/统一响应） 

└── Application.java  # 启动类









### 网站

邮箱检测：https://haveibeenpwned.com/

光标：https://sweezy-cursors.com/



























### 工具

[Shodan](https://www.shodan.io/)：这是一个用于连接互联网设备的搜索引擎。它允许您搜索特定类型和版本的服务器、网络设备、工业控制系统和物联网设备。



[VirusTotal](https://www.virustotal.com/) ：一个在线网站，提供使用多种杀毒引擎文件的病毒扫描服务。它允许用户在一次作中上传文件或提供URL，以便通过多个杀毒引擎和网站扫描器进行扫描。他们甚至可以输入文件哈希值，以检查之前上传文件的结果。



[漏洞数据库](https://www.exploit-db.com/)：列出了来自不同作者的漏洞代码;其中一些漏洞代码经过测试并标记为已验证。



[国家脆弱性数据库](https://nvd.nist.gov/)

[CVE项目](https://www.cve.org/)