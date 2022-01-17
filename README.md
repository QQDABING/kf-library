# kf-library 

一个基于SpringBoot封装的基础库，内置丰富的JDK工具，自动装配了一系列的基础Bean与环境配置项，可用于快速构建SpringCloud项目，让微服务变得更简单.

[更多信息请查看文档](doc/README.md)  

## 工程结构1

```

kf-library
├── kf-library-common                                   核心库,提供了大量基础的Java工具包
├── kf-library-modules                                  模块                      
│   ├── kf-library-module-base                          自动装配WEB应用的基础Beans
│   ├── kf-library-module-launcher                      启动器增强,KFLibrary的Banner展示,自定义SPI组件,默认的profile设置等, 用于替代SpringApplication.run
│   ├── kf-library-module-persist                       自动装配持久化库(Mybatis-plus,Spring-jdbc)
│   ├── kf-library-module-persist-cache                 自动装配持久化库(Mybatis-plus,Spring-jdbc)和缓存库(Jetcache,Spring-redis)
|
│   ├── kf-library-module-health                        自动装配心跳Api支持,SpringCloud适用
|
│   ├── kf-library-module-swagger                       自动装配Swagger支持(Springfox),根据注解生成api测试平台
|
│   ├── kf-library-module-security-support              SpringSecurity认证基础库
│   ├── kf-library-module-security-config               SpringSecurity配置基础库
│   ├── kf-library-module-security-web                  自动装配认证库(SpringSecurity)
│   ├── kf-library-module-security-oauth2               自动装配Oauth2库(SpringSecurityOauth2)
│   ├── kf-library-module-security-social               社交登录功能，OAUTH2(微信公众平台,微信开放平台,支付宝,github等等)
|
│   ├── kf-library-module-data-redis                    自动装配spring-data-redis(RedisTemplate+prefix)和 KfCache(中间表的缓存处理)
│   ├── kf-library-module-data-easticsearch             自动装配spring-data-elasticsearch(es全文检索)
│   ├── kf-library-module-mq                            消息队列(RocketMQ),未实现
|
│   ├── kf-library-module-push                          自动装配推送(腾讯信鸽推送)
│   ├── kf-library-module-websocket-support             websocket基础
│   ├── kf-library-module-websocket                     自动装配websocket
│   ├── kf-library-module-sms                           自动装配短信模块(天翼云短信,阿里云短信)
│   ├── kf-library-module-email                         自动装配邮件模块
│   ├── kf-library-module-encrypt-body                  自动装配全局加解密工具
│   ├── kf-library-module-weixin-support                自动装配微信支持 目前只实现微信公众号消息点对点推送
|
│   ├── kf-library-module-upload                        文件上传库(本地,阿里云OSS,天翼云OSS)
|
│   ├── kf-library-module-opendoc-kit                   OpenDocument处理转换(Office word,Excel), 转换器(jodconverter),能够转换不同格式的文档(Office文档转PDF)
│   ├── kf-library-module-video-kit                     音视频处理转换(jave,ffmpeg),能够处理转换各种音视频,实现一部分
│   ├── kf-library-module-image-kit                     图片处理库
|
│   ├── kf-library-module-pay                           第三方支付(微信支付),未实现

│   ├── kf-library-module-workflow                      工作流
│   ├── kf-library-module-dt-form                       动态表单

│   ├── kf-library-module-canal-adapter                 数据库增量消费端(Canal阿里巴巴基于数据库增量日志解析,提供增量数据订阅&消费)         
|
│   ├── kf-library-module-notify-support                通知和公告基础
│   ├── kf-library-module-nofity                        自动装配通知和公告 
|     
│   ├── kf-library-module-async-task-support            异步任务(上传,下载)基础
│   ├── kf-library-module-async-task                    自动装配异步任务(上传,下载)  
|     
│   ├── kf-library-module-async-dict-support            字典(表)基础
│   ├── kf-library-module-async-dict                    自动装配字典(表)  
|     
│   ├── kf-library-module-qq-robot-support              qq机器人基础
│   ├── kf-library-module-qq-robot                      自动装配qq机器人
│   ├── kf-library-module-weixin-robot-support          微信机器人基础
│   ├── kf-library-module-weixin-robot                  自动装配微信机器人 
|     
│   ├── kf-library-module-ssh-agent                     自动SshAgent模块（SSH代理跳板访问数据库,Redis等资源）
│   ├── kf-library-module-anti-reptile                  自动装配反爬虫模块（IP频繁访问封锁、UserAgent封锁）
│   ├── kf-library-module-system-monitor                自动装配获取服务器运行信息的WEB API的模块(获取CPU,内存,磁盘,操作系统)
|     
├── kf-library-examples                                 基础库示例
│   ├── kf-library-example-simple-boot                  SpringBoot示例
│   ├── kf-library-example-cloud-boot                   SpringCloud示例
│   ├── kf-library-example-canal-adapter                数据库增量消费端示例

```

## Properties参数说明

### BASE
| KEY | 默认值 | 说明 |
| --- | --- | --- |
| kf.server.port | 3030 | http服务端口 |
| kf.exception-handler.enabled | true | 是否启用全局统一异常处理自动配置 |
| 跨域 |  |  |
| kf.cors.allow | true | 是否允许跨域 |ge
| kf.cors.exposedHeaders |  | response允许暴露的Headers | 
| RestTemplate |  |  |
| kf.rest.connect-timeout | 系统“默认” | RestTemplate客户端链接超时时间（单位：毫秒） |
| kf.rest.read-timeout | 系统“默认” | RestTemplate客户端读取超时时间（单位：毫秒） |
| kf.rest.proxy |  | RestTemplate客户端的代理地址,例如本机charles代理: http://127.0.0.1:8888   |
| DTO验证 |  |  |
| kf.validator-in-service | true | 在Service层拦截被标记@Validated的参数(方法),对起进行valid   |

### CACHE
| KEY | 默认值 | 说明 |
| --- | --- | --- |
| kf.redis.keyPrefix | "default:" | 全局的redis前缀 |
| kf.redis.distributed-lock-aop | true | 是否支持AOP方式的分布式锁 |

### PERSIST
| KEY | 默认值 | 说明 |
| --- | --- | --- |
| kf.persist.id-generator.type | snowflake | 全局主键ID默认分配策略(MybatisPlus的IdType=ASSIGN_ID时, 在实体类上使用注解@IdGeneratorType可以覆盖此策略), 2种: snowflake , redis (格式: yymmdd{流水号} ,例: 200102000007) |
| kf.persist.id-generator.redis-incr-step | 1 | redis生成的唯一Id生成步长(使用redis集群时, 每台设置为不一样步长来增加吞吐量) |
| kf.persist.id-generator.redis-incr-format-length | 6 | redis生成的唯一Id的流水号部分的长度 |

### SECURITY
| KEY | 默认值 | 说明 |
| --- | --- | --- |
| kf.security.enabled | true | 是否启用spring security |
| APIS |  |  |
| kf.security.controller | true | 是否启用默认的认证Controller |
| kf.security.apis.login-by-password-api | /api/v1/account-login | 账户密码登入的api地址(POST) |
| kf.security.apis.login-by-mobile-api | /api/v1/mobile-login | 手机验证码登入的api地址(POST) |
| kf.security.apis.send-sms-login-captcha-api | /api/v1/send-mobile-captcha | 手机验证码登入的api地址(POST) |
| kf.security.apis.logout-api | /api/v1/logout | 登出的api地址(POST) |
| kf.security.apis.forgot-api | /api/v1/forgot | 忘记密码(POST) |
| kf.security.apis.forgot-reset-api | /api/v1/forgot-pwd | 通过验证码重置密码(POST) |
| kf.security.apis.reset-api | /api/v1/forgot-pwd | 直接重置密码(POST),需管理员权限(角色SUPER_ADMIN或ADMIN) |
| kf.security.apis.pwd-api | /api/v1/modify-pwd | 修改当前登录账号的密码的api地址(POST) |
| kf.security.apis.pwd-auth-api | /api/v1/modify-auth-pwd | 修改当前登录用户的指定账号的密码的api地址(POST) |
| 验证码 |  |  |
| kf.security.captcha-onetime | false | 短信登录,忘记密码等验证码是否是一次性(阅后即焚) |
| 默认密码 |  |  |
| kf.security.default-password | scttsc2020 | 直接重置密码使用的默认密码 |
| 无授权访问 |  |  |
| kf.security.webIgnored.urls | 略 | 静态资源的无授权访问列表 |
| kf.security.httpIgnored.urls | 略 | HTTP资源的无授权访问列表 |
| JWT |  |  |
| kf.security.jwt.storeRedis | true | jwt是否储存到redis(存了可以实现后端踢人) |
| kf.security.jwt.tokenName | "login_token:" | 登录token在redis中的名称 |
| kf.security.jwt.renew | true | jwt token是否自动续期(仅storeRedis为true时有效) |
| kf.security.jwt.base64Secret | true | jwt的密匙 |
| kf.security.jwt.tokenValidityInSeconds | 259200 | jwt凭证有效期(默认3天,如果开启了redis储存,并且开启了自动续期,凭证中有效期将无效,是否失效由后端redis有效期决定,redis会根据最后一次访问进行自动展期) |
| Oauth服务器 |  |  |
| kf.security.oauth2.authorization-server.enabled | false | Oauth2认证服务开启 |
| kf.security.oauth2.resource-server.enabled | false | Oauth2资源服务开启 |
| 三方认证 |  |  |
| kf.security.social.enabled | false | 是否启用三方认证登录 |
| 三方认证登录APIS |  |  |
| kf.security.social.controller | true | 是否启用默认的三方认证登录Controller |
| kf.security.social.apis.platform-list-api | /api/v1/oauth/platform | 可用的三方认证平台列表api地址(GET) |
| kf.security.social.apis.platform-login-api | /oauth | 跳转到第三方平台进行登录和授权(ANY) |
| kf.security.social.apis.platform-login-callback-api | /oauth/callback | 第三方平台回调访问api地址(GET) |
| kf.security.social.apis.platform-user-bind-api | /api/v1/oauth/bind | 绑定第三方平台用户(与本系统用户,POST) |
| kf.security.social.apis.platform-user-unbind-api | /api/v1/oauth/unbind | 解除第三方平台用户绑定(POST) |
| 三方认证自动注册用户 |  |  |
| kf.security.social.register.enabled | false | 是否开启未绑定本系统的三方用户的自动注册(当第三方用户在本系统中找不到关联关系,不存在时) |
| kf.security.social.register.defalut-role | GUEST | 未绑定本系统的三方平台用户自动注册时使用的默认角色 |
| 三方认证默认重定向地址 |  |  |
| kf.security.social.default-redirect-uri-prefix | http://127.0.0.1:8080 | 默认的Oauth重定向地址(当第三方认证授权完毕后,由第三方平台来进行重定向的地址) |
| kf.security.social.default-fr-redirect-uri | http://127.0.0.1:3000/oauthlogin | 默认的前端重定向重定向地址(成功登录系统后分配好jwttoken后,重定向到前缀url地址) |
| 三方平台配置 |  | 下面只列出来微信的2个平台,实际支持40多个,详情查看me.zhyd.oauth.config.AuthDefaultSource |
| 微信公众平台 |  |  |
| kf.security.social.platforms.wechat_mp.appId |  | 微信公众平台appId |
| kf.security.social.platforms.wechat_mp.appSecret |  | 微信公众平台appSecret |
| 微信开放平台 |  |  |
| kf.security.social.platforms.wechat.appId |  | 微信开放平台appId |
| kf.security.social.platforms.wechat.appSecret |  | 微信开放平台appSecret |

### OTHER
| KEY | 默认值 | 说明 |
| --- | --- | --- |
| kf.sqlprint | false | 是否打印sql语句 |
| 网关 |  |  |
| kf.gateway.dynamic-route.enabled | true | 是否使用动态路由配置 |
| kf.gateway.dynamic-route.data-type | nacos | 使用nacos的远程动态路由配置 |

### UPLOAD
[上传模块](kf-library-modules/kf-library-module-upload/README.md)  


### SWAGGER
[Swagger](kf-library-modules/kf-library-module-swagger/README.md)  

### PUSH
[推送模块](kf-library-modules/kf-library-module-push/README.md)  


### WEBSOCKET
[Websocket模块](kf-library-modules/kf-library-module-websocket/README.md)  

### ENCRYPY-BODY

### NOTIFY

### DICT-ROBOT
[字典表模块](kf-library-modules/kf-library-module-dict/README.md)  


### WEIXIN
[配置](kf-library-modules/kf-library-module-weixin/README.md)  

### QQ-ROBOT
[QQ机器人模块](kf-library-modules/kf-library-module-qq-robot/README.md)  

### WEIXIN-ROBOT
[微信机器人模块](kf-library-modules/kf-library-module-weixin-robot/README.md)  

### ANTI-REPTILE
[反爬虫(机器人)模块](kf-library-modules/kf-library-module-anti-reptile/README.md)  

### SYSTEM-MONITOR
[系统监控(探针)模块](kf-library-modules/kf-library-module-system-monitor/README.md)  

### SSH-AGENT
[SSH代理跳板模块](kf-library-modules/kf-library-module-ssh-agent/README.md)  

### Spring
[SpringBoot的properties文档](https://docs.spring.io/spring-boot/docs/current/reference/html/appendix-application-properties.html#security-properties)



  


