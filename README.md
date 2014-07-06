jquery-performance
==================

jQuery性能研究


### 选择器 ###

- `$("select2", "select1")`其实就是通过一层判断去调用`$("select1").find("select2")`（尽量直接调用方法）
- `$("select1").find("select2")`大约是`$("select1 select2")`耗时的1/3（尽量减少正则解析）
- `$(document.body)`大约是`$("body")`耗时的1/3（原生DOM节点解析较快）
- `$("<img/>", { title: "this is title" })`大约是`$("<img title='this is title'>")`耗时的1/3-1/2（单独的简单标签将会调用`document.createElement()`创建相应的DOM元素，如果是复杂的HTML代码则需要利用innerHTML机制创建）
- 不应该为寻找一个#id元素添加上下文或前缀选择器

### 原形属性和方法 ###

- 优先使用`.length`属性来获取当前对象中元素的个数（`.size()`会增加函数调用的开销，但是测试数据没有表现出来）
- `.first()`的调用顺序：`.first()` -> `.eq(0)` -> `.slice(0, 1)` -> `.pushStack()`
