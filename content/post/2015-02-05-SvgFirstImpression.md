+++
title = "SVG初印象"
date = "2015-02-05T00:06:52Z"
categories = [
    "前端技术"
]
tags = [
    "Svg"
]
+++

<!--img src="/images/post/svg-logo.png"-->

虽然很早就知道SVG，不过那时对SVG的认识就是用来制作图表的，例如折线图、柱状图之类的里面见的比较多，而如今，SVG已经发展了很多，丰富的api和类库让它可以完成很多有趣的事，可以说和canvas很相似。

SVG全称可缩放矢量图形（英语：Scalable Vector Graphics）是基于可扩展标记语言（XML），用于描述二维矢量图形的一种图形格式。SVG 1.1在 2003 年一月，被确立为W3C标准。

<!--more-->

位图是由点构成的，矢量图则是由一些形状元素构成。放大位图可以看到一颗颗的像素点，而放大矢量图看到的仍然是形状。SVG属于矢量图，因此能够无级缩放，而不会导致马赛克，矢量图的优势非常明显。其他的优点，还有：图像文件可读，易于修改和编辑；与现有技术可以互动融合；可以方便的创建文字索引，从而实现基于内容的图像搜索；支持多种滤镜和特殊效果，在不改变图像内容的前提下可以实现位图格式中类似文字阴影的效果；可以用来动态生成图形；与JPEG和GIF图像比起来，尺寸更小，且可压缩性更强。

SVG还有两个子集，SVGB、SVGT，SVGB主要目标是为掌上电脑等高端移动设备提供矢量图形显示格式，SVGT主要目标是为手机等低端移动设备提供矢量图形显示格式。

SVG主要支持3种显示对象：矢量显示对象（基本矢量显示对象包括矩形、圆、椭圆、多边形、直线、任意曲线等），嵌入式外部图像（包括PNG、JPEG、SVG等），文字对象。

SVGZ文件是指经过gzip算法压缩后的SVG文件，压缩会缩减文件尺寸，所以加载会更快。

目前各浏览器对SVG基本功能的支持都比较好，除了IE8及之前的浏览器，其他都能完全或部分支持。 
<img src="/images/post/QQ20150204-2-1024x368.png">

SVG图形制作工具有Adobe Illustrator、Visio以及CorelDRAW等，开源的工具有Scribus、Karbon14、Inkscape以及Sodipodi等。

SVG 文件可通过以下标签嵌入 HTML 文档：embed 、object 或者iframe。

```html
<embed src="rect.svg" width="300" height="100" type="image/svg+xml" pluginspage="http://www.adobe.com/svg/viewer/install/" />
<object data="rect.svg" width="300" height="100" type="image/svg+xml" codebase="http://www.adobe.com/svg/viewer/install/" />
<iframe src="rect.svg" width="300" height="100"></iframe>
``` 

SVG的预定义元素有：矩形 rect，圆形 circle，椭圆 ellipse，直线line，折线polyline，多边形polygon，路径 path。这些元素的属性有坐标x、y，长宽width、height，半径r，圆心cx、cy，圆角rx、ry，样式style等，根据元素不同有略微不同。fill用来设置填充颜色，stroke用来设置边框。

SVG有很多种滤镜，不过滤镜标签filter必须定义在defs标签中，使用的时候通过滤镜的id来调用。

```html
<defs>
    <filter id="Gaussian_Blur">
        <feGaussianBlur in="SourceGraphic" stdDeviation="3" />
    </filter>
</defs>
```  

SVG渐变包括线性渐变和放射性渐变。线性渐变通过两个坐标（x1,y1,x2,y2）来确定渐变的方向，坐标值用百分比的形式表示。在线性渐变标签linearGradient内通过stop标签来定义渐变点，颜色会从一个渐变点的颜色渐变到另一个渐变点的颜色。

```html
<defs>
    <linearGradient id="orange_red" x1="0%" y1="0%" x2="100%" y2="0%">
        <stop offset="0%" style="stop-color:rgb(255,255,0);stop-opacity:1"/>
        <stop offset="50%" style="stop-color:rgb(255,0,255);stop-opacity:1"/>
        <stop offset="100%" style="stop-color:rgb(255,0,0);stop-opacity:1"/>
    </linearGradient>
</defs>
```  

放射性渐变，通过两个坐标（cx、cy，fx、fy）来定义外圈和内圈的圆心位置，r来定义外圈的半径，也有stop标签。

```html
<defs>
    <radialGradient id="grey_blue" cx="50%" cy="50%" r="50%" fx="50%" fy="50%">
        <stop offset="0%" style="stop-color:rgb(200,200,200);stop-opacity:0"/>
        <stop offset="100%" style="stop-color:rgb(0,0,255);stop-opacity:1"/>
    </radialGradient>
</defs>
```
