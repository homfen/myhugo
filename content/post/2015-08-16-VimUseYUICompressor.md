+++
title = "vim中使用yui compressor"
date = "2015-08-16T23:36:44Z"
categories = [
    "工具使用"
]
tags = [
    "Vim"
]
+++

<!--img src="/images/post/201508171439741627750219.png"-->

对于JS和CSS来说，压缩是很常见的操作，通过压缩可以缩小文件尺寸，从而网页加快加载速度。yahoo的yui compressor是一个常用的压缩工具，所以本文就介绍下如何在vim中使用yui compressor。

<!--more-->

首先必须在电脑上安装yui compressor，可以使用npm安装：

```shell
npm install -g yuicompressor
```

这里使用全局安装，这样就能在任何目录中执行了，直接输入yuicompressor会输出帮助文档：

```shell
YUICompressor Version: 2.4.8

Usage: java -jar yuicompressor-2.4.8.jar [options] [input file]

Global Options
  -V, --version Print version information
  -h, --help Displays this information
  --type <js|css> Specifies the type of the input file
  --charset <charset> Read the input file using <charset>
  --line-break <column> Insert a line break after the specified column number
  -v, --verbose Display informational messages and warnings
  -o <file> Place the output into <file>. Defaults to stdout.
                            Multiple files can be processed using the following syntax:
                            java -jar yuicompressor.jar -o '.css$:-min.css' *.css
                            java -jar yuicompressor.jar -o '.js$:-min.js' *.js

JavaScript Options
  --nomunge Minify only, do not obfuscate
  --preserve-semi Preserve all semicolons
  --disable-optimizations Disable all micro optimizations

If no input file is specified, it defaults to stdin. In this case, the 'type'
option is required. Otherwise, the 'type' option is required only if the input
file extension is neither 'js' nor 'css'.
``` 

可见可配置的选项也不多，type用于指定文件类型，charset指定编码格式，line-break用于在行字符超过特定值后进行换行，v用于输出提示消息和警告，o用于指定输出的文件名。对于JS还有3个配置，nomunge表示只进行精简而不进行混淆，preserve-semi用于保留所有的分号，disable-optimizations禁用所有内置的微优化。 接下来对vim进行配置，可以自己写一个插件，这里直接在.vimrc里面操作，添加一个Yui_compressor函数用于压缩：

```shell
function Yui_compressor()
    let nam = expand('%:t:r')
    let ext = expand('%:e')
    let fullnam = nam.'.'.ext
    let mininam = nam.'.min.'.ext
    cal system('yuicompressor -o '.mininam.' '.fullnam)
endfunction
```  

这里要注意，函数名的首字母必须大写，或者以“s”开头。定义了4个变量，nam是文件名，ext是后缀，fullname是全名（也可以用expand('%:t')），mininam是输出的文件名，最后调用yuicompressor命令。 到这里就差不多了，为了调用方便，我们给这个函数绑定一个快捷键，以ctrl+y为例，当然你也可以换成其他的，只要不冲突就好

```shell
map <C-y> :call Yui_compressor()<cr>
``` 

大功告成，以后只要在打开文件是，按下ctrl+y就可以调用yuicompressor对当前文件进行压缩，在当前目录下会生成对应的*.min.css或者*.min.js。


-----------------------------------------我是华丽的分割线----------------------------------------

发现一个挺好用的插件[fecompressor.vim](https://github.com/othree/fecompressor.vim)，之前在压缩css时有点错误，不过已经被我改过来了:D。

