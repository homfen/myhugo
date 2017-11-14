+++
title = "Node.js命令行程序"
date = "2017-11-14T21:53:13Z"
categories = [
    "其他技术"
]
tags = [
    "Node.js",
    "Commandline"
]
+++

Node.js也是可以写命令行程序的，与Web程序的不同之处就在于package.json的设置。

需要在package.json中添加如下配置：
<!--more-->

```json
"preferGlobal": true,
"bin": {
    "command": "index.js"
}
```

preferGlobal的意思是适合全局安装。

bin是一个对象，key是对应的命令行命令，value就是入口js文件，所以可以定义好几个命令。

其他功能和一般的node程序一样。

写完之后，运行全局安装

```javascript
npm i -g ./folder
```

foler对应程序的目录。

安装完后，就可以在命令行中使用bin中的命令了。
