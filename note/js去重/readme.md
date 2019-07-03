# js去重
##1.遍历数组法
实现思路：新建一个数组，遍历去要重的数组，当值不在新数组的时候（indexOf为-1）就加入该新数组中；
```js
var arr=[2,8,5,0,5,2,6,7,2];
function unique1(arr){
  var hash=[];
  for (var i = 0; i < arr.length; i++) {
     if(hash.indexOf(arr[i])==-1){
      hash.push(arr[i]);
     }
  }
  return hash;
}
```

## 2排序比较法（巧妙转换）
```js
function sortarr(arr){
    var arrsort=arr.sort();//对原数组进行排序
    var newarr=[];//新建空数组
    newarr.push(arrsort[0]);//将排序后数值的第一项给添加到新数组
    for(var i=1;i<arrsort.length;i++){//遍历排序后的数组
        if(arrsort[i]!==newarr[newarr.length-1]){newarr.push(arrsort[i])}//若当前项与新数组最后一项不同，这添加到新数组
    }
    return newarr;//返回新数组
}```
