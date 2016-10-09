+++
title = "Responsive Web Design"
date = "2013-12-20T00:28:22Z"
categories = [
    "前端技术"
]
tags = [
    "Responsive"
]
+++

<!--img src="/images/post/fc1f4134970a304e15b91017d0c8a786c8175c47.png"-->

自适应网页设计（英语：Responsive web design，通常缩写为RWD）是一种网页设计的技术做法，该设计可使网站在多种浏览设备（从桌面电脑显示器到移动电话或其他移动产品设备）上阅读和导航，同时减少缩放、平移和滚动。

<!--more-->

**CSS3 Media Query**（媒介查询）插件，这是响应式设计的核心。它根据条件告诉浏览器如何为指定视图宽度渲染页面。媒介查询的数量可以根据需要添加。其目的在于为指定的视图宽度设定不同的CSS规则，来实现不同的布局。

```css
@media only screen and (max-width: 640px){……}
```

**Meta**标签，因为大多数移动浏览器将HTML页面放大为宽的视图（viewport）以符合屏幕分辨率，这可以使用视图的meta标签来进行重置。在部分加入这个meta标签。

```html
<meta name="viewport" content="width=device-width; initial-scale=1.0; maximum-scale=1.0;"/>
```
