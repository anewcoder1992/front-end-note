### 案例

// 实现一个add方法，使计算结果能够满足如下预期：
add(1)(2)(3) =                                  6;
add(1, 2, 3)(4) = 10;
add(1)(2)(3)(4)(5) = 15;
```js
function add() {
    // 第一次执行时，定义一个数组专门用来存储所有的参数
    var _args = Array.prototype.slice.call(arguments);

    // 在内部声明一个函数，利用闭包的特性保存_args并收集所有的参数值
    var _adder = function() {
        _args.push(...arguments);
        return _adder;
    };

    // 利用toString隐式转换的特性，当最后执行时隐式转换，并计算最终的值返回
    _adder.toString = function () {
        return _args.reduce(function (a, b) {
            return a + b;
        });
    }
    return _adder;
}
```

参数不定版本的curry



### 概念
将一个函数的多个参数可以分步输入，逐个输入或者多个输入
### 作用
* 延迟执行
* 提高复用性 细化函数颗粒度功能
* 函数缓存 参数提前缓存

手写  curry 
```js
function curry(func) {
  return function curried(...args) {
    if (args.length >= func.length) {
      return func.apply(this, args);
    } else {
      return function(...args2) {
        return curried.apply(this, args.concat(args2));
      }
    }
  };
}
```

参数不定的curry 案例的解决方案

```js
function add (...args) {
    //求和
    return args.reduce((a, b) => a + b)
}

function currying (fn) {
    let args = []
    return function temp (...newArgs) {
        if (newArgs.length) {
            args = [
                ...args,
                ...newArgs
            ]
            return temp
        } else {
            let val = fn.apply(this, args)
            args = [] //保证再次调用时清空
            return val
        }
    }
}



const currying = (fn: Function) => {
  let args = [];

  return function temp(...newArgs) {
    if (newArgs.length) {
      args.push(...newArgs);
      return temp;
    } else {
      const val = fn.apply(this, args);
      args = [];
      return val;
    }
  };
};
```

