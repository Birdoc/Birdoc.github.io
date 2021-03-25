---
title: "JS数组方法"
date: 2021-03-25T09:27:34+08:00
draft: false
---
pop/push,shift/unshift方法
作用于数组末端的方法
 push  在末端添加一个元素,并返回该元素
 pop  取出并返回数组的最后一个元素
作用于数组首端的方法
 shift  取出并返回数组的第一个元素
 unshift  在数组的首端添加元素
从数组中删除元素
splice
语法：
arr.splice(start[,deleteCount,elem1, ... , elemN])
从索引  start  开始修改  arr  ：删除  deleteCount  个元素并在当前位置插入  elem1, ... , elemN  ,最后返回修改后的数组
例子：
let arr = [1,2,3,4]
arr.splice(2,2,'a','b')
console.log(arr)
//[1,2,'a','b']
slice
语法:
arr.slice([start],[end])
它会返回一个新数组，将所有从索引 start 到 end (不包括 end )的数组项复制到这个新的数组。  
也可以不带参数调用它，通常用于获取副本，以进行不影响原始数组的操作。
concat
 arr.concat  创建一个新数组，其中包含来自于其他数组和其他项的值。
语法：
arr.concat(arg1,arg2...)
它接受任意数量的参数，如果参数  argN  是一个数组，那么其中所有元素都会被复制，否则将复制参数本身。
例如
let arr = [1,2];
console.log(arr.concat([3,4]));//1,2,3,4
console.log(arr.concat([3,4],5));//1,2,3,4,5
如果  argN  为对象，即使它们看起来像数组，仍会被当作整体添加。
但是，如果该对象具有  Symbol.isConcatSpreadable  属性，那么它就会被  concat 当作一个数组来处理。
循环
最古老的方法是  for  循环
let arr = [1,2,3,4]
for(let i = 0;i < arr.length; i++){
    console.log(arr[i])
}
//1,2,3,4
对于数组来说有另一种方式，  for .. of  
let arr2 = [1,2,3,4]
for(let num of arr2){
    console.log(num)
}
 for .. of  不能获取当前元素的索引，只能获取元素值，但大多数情况是够用的。
 forEach  方法允许为数组的每一个元素都运行一个函数
语法:
arr.forEach(function(item,index,array)){
    // ... do something with item            
}
//例如，展示元素在数组中的位置
let arr = ['first','second','third']
arr.forEach((item,index,array)=>{
    alert(`${item}在数组${array}中的下标是${index}`)
})
在数组中搜索
indexOf/lastIndexOf和includes
 arr.indexOf(item,from)  从索引  from  开始搜索  item  ，如果找到则返回索引，否则返回  -1  。
 arr.lastIndexOf(item,from)  与上面相同，只是从右向左搜索。
 arr.includes(item,from)  从索引  from  开始搜索  item  ，如果找到则返回  true  ，否则返回  false  。
find和findIndex
语法
let result = arr.find(function(item,index,array)){
    //如果返回true,则返回item并停止迭代
    //对于假值(flasy)的情况，则返回undefined
}
 arr.findIndex  方法与上面基本相同，但它返回找到元素的索引而非元素本身，并在为找到内容是返回  -1  
filter
语法
let result = arr.filter(function(item,index,array)){
    //如果true item 被push到results，迭代继续
    //如果什么都没找到则返回空数组
}
转换数组
map
 arr.map  对数组的每个元素都调用函数，并返回结果数组。
语法：
let result = arr.map(function(item,index,array)){
    //返回新值而不是当前元素
}
sort(fn)
 sort(fn)  返回修改后的数组，其返回值通常会被忽略，因为修改了原数组。
语法：