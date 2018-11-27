# 2018年11月26日面试题

1. 列举5个HTML5标签，8个CSS3新特性，3个ECMAScript 5新API。
2. 事件对象兼容性写法，事件对象target兼容性写法，阻止默认事件写法，阻止冒泡事件的写法
3. 三层结构渲染
4. 解释作用域链与原型链
5. 用JS实现一个数组合并的方法（要求去重）(3种）
6. `json`对象与`JavaScript`对象的含义与区别
7. 从输入url到获取页面的完整过程
8. 垃圾回收机制的两种方法
9. 介绍短路运算符
10. 代码题
> ```javascript
> var fkx={
>           foo:'bar',
>           way:function(){
>                var self=this;
>                console.log(this.foo)；
>                console.log(self.foo)；
>                (function(){
>                      console.log(this.foo)
>                      console.log(self.foo)
>                }())；
>           }
>    }
>   fkx.way()
> ```
