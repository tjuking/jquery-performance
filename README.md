jquery-performance
==================

jQuery性能研究


### 选择器 ###

- `$("select2", "select1")`或者`$("select1").find("select2")`大约是`$("select1 select2")`耗时的1/3（尽量减少正则解析）
- `$(document.body)`大约是`$("body")`耗时的1/3（原生DOM节点解析较快）
