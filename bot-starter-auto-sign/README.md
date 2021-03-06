# bot-starter-auto-sign

该模块用于自动打卡功能

## 相关指令
**所有指令都是需要私聊机器人**

- [自动打卡]():通过机器人,获取自动打卡相关帮助
- [注册自动打卡 token 学号 联系电话 家长姓名 家长联系电话]():注册自动打卡服务
- [开启自动打卡]():开启自动打卡,需要先注册
- [关闭自动打卡]():关闭自动打卡,需要先注册
- [修改 [相关数据] [新值]](): 修改相关数据
 
   例如: '[修改 token xxx]()';你也可以修改你打卡的地点,格式: '[修改 打卡地点 月球]()'

关于如果获取token,请看: [获取token](#获取token)

## 使用方法
如果你想在bot-core中添加该功能，请按照以下步骤
1. 导入依赖
   
   ```xml
   <dependency>
        <groupId>priv.xds</groupId>
        <artifactId>bot-starter-auto-sign</artifactId>
   </dependency>
   ```

2. 在配置文件上添加
    ```properties
    bot.auto-sign.enabled=true
    ```
   
## 获取token

### token简介
token全称 Json Web Token(JWT)，是一串无状态的字符串，
一旦服务器分发给用户，除非到达设定的时间，无法让其失效！
因此你的Token一旦暴露，建议迅速修改密码，
因为Token中一般附带了密码信息(但是原Token没有失效！只是里面的信息不正确，可能会被服务器拒绝)。

在**一般情况**下Token有效期一般很短，基本只有几个小时！

> 该模块就是利用了学校token过期时间为一个星期的设置!(能把token有效期设置为一星期，就离谱!)

说了这么多，总之就是一句话：**你把token给我，就相当于把你的账号和密码都给我了！**

> 但是亲测这个token是打不开学校的付款界面的,学校付款界面貌似是利用微信的什么功能快速搭建的,安全方面是微信做的,因此十分安全!

### 获取token


#### 1.下载HttpCanary,此处建议高级版(收费的 *~~但只要想搞也不是没办法~~* )
#### 2.打开HttpCanary，点击右下角小飞机开始记录
#### 3.打开企业微信，进入纺大畅行码
#### 4.回到HttpCanary，获取Token

   点击右上角三个点 -> 搜索'authorization'(不要带引号) -> 随便进入一个企业微信的请求 -> 点击中间的'请求'
   -> 在里面可以找到一个 authorization: xxxxxx，将后面的值复制，提交给机器人(这个东西就是Token)