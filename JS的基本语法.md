## 什么是表达式和语句
语句：
JavaScript 程序的执行单位为行（line），也就是一行一行地执行。一般情况下，每一行就是一个语句。

语句（statement）是为了完成某种任务而进行的操作，比如下面就是一行赋值语句。
```JavaScript
var a = 1 + 3;
```
这条语句先用var命令，声明了变量a，然后将1 + 3的运算结果赋值给变量a。
<br>
表达式：
1 + 3叫做表达式（expression），指一个为了得到返回值的计算式。此表达式的值是4；
<br>
add(1,2)表达式的值是函数的返回值
<br>
两者的区别：
1. 表达式一般有值，语句可能有，可能没有；
2. 语句一般会改变环境（声明/赋值）
3. 上面两句话不是绝对的
<br>

## 面试常考点：
下述表达式的值是？ undefined;
```JavaScript
console.log(3)
```
<br>

## 标识符的规则
标识符命名规则如下：

* 第一个字符，可以是任意 Unicode 字母（包括英文字母和其他语言的字母），以及美元符号（$）和下划线（_）。
* 第二个字符及后面的字符，除了 Unicode 字母、美元符号和下划线，还可以用数字0-9。
```JavaScript
var 临时变量 = 1; //中文是合法的标识符，可以用作变量名。
```
* JavaScript 有一些保留字，不能用作标识符：arguments、break、case、catch、class、const、continue、debugger、default、delete、do、else、enum、eval、export、extends、false、finally、for、function、if、implements、import、in、instanceof、interface、let、new、null、package、private、protected、public、return、static、super、switch、this、throw、true、try、typeof、var、void、while、with、yield。
* 大小写敏感 var a =1和var A=1 是不同的
* 大部分空格是无实际意义的，但是有一个特例：
## 这是面试考点，只有一个地方不能加回车，就是return后面
```JavaScript
function fn(){
    return 3
}
fn() //3

function fn(){
    return
    3
}
fn() //undefined
```
<br>

## if else 语句
* if(表达式){语句1}else{语句2}
* {}在语句只有一句的时候可以省略，不过不建议
```JavaScript
var a=2;
if（a=1）{
    console.log('1')
}else{
    console.log('2')
}
最终输出的是1，因为a=1,的意思是把a赋值为1

正确的写法应该是：
var a=2;
if（a===1）{
    console.log('1')
}else{
    console.log('2')
}
那么最终输出的才会是2
```
## 面试考点：
```JavaScript
var a=1;
if(a===2)
    console.log('a');
    console.log('a=2')
    //结果console.log打出的是’a=2‘
因为前面说到当{}里面内容只有一句是可以省略，所以代码实际是
var a=1;
if(a===2){
    console.log('a');
}
console.log('a=2')
```
```JavaScript
var a=1;
if(a===2)
    console.log('a'),console.log('a=2');
    //什么都不会打印出来，因为，代表还没有结束这句话，所以上面的其实是一句话。完整表达式是下面
var a=1;
if(a===2){
    console.log('a')，console.log('a=2')
}else{}


```

##  switch 语句
   switch语句
```JavaScript
  switch (fruit) {
  case 1:
    // 执行语句
    break;
  case 2:
    // 执行语句
    break;
  default:
    // 当参数不是case1和case2时，执行的代码，执行完后退出switch
}
```
## 问号冒号表达式
```JavaScript
function max(a,b){
    return a>b? a:b
    //如果a>b为true，则返回a；false则返回b
}

他等于下面代码的简洁模式:
function max(a,b){
    if(a>b){
        return a;
    }else{
        return b;
    }
```

## &&短路逻辑
* && 的判断是如果左边的表达式值为 false，那么就不会再执行右边的表达式了，如果左表达式为 true，就会继续执行右表达式，直到最后一个表达式。
* 所以结论是：A&&B&&C&&D 会取第一个假值或者最后一个表达式D的值
 ```JavaScript
 fn()&&fn()
 //如果fn函数存在，则调用fn()
 ```

## ||短路逻辑
* || 的判断是如果左表达式值为 true，那么就不用执行右边的表达式了，如果左表达式为 false，就会继续执行右表达式，直到最后一个表达式。
* 所以结论是：A||B||C||D 会取第一个真值或者最后一个表达式D的值
```JavaScript
a= a ||100
//如果a存在，则a=a,如果不存在则a=100，赋予a一个保底值
```

## while语句
while(表达式){语句}
```JavaScript
var i=0; //初始化
while(i<10){ //判断
    console.log(i) //循环体
    i=i+1 //增长
}
//会打印出0~9
```
需要注意的是，如果while却一部分都会导致死循环
下面是会导致死循环的特列
```JavaScript
var a=0.1;
while(a!===1){
    console.log(a);
    a=a+0.1
}
这里会死循环，因为小数点是不准确的，本来在第十次的时候a应该等于1，但是并不会真的等于1，所以永远都不会等于1的时候，就会死循环
```
## for循环
```JavaScript
for(语句1（初始化）；表达式2（判断）；语句3（增长）){
    循环体
}
```
1. 先执行语句1
2. 然后判断表达式2
3. ## 重点：如果为真，先执行循环体，然后再执行语句3
4. 如果为假，直接退出循环，执行外面的语句

```JavaScript
for(var i =0; i<5; i++){
    console.log(i)
}
/*最终输出值为0 1 2 3 4； 但是i=5;
因为先执行了console.log(i)，再执行i++ */
```

## 陷阱：
```JavaScript
for(var i =0; i<5; i++){
    setTimeout()=>{
        console.log(i)
    }
}
//最终输出为打印了5次5
//因为setTimeout()是延迟执行的意思，所以会等for循环全部循环完后再执行，这个时候i=5;所以打印了5次5

for(let i =0; i<5; i++){
    setTimeout()=>{
        console.log(i)
    }
}
//for循环在let的时候会有特例，这个时候输出的是0~4
```

## break continue
break是退出所有的循环
```JavaScript
for(var i =0; i<5; i++){
    if（i%2===1）{
        break
    }
}
// i=1 如果是单数就退出循环，所以当第一个单数1出现的时候就退出循环了
```

* break只退出离他最近的for循环
  ```JavaScript
  for(var i =0; i<10; i++){
      for(var j =100; j<110; j++){
          if(i===5){
              break;
          }
      }
    }
    console.log(i) //10
    //不是到5停止的原因是，break只退出离他最近的for循环
<br>
continue是退出当前一次循环

```JavaScript
for(var i =0; i<5; i++){
    if（i%2===1）{
        continue
    }
}else{
    console.log(i)
}
//打印了0 2 4；
```

## label标签

JavaScript 语言允许，语句的前面有标签（label），相当于定位符，用于跳转到程序的任意位置，标签的格式如下。


```JavaScript
label:
  语句
```

* *标签通常与break语句和continue语句配合使用，跳出特定的循环。
```JavaScript
top:
  for (var i = 0; i < 3; i++){
    for (var j = 0; j < 3; j++){
      if (i === 1 && j === 1) break top;
      console.log('i=' + i + ', j=' + j);
    }
  }
```
上面代码为一个双重循环区块，break命令后面加上了top标签（注意，top不用加引号），满足条件时，直接跳出双层循环。如果break语句后面不使用标签，则只能跳出内层循环，进入下一次的外层循环。

* continue语句也可以与标签配合使用。
```JavaScript
top:
  for (var i = 0; i < 3; i++){
    for (var j = 0; j < 3; j++){
      if (i === 1 && j === 1) continue top;
      console.log('i=' + i + ', j=' + j);
    }
  }
```
上面代码中，continue命令后面有一个标签名，满足条件时，会跳过当前循环，直接进入下一轮外层循环。如果continue语句后面不使用标签，则只能进入下一轮的内层循环。

## 面试考点
{foo:1}这是什么？
<br>
答：这不是对象，这是一个标签label，内容是1；
var a = {foo:1}才是对象
