2018年11月27日面试题
===================
#1、说出3种web安全问题
答：(1)sql注入；
   (2)XSS跨站脚本攻击；
   (3)CSRF：跨站请求伪造。
#2、
#let fun=()=>{ console.log(this.foo); } 
#let c={ 
#        foo:'foo', 
#        baz:'bar', 
#        say(){
#                fun(); 
#                (function(){ console.log(this.baz); }()) 
#          } 
#   } 
#  var foo='baz'; 
#  c.say();
答：'baz' undefined.
# 3、数组移除第一个元素的方法有哪些？
答：(1)delete arr[0];
    (2)arr.shift();
    (3)arr.splice(0,1);
    (4)arr.filter((value,index,arr)=>index!==0);
    (5)newarr=arr.slice(1);
    等等...
# 4、使元素消失的方法有哪些？
答：(1)display:none;
   (2)opacity:0;
   (3)visibility:hidden;
   (4)position 利用z-index;
   (5)overflow:hidden;
   (6)transform中的translateX（Y）的值为-100%;
   (7)将元素的font-size，line-height,width,height设置为0;
   (8)设置元素的clip（在新的css中使用clip-path来代替clip)要让其生效，必须给元素的position的值设置为absolute或者fixed;
   等等...
# 5、var arr=[]; console.log(typeof arr) ??? typeof 会返回几种数据类型
答：object
    (1)null
    (2)undefined
    (3)boolean
    (4)string
    (5)number
    (6)object
    (7)symbol
# 6、使用js，返回1到400所有自然数中一共出现过多少次“1”，并返回出现次数
  function check(start,end,n=1){
    const count=end+1;
    let num=0;
    let arr=[];
    for(let i=start;i<count;i++){
      arr.push(...i.toString().split(""),);
    }
    const num1=arr.length;
    for(let i=0;i<num1;i++){
      if(arr[i]==n){
        num++;
      }
    }
    return num;
  }
  console.log(check(1,400));
# 7、ajax请求的时候get 和post方式的区别
答：Get和Post都是向服务器发送的一种请求，只是发送机制不同；
    (1)GET请求会将参数跟在URL后进行传递，而POST请求则是作为HTTP消息的实体内容发送给WEB服务器。当然在Ajax请求中，这种区别对用户是不可见的。
    (2)首先是"GET方式提交的数据最多只能是1024字节"，因为GET是通过URL提交数据，那么GET可提交的数据量就跟URL的长度有直接关系了。而实际上，URL不存在参数上限的问题，HTTP协议规范没有对URL长度进行限制。这个限制是特定的浏览器及服务器对它的限制。IE对URL长度的限制是2083字节(2K+35)。对于其他浏览器，如Netscape、FireFox等，理论上没有长度限制，其限制取决于操作系统的支持。注意这是限制是整个URL长度，而不仅仅是你的参数值数据长度。
    (3)GET方式请求的数据会被浏览器缓存起来，因此其他人就可以从浏览器的历史记录中读取到这些数据，例如账号和密码等。在某种情况下，GET方式会带来严重的安全问题。而POST方式相对来说就可以避免这些问题。

    get请求和post请求在服务器端的区别:
    (4)在客户端使用get请求时,服务器端使用Request.QueryString来获取参数,而客户端使用post请求时,服务器端使用Request.Form来获取参数.
    HTTP标准包含这两种方法是为了达到不同的目的。POST用于创建资源，资源的内容会被编入HTTP请示的内容中。例如，处理订货表单、在数据库中加入新数据行等。
    当请求无副作用时（如进行搜索），便可使用GET方法；当请求有副作用时（如添加数据行），则用POST方法。一个比较实际的问题是：GET方法可能会产生很长的URL，或许会超过某些浏览器与服务器对URL长度的限制。

    若符合下列任一情况，则用POST方法：
       请求的结果有持续性的副作用，例如，数据库内添加新的数据行。
       若使用GET方法，则表单上收集的数据可能让URL过长。
       要传送的数据不是采用7位的ASCII编码。

    若符合下列任一情况，则用GET方法：

       请求是为了查找资源，HTML表单数据仅用来帮助搜索。
       请求结果无持续性的副作用。
       收集的数据及HTML表单内的输入字段名称的总长不超过1024个字符。
# 8、'=='和'==='和Object.is()的不同
答：(1)==和===的区别是，'=='在比较的时候会对作比较的数据进行隐式类型转换，比较的只是值是否相等；而'==='在比较的过程中除了比较值是否相等之外还比较类      型是否相同；
    (2)Object.is()与'==='的作用基本相同，只是在+0、-0、NaN的问题上有分歧，在ES5中，-0===+0  ==> true , NaN===NaN ==>false;而在ES6中，   Object.is(-0,+0) ==>false,Object.is(NaN,NaN) ==>true,除了这两处不同以外它们两个在用法上没什么区别。
# 9、js有几种函数调用方式?
答：(1)func();
   (2)call
   (3)apply
   (4)setTimeout
   (5)setInterval
   (6)new Person();
   (7)obj.func();
   等等...
# 10、js实现对象的深拷贝浅拷贝
答：(1)浅拷贝
       let a={
           name:lily,
           age:20,
           sayName(){
               console.log(this.name);
           }
       };
       const b=a;
    (2)深拷贝
     let a={
           name:'lily',
           age:20,
           tel:13131313131
       };
     let deepClone=(object)=>JSON.parse(JSON.stringify(object));
     const b=deepClone(a);