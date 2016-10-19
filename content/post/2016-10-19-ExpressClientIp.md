+++
title = "Express.js Get Client IP"
date = "2016-10-19T22:13:44Z"
description = "Express.js获取客户端IP"
categories = [
    "后端技术"
]
tags = [
    "node.js",
    "express.js",
    "nginx"
]
+++

Express中如果想获取客户端的IP，首先要设置trust proxy:
```javascript
app.set('trust proxy', 1);
// or
app.enable('trust proxy');
```

设置完之后，就可以从req中取到IP了：
```javascript
var ip = req.ip;
// or
ip = req.headers['x-forwarded-for'] || req.connection.remoteAddress;
```

<!--more-->

如果这样还不能获取到IP，比如获取到的是“:::ffff:x.x.x.x”这样的IP，那么大概就是代理搞得鬼了。比如nginx，如果没有配置，那么这些信息在转发的时候就都丢失了，只需要加上这几句：
```bash
proxy_set_header X-Real-IP $remote_addr;
proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
proxy_set_header Host $http_host;
```
