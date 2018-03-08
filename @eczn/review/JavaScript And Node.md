
# String Object Array Number 上的常用方法 

总之很多很多。。 需要积累，去mdn上看 

[JavaScript 标准库一览](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects)


# 词法作用域 

var, function, let, const 

变量提升，作用域链，变量如何查找

# 函数和闭包

函数也是一类对象，是一等公民，是可以被调用的对象，其构成是：函数声明和函数体。 

闭包是这样的一个三元组：函数体、函数声明、函数所能访问的各种变量的集合。 

换言之，一等公民函数 + 词法作用域会产生闭包这种现象。 

JS 里的每一个函数，从技术的角度上来说，都是闭包（静态的函数有函数体和函数声明，动态的函数有作用域，因此构成了闭包）。 

# 对象和原型继承 

。。。。 变量如何查找 (原型链)

new 的那几步是怎样的: 

1. 创建一个对象 o 
2. 给对象 o 绑定原型 
3. 函数执行的 this 指向到 o 
4. 执行代码 
5. 返回 o 

# Promise 

Promise 实现了对异步的抽象。 async / await 基于它和 generator 实现

关于异步，详见 `./异步问题.md`


# 字面量解构、rest / spread 

``` js 
let { a } = { a: '123' }; 
// a = '123' 

let arr = [1, 2, 3]; 

console.log(...arr); 
// => console.log(1, 2, 3)

let sum = ...args => args.reduce((sum, c) => sum + c);

sum(1, 2, 3); 
// => 1 + 2 + 3 = 6 
```

# 数组、队列、链表、堆、二叉树、哈希表

Array.prototype 上面就可以完成数组和队列的设计。 

对象本身就是一类哈希表。 

链表的实现：-> 参阅我博客的 《变量、函数、调用》 的中间关于词法作用域的实现 

二叉树：可以看看 DOM 的结构，它是广义的树，更为普适，掌握了它二叉树也能轻易写出。 

堆：比较复杂的二叉树，一句话：完全二叉树

# EventEmmiter 

实现了对事件监听、触发、管理的抽象，通常使用方法是继承它。 

自己实现一个看看。 

# Koa & Express 

Koa 。。。 嗯。。 

Express 。。。 嗯。。

难讲。。 Koa 实现了异步的洋葱模型，使得原本的问题变简单了。 

Express 的中间件虽然直观，但是大型化之后会变复杂，可控性降低。 


# node 常用模块 

Node 采用的是 CommonJS 的模块加载机制。 

以下是我常用的

1. path: 路径相关 
2. http: 服务器相关 
3. fs: 文件io 
4. Buffer: Buffer 对象 
5. chokidar: 监听文件系统改动，比原生的 fs.watch 厉害 
6. commander: 命令行程序框架 
7. gulp / webpack 这些构建工具 

等等等等。。 

