第3章 类型、值和变量

# 数字
JavaScript 不区分整数和浮点数，所有数字都是用浮点数表示。JavaScript实际操作基于32位整数。

## 整形直接量
用一个数字序列表示一个十进制整数


## 浮点型直接量
语法表示:
```
[digits][.digits][(E|e)[(+|-)]digits]
```
比如:

```
3.14
2345.789
.3333
6.02e56
1.478785E-32
```


## JavaScript 中的算术运算
JavaScript运算结果超过了JavaScript能表示的数字上限就`溢出(overflow)`，结果是`无穷大`,用`Infinity`表示，如果是负数无穷大，则是`-Infinity`

JavaScript运算结果无限接近零并比JavaScript能表示的最小值还小的时候发生`下溢(underflow)`，这个时候返回0


##　二进制浮点数和四舍五入错误

```
var x=3.5-3.1;
var y=4.6-4.2;
x==y //false
x // 0.3999999999999999
y // 0.39999999999999947
```

## 日期和时间
Date()构造函数用来创建表示日期和时间的对象


# 文本
字符串是由一组16位值组成的不可变的有序序列。字符串长度就是16位值的个数。

## 字符串直接量
由双引号/单引号括起来的字符序列
ECMAScript3中，字符串必须写在一行中，ECMAScript5中可以拆分成多行，但是每行必须是反斜线(`\`)结束。


## 转义字符
字符串中反斜线(`\`)有特殊作用，反斜线后面加一个字符不再表示字符的字面意思


>`You\'re right,it can\'t be a quote'


JavaScript转义字符

| 转义字符 | 含义 |
| :-: | :-: |
| \o | Nul字符 |
| \b | 退格符 |
| \t | 水平制表符 |
| \n | 换行符 |
| \v | 垂直制表符 |
| \f | 换页符 |
| \r | 回车符 |
| \ " | 双引号 |
| \ ' | 单引号 |
| \ \ | 反斜线 |
| \xXX | 由两位十六进制数XX指定的Latin-1字符 |
| \uXXXX | 由四位十六进制数XXXX指定的Unicode字符|

##　字符串的使用
加号(`+`)用在两个字符串之间，表示将两个字符串拼接在一起。

获得字符串string的长度:

```
string.length
```

**JavaScript中字符串是固定不变的。**
在ECMAScript5中，字符串可以当作只读数组，通过`charAt()`方法，可以访问字符串中的单个字符


## 模式匹配
JavaScript定义构造函数`RegExp()`来创建表示文本匹配模式的对象，这些模式就是正则表达式


# 布尔值
指代真假，是否，开关

# null和undefined

```
typeof null //"object"
typeof undefined //"undefined"
```

如果想赋值给变量或者属性，或者作为参数传入函数，最佳选择是null

# 全局对象
全局对象是全局定义的符号，JavaScript程序可以直接使用。包含以下初始属性:

全局属性，比如`undefined` `Infinity`和`NaN`

全局函数，比如`isNaN()` `parseInt()` `eval()`

构造函数，比如`Date()` `RegExp()` `String()` `Object()` `Array()`

全局对象，比如`Math`和`JSON`

对于客户端JavaScript，Window对象定义了额外的全局属性。

在代码最顶层，不在任何函数内，可以使用关键字`this`指代全局对象。
对于浏览器客户端，Window对象充当了全局对象，Window对象的一个属性Window引用其自身，可以代替this引用全局对象

# 包装对象
JavaScript对象是一种复合值，是属性或已命名值的集合，通过点"`.`"符号来引用属性值。

String(),Number(),Boolean() 临时创建一个对象，让这个对象拥有对应的属性，但是这个对象是临时的，最后会被销毁。


# 不可变的原始值和可变的对象引用
JavaScript的原始值(`undefined` `null` `布尔值` `数字`和`字符串`)是不可改变的。
原始值是值的比较。

JavaScript的对象(包括`数组`和`函数`)是可变的，对象的比较不是值的比较。


# 类型转换

|值 | 转换为字符串 | 转换为数字 | 转换为布尔值 | 转换为对象 |
| :-: | :-: | :-: | :-: | :-: |
| undefined | "undefined" | NaN | false | throws TypeError |
| null | "null" | 0 | false | throws TypeError |
| true | "true" | 1 |  | new Boolean(true) |
| false | "false" | 0 |  | new Boolean(false) |
| "" |  | 0 | false | new String("") |
| "1.2"(非空，数字) |  | 1.2 | true | new String("1.2") |
| "one"(非空，非数字) |  | NaN | true | new String("one") |
| 0 | "0" |  | false | new Number(0) |
| -0 | "0" |  | false | new Number(-0) |
| NaN | "NaN" |  | false | new Number(NaN) |
| Infinity | "Infinity" |  | true | new Number(Infinity) |
| -Infinity | "-Infinity" |  | true | new Number(-Infinity) |
| 1(无穷大，非零) | "1" |  | true | new Number(1) |
| `{}`(任意对象) |  |  | true |  |
| `[]`(任意数组) | "" | 0 | true |  |
| `[9]`(1个数字元素) | "9" | 9 | true |  |
| `['a']`(其他数组) | 使用join()方法 | NaN | true |  |
| `function(){}`(任意函数) |  | NaN | true |  |


## 转换和相等性
一个值转换成另外一个值不意味两个值是相等的

## 显式类型转换
使用`Boolean()` `Number()` `String()` 或者`Object()`函数做显式类型转换

全局函数`parseInt()`和`parseFloat()`可以分别解析整数和浮点数


## 对象转换为原始值

对象转换为布尔值，所有对象（包括数组和函数）全部转换为`true`

对象转换为字符串，首先调用`toString()`,如果没有就调用`valueof()`,并返回原始值，否则抛出TypeError

对象转换为数字，首先调用`valueof()`，否则调用`toString()`


# 变量声明
使用`var`声明变量，如果没有指定初始值，则初始值是`undefined`

重复的声明和遗漏的声明

在非严格模式下，给未声明的变量赋值，相当于给全局对象创建一个同名属性，看起来像一个正确声明的全局变量

# 变量作用域

全局作用域和局部作用域（函数作用域）

函数内如果声明的变量和全局变量重名，则在函数内全局变量被遮盖。

声明局部变量一定要使用`var`，不然可能会修改全局变量

## 函数作用域和声明提前

函数里声明的变量（**不涉及赋值**）被“提前”到函数体的顶部


## 作为属性的变量

声明一个全局变量实际上定义全局对象的一个属性，使用`var`声明的变量是不可配置的，无法通过`delete`删除这个变量。


## 作用域链
全局变量在程序中始终是有定义的，局部变量在声明它的函数体内和嵌套的函数内都是有定义的

JavaScript代码（全局代码或者是函数）都有一个关联的作用域链。这个作用域链式一个对象列表或对象链表。

最顶层代码的作用域链由一个全局对象组成。

不含嵌套的函数体内，作用域链有两个对象，第一个对象是函数参数和局部变量的对象，另外一个是全局对象。

含嵌套的函数体内，作用域链至少是有三个对象

