# call、apply、bind 的用法分别是什么？
先看一段代码
```
const person = {
    name:'xiaowang',
    age:24,
    introduce(){
        console.log(`Hello everyone!My name is ${this.name}. I'm ${this.age} years old.`);
    }
};
console.log(person.introduce()); // => Hello everyone! My name is xiaowang. I'm 24 years old. 
```
## call
```
const myFriend = {
    name: 'dongdong',
    age: 23,
};
​
console.log(person.introduce.call(myFriend)); // => Hello everyone! My name is dongdong. I'm 23 years old. 
```
可以看出来`introduce`这个函数中的this指向被改为了`myFriend`  
>>call方法调用一个函数，其具有一个指定的this值和分别地提供的参数（参数列表）  

语法
>>fun.call(thisArg,arg1,age2,...)
## apply
apply 和 call 的区别只有一个，就是它只有两个参数，而且第二个参数为调用函数时的参数构成的数组。函数签名：`func.apply(thisArg, [argsArray])`。如果不用给函数传参数，那么他俩就其实是完全一样的，需要传参数的时候注意它的应该将参数转换成数组形式。
来一个例子
```
var obj ={
    name:'小张',
    objAge:this.age,
    myFun:function(fm,t){
        console.log(this.name+"今年"+this.age,"岁， 来之"+fm+"去往"+t);
    }
}
var db ={
    name:'豆豆',
    age:19
}
```
```
obj.myFun.call(db,'成都','上海')；　// 豆豆 年龄 19  来自 成都去往上海
obj.myFun.apply(db,['成都','上海']);   // 豆豆 年龄 19  来自 成都去往上海  
```
## 再来看看bind
我们还是以上面这个函数为例
```
obj.myFun.call(db,'成都','上海')；　　　　 // 豆豆 年龄 19  来自 成都去往上海
obj.myFun.apply(db,['成都','上海']);      // 豆豆 年龄 19  来自 成都去往上海  
obj.myFun.bind(db,'成都','上海')();       // 豆豆 年龄 19  来自 成都去往上海
obj.myFun.bind(db,['成都','上海'])();　　 // 豆豆 年龄 19  来自 成都, 上海去往 undefined
```
可见：
三个输出都是19，但是注意看使用bind()方法的，他后面多了一对括号。也就是说，区别是：当你希望改变上下文环境之后并非立即执行，而是回调执行的时候，使用bind()方法
总结有以下几点：
* apply、call、bind 三者都是用来改变函数this对象的指向。
* apply、call、bind 三者第一个参数都是this要指向的对象，也就是指定的上下文。
* apply、call、bind 三者都可以利用后续参数传参。

* bind是返回对应的函数，便于稍后调用。
* apply、call 则是立即调用。
  

