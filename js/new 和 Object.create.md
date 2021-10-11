Stack Overflow的高分解释：
>Very simply said, new X is Object.create(X.prototype) with additionally running the constructor function. (And giving the constructor the chance to return the actual object that should be the result of the expression instead of this.)

### 步骤分析区别
new Test():
1. create new Object() obj
2. set obj.__proto__ to Test.prototype
3. return Test.call(obj) || obj;
    // normally obj is returned but constructors in JS can return a value
    
    
Object.create(Test.prototype)
1. create new Object() obj
2. set obj.__proto__ to Test.prototype
3. return obj;
    
  
