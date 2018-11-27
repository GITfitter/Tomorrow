# 20181124作业

## 1. 说出3中web安全问题

>1. XSS(跨站脚本攻击)
>    在URL或者页面输入框中插入js代码。
>    防范： 设置httpOnly，禁止用document.cookie操作； 对输出转义，xss.js.
>2. CSRF(跨站请求伪造)
>    攻击者通过一些技术手段欺骗用户的浏览器访问一个自己曾经认证过的网站并执行一些操作,主要是拿到了用户的登录状态。
>    防范：检查referer字段，查看请求源地址；添加Token；输入验证码。
>3. SQL注入
>    通过SQL命令插入到web表单提交或输入域名或页面请求的查询字符串，最终达到欺骗服务器执行恶意的SQL命令。
>    防范： 对用户输入校验；不要动态拼装SQL；不要用管理员权限的数据库连接。

## 2. 也是读值的题

```javascript
baz  
undefined
// 两个this都指向全局环境
```

## 3. 移除数组第一个元素的方法

```javascript
const arr = [1, 2, 3, 4, 5];

// 方法一
arr.shift();

// 方法二
let newarr = arr.slice(1);

// 方法三
let newarr = arr.splice(0, 1);

// 方法四
let newarr = arr.filter((value, index) => index > 0);

// 方法五
// 略
```

## 4. 使元素消失的方法

>1. `display: none`
>2. `visible: hidden`
>3. 宽度或高度设置为0，`overflow: hidden`
>4. `opacity: 0`
>5. `transform: scale(0)`
>6. `z-index: -1` 移动到其他元素后边
>7. 使用位移在视口中移出该元素
>8. 标签里添加`hidden`属性
>9. input类型设置为hidden
>10. `background: transparent`, `color: transparent`
>11. 背景色和颜色,设置与背景元素相同

## 5. typeof会返回几种数据类型

>1. **`object`**
>2. `string`
>3. `number`
>4. `boolean`
>5. `undefined`
>6. `function`
>7. `symbol`
>8. `Implementation-dependent`

## 6. 一个简单编程

```js
const arr = [];
for (let i = 0; i < 400 ; i++) {
    if (i.toString().match(/1/)) {
        arr.push(i);
    }
}
console.log(arr.length); // 157
```

## 7. AJAX请求时，get和post区别  [参考链接](https://www.cnblogs.com/ranyonsue/p/5888692.html "ajax请求中get和post区别")

>1. get请求参数在URL进行传递，post请求则是作为HTTP消息的实体内容发送给服务器。当然，这种区别用户看不到
>2. get通过URL提交数据，数据长度受到浏览器限制。post没有限制
>3. get请求的数据会被浏览器缓存，有可能带来安全问题，post方式相对安全。
>4. 服务器端接受方式有所不同.
>  以下情况使用一般用GET方法：
>* 请求是为了查找资源，HTML表单数据仅用来帮助搜索
>* 请求结果无持续性副作用（如搜索）
>* 收集的数据及HTML表单的输入字段名称总长度小于1024字节

## 8. `==`和`===`和`Object.is()`的不同  [参考链接](https://wangdoc.com/javascript/operators/comparison.html)

> * JS提供两种相等运算符： `==` 和 `===`
> * 简单说，它们的区别是相等运算符`==`比较两个值是否相等，严格相等运算符`===`比较它们是否为“同一个值”。如果两个值不是同一类型，严格相等运算符`===`直接返回false，而相等运算符`==`会将它们转换成同一个类型，再用严格相等运算符进行比较。
> * 两种比较运算符对于 `NaN === NaN` 会返回 `flase`,对于 `+0 === -0` 会返回 `true`。
> * Object.is()是ES6新增的判断值是否相等的方法，遵循严格等于的同时，修正了上面的问题，`Object.is(NaN, NaN)` 会返回`true`, `+0 === -0` 会返回 `false`。

## 9. js有几种函数调用方式  [参考链接](https://blog.csdn.net/Rainy_X/article/details/80022684)

> 1. 函数调用模式
> 先声明，后单独独立的调用。即**函数名（参数）**
> 2. 方法调用模式
> 用对象的方法调用，方法不是单独独立的，而是要通过一个对象来调用。即**对象.方法（参数）**
> 3. 构造函数模式
> 使用new关键字引导，实例化对象
> 4. 作为函数方法调用
> 通过`Function.prorotype.call()` 或者 `Function.prototype.apply()` 调用。

## 10. JS深拷贝浅拷贝

```javascript
// 深拷贝：迭代复制所有对象的拷贝方式  
const arr = [1, 2, 3, 4];
let deepClone = obj => JSON.parse(JSON.stringify(obj));
const newarr = deepClone(arr);

// 浅拷贝：仅复制最顶层对象的拷贝方式
const obj1 = {a: 1};
const obj2 = Object.assign({}, obj1);
```