---
layout: default
title: javascript三个点运算符
---

# {{ page.title }}

## 合并数组
```javascript
let arr1 = [1, 2], arr2 = [3,4]
arr1.push(...arr2) //相当于arr1.push(3, 4)
//注：push返回数组元素个数
arr1.unshift(...arr2)
```

## 复制对象
```javascript
let obj = {a: 11}
let obj2 = {...obj, b: 222}
//等价于
Object.assign({}, obj, {b:222})

```
