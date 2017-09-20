## Front-end JavaScript Interview Q/A

* Explain event delegation
  * 将事件绑定在父/祖节点上，避免在每个子节点上绑定相同的事件
* Explain how `this` works in JavaScript
  * 非严格模式直接调用函数`this`会指向window(browser)，global(node) 严格模式`undefined`
  * 使用`new`关键字 `this`指向实例
  * 调用对象的方法`this`指向对象本身
* Explain how prototypal inheritance works
  * 访问对象的属性先从`this`中查找，如果找不到开始从原型链中查找，原型链以当前对象的构造函数的原型对象开始以
    `Object.prototype`结束。
    * `this.constructor.prototype === this.__proto__ //true`
* What do you think of AMD vs CommonJS?
  * 二者都是为了解决JavaScript模块话而产生，AMD多用于前端，CommonJS是NodeJS的模块化标准，AMD是异步加载依赖，CommonJS为同步加载。CMD，UMD的出现同一了二者。
* Explain why the following doesn't work as an IIFE: `function foo(){ }();`.
  * 编译器识别到以`function`开始的语句认为只是一条函数声明，而函数声明不可以`)`结束。
  * What needs to be changed to properly make it an IIFE?
    * 将函数声明改成函数表达式 `(function(){})()`
* What's the difference between a variable that is: `null`, `undefined` or undeclared?
  * `null` 代表空值
  * `undefined` 代表声明了而未定义
  * How would you go about checking for any of these states?
    * `typeof` 
    * `undefined == null //true`
    * `undefined === null false`
* What is a closure, and how/why would you use one?
  * 利用作用域特性在函数内部定义函数并返回，使得返回的函数能访问内部私有作用域，而外部无法访问内部。
    * 命名空间
    * 变量私有化
* What's a typical use case for anonymous functions?
  * addEventListener
  * map/forEach...
* How do you organize your code? (module pattern, classical inheritance?)
  * 按职责划分module，以方法抽象class
* What's the difference between host objects and native objects?
  * ECMA-262的所有内置对象都是本地对象 Array, Object...
  * 非内置对象都是宿主对象 DOM, BOM...
* Difference between: `function Person(){}`, `var person = Person()`, and `var person = new Person()`?
  * 函数声明
  * 函数调用
  * 实例化
* What's the difference between `.call` and `.apply`?
  * `apply`第二个参数是数组
  * `call`参数以逗号分隔
* Explain `Function.prototype.bind`.
  * 改变函数上下文 对`()=>{}`无效
* When would you use `document.write()`?
* What's the difference between feature detection, feature inference, and using the UA string?
* Explain Ajax in as much detail as possible.
* What are the advantages and disadvantages of using Ajax?
* Explain how JSONP works (and how it's not really Ajax).
  * 利用`script`标签可加载跨域资源特性，用src访问资源返回可执行函数以数据作为参数运行
* Have you ever used JavaScript templating?
  * If so, what libraries have you used?
* Explain "hoisting".
  * `var x = 1`;
  * 等同于 `var x`
  * `x = 1`
  * 声明式函数可先调用后声明
* Describe event bubbling.
  * 捕捉自上而下
  * 冒泡自下而上
* What's the difference between an "attribute" and a "property"?
  * attribute需要使用set/get获取 与`prototype`类似
  * property用`.`获取即可 与`this`类似
* Why is extending built-in JavaScript objects not a good idea?
  * 由于原型链的存在直接修改内置对象会污染所有的派生对象
* Difference between document load event and document DOMContentLoaded event?
  * onLoad 所有资源记载完被调用
  * DOMContentLoaded DOM树构建完成时调用
* What is the difference between `==` and `===`?
  * `==` 不检测类型
* Explain the same-origin policy with regards to JavaScript.
  * cookie
  * storages
  * ajax
* Make this work:
```javascript
duplicate([1,2,3,4,5]); // [1,2,3,4,5,1,2,3,4,5]
```
```javascript
  function duplicate(arr: any[]){
    return arr.concat(arr);
  }
```
* Why is it called a Ternary expression, what does the word "Ternary" indicate?
* What is `"use strict";`? what are the advantages and disadvantages to using it?
  * 开启严格模式js引擎不会进行类型转换
* Create a for loop that iterates up to `100` while outputting **"fizz"** at multiples of `3`, **"buzz"** at multiples of `5` and **"fizzbuzz"** at multiples of `3` and `5`

```javascript
let i = 0;
while(++i <= 100){
  let str = "";
  if ( i % 3 ) { str += "fizz"; }
  if ( i % 5 ) { str += "buzz"; }
  console.log(str);
}
```
* Why is it, in general, a good idea to leave the global scope of a website as-is and never touch it?
  * 所有的对象都挂载在window下，修改可能会影响浏览器本身或者其他框架
* Why would you use something like the `load` event? Does this event have disadvantages? Do you know any alternatives, and why would you use those?
* Explain what a single page app is and how to make one SEO-friendly.
* What is the extent of your experience with Promises and/or their polyfills?
* What are the pros and cons of using Promises instead of callbacks?
* What are some of the advantages/disadvantages of writing JavaScript code in a language that compiles to JavaScript?
* What tools and techniques do you use debugging JavaScript code?
* What language constructions do you use for iterating over object properties and array items?
* Explain the difference between mutable and immutable objects.
  * What is an example of an immutable object in JavaScript?
  * What are the pros and cons of immutability?
  * How can you achieve immutability in your own code?
* Explain the difference between synchronous and asynchronous functions.
* What is event loop?
  * What is the difference between call stack and task queue?
* Explain the differences on the usage of `foo` between `function foo() {}` and `var foo = function() {}`