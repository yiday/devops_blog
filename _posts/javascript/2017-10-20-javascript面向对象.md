---
layout: default
title: javascript面向对象
---

# {{ page.title }}

## 简单数据类型
数字、字符串、布尔值、null、undefined
它们都是“貌似”对象，因为它们拥有方法，但它们是不可变的。

## 对象
数组、函数、正则表达式、*对象*

## 对象特性
1. 无类型的(class-free)
2. 对象是属性的容器,属性值可以是除undefined外的任何值
3. 原型链特性


## 对象字面量表示
```javascript
var lucy = {
  name: 'Lucy Le',
  email: 'lucy@qq.com',
  website: 'http://devops.scjia.cc',
}
```
访问对象的成员
```javascript
//以成员的方法
lucy.name
lucy.email
lucy.website

//以hash map方式
lucy["name"]
lucy["email"]
lucy["website"]
```

key可以用引号（单、双）括起来，如果key里有中划线，则必须要引起来，如
first-name => "first-name"

## 定义成员函数
### 非规范写法
通过定义一个全局成员函数，用直接赋值的方法，动态给对象增加方法
```javascript
var sayHello = function() {
  var hello = "hello,I am "+this.name
  alert(hello)
}

lucy.Hello = sayHello
lucy.Hello()
```
### 比较规范的写法
```javascript
var Person = function(name, email, website) {
  this.name = name
  this.email = email
  this.website = website
  this.sayHello = function() {
    var hello = "hello,I am "+this.name
    alert(hello)
  }
}

var lucy = new Person('Lucy', 'lucy@qq.com', 'http://devops.scjia.cc')
lucy.sayHello()
```

删除一个对象属性（方法）
```javascript
delete lucy['email']
```

## 通过Object创建对象

### 构造函数
```javascript
//创建对象
//new Object([value])
//如果value为null或undefined则会创建一个空对象
new Object(null)
Object.create(null)
```

### 构造函数的方法
Object.assign()
 通过复制一个或多个对象来创建一个新的对象

Object.create()
 使用指定的原型对象和属性创建一个新对象

Object.defineProperty()
 给对象添加一个属性并指定该属性的配置
 ```javascript
  var Alien = new Object(null)
  Object.defineProperty(Alien, 'name', {value: 'Alien', writable: true, configurable: true, enumerable: true})

  alert(Alien.name)
 ```
 definePropertity()方法还有get/set访问器，但不能和value一起用,还不能添加writable属性
 ```javascript
  var Alien = new Object(null)
  var nameValue = ''
  Object.defineProperty(Alien, 'name',
  						{
  							get: function() {
  								return nameValue
  							},
  							set: function(val) {
  								nameValue = val
  							},
  							// writable: true,
  							configurable: true,
  							enumerable: true
  						}
  					 )

  Alien.name = 'bbb'
  alert(Alien.name)
```

Object.defineProperties()
 给对像添加多个属性


 ## 原型

![avatar](http://images.cnitblog.com/blog/476499/201310/10141012-dcee2678158a4c95a1338d358144403a.jpg)

 所有对象字面量创建的对象都连接到Object.prototype（标配对象）
 原型连接只有在检索值的时候才被用到

 ### \_\_proto\_\_ 与prototype
 指向创建这个对象的函数的显式原型(prototype)，关键点：找到创建这个对象的构造函数

 **所有构造函数的\_\_proto\_\_都指向Function.prototype，它是一个空函数（Empty function）**
prototype是什么？
是一个函数,是对象
对象的\_\_proto\_\_是什么？
是一个属性,指向这个对象的构造函数的prototye
```javascript
var Foo = function() {}

var f1 = new Foo()
f1.__proto__ === Foo.prototype // true

```

函数的构造函数是什么？
是Function,所以
```javascript
Foo.__proto__ === Function.prototype //true

```



.prototype是一个对象的原型对象，而.\_\_proto\_\_则是对原型对象的引用！


* Object.prototype 指向的原型是null
* 函数都继承自Function.prototype
   ```javascript
   var Foo = function() {}
   Foo.__proto__ === Function.prototype // true
   ```

三种创建对象的方式

* 字面量对象
   ```javascript
   var person = {}
   person.__proto__ === Object.prototype //true

   ```

* 通过构造函数生成的对象
  ```javascript
  function Person() {}
  var p = new Person()
  p.__proto__ === Person.prototype // true
  Person.__proto__ === Function.prototype // true
  ```

* Object.create构造
  ```javascript
  var person = {}
  var p = Object.create(person)
  p.__proto__ === person //true

  ```
  在没有Object.create的时候，通常可以这样做，
  ```javascript
  Object.create = function(p) {
    function f(){}
    f.prototype = p;
    return new f();
  }

  ```
