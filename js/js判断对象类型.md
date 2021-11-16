```js
const isType = type=> obj => `[object ${type}]` === Object.prototype.toString.call([])
```
不能 用于判断基本类型 因为会进行装箱操作