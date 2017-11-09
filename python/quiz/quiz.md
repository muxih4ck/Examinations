# 测验

实现一个超级简单用户系统 + 简单的发送POST的页面 + 查看所有人的所有的文章的页面


***

数据库部分:

+ 用户表:
    + id `Column`
    + 姓名 `Column`
    + 连接文章的relationship `Column`

+ 文章表:
    + id `Column`
    + 内容 `Column`
    + 连接用户id的外键 `Column`

***

页面部分:

+ 首页(URL:`/`)

![](http://wx3.sinaimg.cn/mw690/006yEyQ0gy1fl65rwnf91j30m30o7js1.jpg)

点击Submit按钮会在`数据库`中添加一个用户，并`跳转`到该用户发送文章的页面

+  发送文章页面(URL:`/user/<int : user_id>`)

![](http://wx3.sinaimg.cn/mw690/006yEyQ0gy1fl65rugpsfj30m10o7q3n.jpg)

通过点击POST会在数据库中添加一个文章，文章内容为Text对应内容，文章的user_id为该用户的id.
通过AllUser&Post跳转到getall页面


+ All页面 (URL:`/getall`)

![](http://wx2.sinaimg.cn/mw690/006yEyQ0gy1fl65rpris0j30m10o0wfb.jpg)

在点击AllUser&Post后跳转到该页面.
格式为
## 用户1

---内容1

---内容2

## 用户2

---内容1

---内容2

## 用户3

---内容1

---内容2

---内容3

---内容4

...


