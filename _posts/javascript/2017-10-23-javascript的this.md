---
layout: default
title: javascript的this
---

# {{ page.title }}

## this与window
在浏览器的全局环境中，this就是window,指代全局对象
```javascript
this === window
a = 37
this.a // 37
```

## 函数内部
在函数内部，this的值取决于函数被调用的方式

1. 直接调用
   ```javascript
   function f1() {
     return this
   }
   f1() === window // true

   //严格模式下，this将保持他进入执行上下文时的值，所以下面的this会默认为undefined
   function f2() {
     'use strict'
     return this
   }

   f2() === window // false
   ```

2. call和apply方法（间接调用）
   将this的值从一个context传到另一个，就要用call或apply方法。
   ```javascript
    // 一个对象可以作为call和apply的第一个参数，并且this会被绑定到这个对象。
    var obj = {a: 'Custom'};

    // 这个属性是在global对象定义的。
    var a = 'Global';

    function whatsThis(arg) {
      return this.a;  // this的值取决于函数的调用方式
    }

    whatsThis();          // 直接调用，      返回'Global'
    whatsThis.call(obj);  // 通过call调用，  返回'Custom'
    whatsThis.apply(obj); // 通过apply调用 ，返回'Custom'

   ```
  whatsThis.call(obj)的意思是将obj当作call的第一个参数传入，whatsThis内部的this将会绑定到这个obj上。

  **注意** : 如果call\apply传入的不是对象，则js会尝试使用内部的<code>ToObject</code>操作

3. bind方法
   调用f.bind(obj)将会**创建**一个与f一样具有相同函数体和作用域的函数，但这个函数中的this将会**永久**被绑定到obj上
  ```javascript
  function f() {
  	return this.a
  }
  var log = console.log.bind(console)

  var obj = { a: 'dog' }

  var g = f.bind(obj)
  console.log(g()) //dog
  ```

4. 箭头函数
  ```javascript
  var globalObject = this
  var foo = (() => this)
  console.log(foo() == globalObject) //true
  ```
5. 作为一个对象的方法
   当以对象里的方法的方式调用函数时，它们的 this 是调用该函数的对象.
   ```javascript
   var o = {
     prop: 37,
     f: function() {
       return this.prop;
     }
   };

   console.log(o.f()); // logs 37

   ```

6. 原型链中的this


7. getter与setter中的this

8. 作为一个构造函数

9. 作为一个DOM事件的处理函数

10. 作为一个内联事件处理函数
