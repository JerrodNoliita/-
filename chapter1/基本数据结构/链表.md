### Chain

因为传统数组的存储空间都是连续的，元素的增删操作非常麻烦，所以链表这种数据结构就被设计出来了。 链表元素的存储空间都是分散的，每个元素除了保存本身的值之外，还保存着其他元素的内存地址，根据地址就可以将整个链表串起来了。 根据这个特点，只要我们改写一个元素指向的内存地址指向一个新的链表元素，然后设置新的链表元素指向原来元素指向的地址，就插入了一个链表元素。 由于链表的所有元素的实际内存地址并不连续，所以也就不必像定义数组一样声明其存储空间了，换言之链表占用的是动态空间。

[![](https://github.com/qieguo2016/algorithm/raw/master/resource/Chain001.jpg "链表插入动画")](https://github.com/qieguo2016/algorithm/blob/master/resource/Chain001.jpg)

js中数组本身就不是连续的，所以在js中直接使用数组即可，没必要使用链表结构。

为了加深理解，这里也给出一个在js中通过对象来模拟链表结构的写法，更多方法参考[chain.js](https://github.com/qieguo2016/algorithm/blob/master/chain.js)文件。

```js
function Chain(key, value) {
    this.next = null;
    this.key = key;
    this.value = value;
    this.length = 1;
}

// 插入元素
Chain.prototype.insertAfter = function (pos, key, value) {
    var currentObj = this;
    var addObj = {
        key  : key,
        value: value
    }
    while (currentObj.key !== pos) {
        currentObj = currentObj.next;
    }
    addObj.next = currentObj.next;
    currentObj.next = addObj;
    this.length++;
    return this;
}

// 删除元素
Chain.prototype.delele = function (key) {
    var last = null;
    var currentObj = this;
    while (currentObj.key !== key) {
        last = currentObj;
        currentObj = currentObj.next;
    }
    last.next = currentObj.next;
    this.length--;
    return this;
}

// 查找元素
Chain.prototype.find = function (key) {
    var currentObj = this;
    while (currentObj.key !== key) {
        currentObj = currentObj.next;
    }
    return currentObj.value;
}
```

以上所说的都是单向链表，根据上述原理双向链表也很容易实现，这里就不再赘述了。

