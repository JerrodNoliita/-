### [数组](https://github.com/qieguo2016/algorithm/blob/master/%E6%95%B0%E7%BB%84%E4%B8%8E%E9%93%BE%E8%A1%A8%EF%BC%8C%E5%A0%86%E6%A0%88%E4%B8%8E%E9%98%9F%E5%88%97.md#array)

计算机中的数组与数学中的数组概念类似，只是计算机中的数组的值可以是多种类型。 一般语言中的数组，指的都是连续线性表，由于数据保存在连续的内存块中、数组头保存了数组的地址，所以数据的定位是非常方便的。 根据数组地址+元素的偏移量算出指定元素的内存地址，直接移动指针到该处即可进行数据的读写。

但是由于数据存储的空间连续，所以对元素的增删就变得非常麻烦，比如要在第五位插入一个元素，那么第五位后面的所有元素都要向后挪一个数组空间的位置。 如果是删除元素，那么就需要将后面的元素依次向前挪一个位置。实际操作中我们还需要额外的临时空间来保存要移动的元素，然后依次移动各个元素，相当繁琐。

但js与传统数组不一样，js中的数据结构就只有一种：哈希表。哈希表用来描述Object，其他所有的数据结构，都是建立在哈希表上的伪结构。 js中的数组，其实就是key为index的对象，其底层也就是哈希表。 所以js中的数组并不储存在一片连续的存储空间里，因此数组的操作也跟传统的数组操作不一样。

> ES6中的typed Array和ArrayBuffer是存储连续内存的数组，与传统意义上的数组一样。

[![](https://github.com/qieguo2016/algorithm/raw/master/resource/Array001.png "数组插入动画")](https://github.com/qieguo2016/algorithm/blob/master/resource/Array001.png)

js中封装好的操作数组元素的方法有：

* push：向数组末尾添加
  **任意**
  个元素，@return 修改后的新数组长度
* pop：从数组末尾移除最后
  **一个**
  元素，@return 被移除的元素
* shift：从数组头部移除最前
  **一个**
  元素，@return 被移除的元素
* unshift：向数组头部添加
  **任意**
  个元素，@return 修改后的新数组长度
* splice：前2个参数为操作起始点和删除个数，第3个参数开始是插入的元素，@return 被删除项组成的数组
* sort和reverse：数组排序和反转，其中排序方法接受一个排序函数，可以自定义排序规则。例如：

```
array.sort(function (pre, next) {
   return pre - next; // 返回负数则pre在前，返回正数则pre在后 
});
```

注: 以上这些操作都是对数组元素的操作，是直接改变原数组的方法；以下方法不改变原数组，只返回新数组：

* concat：连接两个或者多个数组。
* slice：从当前数组中截取得到一个新数组。

还有一些比较实用的方法：

* forEach：对数组的所有元素都执行传入函数，无返回值
* map: 对数组的所有元素都执行传入函数，@return 函数返回值组成的数组，也就是数组映射
* filter：对数组的所有元素都执行传入函数，@return 函数返回值为真的元素组成的数组，也就是数组过滤
* every：对数组的所有元素都执行传入函数，@return 当所有元素的返回值都为真时，返回真。数组全体的与操作
* some：对数组的所有元素都执行传入函数，@return 当任一元素的返回值为真是，返回真。数组全体的或操作。 以上传入函数的参数均为 item、index、array，后两项为可选参数。例如平方映射函数：

```
array.map(function (item,index,array) {
  return item * item;
})
```

* reduce：从头到尾依次迭代，将每次迭代的结果作为输入与当前元素执行传入函数。
* reduceRight：从尾到头依次迭代，刚好与reduce相反。 例如一个数组求和：

```
array.reduce(function (prev,next,index,array) {
    return prev + next;
})
```



