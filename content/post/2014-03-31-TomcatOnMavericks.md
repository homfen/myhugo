+++
title = "Tomcat on Mavericks"
date = "2014-03-31T00:32:25Z"
categories = [
    "后端技术"
]
tags = [
    "Tomcat"
]
+++

<!--img src="/images/post/tomcat.jpeg"-->

在Mac上安装Tomcat非常简单 第一步，从<a href="http://tomcat.apache.org/index.html" target="_blank">Tomcat</a>官网下载压缩包，然后解压  
第二步，将解压好的文件夹重新命名一个简单的名字，复制到/Library目录下  
第三步，进入Tomcat下的bin目录中，设置startup.sh、shutdown.sh、catalina.sh三个文件的权限，添加执行权限，可以使用命令：

<!--more-->

```shell
chmod u+x 文件名
```

第四步，运行startup.sh，启动Tomcat，此时，如果设置正常，打开浏览器，输入localhost:8080就能看到Tomcat的欢迎页面，如果遇到错误，如：

```java
Exception in thread "main" java.lang.UnsupportedClassVersionError: org/apache/catalina/startup/Bootstrap : Unsupported major.minor version 51.0
```

是由于Tomcat版本与Mac上的Java版本不匹配。在终端中输入：java -version查看java版本，对应关系为：

```shell
tomcat version:8.0.x -------> java version:7 and later 
tomcat version:7.0.x -------> java version:6 and later 
tomcat version:6.0.x -------> java version:5 and later 
```

Mavericks默认java版本为1.6.0_65,如果想升级到7有一定的风险，因为7只能在64位浏览器下运行，而Mac上的Chrome只有32位

第五步：运行shutdown.sh，关闭Tomcat  
当然你也可以设置软链接，这样就能在终端中快速启动和关闭Tomcat
