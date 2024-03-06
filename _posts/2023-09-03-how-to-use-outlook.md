---
layout: post
title: outlook使用教程
categories: [Tutorial, software]
description: how to use outlook
keywords: Tutorial, software, outlook
mermaid: false
sequence: false
flow: false
mathjax: false
mindmap: false
mindmap2: false
typora-root-url: ../
---

本文介绍了我使用outlook软件的一些问题

## 微软账号和QQ邮箱一致问题

微软账号是用QQ邮箱注册的，显示的是QQ邮箱
但实际上，微软账号有单独的系统，仅仅是显示QQ邮箱罢了
接收到的邮件、日历、todolist等全都是在微软的系统里面（其实就是一个支持Exchange协议的邮箱）

所以微软账号对应的邮箱也要登录（才可以用到同步功能）

---
解决方案：添加电子邮件（账户别名）

进入microsoft网站，登录后，【点击头像-我的个人资料-编辑账户信息-添加电子邮件】
*若点击头像后没有【我的个人资料】，就点击【我的microsoft账户】，跳转后再点头像就有【个人资料】了*

添加的电子邮件要是outlook后缀的（也就是微软官方的），可以直接再添加的界面新建一个。

新建就可以了，不需要将之设为主要或登录方式。（不确定改了后会不会有其他麻烦，毕竟电脑windows系统是QQ邮箱登录的）
大胆点可以直接将新建的outlook邮箱直接设置为microsoft的名称，这样就不会有冲突了

有了outlook邮箱别名后，可以使用这个邮箱登录microsoft
可以在手机上下载一个microsoft authenticator软件，作为微软的登录验证（挺快挺爽的）

## 添加邮箱

注意：如果microsoft账户是使用的qq邮箱，务必先添加qq邮箱。
否则会提示，已添加这个邮箱（实际上没有）
*如果自动出现了使用QQ邮箱名的微软账号，先试一下能不能再加QQ邮箱，不能的话就把自动出现的先删了*

再用微软账号的别名（额外添加的outlook邮箱）添加，这时添加的是微软账号了

如果使用microsoft store下载的【邮件】，就不会有冲突。
推荐使用这个，更快更轻量些

outlook软件是将邮件、日历、TODO三个集成在一起了

按需选择使用
## qq邮箱

### QQ邮箱在第三方客户端/服务怎么设置

登录时，请在第三方客户端的**密码输入框**里面填入**授权码**进行验证。（不是填入QQ的密码）

### 获得授权码

打开QQ邮箱，点进左上角【设置】，进入【账号】界面

![image-20230907131035325](/images/posts/2023-09-03-how-to-use-outlook/image-20230907131035325.png)

找到【IMAP/SMTP】选项，开启服务

开启后，点击【管理服务】，进入QQ邮箱账号与安全界面

![image-20230907131901626](/images/posts/2023-09-03-how-to-use-outlook/image-20230907131901626.png)

---
在【安全设置】选项中的 IMAP/SMTP 服务这里点击生成授权码

![image.png](/images/posts/2023-09-03-how-to-use-outlook/image-20230907131915657.png)

---
**授权码只显示一次，可以重复利用，也可以每次要用都生成新的授权码（建议截图保存，因为手机端的outlook软件也需要同样的再操作一次）**

在【设备管理 - 授权码管理】可以停用授权码

#### **[IMAP/SMTP 设置方法](https://wx.mail.qq.com/list/readtemplate?name=app_intro.html#/agreement/authorizationCode)**

<b><u>这是在outlook的设置参数</u></b>

**用户名/帐户：** 你的QQ邮箱完整的地址

**密码：** 生成的**授权码**

**电子邮件地址：** 你的QQ邮箱的完整邮件地址

**接收邮件服务器：** imap.qq.com，使用SSL，端口号993

**发送邮件服务器：** smtp.qq.com，使用SSL，端口号465或587

### outlook添加QQ邮箱

点击左上方【文件】选项，再点击【添加账户】按钮：

![image.png](/images/posts/2023-09-03-how-to-use-outlook/image-20230907131929538.png)

---
【高级选项】点开后，勾选选项

点击【连接】

![image.png](/images/posts/2023-09-03-how-to-use-outlook/image-20230907131940199.png)

---
选择【IMAP】方法

![image-20230907131953715](/images/posts/2023-09-03-how-to-use-outlook/image-20230907131953715.png)

---
接下来是【账户设置】，填写内容按照前面的设置信息

填好后，点击【下一步】

![image.png](/images/posts/2023-09-03-how-to-use-outlook/image-20230907132012911.png)

---
最后输入密码，这里的是刚才在QQ邮箱获取的授权码，不是QQ密码

填入授权码后连接即可

![image-20230907132023703](/images/posts/2023-09-03-how-to-use-outlook/image-20230907132023703.png)

---
已经连接上了

## 推荐使用windows microsoft store自带的 邮件、日历、todolist软件

使用更快、与windows结合更深

邮件界面：

可进行的设置也更多：

![image.png](/images/posts/2023-09-03-how-to-use-outlook/image-20230907132104454.png)

---
使用时自动登录了微软账号的邮箱，再添加QQ邮箱等常用邮件即可
（没有outlook软件上，微软邮箱和QQ邮箱一致时导致的无法两个都添加的问题）

可以对添加的账号进行设置，如果微软账号的邮箱不用的话，设置不同步邮件即可

日历、联系人的信息是和微软账号的邮箱关联的（onedrive可能？所以得加上）

![image-20230907132131004](/images/posts/2023-09-03-how-to-use-outlook/image-20230907132131004.png)

---
侧边栏的日历、联系人、todolist

和outlook软件不同，在microsoft store上是单独的软件

日历对应的就是微软账号附带的
（这个和邮箱本身有关，比如谷歌邮箱也有日历功能，加上谷歌邮箱的话也可以同步日历，具体自行搜索）

如果outlook只加上QQ邮箱，那么日历就是本地日历（无法同步）

![image-20230907132153087](/images/posts/2023-09-03-how-to-use-outlook/image-20230907132153087.png)

---

## 其他邮箱

直接看outlook添加邮箱界面，如果是其包含的邮箱，那么直接点击

如果不是的话，那就和QQ邮箱一样的流程

---
outlook是第三方，除了outlook后缀的邮件外，其他邮箱都要有类似QQ邮箱的操作：
开通【IMAP】服务，拿到授权码

一般要输入的密码都是授权码，授权码只显示一次
（密码和授权码都试试）

具体的自行搜索


## 不同设备端同步

主要同步【日历】、【to do list】功能，那么就是要加上微软账号的邮箱

在手机上的操作是一样的，使用IMAP的记住授权码（是授权码不是密码）

手机上的outlook集成邮件和日历功能，todolist是单独的软件

## 日历

待更新。。。自行摸索


## TO DO

待更新。。。自行摸索