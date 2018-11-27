1.列举5个HTML5标签，8个CSS3新特性，3个ECMAScript 5新API。
答：html5标签：<canvas></canvas>、<header></header>、<nav></nav>、<section></section>、<article></article>... 
Css3新特性：css3选择器、文字特效、背景图片、边框、2D/3D切换、动画、多列布局、用户界面...
ES5新API：严格模式(use strict)、JSON对象、Function.prototype.bind()、Object和Array新增接口等。
2.事件对象兼容性写法，事件对象target兼容性写法，阻止默认事件写法，阻止冒泡事件的写法
答：事件对象兼容性写法：e=e || window.event;
事件对象target兼容性写法:e.target=e.target || e.srcElement;
阻止默认事件写法:
a1.onclick=function(e){
    e=e || window.event;
if(e.preventDefault){
e.preventDefault();
}else{
e.returnValue=false;
}
}
阻止冒泡事件的写法:
a1.onclick=function(e){
    e=e || window.event;
if(e.stopPropagation){
e.stopPropagation();
}else{
e.cancelBubble=true;
}
}
3.三层结构渲染
答：HTML结构层、CSS表现层、JavaScript行为层。
4.解释作用域链与原型链
答：作用域链：[[scope]]中所存储的执行期上下文对象的集合，这个集合呈链式链接，我们把这种链式链接叫做作用域链。
    原型链：原型链就是一个对象的原型，以及该对象原型对象的原型，直到顶级原型Object，这些原型对象呈链式链接，我们把这种链式链接叫做原型链。
5.用JS实现一个数组合并的方法（要求去重）(3种）
答：
let arr1=[1,2,3,4,5];
let arr2=[1,5,6,8,7,88,2];
//方法1
let a=(ar1,ar2)=>new Set(ar1.concat(ar2));
console.log(a(arr1,arr2));
//方法2
let a=(ar1,ar2)=>{
let newarr=[...ar1,...ar2];
let newarr1=[];
const count=newarr.length;
for(let i=0;i<count;i++){
if(newarr1.indexOf(newarr[i])==-1){
newarr1.push(newarr[i]);
}
}
return newarr1;
}
console.log(a(arr1,arr2));
//方法3
let a=(ar1,ar2)=>{
Array.prototype.push.apply(ar1,ar2);
let json={},
arr=[];
const count=ar1.length;
for(let i=0;i<count;i++){
if(json[ar1[i]]==undefined){
json[ar1[i]]=ar1[i];
arr.push(ar1[i]);
}
}
return arr;
}
console.log(a(arr1,arr2));

6.json对象与JavaScript对象的含义与区别
答：json是一种轻量级的数据交互格式，而js对象是一种javascript的引用类型；
   区别：
对比内容	JSON	Javascript 对象
键名	必须是加双引号	可允许加单引号，双引号，也可以不加
属性值	只能是数值(10进制) ,字符串(双引号),布尔值和null,也可以是数组,符合JSON的对象，不能是函数,NaN,Infinity,-Infinity和undefined	javascript 中的任意值
逗号问题	最后一个值后面不能有逗号	可以有逗号
数值问题	前导不能为0，小数点后会有值	都可以

7.var fkx={
          foo:'bar',
          way:function(){
               var self=this;
               console.log(this.foo)；
               console.log(self.foo)；
               (function(){
                     console.log(this.foo)
                     console.log(self.foo)
               }())；
          }
   }
  fkx.way()
‘bar’‘bar’‘undefined’‘bar’(this指向问题)
8.从输入url到获取页面的完整过程
答：（1）输入网址；
（2）发送到DNS服务器，并获取域名对应的web服务器对应的ip地址；
（3）与web服务器建立TCP连接；
（4）浏览器向web服务器发送http请求；
（5）web服务器响应请求，并返回指定url的数据（或错误信息，或重定向的新的url地址）；
（6）浏览器下载web服务器返回的数据及解析html源文件；
（7）生成DOM树，解析css和js，渲染页面，直至显示完成；
9.垃圾回收机制的两种方法 
答：原理：垃圾收集器会定期（周期性）找出那些不在继续使用的变量，然后释放其内存。
（1）标记清除法
在函数声明一个变量的时候，就将这个变量标记为“进入环境”。从逻辑上讲，永远都不能释放进入环境的变量所占用的内存，因为只要执行流进入相应的环境，就可能会用到它们。而当变量离开环境时，则将其标记为“离开环境”。垃圾回收器在运行时候会给存储在内存中中的所有变量都加上标记。然后它会去掉环境中的变量以及被环境中的变量引用的变量的标记（闭包）。在此之后再被标记的变量将被视为准备删除的变量，原因是环境中的变量已经无法访问到这些变量了。最后，垃圾回收器完成内存清除工作，销毁那些带标记的值并回收他们所占用的内存空间。
（2）引用计数法
    引用计数的含义是跟踪记录每个值被引用的次数。当声明了一个变量并将一个引用类型值赋给该变量时，则这个值的引用次数就是1。如果同一个值又被赋给另一个变量，则该值的引用次数加1。相反，如果包含对这个值引用的变量又取得了另外一个值，则这个值的引用次数减1。当这个值的引用次数变成0时，则说明没有办法再访问这个值了，因而就可以将其占用的内存空间回收回来。这样，当垃圾回收器下次再运行时，它就会释放那些引用次数为0的值所占用的内存。
    但是很重要的一点是当遇到循环引用的时候，函数的引用次数就不会为0，所以不会被垃圾回收器回收内存，会造成内存泄露。在IE中涉及COM对象，就会存在循环引用的问题。
10.介绍短路运算符
答：&&（逻辑与）和||（逻辑或）
  原理：当有多个表达式时，左边的表达式可以确定结果时，就不再继续运算右边的表达式的值。