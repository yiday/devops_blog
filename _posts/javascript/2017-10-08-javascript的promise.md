---
layout: default
title: javascript的promise用法
---

# {{ page.title }}

## 构造函数同步，then函数异步
```javascript
const promise = new Promise((resolve, reject) => {
	console.log(1)
	resolve()
	console.log(2)
})

promise.then(() => {
	console.log(3)
})

console.log(4)

```
输出顺序
<pre>
1
2
4
3
</pre>
