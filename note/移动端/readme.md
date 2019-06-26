# 左滑动出现菜单栏
```js
<style>
html, body {
  height: 100%;
}
.wrap {
  /*position: relative;*/
  height: 100%;
  background: #000;
  color: #fff;
  font-size: 30px;
}
.box {
  position: absolute;
  left: -100px;
  width: 100px;
  height: 100%;
  background: #f00;
}
</style>
<body>
<div class="wrap" id="wrap">
  <div class="box" id="box"></div>
</div>
<script type="text/javascript" src="js/zepto.min.js"></script>
<script type="text/javascript" src="js/zepto-master/src/touch.js"></script>
<script>
var btn = document.getElementById('wrap');
var box = document.getElementById('box');
var disS = 0;
var disE = 0;
btn.addEventListener("touchstart", function(event) {
  // event.preventDefault();
  if (event.touches.length == 1) {
    disS = event.touches[0].clientX;
  };
}, false);
btn.addEventListener("touchmove", function(event) {
    if (event.touches.length == 1) {
      disE = event.touches[0].clientX;
  };
}, false);
btn.addEventListener("touchend", function(event) {
  // event.preventDefault();
  var res = disE - disS;
  console.log(res)
  if (res >= 100 ) {
    console.log('a')
    box.style.left = "0px";
    btn.style.marginLeft = "100px";
  } else {
    box.style.left = "-100px";
    btn.style.marginLeft = "0px";
  };
}, false);
</script>
```
