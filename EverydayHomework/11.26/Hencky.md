1. **列举5个HTML5标签，8个css3新特性， 3个ECMAScript5新api**
    ```html
    1) <h1></h1>  <div></div> <span></span> <p></p> <aside></aside> <nav></nav> <header></header> <footer></footer> <figure></figure>
    <figcaption></figcaption> <mark></mark> <progress></progress> <datalist></datalist> <button></button>  <canvas></canvas>等
    2）设置多个背景， 背景大小设置， 文本设置， 边框图片， 弹性盒子布局， transfrom， 过渡动画， 帧动画， 盒子阴影， 新增选择器， calc， 自定义字体, 媒介查询
    3） 可拖拽相关API, 地理位置API， webscoket， canvas， Storage
2. **事件对象的兼容性写法，target的兼容性写法， 阻止默认事件，阻止冒泡。**
    ```javascript
    function test(e) {
        e = window.event || e;
        obj = e.target || e.srcElement;
        e.preventDefault ? e.preventDefault() : e.returnValue = false;  // 阻止默认事件
        // return false 或者
        e.stopPropagation ? e.stopPropagation() : e.cancelBubble = true;
    }
3. **三层结构渲染**      [参考链接](https://juejin.im/post/5bbaa549e51d450e827b6b13#heading-7)
    ```c
    1. 浏览器通过HTML解析器，根据深度遍历的原则把HTML解析成DOM Tree。
    2. 将CSS解析成CSS Rule Tree（CSSOM Tree）
    3. 根据DOM树和CSSOM树来构造render tree
    4. layout：根据得到的渲染树（render tree）来计算所有节点在屏幕的位置
    5. paint： 遍历render树，并调用搞硬件硬件图形API来绘制每个节点。
4. **解释作用域链与原型链** [参考链接](https://juejin.im/post/59535cf66fb9a06bc06a37c6)
    ```c
    在ES6之前，没有块级作用域，只有函数可以创建作用域。多个函数嵌套，就形成了作用域链。浏览器查找变量时，会优先在本作用域中查找，如果没有找到，就往上一层作用域中查找，以此类推，直到顶层作用域。如果再没有找到，则会停止搜索。
    所有的函数都有一个特殊的属性：prototype（原型），指向原型对象，原型对象中的方法和属性可以被函数的实例共享。当使用new操作符实例化一个构造函数时，构造函数返回的对象的prototype指向都早函数的原型对象，可以使用__proto__访问（当然并不推荐，推荐使用ES6的Object.getPrototypeOf()）。这样就行成了一个关系链：实例对象的原型（具体应该是原型的constructor属性）指向构造函数，构造函数的原型是funciton，function的原型是Object.这就构成了一条原型链。而Object的原型是null。当使用某属性或方法时，会在原型链中一次查找，若果当前的原型中已经找到了所要的属性或方法，那么会停止查找，否则会一直向后查找原型链，直到原型链的结尾。
    **作用域链主要用于查找标识符，当作用域需要查询变量的时候会沿着作用域链依次查找，如果找到标识符就会停止搜索，否则会沿着作用域链一次向后查找，直到作用域链的结尾.而原型链是查找应用类型的属性，查找属性会沿着原型链依次进行，如果找到该属性会停止搜索并做相应的操作，否则将会沿着原型链依次查找直到结尾。**
5. **数组合并去重**
    ```javascript
    const arr1 = [1, 2, 3, 4, 5, 4, 3, 2];
    const arr2 = [1, 2, 3, 4, 5, 7, 8];
    
    // 方法一
    const newarr = [...new Set([...arr1, ...arr2])];

    // 方法二
    const newarr = arr1.concat(arr2).filter((value, index, arr) => arr.indexOf(value) === index);

    // 方法三
    function test(...rest) {
        let _arrList = [];
        let _argList = Array.from(arguments).flat();
        for (let i of _argList) {
            if (_arrList.indexOf(i) < 0) {
                _arrList.push(i);
            }
        }
        return _arrList;
    }
    let newarr = test(arr1, arr2);
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
    1. 用户输入URL，浏览器获取URL
    2. 浏览器进行DNS解析
    3. 根据解析出的IP地址，浏览器发出HTTP请求
    4. 通过三次握手，建立连接。
    5. 服务器发送数据
    6. 客户端接收数据，浏览器解析加载
9. **垃圾回收机制**  [参考链接](https://juejin.im/post/5bb470295188255c5e66f88f#heading-2)
    ```js
    1. 标记清除（最常用）
        垃圾收集器在运行的时候会给存储在内存中的所有变量都加上标记（可以使用任何标记方式）。然后，它会去掉环境中的变量以及被环境中的变量引用的变量的标记。而在此之后再被加上标记的变量将被视为准备删除的变量，原因是环境中的变量已经无法访问到这些变量了。最后，垃圾收集器完成内存清除工作，销毁那些带标记的值并回收它们所占用的内存空间。
    2. 引用计数
        引用计数（reference counting）的含义是跟踪记录每个值被引用的次数。当声明了一个变量并将一个引用类型值赋给该变量时，则这个值的引用次数就是1。如果同一个值又被赋给另一个变量，则该值的引用次数加1。相反，如果包含对这个值引用的变量又取得了另外一个值，则这个值的引用次数减1。当这个值的引用次数变成0 时，则说明没有办法再访问这个值了，因而就可以将其占用的内存空间回收回来。这样，当垃圾收集器下次再运行时，它就会释放那些引用次数为零的值所占用的内存。
10. **介绍短路操作符**  [参考链接](https://wangdoc.com/javascript/operators/boolean.html#%E4%B8%94%E8%BF%90%E7%AE%97%E7%AC%A6%EF%BC%88%EF%BC%89)
    ```js
    且运算符&&，它的运算规则是：如果第一个运算子的布尔值为true，则返回第二个运算子的值（注意是值，不是布尔值）；如果第一个运算子的布尔值为false，则直接返回第一个运算子的值，且不再对第二个运算子求值。
    或运算符||，或运算符（||）也用于多个表达式的求值。它的运算规则是：如果第一个运算子的布尔值为true，则返回第一个运算子的值，且不再对第二个运算子求值；如果第一个运算子的布尔值为false，则返回第二个运算子的值。