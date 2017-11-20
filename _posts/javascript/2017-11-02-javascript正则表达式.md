---
layout: default
title: javascript 正则表达式
---

# {{ page.title }}

## 非打印字符
| 字符 | 描述 |
| ------| ------ |
| \S | 匹配任何非空白字符 |
| \s | 匹配任何空白字符，包括空格、制表符、换页符等|
| \f | 匹配换页符 |
| \t | 匹配制表符 |
| \n | 匹配换行符 |
| \r | 匹配回车符 |

## 创建正则表达式
1. 使用<code>/</code>包含一个正则语法字符串
```javascript
var re = /ell/
```

2. 使用RegExp对象
```javascript
var re = new RegExp("ell")
```

## 使用正则
1. exec
用正则表达式模式在字符串中查找，如果找到则返回结果数组
否则返回
```javascript
var re = /ell/
re.exec("Hello")
```
反回一个数组：["ell", index: 1, input: "Hello"]

2. match
```javascript
var re = /ell/
var str = "Hello"

str.match(re)

```
如果匹配到，反回的和exec一样是个数组对象


3. search
