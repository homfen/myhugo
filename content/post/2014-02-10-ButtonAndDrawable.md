+++
title = "Button and Drawable"
date = "2014-02-10T00:16:34Z"
categories = [
    "其他技术"
]
tags = [
    "Android"
]
+++

如何获取Button中的Drawable

```java
Drawable img1 = button.getCompoundDrawables()[0];
```   

与其他Drawable比较

```java
Drawable img2 = getResources().getDrawable(R.drawable.name);
Bitmap bitmap1 = ((BitmapDrawable)img1).getBitmap();
Bitmap bitmap2 = ((BitmapDrawable)img2).getBitmap();
if(bitmap1==bitmap2){
    ...     
}
```
