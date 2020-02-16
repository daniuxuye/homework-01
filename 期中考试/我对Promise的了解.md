# Promise的用途
Promise是前端解决异步问题的统一方案,比传统的回调函数和事件更合理和强大。
# 怎么创建一个new Promise
return new Promise((resolve,reject)=>{})
# 如何使用Promise.prototype.then
**then()**方法返回一个 Promise。它最多需要有两个参数：Promise 的成功和失败情况的回调函数
```
p.then(onFulfilled[, onRejected]);

p.then(value => {
  // fulfillment
}, reason => {
  // rejection
});
```
# 如何使用 Promise.all
**Promise.all(iterable)** 方法返回一个 Promise 实例，此实例在 iterable 参数内所有的 promise 都“完成（resolved）”或参数中不包含 promise 时回调完成（resolve）；如果参数中  promise 有一个失败（rejected），此实例回调失败（reject），失败原因的是第一个失败 promise 的结果。

# 如何使用 Promise.race
**Promise.race(iterable)** 方法返回一个 promise，一旦迭代器中的某个promise解决或拒绝，返回的 promise就会解决或拒绝。
