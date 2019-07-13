##返回顶部
```js
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
  <style>
    body{
      margin: 0
    }
    ul{
      margin: 0;
    }
    .wrap-box {
      background: #cfc;
    }
    .wrap-box li {
      height: 30px;
      line-height: 30px;

    }
    .btn {
      position: fixed;
      bottom: 100px;
      right: 100px;
      width: 50px;
      height: 50px;
      border: 1px solid #000;
      background-color: #fff;
    }
  </style>
</head>
<body>
  <div id='btn' class='btn'>返回顶部</div>
  <ul id="wrap" class="wrap-box"></ul>
  <script>
    let wrap = document.querySelector("#wrap")
    for (var i = 0; i < 100; i++) {
      wrap.innerHTML = wrap.innerHTML+'<li>'+i+'</li>'
    }
    let btn = document.querySelector("#btn")
    btn.onclick = function () {
      topScroll = document.documentElement.scrollTop||document.body.scrollTop
      time = setInterval(function () {
        topScroll = topScroll - 50
        if (document.documentElement.scrollTop) {
          document.documentElement.scrollTop=topScroll
        }else {
          document.body.scrollTop = topScroll
        }
        if (topScroll<=0) {
          topScroll = 0
          clearInterval(time)
        }
      },20)
    }
  </script>
</body>
</html>
```
