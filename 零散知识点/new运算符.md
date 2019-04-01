# new

new操作符做了什么？

1. 创新
2. 链原（取constuctor）
3. 绑this
4. 返新

```javascript
function myNew() {
    let obj = new Object();
    obj.__proto__ = myNew.prototype;
    let res = myNew.apply(obj,arguments);
    return typeof res === 'object'? res : obj;
}
```

