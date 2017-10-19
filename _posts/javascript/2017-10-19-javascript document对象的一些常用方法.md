---
layout: default
title: javascript document对象的一些常用方法
---

# {{ page.title }}

## querySelector(String selector)
返回文档中第一个匹配指定选择器的元素

```HTML
<ul>
  <li><a href="/first" class="">first</a></li>
  <li><a href="/second" class="">second</a></li>
  <li><a href="/three" class="">three</a></li>
</ul>
```

```javascript
document.querySelector("a") //<a href="/first" class="">first</a>
```


## getElementById(String selector)
返回一个对识别元素的对象引用
