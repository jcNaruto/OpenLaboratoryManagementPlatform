# Laboratory
基于IOT的实验室管理平台，代码仅包括数据后台，移动端，前台代码即将上线

## 1.作品简介
本作品是一个面向开放式实验教学的时代需求而制作的应用于 Android 平台的手机 APP。APP 提供了以下几项主要功能：
1. 科技咨询获取
2. 学生权限管理
3. 课程和活动管理
4. 实验工具、门禁管理
5. 身份认证
6. 课程资源管理等功能。

通过这些功能，教师可以轻松地完成对实验室人员、物资、课程活动等的管理和信息发布；学生可以在平台上轻松地完成课程的选取、实验室工具的借用和课程资源的获取。除此之外，学生还可以在打开 APP 的首页看到最新的科技咨询图文消息，方便同学们在学习之余了解科技发展的最新资讯。
## 2.数据后台
（springMVC+spring+mybatis)+tomcat+MySQL+Redis+maven+shiro+jdk1.8）
### 2.1 后台总技术栈
![image](https://github.com/jcNaruto/Laboratory/blob/master/images/Snipaste_2019-06-07_09-39-43.png)
### 2.2 数据后台系统架构简介
![image](https://github.com/jcNaruto/Laboratory/blob/master/images/Snipaste_2019-06-05_20-32-07.png)
### 2.3 数据后台具体业务
1. 用户注册登陆，退出登陆，修改密码：通过使用学生现实唯一的学号作为学生表的主键，通过Email发送验证码（Redis确保验证码有效时间），完成用户注册，使用cookie作为会话技术，修改密码则通过发送邮箱验证码确保其合法性。
2. 看课选课，老套业务，没什么可说的。
3. 门禁，借用归还物品，查看物品列表：涉及到物联网，后台生成具备一定信息的String,该String又会用于生成二维码，树莓派扫描到该二维码之后又会拿着该String向后台发起请求，之后接收到参数，看是否具有权限，是否执行具体操作，并且在树莓派发送请求之后，如果操作成功，还要将相应物品的借用归还状态改变，在获取物品列表的时候将其状态一并返回。
4. 操作历史，在树莓派发送请求之后，如果操作成功，后台在异步的插入操作记录，如果操作失败则进行日志记录。


总结：业务：注册，登陆，退出登陆，修改密码，看课，选课，与硬件进行扫码交互，硬件操作历史的维护
## 3.不足之处
第一个项目，没有加HTTPS，没有严格的遵守XXX代码规范，使用SSM框架，配置文件过多，没有遵守RestFul或其他标准，为日后的扩展添加了局限
## 4.项目结果
1. 校级，省级，国家级相关比赛均有获奖。
2. 软件著作权正在申请
3. 校内推广，正在洽谈