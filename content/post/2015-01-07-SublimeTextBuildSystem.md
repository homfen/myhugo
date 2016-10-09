+++
title = "Sublime Text Build System"
date = "2015-01-07T03:08:12Z"
categories = [
    "工具使用"
]
tags = [
    "Sublime"
]
+++

前端的同学应该都使用过或听说过Sublime这个工具，大部分人可能只是用它来编写html、css、js代码，其实它还有一个强大的功能叫Build System，下面就通过一个例子来介绍一下这个功能。

使用VS的同学可能会知道一个工具叫“Microsoft Ajax Minifier”，就是用来压缩js和css文件的，通过减少文件的大小来提升网站的加载速度。使用Build System，也可以在Sublime中使用这个工具。

<!--more-->

首先在AjaxMin的<a href="http://ajaxmin.codeplex.com/" target="_blank">官方网站</a>下载这个工具，并安装。安装完毕后，将安装目录添加的系统的环境变量中。如果一切顺利，这时候打开控制台，并输入“ajaxmin”就会看到如下结果：

<img src="/images/post/201505141431596556829319.png">

第二步，打开Sublime，从菜单栏选择tools->Build System->New Build System...

<img src="/images/post/201505141431596653139320.png">

在打开的文件中输入以下代码：

```json
{
    "shell":true,
    "cmd":[
        "ajaxmin", "-xml", "files.xml","-out","..\\minjs"
    ],
    "encoding":"GB2312"
}
```

采用shell的方式，执行cmd中的命令，如果有多条命令，则每条命令之间用"&;"隔开，这样就可以执行多条命令了，使用GB2312的编码。这句命令（ajaxmin -xml files.xml -out ..\minjs）的意思，就是按照files.xml提供的文件列表进行压缩，并把结果输出到上一级目录下的minjs目录中。更多命令可以查看ajaxmin的官方文档。

将文件保存为AjaxMin.sublime-build，重启Sublime，就可以看到我们自定义的Build System了：tools->Build System->AjaxMin。勾选它成为默认的build方案，这时候随意打开一个js文件，并在它的同级目录下新建一个files.xml文件，然后Ctrl+B快捷键进行编译，就可以在上级目录下发现多了一个minjs目录，里面有压缩过的js文件。

