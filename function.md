## 定义一个函数
* 具名函数
```JavaScript
function 函数名(形式参数1, 形式参数2){
  语句
  return 返回值
}
```
* 匿名函数
```JavaScript
上面的具名函数，去掉函数名就是匿名函数
let a = function(x, y){ return x+y }
也叫函数表达式
```

* 箭头函数
```JavaScript
let f1 = x => x*x 
let f2 = (x,y) => x+y // 多个参数时，圆括号不能省
let f3 = (x,y) => {return x+y； console.log('hi')} // 内容超过一行时，{}和return不能省
let f4 = (x,y) => ({name:x, age: y}) // 直接输出对象会出问题，需要加个圆括号
```

## 函数的调用时机
```JavaScript
let a = 1
function fn(){
  console.log(a)
}

a = 2
fn() //2
```
```JavaScript
let a = 1
function fn(){
  console.log(a)
}

fn() //1
a = 2
```
* 区别是案例一是先a = 2，再调用的函数。而案例而是先调用了函数，a再重新赋值。所以调用函数的时机不一样，结果就会不同

```JavaScript
let i = 0
for(i = 0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
}

打印出6个6
```
* 因为setTimeout(()=>{
    console.log(i)
  },0)是等for循环结束后立刻执行console.log(i)的意思；
* for循环结束的时候i=6，所以会打印出6个6

```JavaScript
for(let i = 0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
}
```
如果是用let声明变量i的话，打印出的则是0、1、2、3、4、5


## 作用域
* 如果多个作用域有同名变量 a
* 那么查找 a 的声明时，就向上取最近的作用域
* 简称「就近原则」
* 查找 a 的过程与函数执行无关
* 但 a 的值与函数执行有关

```JavaScript
function f1(){
  let a = 1
  
  function f2(){
    let a = 2
    console.log(a)
  }

  console.log(a)
  a = 3
  f2()
}
f1() //1 2
```
* 调用f1(),虽然先看到的f2()，但是那是还没有调用，所以先输出f1里的a=1,调用f2()的时候再输出f2作用域里面的a。

## 闭包
* 如果一个函数用到了外部的变量,那么这个函数加这个变量,就叫做闭包。
```JavaScript
function f1(){
  let a = 1
  function f2(){
    let a = 2
    function f3(){
      console.log(a) //左边的 a 和 f3 组成了闭包。
    }
    a = 22
    f3()
  }
  console.log(a)
  a = 100
  f2()
}
f1() //1 22
```
