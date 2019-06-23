#原型链
三种方式

1、简单继承
2、借用构造函数继承
3、组合模式的继承

简单继承
```js
// 父类
 function Parent() {
   this.name = "123";
   this.friends = ["11", "22"];
 }
 Parent.prototype.showInfo = function() {
   console.log('parent:', this.friends);
 }
 // 子类
 function Son(age) {
   this.age = age;
 }
 // 继承
 // 子级的原型对象被父级的实例覆盖
 Son.prototype = new Parent();
 Son.prototype.showInfo = function() {
   console.log('son:', this.friends);
   console.log('age:', this.age)
 }
 //查找自己,往上以及查找原型对象，依次类推（作用域链一样）
 var demo1 = new Son(22);
 var demo2 = new Son(23);
 demo1.friends.push("33");
 console.log(demo1.showInfo == demo2.showInfo);
 demo1.showInfo();
 demo2.showInfo();
 ```
