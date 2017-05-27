# 对一个数组进行去除重复项


```javascript
var arr=[1,2,4,5,6,3,46,3,2,88];

function isInArray(val,arr){ //检测值是否存在于数组中
    for(var i in arr){
        if(arr[i]==val){
            return true
        }
    }
    return false
}
function removeItem(arr){
    var newArr=[];
    for(var i in arr){
        if(!isInArray(arr[i],newArr)){
            newArr.push(arr[i]) //push（）向数组追加一个元素 放在最后
        }
    }
    return newArr
}
console.log(removeItem(arr))

```