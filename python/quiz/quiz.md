# 木犀后台组2017.11测验

实现一个简单用户系统，用户可以发送动态，并有一个页面可以查看所有人的所有的文章。


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

![](http://ohr9krjig.bkt.clouddn.com/pic1111.png)

点击Submit按钮会在`数据库`中添加一个用户，并`跳转`到该用户发送文章的页面

+  发送文章页面(URL:`/user/<int : user_id>`)

![](http://ohr9krjig.bkt.clouddn.com/pic2222.png)

通过点击POST会在数据库中添加一个文章，文章内容为Text对应内容，文章的user_id为该用户的id.
通过AllUser&Post跳转到getall页面


+ All页面 (URL:`/getall`)

在点击AllUser&Post后跳转到该页面.

![](http://ohr9krjig.bkt.clouddn.com/pic3333.png)

***

附加题1:对自己的评价

***

附加题2:对团队的评价

