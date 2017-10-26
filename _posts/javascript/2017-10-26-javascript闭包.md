---
layout: default
title: javascript闭包
---

# {{ page.title }}

## 变量的作用域
变量的作用域只有两种：全局变量和局部变量
1. 函数内可以直接**读取**和**修改**全局作用域
```javascript
var n = 999
function func() {
  alert(n)
}
```

2. 函数外部无法读取函数内部变量
```javascript
function f1(){
　　　　var n=999;
　　}
　　alert(n); // error
```

3. var创建的变量
  var 语句声明的变量的作用域是当前执行位置的执行环境（执行上下文）：
  函数内部、全局
  不用var声明的变量，则是全局的
  ```javascript
  function f1() {
  	var fval = 999
    gval = 333
  	function f2() {
  		console.log(fval)
  	}
  	return f2
  }
  console.log(fval) // error,
  console.log(gval) // 333
  ```

3. 函数的this指向哪个作用域？

```javascript
   var name = "The Window";
　　var object = {
　　　　name : "My Object",
　　　　getNameFunc : function(){
　　　　　　return function(){
　　　　　　　　return this.name;
　　　　　　};
　　　　}
　　};
　　alert(object.getNameFunc()()); // The Window

```

```javascript
   var name = "The Window";
　　var object = {
　　　　name : "My Object",
　　　　getNameFunc : function(){
　　　　　　var that = this;
　　　　　　return function(){
　　　　　　　　return that.name;
　　　　　　};
　　　　}
　　};
　　alert(object.getNameFunc()()); // My Object

```

## 链式作用域（chain scope）
简单的闭包，定义在一个函数内部的函数。
```javascript
function f1() {
	var n = 99
	function f2() {
		alert(n)
	}
	return f2
}

var result = f1()
result()
```


## 如何从外部读取局部变量？
