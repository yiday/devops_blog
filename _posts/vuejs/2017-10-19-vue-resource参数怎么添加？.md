---
layout: default
title: vue-resource参数怎么添加？
---

# {{ page.title }}

## 为url添加参数
在jsonp第二个参数里添加params作为key
```javascript
this.$http.jsonp('https://api.douban.com/v2/movie/top250', {params:{count:10}}, {
        headers: {

        },

        emulateJSON: true
    }
url 相当于 https://api.douban.com/v2/movie/top250?count=10
```
