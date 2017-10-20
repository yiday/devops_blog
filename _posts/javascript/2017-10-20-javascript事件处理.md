---
layout: default
title: javascript事件处理
---

# {{ page.title }}

## 注册事件处理程序
### 设置事件目标属性为事件处理函数
```javascript
//当文档加载完毕时调用它
window.onload = function() {
  // 查找form元素
  var elt = document.getElementById("shipping_address")
  // 注册事件处理函数
  elt.onsubmit = function() {
    return validate(this)
  }
}
```

### addEventListener()
通过此函数，可以为同一对象注册多个处理程序函数
```javascript
var b = document.querySelector("button")
	b.onclick = function() {
		alert('btn click...')
	}

	b.addEventListener('click', function() {
		alert('listen click')
	}, false)
```
