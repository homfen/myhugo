+++
title = "Duff's Device（达夫设备）"
date = "2014-06-14T16:42:18Z"
categories = [
    "前端技术"
]
tags = [
    "Javascript"
]
+++

达夫设备算法可以减少循环的迭代次数，如果循环迭代次数少于1000次，你可能只能看到它与普通循环相比微不足道的性能提升，但当循环迭代次数超过1000次，达夫设备的效率将显著提升。  
原理十分简单，将总的迭代次数以8为基数进行分组，一次迭代执行8次操作，最后再处理余下的小于8次的迭代，所以迭代的总次数由原来的count次变为count/8[+1]次。

<!--more-->

第一种形式：

```javascript
function duffLoop(items,process){
    var iterations = Math.floor(items.length / 8), 
        startAt = items.length % 8,
        i = 0;
    do {
        switch(startAt){
            case 0: process(items[i++]); 
            case 7: process(items[i++]); 
            case 6: process(items[i++]); 
            case 5: process(items[i++]); 
            case 4: process(items[i++]); 
            case 3: process(items[i++]); 
            case 2: process(items[i++]); 
            case 1: process(items[i++]);
        }
        startAt = 0;
    } while (--iterations);
}
```   

第二种形式：

```javascript
function duffLoop(items,process){
    var i = items.length-1;
    var ii = items.length % 8; 
    while(ii--){
        process(items[i--]); 
    }
    var iii = Math.floor(items.length / 8); 
    while(iii--){
        process(items[i--]); 
        process(items[i--]); 
        process(items[i--]); 
        process(items[i--]); 
        process(items[i--]); 
        process(items[i--]); 
        process(items[i--]); 
        process(items[i--]);
    }
}
```    

第三种形式：

```javascript
function duffLoop(items, process){
    var idx = 0;
    var len = items.length;
    var itr = len / 8;
    while (itr--) {
        process(items[idx++]);
        process(items[idx++]);
        process(items[idx++]);
        process(items[idx++]);
        process(items[idx++]);
        process(items[idx++]);
        process(items[idx++]);
        process(items[idx++]);
    }
    itr = len % 8;
    while (itr--) {
        process(items[idx++]);
    }
}
```
