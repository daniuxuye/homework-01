# 基于原型
***
这个原型我看了好多篇文章始终没有特凑的理解，最后看了方大大的知乎上的[方三篇]又结合阮大大的文章才理解差不多了。
***
比如说我们构造一个DOG的原型函数
```
function DOG(name){

　　　　this.name = name;

　　　　this.species = '犬科';

　　}
```
然后，生成两个实例对象：
```
　　var dogA = new DOG('阿黄');

　　var dogB = new DOG('小白');
```
但是这两个对象的species属性是独立的，修改其中一个，不会影响到另一个。
```
　  dogA.species = '猫科';
 
　　alert(dogB.species); // 显示"犬科"，不受dogA的影响
```
每一个实例对象，都有自己的属性和方法的副本。这不仅无法做到数据共享，也是极大的资源浪费。
## 怎么办呢？
这个时候**prototype属性的引入**可以很好的解决这个问题2.
还是以DOG构造函数为例，现在用prototype属性进行改写：
```
function DOG(name){

　　　　this.name = name;

　　}

　　DOG.prototype = { species : '犬科' };
   // DOG.prototype.species = '犬科';


　　var dogA = new DOG('大黄');

　　var dogB = new DOG('小白');


　　alert(dogA.species); // 犬科

　　alert(dogB.species); // 犬科
```

## 总结
这就是我对与基于原型的JS继承的理解
**原型公式**
```
arr._proto_ === Array.prototype
```

# 基于class
ES6引入了一个新语法--<font color=#00ffff size=4>class</font>语法
其实class就是上面原型的简便写法
基于原型的写法
```
function DOG(name){

　　　　this.name = name;

　　}

　　DOG.prototype = { species : '犬科' };
```
用class改写
```
class DOG{
    constructor(name){
        this.name = name;
    }
    species(){
        return '犬科'
    }
}
```
除此以外，class还引入了一些新的语法。
比如说
```
class DOG{
    name = '波奇'
    constructor(name){
        this.name = name;
    }
    species(){
        return '犬科'
    }
}
```
可以在里面加上一些初始属性。
等待这些ES6的新语法。这些我决定慢慢学，用到哪个学哪个。
可以参考[ES 6新特点列表](https://fangyinghang.com/es-6-tutorials/)






