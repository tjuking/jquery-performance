jquery-performance
==================

jQuery性能研究


### 选择器 ###

- `$("select2", "select1")`或者`$("select1").find("select2")`大约是`$("select1 select2")`耗时的1/3
- `$(document.body)`大约是`$("body")`耗时的1/3
