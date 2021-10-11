```js
lazyMan(name){
  this.tasks=[];
  const initFun=()=>{
      console.log(`Hi! This is ${name}!`)
      this.next()
  }
  this.tasks.push(initFun)
  setTimeout(()=>{
    this.next()
  },0)
}
lazyMan.prototype.next=function(){
  let f=this.task.shift()
  f && f()
}
lazyMan.prototype.eat=function(name){
  const excuteFn=()=>{
    console.log(`Eat ${name}~`)
    this.next()
  }
  this.task.push(excuteFn)
  return this
}
lazyMan.prototype.sleep=function(time){
 const excutFn= setTimeOut(()=>{
    this.next()
  },time)
  this.tasks.push(excutFn)
  return this
}

lazyMan.prototype.cancle=function(){
  this.tasks.pop()
  return this
}
```