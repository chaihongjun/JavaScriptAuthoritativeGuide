第7章 数组
JavaScript数组是无类型的，元素可以是任意类型

# 创建数组
```
var arr=[];
var a=new Array();

```
对于空缺的数组项，用`undefined`

# 数组元素的读和写
通过`[]`操作符来访问或者设置数组中的元素


# 稀疏数组
从索引位置0开始的不连续的数组

# 数组长度

设置数组长度将会改变数组的内容

# 数组元素的添加和删除
同过赋值表达式添加数组元素，或者使用`push()`方法在数组末尾添加元素，
可以使用`unshift()`在数组首部插入元素

通过`delete`删除数组元素，但不会影响数组的`length`,而且数组的其他元素不受影响

# 数组遍历
使用For循环遍历数组


# 多维数组

```
//创建多维数组
var table=new Array(10);
    for(var i=0;i<table.length;i++){
        table[i]=new Array(10);
}
//遍历初始化二位数组
for(var row=0;row<table.length;row++){
    for(var col=0;col<table[row].length;col++){
            table[row][col]=row*col;
   }
}

```


# 数组方法

## join()

`Array.join()` 将数组中所有元素转化为字符串并连接起来，默认使用逗号分隔各个数组元素
`String.split()` 是它的逆向操作

## reverse()

`Array.reverse()` 将数组中的元素顺序颠倒，返回逆序的数组

## sort()

`Array.sort()` 返回排序之后的数组。默认是以字母表顺序排序
如果按照其他方式非字母表排序，必须传入一个比较函数，这个函数决定了它的两个参数在排好的数值中的先后顺序，如果第一个参数在前面，则比较函数返回小于0的值，如果第一个函数在后面返回大于0的数值，如果两个参数相等，返回0：

```
var a=[33,4,1111,222];
a.sort();
a.sort(function(a,b){
    if(a>b) return 1;
    if(a<b) return -1;
    return 0;
})
```
## contact()
`Array.contact()` 相当于合并两个数组，但是不会做递归处理，不会影响原来两个数组，返回一个新的数组

## slice()

`Array.slice()` 返回指定数组的一个片段或子数组，不影响原来的数组，两个参数分别指定片段开始和结束的位置

**
返回的数组包含第一个参数指定的位置和所有但不含第二个参数指定的位置之间的所有数组元素。
如果只指定一个参数，则从指定位置开始一直到最后。
如果参数有负数，表示相当最后一个元素位置
**
```
var a=[1,2,3,4,5];
a.slice(0,3) // [1,2,3]
a.slice(3)  // [4,5]
a.slice(1,-1) //[2,3,4]
a.slice(-3,-2) //[3]
```

## splice()
`Array.splice()` 是在数组中插入或者删除元素的通用方法
**
第一参数指定了插入（或者删除）的起始位置。第二个参数指定了插入（或者删除）的元素个数。
如果第二个参数省略，则“一删到底”。从第三个参数开始指定的是需要插入的元素。`splice()` 会影响原数组，返回的是一个由删除元素组成的数组**

```
var a=[1,2,3,4,5,6,7,8];
a.splice(4) //从索引4开始删除到最后，返回[5,6,7,8] a是[1,2,3,4]
a.splice(1,2) //从索引1开始删除，一共删除2个元素，返回[2，3] a是[1,4]
a.splice(1,1) //从索引1开始删除一个元素 返回 [4] a是[1]
```

## push()和pop()

把数组当堆栈使用。`push()`在数组尾部添加元素，返回新数组的长度。`pop()`在数组尾部删除一个元素，并返回被删除的元素。数组的长度都会自动更新。

## unshift()和shift()
`unshift()`在数组头部添加元素并非返回数组新的长度，`shift()`在数组头部删除元素，并返回被删除的元素。数组的长度都会自动更新

## toString()和toLocaleString()
将数组元素转化为字符串并用逗号发分隔符串联起来，与不使用参数的`join()`的方法返回的字符串是一样的。

# ECMAScript5中的数组方法
大多数情况下，ECMAScript5中数组的的方法第一个参数接收函数，数组的每个元素调用一次函数。
这个函数接收三个参数：数组元素，索引和数组本身。

通常函数的第二和第三个参数可省略


## forEach()
从头到尾遍历数组，对每个数组元素指定函数，但没有发返回值。

```
array.forEach(callback(currentValue, index, array){
    //do something
}, this)

array.forEach(callback[, thisArg])
```
数组元素求和：
```
var data=[1,2,3,4,5];
var sum=0;
data.forEach(
    function(value){  //value指向当前的元素值
        sum+=value;
            }
);
```
## map()
将数组每个元素传递给指定的函数，并返回一个新数组，包含函数的返回值

```
var a=[1,2,3];
b=a.map(function(x){return x*x;});  //b是[1,4,9]
```

**`forEach()`和`map()`调用函数的方式是一样的，但是`map()`有返回值。**

## filter()
返回的是调用数组的一个子集。传递的函数用来逻辑判断，函数返回true或者false

```
var a=[5,4,3,2,1];
smallValues=a.filter(function(x){return x<3});  //[2,1]
everyother = a.filter(function(x,i){return i%2==0});  //[5,3,1]

```

**filter()会跳过稀疏数组中缺少的元素，map()则不会**
如果想压缩数组，清除掉undefined和null,可以这样:

```
a=[1,2,3,,,undefined];
a=a.filter(function(x){return x!==undefined && x!= null;});

```

##　every()和some()

`every()`和`some()` 是数组的逻辑判定，对数组元素应用指定的函数进行判定，返回true或者false.

`every()`当且仅当数组所有项调用函数都返回true，则方法才返回true
`some()`至少有一个数组项调用函数返回true，方法就返回true

```
a=[1,2,3,4,5];
a.every(function(x){return x<10;})  //返回true
a.every(function(x){return x%2===0;})  //false 

a.some(function(x){ x%2===0;})  //true
```


##　reduce()和reduceRight()
使用指定的函数将数组元素进行组合生成单个值。

`reduce()`方法需要两个参数，第一个参数是执行简化操作的函数，第二个参数是传递给函数的一个初始值

```
arr.reduce(callback[, initialValue])

arr.reduce(function(accumulator,currentValue,currentIndex,array){}[,initialValue])
```

```
var a=[1,2,3,4,5];
var sum=a.reduce(function(x,y){ return x+y},0); //0+1+2+3+4+5
```

`reduceRight()`工作原理和`reduce()`一样，只不过是按照数组索引从高到低处理


##　indexOf()和lastIndexOf()
搜索给定值的元素，返回第一个符合元素的索引，如果没找到则返回-1
indexOf()从头至尾搜索，lastIndexOf()则是反向搜索
第一个参数是要搜索的数组值，第二个参数可选是从哪个索引位置开始
```
arr.indexOf(searchElement)
arr.indexOf(searchElement[, fromIndex = 0])
```

# 数组类型
ECMAScript5判断是不是数组:
```
Array.isArray([])  //true
```



# 类数组对象
javascript数组独具的特征:
1. 数组元素更新，length自动更新
2. 设置较小的length,可以截断数组
3. 从Array.prototype继承一些方法
4. 属性是Array
