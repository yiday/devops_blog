---
layout: default
title: javascript函数
---

# {{ page.title }}

## 函数字面量
```javascript
var add = function(a, b) {
  return a + b
}
//因为没有函数名，所以是匿名函数

```

## 闭包
通过函数字面量创建的函数对象包含一个连接到外部上下文的连接，这被称为闭包(closure).

## 调用
1. 方法调用

   当函数被保存为对象的一个属性时，则它是一个方法
   ```javascript
   var myObj = {
     value: 0,
     increment: function(inc) {
       this.value += typeof inc === 'number' ? inc : 1
     }
   }
   myObj.increment()
   myObj.increment(2)

   ```
   方法可以使用this访问自己所属的对象，所以可以通过方法进行取值或对对象进行修改。
   通过this可取得它们所属对象的上下文的方法称为公共方法。
2. 函数调用

   var sum = add(3, 4)
   this被绑定到全局对象。
3. 构造器调用

   如果在一个函数前面带上new调用，那么将会创建一个连接到该函数的prototype成员的新对象，同时，this会被绑定到那个新对象上。
   ```javascript
    //构造函数（不推荐）
    var Quo = function(string) {
		    this.status = string
  	}

  	Quo.prototype.get_status = function() {
  	   return this.status
  	}

  	var myQuo = new Quo("confused")
  	alert(myQuo.get_status())

   ```
4. apply调用
  因为是函数式面向对象语言，所有函数可以拥有方法
  ```javascript
   var array = [3, 4]
   var sum = add.apply(null, array)


  ```

## 参数
1. 实参与形参个数可以不匹配
2. 实参多于形参时，超出的会被忽略
3. 实参少于形参时，缺失的会被替换为undefined

## arguments
arguments 并不是一个真正的数组，只是一个“array-like”对象，拥有一个length属性，但没有任何数组方法。

```javascript
  var sum = function() {
    var i, sum = 0;
    for (i = 0; i < arguments.length; i += 1) {
      sum += arguments[i]
    }
    return sum
  }
//调用
sum(4,3,2,4,5)
```

## 异常
```javascript
var add = function(a, b) {
  if(typeof a !== 'number' || typeof b !== 'number') {
    throw {
      name: 'TypeError',
      message: 'add needs number',
    }
  }
  return a + b
}

alert(add('4', 5))
// try catch
try{
	add('4', 5)
}catch(e) {
	alert(e.name + ': ' + e.message)
}
```


## 记忆(memoization)
函数可以将先前的操作结果记录到某个对象里，从而避免重复运算

```javascript
var memoizer = function (memo, formula) {
  var recur = function(n) {
    var result = memo[n]
    if (typeof result !== 'number') {
      result = formula (recur, n)
      memo[n] = result
    }
    return result
  }
  return recur
}

var fibonacci = memoizer([0, 1], function(recur, n) {
  return recur (n-1) + recur(n-2)
})
```


## 高阶函数（Higher-order function）
JavaScript的函数其实都指向某个变量。既然变量可以指向函数，函数的参数能接收变量，那么一个函数就可以接收另一个函数作为参数，这种函数就称之为高阶函数。

```javascript
function add(x, y, func) {
  return func(x) + func(y)
}

add(-4, -5, Math.abs)
```

### map


### reduce


### filter
根据传入的函数依次作用于每个元素，然后根据返回值是true还是false决定保留还是丢弃该元素。

例如，以下filter是去除arr中的偶数
```javascript
var arr = [1,2,3,4,5,6]
arr.filter(function(x) {
  return x % 2 !== 0
})

```
### sort
