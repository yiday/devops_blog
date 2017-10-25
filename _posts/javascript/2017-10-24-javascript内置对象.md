---
layout: default
title: javascript内置对象
---

# {{ page.title }}

## Math

### 简介
Math对象的所有属性和方法都是静态的
1. 全精度（double）
   占用8字节，64位， 有效小数位16位
   ps:单精度(float),占用4字节，16位，有效小数位7位

### 常用方法
#### ceil(x)
返回x向上取整后的值
```javascript
var i = 33.1
Math.ceil(i) // 34
```

如果x是负数，则返回大于x的负整数
```javascript
Math.ceil(-1.1) // -1
```

#### floor(x)
返回小于x的最大整数

```javascript
var i = 33.1
Math.floor(i) // 33
```

如果x是负数，则返回小于x的负整数
```javascript
Math.floor(-1.1) // -2
```

实际应用
```javascript
Function.prototype.method = function(name, func) {
	this.prototype[name] = func
	return this
}

Number.method('integer', function() {
	return Math[this < 0 ? 'ceil' : 'floor'](this)
})
console.log(11.3.integer()) //11
console.log(-11.3.integer()) //-11
```

简写：**~~number**
```javascript
~~4.5 // 4
```

#### abs(x)
返回x的绝对值

#### sign(x)
返回x的符号函数，判定x是正数，负数还是0
```javascript
Math.sign(-11.2) //-1
Math.sign(0) //0
Math.sign(11.2) //1
```

#### max([x[,y[,...]]])
返回0个到多个数值中最大值

### min([x[,y[,...]]])
返回0个到多个数值中最小值


### pow(base, exponent)
返回基数(base)的指数(exponent)次幂
```javascript
Math.pow(2, 3) //8
```
