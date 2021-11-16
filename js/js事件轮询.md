参阅资料

[https://github.com/sunyongjian/blog/issues/38](https://github.com/sunyongjian/blog/issues/38)

[js引擎](https://juejin.cn/post/6844904051033767944)


题目练习
    
```js
    console.log('1');

setTimeout(function() {
    console.log('2');
    process.nextTick(function() {
        console.log('3');
    })
    new Promise(function(resolve) {
        console.log('4');
        resolve();
    }).then(function() {
        console.log('5')
    })
})
process.nextTick(function() {
    console.log('6');
})
new Promise(function(resolve) {
    console.log('7');
    resolve();
}).then(function() {
    console.log('8')
})

setTimeout(function() {
    console.log('9');
    process.nextTick(function() {
        console.log('10');
    })
    new Promise(function(resolve) {
        console.log('11');
        resolve();
    }).then(function() {
        console.log('12')
    })
})
```

答案：1 7 6 8 2 4 3 5 9 11 10 12 

[这一次，彻底弄懂 JavaScript 执行机制 ](https://juejin.cn/post/6844903512845860872)

