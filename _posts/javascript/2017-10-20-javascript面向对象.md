---
layout: default
title: javascript面向对象
---

# {{ page.title }}

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
