# Quiz

参考[tutorial.md](./tutorial.md)中的内容使用**Python + Flask**搭建一个网站，开发过程中遇到不懂得问题可以使用各大搜索引擎。开发环境最好使用Unix/Linux，使用Windows的同学可以参考**tutorial.md**顶部给出的教程使用**Virtual Box**安装Ubuntu虚拟机。

开发过程中会使用到的静态页面的文件都存放在templates文件夹中，可以通过`git clone`, 或者复制所需要的文件至本地。

希望实现的效果：

1. 使用浏览器访问 `http://127.0.0.1:5000/` 得到首页(templates/index.html)的内容。
1. 使用浏览器访问 `http://127.0.0.1:5000/anonymous/` 得到用户页面(templates/anonymous.html)的内容，页面中显示"Hello, Anonymous!", 且下方有一个表单要求填入一个用户名"rose"，点击“提交”之后，跳转至`http://127.0.0.1:5000/user/rose/`, 如果填写的用户名为"jack"，则跳转至`http://127.0.0.1:5000/user/jack/`
1. 定义一个处理404错误的路由(router)，当访问一个不存在的页面时，页面显示(templates/page\_not\_found.html)的内容。

完成之后打包成 `你的姓名.tar.gz` 以附件形式发送到`i@muxistudio.com` 
