# 前端面试题
## 浏览器（HTTP与HTTPS）工作流程/渲染过程
+基础知识：1.原型  原型链   2.作用域  闭包  3.异步 单线程 +JS-API:   1. DOM操作   2.Ajax   3.时间绑定
+开发环境：  1.版本管理  2.模块化  3.打包工具
+运行环境：  1.页面渲染  2.性能优化
## 一.直入今天的主题：变量类型和计算

1.JS中使用typeof能得到那些类型？  2. 何时使用'==',何时使用'===' 3. JS中有哪些内置函数   4.JS变量按照存储方式分为哪些类型？并讲述其特点   5. 如何理解JSON你能答对几道题？

## 二.知识点梳理：变量类型    变量计算
1.变量类型：值类型引用类型 值类型举例：
```js
var a = 100;  var b = a; a = 200; console.log(b)    // 100
```

3.变量计算-强制类型转换 3.1 字符串拼接
```js
var a = 100 + 10   //   110    
var a = 100 + '10' //   '10010'
```

3.2    ==运算符 100 == '100'            //    true 0 == ' '                //   true null == undifined      //  true

3.3    if语句 var a = 100; if(a){ //   }

3.4    逻辑运算符 console.log（10 && 0）  //  0 console.log(' ' || ' abc')     //  'abc'    很实用的技巧  var a = 100; console.log(!!a)    //  true


## 三.解答开篇的面试题：

1. js中使用typeof能得到6种类型，typeof 值类型 分别是undifined string number boolean，typeof 引用类型 是boject function，发现规律了吗？引用类型返回的都是object（函数不算，特殊

2.何时使用'==',何时使用'===' if （obj.a == null）{//   这里相当于obj.a === null || obj.a === undifined   JQ推荐写法，其他情况的判断要用 ===  这样答题是不是NB了很多？}

3.JS中有哪些内置函数

Object    Array    Boolean    Number    String    Function Date RegExp    Error    (Math和JSON属于对象，不是函数)

4. JS量按照存储方式分为哪些类型？并讲述其特点值类型和引用类型，特点看上边

5. 如何理解JSONJSON不过是JS对象而已，同Math。JSON.stringify({a})   JSON.parse('{"a":10,"b":5}')












##一.加密/算法基本知识
非对称加密算法：RSA，DSA/DSS     需要两个密钥：公开密钥和私有密钥；公开密钥与私有密钥是一对。如果用公开密钥对数据进行加密，只有用对应的私有密钥才能解密；如果用私有密钥对数据进行加密，那么只有用对应的公开密钥才能解密。因为加密和解密使用的是两个不同的密钥，所以这种算法叫作非对称加密算法。主要是用来保护传输客户端生成的用于对称加密的随机数私钥
对称加密算法：AES，RC4，3DES，IDEA     特点是文件加密和解密使用相同的密钥加密；对称加密算法使用起来简单快捷，密钥较短，且破译困难。除了数据加密标准（DES），另一个对称密钥加密系统是国际数据加密算法（IDEA），它比DES的加密性好，而且对计算机功能要求也没有那么高。
HASH算法：BASE64、MD5、SHA、HMAC 是一种单向算法，用户可以通过hash算法对目标信息生成一段特定长度的唯一hash值，却不能通过这个hash值重新获得目标信息。因此Hash算法常用在不可还原的密码存储、信息完整性校验等。比如在确认握手消息没有被篡改时使用 ；
常用Java加密算法/HASH算法：

1.BASE64 （严格来说属于编码格式，而非加密算法）：是网络上最常见的用于传输8bit字节代码的编码方式之一。base64编码可用于在http环境下传递较长的标识信息，采用base64编码具有不可读性，即所编码的数据不会被人用肉眼所直接看到。

2.MD5(信息摘要算法)：用于确保信息传输完整一致，又名杂凑算法，摘要算法、哈希算法；将数据（如汉字）运算为另一固定长度值，是杂凑算法的基础原理。广泛用于加密和解密技术，常用于文件校验，不管文件多大，经过md5后都能生成唯一的MD5值。比如ISO校验，把ISO经过MD5后产生的MD5值，一般下载linux-ISO会看到下载链接旁边放着MD5的串，就是用来验证文件是否一致。

MD5算法具有以下特点：

1>压缩性：任意长度的数据，算出的MD5值长度都是固定的。
2>容易计算：从原数据计算出MD5值很容易。
3>抗修改性：对原数据进行任何改动，哪怕只修改1个字节，所得到的MD5值都有很大区别。
4>弱抗碰撞：已知原数据和其MD5值，想找到一个具有相同MD5值的数据（即伪造数据）是非常困难的。
5>强抗碰撞：想找到两个不同的数据，使它们具有相同的MD5值，是非常困难的。

3.SHA(安全散列算法)：主要适用于数字签名标准里面定义的数字签名算法。对于长度小于2^64位的消息，SHA1会产生一个160位的消息摘要。该算法的思想是接收一段明文，然后以一种不可逆的方式将它转换成一段（通常更小）密文，也可理解为取一串输入码，并把他们转为长度较短、位数固定的输出序列即散列值（也称为信息摘要或信息认证代码）的过程。散列函数值可以说是对明文的一种“指纹”或“摘要”所以对散列值的数字签名就可以视为对此明文的数字签名。

SHA-1与MD5的比较：二者均由MD4导出，SHA-1和MD5彼此很相似。但还有以下几点不同：

1>对强行攻击的安全性：最显著和最重要的区别是SHA-1摘要比MD5摘要长32 位。SHA-1对强行攻击有更大的强度。

2>对密码分析的安全性：由于MD5的设计，易受密码分析的攻击，SHA-1显得不易受这样的攻击。

3>速度：在相同的硬件上，SHA-1的运行速度比MD5慢。

4.HMAC(散列消息鉴别码)：基于密钥的Hash算法的认证协议，它实现的原理是，用公开函数和密钥产生一个固定长度的值作为认证标识，用这个标识鉴别消息的完整性。使用一个密钥生成一个固定大小的小数据块，即MAC，并将其加入到消息中，然后传出，接收方利用与发送方共享的密钥进行鉴别认证等。

## 前端面试题必考（六）- JS快速复习（面向对象/常用封装写法/闭包/继承）
一.描述面向对象/特点
1.面向对象由属性和方法组成，并有三个基本特征：

封装：只能通过对象来访问方法；
继承：从已有对象上继承出新的对象；JS不支持接口继承，实现继承的方式依靠原型链完成。
多态：多对象的不同形态；允许将子类类型的指针赋值给父类类型的指针。实现多态，有二种方式：覆盖，重载，接口。
*删除对象：JavaScript自己垃圾回收机制，就是自己在没有引用的时候释放内存(销毁)

var obj=new Object();
obj.name="haha";
alert(obj);//{name:"haha"}
//obj=null;
//obj={};
obj=new Object();
alert(obj);//{}
*删除对象属性：

var obj={name:"haha"};
delete obj.name;
alert(obj.name);//undefined
二.原型封装（js面向对象的几种常见写法，参考：https://www.cnblogs.com/leejersey/p/4205252.html，http://www.cnblogs.com/jnslove/p/7028487.html）
1>工厂模式

var Circle = function() {
   var obj = new Object();
   obj.PI = 3.14159;

   obj.area = function( r ) {
       return this.PI * r * r;
   }
   return obj;
}

var c = new Circle();
alert( c.area( 1.0 ) );
2>构造函数模式，与工厂模式的区别：没有显式的创建对象；直接将属性和方法赋给this对象；没有return语句

function CreatePerson(name){

    this.name = name;
    this.showName = function(){
        alert( this.name );
    };
}
var p1 = new CreatePerson('小明');
//p1.showName();
var p2 = new CreatePerson('小强');
//p2.showName();
alert( p1.showName == p2.showName );  //false  它们的值相同，地址不同
3>原型模式：原型（prototype），重写对象下面公用的属性或方法，让公用的属性或方法在内存中只存在一份（提高性能），也就是说所有在原型对象中创建的属性或方法都直接被所有对象实例共享。原型：类比css中的class；普通方法：类比css中的style

var arr = [1,2,3,4,5];
var arr2 = [2,2,2,2,2];
Array.prototype.sum = function(){//原型prototype : 要写在构造函数的下面
    var result = 0;
    for(var i=0;i<this.length;i++){
        result += this[i];
    }
    return result;
};
alert( arr.sum() );  //15
alert( arr2.sum() );  //10
注意：原型优先级，如果在实例中添加了一个属性，而该属性与实例原型中的一个属性同名，该属性将会屏蔽原型中的那个属性

例1：

var arr = [];
arr.number = 10;
Array.prototype.number = 20;
alert(arr.number);//10
例2：

Array.prototype.a=12;//原型属性
var arr=[1,2,3];
alert(arr.a);//12
arr.a=5;//实例属性
alert(arr.a);//5
3>工厂方式之原型

例1：

function Circle(r) {
      this.r = r;
}
Circle.PI = 3.14159;
Circle.prototype.area = function() {
  return Circle.PI * this.r * this.r;
}

var c = new Circle(1.0);   
alert(c.area());
例2：

var Circle=function(r){
        this.r=r;
}
Circle.PI = 3.14159;
Circle.prototype={
    area:function(){
        return this.r*this.r*Circle.PI;
    }
}
var obj=new Circle(1.0);
alert(obj.area())
例3：

function CreatePerson(name){//普通方法
this.name=name;
}
CreatePerson.prototype.showName=function(){//原型
alert(this.name);
}
var p1=new CreatePerson('小明');
p1.showName();
var p2=new CreatePerson('小强');
p2.showName();
alert( p1.showName== p2.showName);//true  
 

4>JSON写法

var Circle={
   "PI":3.14159,
 "area":function(r){
          return this.PI * r * r;
        }
};
alert( Circle.area(1.0) );
5>JSON写法的扩展小实例

var show={
        btn:$('.div1'),
        init:function(){
            var that=this;
            alert(this);
            this.btn.click(function(){
                    that.change();
                    alert(this);
                })

        },
        change:function(){
            this.btn.css({'background':'green'});

        }
}
show.init();
三.闭包（参考：https://www.cnblogs.com/yunfeifei/p/4019504.html）
Javascript允许使用内部函数---即函数定义和函数表达式位于另一个函数的函数体内。而且，这些内部函数可以访问它们所在的外部函数中声明的所有局部变量、参数和声明的其他内部函数。当其中一个这样的内部函数在包含它们的外部函数之外被调用时，就会形成闭包。

上述原型的例子写法都属于闭包，除此之外还有一种常见写法：

var Circle = new Function(
this.PI = 3.14159;
this.area = function( r ) {return r*r*this.PI;}
);  
alert( (new Circle()).area(1.0) );  
四.继承（参考：https://www.cnblogs.com/jingwhale/p/4678656.html）
在现代浏览器中可以使用 Object.create 实现继承。
ECMAScript 只支持继承，不支持接口实现，而实现继承的方式依靠原型链完成。
1.call+遍历

属性使用对象冒充（call）（实质上是改变了this指针的指向）继承基类，方法用遍历基类原型。可以实现多继承。

function A(){
    this.abc=12;
}
A.prototype.show=function (){
    alert(this.abc);
};
//继承A
function B(){
    //继承属性；this->new B()
    A.call(this);   //有参数可以传参数A.call(this,name,age)
}
//继承方法；B.prototype=A.prototype;
for(var i in A.prototype){
    B.prototype[i]=A.prototype[i];
}
//添加自己的方法
B.prototype.fn=function (){
    alert('abc');
};
var objB=new B();
var objA=new A();
objB.show();
2.寄生组合继承主要是Desk.prototype = new Box(); Desk 继承了Box，通过原型，形成链条。主要通过临时中转函数和寄生函数实现。

临时中转函数：基于已有的对象创建新对象，同时还不必因此创建自定义类型
寄生函数：目的是为了封装创建对象的过程
//临时中转函数
function obj(o) { //o表示将要传递进入的一个对象
    function F() {} //F构造是一个临时新建的对象，用来存储传递过来的对象
    F.prototype = o; //将o对象实例赋值给F构造的原型对象
    return new F(); //最后返回这个得到传递过来对象的对象实例
}
//寄生函数
function create(box, desk) {
    var f = obj(box.prototype);
    f.constructor = desk; //调整原型构造指针
    desk.prototype = f;
}
function Box(name) {
    this.name = name;
    this.arr = ['apple','pear','orange'];
}
Box.prototype.run = function () { return this.name; };
function Desk(name, age) {
    Box.call(this, name);
    this.age = age;
}
//通过寄生组合继承实现继承
create(Box, Desk);
//这句话用来替代Desk.prototype = new Box();
var desk = new Desk('Lee',100);
desk.arr.push('peach');
alert(desk.arr);
alert(desk.run());
临时中转函数和寄生函数主要做的工作流程：

临时中转函数：返回的是基类的实例对象函数
寄生函数：将返回的基类的实例对象函数的constructor指向派生类，派生类的prototype指向基类的实例对象函数（是一个函数原型），从而实现继承。
 
