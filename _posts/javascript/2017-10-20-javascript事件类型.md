---
layout: default
title: javascript事件类型
---

# {{ page.title }}

## 事件的种类

### 表单事件
 form 元素触发submit和reset事件，点击表单的按钮时，会触发click事件。输入文字，选择项等，会触发change事件，得到或失去焦点时，会触发focus和blur事件

### window事件
指事件的发生与浏览器窗口本身与非窗口中显示的内容相关。
#### load事件
当文档与其所有外部资源完全加载并显示给用户时触发
替代方案：DOMContentLoaded和readystatechange

unload事件与load相对，可以用于保存用户状态


### 鼠标事件
在文档上移动或单击鼠标时会发生鼠标事件

#### mousemove
每次移动或拖动鼠标时

因为事件的发生非常频繁，所以不能用来触发计算密集型任务

#### mousedown & mouseup
按下或释放鼠标按键时

#### mouseover & mouseout
移动鼠标指针从而使它悬停到新元素上时

### 键盘事件

#### keydown & keyup
键盘的某些键被按下或释放

#### keypress
在keydown和keyup之间会产生keypress


### DOM事件


### HTML5事件
