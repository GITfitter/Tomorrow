1. **列举5个HTML5标签，8个css3新特性， 3个ECMAScript5新api**
    ```html
    1) <h1></h1>  <div></div> <span></span> <p></p> <aside></aside> <nav></nav> <header></header> <footer></footer> <figure></figure>
    <figcaption></figcaption> <mark></mark> <progress></progress> <datalist></datalist> <button></button>  <canvas></canvas>等
    2）设置多个背景， 背景大小设置， 文本设置， 边框图片， 弹性盒子布局， transfrom， 过渡动画， 帧动画， 盒子阴影， 新增选择器， calc， 自定义字体, 媒介查询
    3） document.querySelector() 获取单个元素
		document.querySelectorAll() 获取所有符合条件的元素
		
		node.classList.add()添加类名
		node.classList.remove()删除类名
		node.classList.contains()判断是否包含指定的类名
		node.classList.toggle()切换指定的类名
2. **事件对象的兼容性写法，target的兼容性写法， 阻止默认事件，阻止冒泡。**
    ```javascript
    事件对象的兼容性
		function(e){
			e = e || window.event;
		}
	事件对象target兼容性
		function(e){
			e = e || window.event;
			if(e.target){
				e.target;
			}else{
				e.srcElement
			}
		}
	阻止默认事件
		if(e.preventDefault){
			e.preventDefault();
		}else{
			event.returnValue = false;
		}
	阻止冒泡事件
		if(e.stopPropagation){
			e.stopPropagation();
		}else{
			e.cancelBubble = true;
		}
3. **三层结构渲染**      
    ```c
    第一步、用HTML分析器，分析HTML元素，构建一个DOM树
	第二步、用CSS分析器，分析css文件和元素上的inline样式，生成页面的样式表
	第三步、将上面的DOM树和样式表关联起来，构建成一个Render树。这一过程又称为Attachment。每个DOM节点都有attach方法，接受样式信息，返回一个render对象最终会被构建成一颗render树。
	第四步、有了Render树后，浏览器开始布局，会为每个Render树上的节点确定一个在显示屏上出现的精确坐标值。
	第五步、Render树有了，节点显示的位置坐标也有了，最后就是调用每个节点的paint方法，让它们显示出来。
4. **解释作用域链与原型链** 
    ```c
    作用域链
    每次进入一个新的执行环境，都会创建一个用于搜索变量和函数的作用域链。作用域链是函数被创建的作用域中对象的集合。作用域链可以保证对		执行环境有	权访问的所有变量和函数的有序访问。
    作用域链的最前端始终是当前执行的代码所在环境的变量对象（如果该环境是函数，则将其活动对象作为变量对象），下一个变量对象来自包含环境（包含当前还行环境的环境），下一个变量对象来自包含环境的包含环境，依次往上，直到全局执行环境的变量对象。全局执行环境的变量对象始终是作用域链中的最后一个对象。
    标识符解析是沿着作用域一级一级的向上搜索标识符的过程。搜索过程始终是从作用域的前端逐地向后回溯，直到找到标识符（找不到，就会导致错误发生）。
        原型链
    由于__proto__是任何对象都有的属性，而js里万物皆对象，所以会形成一条__proto__连起来的链条，递归访问__proto__必会到头，并且值是null。
    当js引擎查找对象的属性时，先查找对象本身是否存在该属性，如果不存在，会在原型链上查找，但不会查找自身的prototype
5. **数组合并去重**
    ```javascript
    数组合并&&去重（3种）
	let a = [1,2,3];
	let b = [1,3,4,5,6];
	1)
	let x = [...new Set([...a,...b])];
	2)
	let x = [...new Set(a.concat(b))];
	3)
	    let a = [1,2,3];
    let b = [1,3,4,5,6];
    let x =[];
    for(let i in a){
        let ind = 1;
        for(let j in b){
            if(a[i]==b[j]){
                ind = 0;
                break;
            }
        }
        if(ind){
            x.push(a[i]);
        }
    }
    x=x.concat(b);
	4）indexof
			let arr1=[1,2,3]
			let arr2=[2,3,4,5]
			let newarr=arr1.concat(arr2)
			let lastarr=[]
			console.log(newarr)
			for( var i = 0 ; i < newarr.length ; i++){
				if(lastarr.indexOf(newarr[i])==-1){
					lastarr.push(newarr[i])
				}
			}
			console.log(lastarr)
6. **json对象与JavaScript对象的含义与区别**
    ```js
    JSON:一种轻量化的数据交互格式，可以跨平台传输；js对象： 一种数据类型，不能传输。
    JSON的键名必须加双引号，js对象可无，可单可双；
    JSON值不能是函数，不能是underfined NaN等，JS对象值可为任意类型；
    JSON可以通过JSON.parse()或者eval()转换为JS对象，JS对象通过JSON.stringify()转换为JSON；
    可以通过Paste as JSON插件，将JSON转为JS代码。
7. **这个一个读取值的题目**
    ```js
    bar bar undefined(这个this指向window) bar
8. **从输入URL到获取页面的完整过程**
    ```
    输入网址（URL）
    缓冲解析
        先从浏览器缓存中寻找可用资源加载，有的话就用，没有的话从网络获取
    网址的请求同时，远程服务器启动DNS查询，使得浏览器获得相应的IP地址
    tcp连接，三次握手(客户端两次，服务器一次)
    握手成功后，服务器返回响应头和响应体（内包含html）
    浏览器开始解析html（页面渲染）
9. **垃圾回收机制**  [参考链接](https://juejin.im/post/5bb470295188255c5e66f88f#heading-2)
    ```js
    1. 标记清除（最常用）
        垃圾收集器在运行的时候会给存储在内存中的所有变量都加上标记（可以使用任何标记方式）。然后，它会去掉环境中的变量以及被环境中的变量引用的变量的标记。而在此之后再被加上标记的变量将被视为准备删除的变量，原因是环境中的变量已经无法访问到这些变量了。最后，垃圾收集器完成内存清除工作，销毁那些带标记的值并回收它们所占用的内存空间。
    2. 引用计数
        引用计数（reference counting）的含义是跟踪记录每个值被引用的次数。当声明了一个变量并将一个引用类型值赋给该变量时，则这个值的引用次数就是1。如果同一个值又被赋给另一个变量，则该值的引用次数加1。相反，如果包含对这个值引用的变量又取得了另外一个值，则这个值的引用次数减1。当这个值的引用次数变成0 时，则说明没有办法再访问这个值了，因而就可以将其占用的内存空间回收回来。这样，当垃圾收集器下次再运行时，它就会释放那些引用次数为零的值所占用的内存。
10. **介绍短路操作符**  
    ```js
    短路运算符，利用逻辑或的规则，当或前满足时，将不执行或之后的代码了