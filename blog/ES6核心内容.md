---
title: ES6/ES2015核心内容
date: 2017/1/11
tags:
- WEB
- ES6
---

### 最常用的ES6特性
目前浏览器还未全部兼容ES6,但是可以通过babel进行转义
- let,const
- class,extends,super
- arrow function
- template string
- destructuring
- default rest
- import export

### let const
- let 块级作用域,防止内层变量覆盖外层变量以及当计数时循环变量泄露为全局变量
```javascript
    //以前会发生的情况
    var name = 'xy';
    while(true){
        var name = 'xy';
        console.log(name);//'xy'
        break;
    }
    console.log(name); //'xy'
    //使用let
    let name = 'xy'
     
    while (true) {
        let name = 'xuyu'
        console.log(name)  //xuyu
        break
    }  
    console.log(name)  //xy
```
- const
```javascript
    //用来声明变量，但是声明的是常量。一旦声明，常量的值就不能改变。
    const PI = Math.PI
    PI = 23 //Module build failed: SyntaxError: /es6/app.js: "PI" is read-only
    //引用第三方库的时声明的变量，用const来声明可以避免未来不小心重命名而导致出现bug
    const monent = require('moment')
```
### class extends super
ES6的继承机制，实质是先创造父类的实例对象this（所以必须先调用super方法），然后再用子类的构造函数修改this
```javascript
class Animal { //class定义了一个“类
    constructor(){ //constructor方法，这就是构造方法
        this.type = 'animal' //this关键字则代表实例对象
    }
    
    says(say){
        console.log(this.type + ' says ' + say)
    }
}
 // constructor内定义的方法和属性是实例对象自己的，而constructor外定义的方法和属性则是所有实例对象可以共享的

let animal = new Animal()
animal.says('hello') //animal says hello
 
class Cat extends Animal { //Class之间可以通过extends关键字实现继承
    constructor(){
        super() //super关键字，它指代父类的实例（即父类的this对象）
        this.type = 'cat'
    }
}
 //子类没有自己的this对象，而是继承父类的this对象，然后对其进行加工。如果不调用super方法，子类就得不到this对象
let cat = new Cat()
cat.says('hello') //cat says hello
```

### 箭头函数(arrow function)
当我们使用箭头函数时，函数体内的this对象，就是定义时所在的对象，而不是使用时所在的对象。并不是因为箭头函数内部有绑定this的机制，实际原因是箭头函数根本没有自己的this，它的this是继承外面的，因此内部的this就是外层代码块的this。
```javascript
function(i){ return i + 1; } //ES5
(i) => i + 1 //ES6

class Animal {
    constructor(){
        this.type = 'animal'
    }
    says(say){
        
        setTimeout(function(){
            console.log(this.type + ' says ' + say)
        }, 1000)
    }
}
 
 var animal = new Animal()
 animal.says('hi')//undefined says hi
 //bind
 setTimeout(function(){ //setTimeout是全局函数,里面的this是全局的
             console.log(this.type + ' says ' + say)
         }.bind(this), 1000)
  //that
  setTimeout(function(){
      var that=this
              console.log(that.type + ' says ' + say)
          }, 1000)
  //=>
  setTimeout( ()=>{
       console.log(this.type + ' says ' + say)
          }, 1000)
```
### template string
用反引号（\）来标识起始，用${}`来引用变量
```
//old
$("#result").append(
  "There are <b>" + basket.count + "</b> " +
  "items in your basket, " +
  "<em>" + basket.onSale +
  "</em> are on sale!"
);
//now
$("#result").append(`
  There are <b>${basket.count}</b> items
   in your basket, <em>${basket.onSale}</em>
  are on sale!
`);
```

### destructuring
按照一定模式，从数组和对象中提取值，对变量进行赋值，这被称为解构（Destructuring）。
```
//old
let cat = 'ken'
let dog = 'lili'
let zoo = {cat: cat, dog: dog}
console.log(zoo)  //Object {cat: "ken", dog: "lili"}
//now
let cat = 'ken'
let dog = 'lili'
let zoo = {cat, dog}
console.log(zoo)  //Object {cat: "ken", dog: "lili"}
```
### default rest
```
//old
function animal(type){
    type = type || 'cat'  
    console.log(type)
}
animal()
//now
function animal(type = 'cat'){
    console.log(type)
}
animal()

//rest
function animals(...types){
    console.log(types)
}
animals('cat', 'dog', 'fish') //["cat", "dog", "fish"]
//否则用arguments
```