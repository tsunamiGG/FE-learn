# Event loop

js是单线程的。其事件轮询由：同步任务，异步任务，macrotask（宏任务），microtask （微任务）组成。这里不再赘述概念，简单说明执行过程。

> - 同步任务： 主线程上的任务，前一个完成后后一个执行。
> - 异步任务：进入任务队列（task queue)中执行，等于macrotask。
> - macrotask：任务队列的主体，“先进先出”执行。
> - microtask ：总在任务队列末尾执行，有新的microtask 继续加在末尾执行。

- [ ] 执行过程：1.同步任务执行 2.  宏任务按队列依次执行 3.微任务按队列依次执行 4.重复1-3

常见的宏任务和微任务：

**宏任务**：

- setTimeout
- setInterval
- setImmediate
- requestAnimationFrame
- I/O
- UI rendering

**微任务**：

- process.nextTick
- Promises
- Object.observe
- MutationObserver

小练习

```javascript
async function async1(){
    console.log('async1 start')
    await async2()
    console.log('async1 end')
}
async function async2(){
    console.log('async2')
}
console.log('script start')
setTimeout(function(){
    console.log('setTimeout') 
},0)  
async1();
new Promise(function(resolve){
    console.log('promise1')
    resolve();
}).then(function(){
    console.log('promise2')
})
console.log('script end')
// 浏览器输出顺序：
// script start->async1 start->async2->promise1->script end->async1 end->promise2->setTimeout
```

> - await会将之后的代码抛入下一个执行队列，代码上的表现就是执行完await的会跳出函数体执行其他的同步任务。
>
> - setTimeout的回调函数会进入下一个同步任务队列中。
>
> - 如果输出顺序不一致，是因为各大浏览器对异步的处理是不一样的，没什么奇怪的。
>
> - 另外，node环境输出顺序也有很大差异。

