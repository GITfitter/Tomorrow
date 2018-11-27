# 2018年11月27日面试题
1. 说出3种web安全问题
2. 	
	let fun=()=>{
		console.log(this.foo);
		}
let  c={
		foo:'foo',
		baz:'bar',
		say(){
            fun();
            (function(){
                console.log(this.baz);
            }())
		}
}
		var foo='baz';
		c.say();
3. 数组移除第一个元素的方法有哪些？
4. 使元素消失的方法有哪些？
5. var arr=[];
console.log(typeof arr)  ???
typeof  会返回几种数据类型
6. 使用js，返回1到400所有自然数中一共出现过多少次“1”，并返回出现次数  
7. ajax请求的时候get 和post方式的区别
8. '\=\='和'\=\=\='和Object.is()的不同
9. js有几种函数调用方式?
10. js实现对象的深拷贝浅拷贝