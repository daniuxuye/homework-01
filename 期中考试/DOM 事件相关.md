# 什么是事件委托
事件委托，通俗地来讲，就是把一个元素响应事件（click、keydown......）的函数委托到另一个元素；
一般来讲，会把一个或者一组元素的事件委托到它的父层或者更外层元素上，真正绑定事件的是外层元素，当事件响应到需要绑定的元素上时，会通过事件冒泡机制从而触发它的外层元素的绑定事件上，然后在外层元素上去执行函数。
# 怎么阻止默认动作
**w3c的方法是e.preventDefault()，IE则是使用e.returnValue = false;**
preventDefault它是事件对象(Event)的一个方法，作用是取消一个目标元素的默认行为。
链接`<a>`的默认动作就是跳转到指定页面，下面就以它为例，阻止它的跳转：
```
<a href="http://dasadsas.com/" id="testA" >dasadsas.com</a>


var a = document.getElementById("testA");
a.onclick =function(e){
  if(e.preventDefault){
     e.preventDefault();
  }else{
     window.event.returnValue == false;
  }
}
```
# 如何防止冒泡

**w3c的方法是e.stopPropagation()，IE则是使用e.cancelBubble = true**
stopPropagation也是事件对象(Event)的一个方法，作用是阻止目标元素的冒泡事件，但是不会阻止默认行为。什么是冒泡事件？如在一个按钮是绑定一个”click”事件，那么”click”事件会依次在它的父级元素中被触发 。stopPropagation就是阻止目标元素的事件冒泡到父级元素。  
如：
```
<div id='div' onclick='alert("div");'>
   <ul onclick='alert("ul");'>
      <li onclick='alert("li");'>test</li>
   </ul>
</div>
```
阻止冒泡
```
window.event? window.event.cancelBubble = true : e.stopPropagation(); 
```