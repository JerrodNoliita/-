# 原生编写一个方法，通过className获取元素

```javascript
// 例：<div class="list"></div>
var $={
byId:function(id){
return typeof id==='string'document.getElementsById(id):id;
},
byClass:function(cls,parent){
parent=parent?this.byId(parent):document;
var eles=document.getElementsByTagName("*");
var arr=[];
for(var i=0,len=eles.length;i<len;i++){
// 匹配空格list list list空格,当正则表达式中包含变量时，必须使用new RegExp 不能用//定界符 
if(eles[i].className.match(new RegExp('(^| )'+cls+'( |$)'))){
arr.push(eles[i])
}
}
return arr;
}
}
console.log($.byClass("list"))
```