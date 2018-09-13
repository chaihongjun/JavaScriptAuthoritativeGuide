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
Array.join() 将数组中所有元素都
