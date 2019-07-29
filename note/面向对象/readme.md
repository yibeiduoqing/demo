# 面向对象
## 工厂模式
```js
	function people(name,age) {
		let obj={}
		obj.name = name;
		obj.age = age;
		obj.hh = function () {
			if (age>20) {
				console.log("老人");
			}else {
				console.log("青年");
			};
		};
		return obj
	}
	var p = people("黎明",23);
	p.hh();//老人

```
## 构造函数
```js
  function people(name,age) {
    this.name = name;
    this.age = age;
    this.item = function () {
			if (age>20) {
				console.log("老人");
			}else {
				console.log("青年");
			};
		};
  }
  var p = new people("黎明",23)
  p.item()
  ```

## 原型模式
构造函数 prototype

## 混合模式
```js
function someone(name,age) {
  this.name = name
  this.age = age
};
someone.prototype.showInfo = function(){
  console.log(this.name+this.age)
};
let sss = new someone("肖战",22);
sss.showInfo()
