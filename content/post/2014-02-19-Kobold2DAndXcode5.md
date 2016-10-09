+++
title = "Kobold2D and XCode5"
date = "2014-02-19T02:08:52Z"
categories = [
    "其他技术"
]
tags = [
    "Kobold2D"
]
+++

用Xcode新建Kobold2D项目时，报错：

```c
int newSize = [(SingleFileDownloader*)[_sizeCheckers objectAtIndex: _curFile] contentLength];
```   

Multiple methods named 'contentLength'

解决方法，打开终端，输入：

```shell
curl https://s3.amazonaws.com/mgwu-misc/xcode5-kobold.sh | sh
```
