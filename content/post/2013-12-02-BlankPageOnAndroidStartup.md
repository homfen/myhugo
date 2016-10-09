+++
title = "Blank page on android application startup"
date = "2013-12-02T16:30:21Z"
categories = [
    "其他技术"
]
tags = [
    "Android"
]
+++

现象： 打开应用时先出现1秒左右的带有标题的空白页面，然后进入LAUNCHER Activity

原因分析： 在自定义的主题中，设置的父主题，如：

```html
<style name="customTheme" parent="android:Theme.Light">
```

解决方法： 将主题设置为android:Theme.Wallpaper

```html
<style name="customTheme" parent="android:Theme.Wallpaper">
```
