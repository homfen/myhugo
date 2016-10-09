+++
title = "XMLHttpRequest"
date = "2014-08-22T12:53:04Z"
categories = [
    "前端技术"
]
tags = [
    "Javascript"
]
+++

XMLHTTP是一组API函数集，可被JavaScript、JScript、VBScript以及其它web浏览器内嵌的脚本语言调用，通过HTTP在浏览器和web服务器之间收发XML或其它数据。XMLHTTP最大的好处在于可以动态地更新网页，它无需重新从服务器读取整个网页，也不需要安装额外的插件。该技术被许多网站使用，以实现快速响应的动态网页应用。

<!--more-->

ActiveXObject用于兼容IE，XDomainRequest用于兼容IE8。

```javascript
function getData(type, url, postData, callback) {
    var xmlrequest, isXDomain = false;
    if (window.XDomainRequest) {
        xmlrequest = new XDomainRequest();
        isXDomain = true;
    } else if (window.ActiveXObject) {
        try {
            xmlrequest = new ActiveXObject("Msxml3.XMLHTTP");
        } catch (e1) {
            try {
                xmlrequest = new ActiveXObject("Msxml2.XMLHTTP.6.0");
            }
            catch (e2) {
                try {
                    xmlrequest = new ActiveXObject("Msxml2.XMLHTTP.3.0");
                }
                catch (e3) {
                    try {
                        xmlrequest = new ActiveXObject("Microsoft.XMLHTTP");
                    }
                    catch (e4) {
                        alertMsg("您的浏览器版本太低，请升级浏览器或更换浏览器。");
                        return;
                    }
                }
            }
        }
    } else if (window.XMLHttpRequest) {
        xmlrequest = new XMLHttpRequest();
    } else {
        alertMsg("您的浏览器版本太低，请升级浏览器或更换浏览器。");
        return;
    }
    xmlrequest.onreadystatechange = function () {
        if (xmlrequest.readyState == 4) {
            if (xmlrequest.status == 0 || xmlrequest.status == 200) {
                callback(xmlrequest.responseText);
            }
        }
    }
    xmlrequest.open(type, url, true);
    if (!isXDomain) {
         xmlrequest.setRequestHeader("Content-Type", "application/x-www-form-urlencoded");
    }
    xmlrequest.send(postData);
}
```
