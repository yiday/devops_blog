---
layout: default
title: javascript的null和undefined
---

# {{ page.title }}

## null
null是关键字，表示一个特殊值，用来描述空值。
```javascript
typeof(null) // "object"
```
typeof(null)返回的是一个对象，它可以用来表示数字、对象、字符串的无值。

## undefined
表示未定义的值，具胡更深层次。它是变量的一种取值，表明变量没有初始化.
undefined是只读的
### 返回undefined的情况
* 函数没返回任何值
* 引用没有实参的形参

```javascript
typeof(undefined) //"undefined"
```

## 比较null和undefined
```javascript
null == undefined // true
null === undefined // false
```

 *null 和 undefined 不包含任何方法，如果对它们执行. [] 会抛错*
