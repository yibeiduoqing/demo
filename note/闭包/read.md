# 实际开发中闭包的使用
1.主要用于 封装变量  收敛权限
2.用在循环中
 函数作为返回值||作为参数传递
 举例
 ```js
 function F1() {
   var a=1
   return function () {
     console.log(a);
   }
  }
  var f1 = F1()
  var a = 10
  f1()
```

## 例子
 创建 10 个<a>标签，点击的时候弹出来对应的序号
 错误的写法
 ```js
 var i, a
for (i = 0; i < 10; i++) {
    a = document.createElement('a')
    a.innerHTML = i + '<br>'
    a.addEventListener('click', function (e) {
        e.preventDefault()
        alert(i)
    })
    document.body.appendChild(a)
}
```

正确
```js
var i
for (i = 0; i < 10; i++) {
    (function (i) {
        var a = document.createElement('a')
        a.innerHTML = i + '<br>'
        a.addEventListener('click', function (e) {
            e.preventDefault()
            alert(i)
        })
        document.body.appendChild(a)
    })(i)
}
```
或者改为let
```js
for (let i = 0; i < 10; i++) {
    a = document.createElement('a')
    a.innerHTML = i + '<br>'
    a.addEventListener('click', function (e) {
        e.preventDefault()
        alert(i)
    })
    document.body.appendChild(a)
}
```
