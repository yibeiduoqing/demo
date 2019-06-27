# 前端面试题
## 浏览器（HTTP与HTTPS）工作流程/渲染过程
A.基础知识：1.原型  原型链   2.作用域  闭包  3.异步 单线程
B. JS-API:   1. DOM操作   2.Ajax   3.时间绑定
C. 开发环境：  1.版本管理  2.模块化  3.打包工具
D. 运行环境：  1.页面渲染  2.性能优化
## 一.直入今天的主题：变量类型和计算
1. JS中使用typeof能得到那些类型？
2. 何时使用'==',何时使用'==='
3. JS中有哪些内置函数
4. JS变量按照存储方式分为哪些类型？并讲述其特点
5. 如何理解JSON你能答对几道题？
## 二.知识点梳理：变量类型    变量计算
1.变量类型：值类型引用类型
值类型举例：```js var a = 100;  var b = a; a = 200; console.log(b)    // 100```
引用类型举例```jsvar a = {age:50}; var b = a; b.age = 60; console.log(a.age)  //  60 ```
引用类型：对象、数组、函数，为了节约内存，多个变量共用一个内存块，声明的a和b就是指向同一个内存块的指针，所以console.log(a.age)  打印出来的是60，而不是50
2.typeof运算符
typeof undifined  //  undifined
typeof 'abc'  //  string
typeof 123  //  number
typeof true  //  boolean
typeof {}  //  boject
typeof []  //  boject
typeof null  //  boject    null就是一个不指向任何地方的空指针
typeof console.log()  //  function
规律:js中使用typeof能得到6种类型，typeof 值类型 分别是undifined string number boolean，typeof 引用类型 是boject function

3.变量计算-强制类型转换
3.1 字符串拼接
```js
var a = 100 + 10   //   110    
var a = 100 + '10' //   '10010'
```

3.2    ==运算符
100 == '100'            //    true
0 == ' '                //   true
null == undifined      //  true

3.3    if语句
var a = 100; if(a){ //   }

3.4    逻辑运算符
console.log（10 && 0）  //  0
console.log(' ' || ' abc')     //  'abc'    很实用的技巧  var a = 100;
console.log(!!a)    //  true

## 三.    解答开篇的面试题：
### 1.JS中使用typeof能得到那些类型？ 
js中使用typeof能得到6种类型，typeof 值类型 分别是undifined string number boolean，typeof 引用类型 是boject function，发现规律了吗？引用类型返回的都是object（函数不算，特殊

2.何时使用'==',何时使用'==='
if （obj.a == null）{//   这里相当于obj.a === null || obj.a === undifined   JQ推荐写法，其他情况的判断要用 ===  这样答题是不是NB了很多？}

3.JS中有哪些内置函数

Object    Array    Boolean    Number    String    Function Date RegExp    Error    (Math和JSON属于对象，不是函数)

4. JS量按照存储方式分为哪些类型？并讲述其特点值类型和引用类型，特点看上边

5. 如何理解JSONJSON不过是JS对象而已，同Math。JSON.stringify({a})   JSON.parse('{"a":10,"b":5}')
