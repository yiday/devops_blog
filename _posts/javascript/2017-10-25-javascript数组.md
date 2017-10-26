---
layout: default
title: javascript数组
---

# {{ page.title }}

## map方法
```javascript
var arr = [1,2,3,4,5]

var newArr = arr.map(function(x) {
	return x * x
})

console.log(newArr) // [1, 4, 9, 16, 25]

var newArr2 = arr.filter(function(x) {
	return x % 2 !== 0
})
console.log(newArr2) //[1, 3, 5]

```
