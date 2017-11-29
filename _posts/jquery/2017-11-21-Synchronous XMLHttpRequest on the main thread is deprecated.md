---
layout: default
title: Synchronous XMLHttpRequest on the main thread is deprecated
---

# {{ page.title }}

## 在主进程同步引发的错误
jquery 报
<pre>
Synchronous XMLHttpRequest on the main thread is deprecated because of its detrimental effects to the end user's experience. For more help, check https://xhr.spec.whatwg.org/.
</pre>
查了有关资料，应该是因为主进程不支持用ajax进行同步方式获取数据，因为这样会阻塞主进程，影响用户体验。
