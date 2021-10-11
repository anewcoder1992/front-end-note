1. 借用构造函数继承
```js
   son(){

      parent.call(this,agrs)

   }
```
2. 原型函数继承
```js
   son.prototype =new parent
```
   

3. 组合方式

   结合 1,2

4. es3 

   1. 利用 Person.call(this) 执行“方法借用”，获取 Person 的属性
   2. 利用一个空函数将 Person.prototype 加入原型链

   ```js
   function Person(name) {
     this.name = name;
   }
   Person.prototype.printName = function() {
     console.log(this.name);
   };
   function Bob() {
     Person.call(this, "Bob");
     this.hobby = "Histroy";
   }
   function inheritProto(Parent, Child) {
     var Fn = function() {};
     Fn.prototype = Parent.prototype;
     Child.prototype = new Fn();
     Child.prototype.constructor = Child;
   }
   inheritProto(Person, Bob);
   Bob.prototype.printHobby = function() {
     console.log(this.hobby);
   };
   console.dir(new Bob());
   ```

5. es5

   1. 利用 Person.call(this) 执行“方法借用”，获取 Person 的属性
   2. 利用 ES5 增加的 Object.create 方法将 Person.prototype 加入原型链

   ```js
   function Person(name) {
     this.name = name;
   }
   
   Person.prototype.printName = function() {
     console.log(this.name);
   };
   
   function Bob() {
     Person.call(this, "Bob");
     this.hobby = "Histroy";
   }
   
   Bob.prototype  = Object.create(Person.prototype, {
     constructor: {
       value: Bob,
       enumerable: false,
       configurable: true,
       writable: true
     }
   });
   
   Bob.prototype.printHobby = function() {
     console.log(this.hobby);
   };
   
   console.dir(new Bob());
   ```

6. es6  方式

   