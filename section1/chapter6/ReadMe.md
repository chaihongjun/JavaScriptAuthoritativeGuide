第6章  对象
JavaScript对象可理解成熟字符串到值的映射。

JavaScript对象还可以从一个称为原型的对象继承属性，对象的方法通常是继承的属性

JavaScript对象是动态的，可以增删属性，但是通常模拟静态对象。

除了字符串，数字，false,true,null和undefined之外，JavaScript中的值都是对象

**对象的属性有三个“属性特性”：**

1. 可写（设置属性值）
2. 可枚举（通过for/in循环返回属性）
3. 可配置（可删除或者修改属性）

**另外，对象还有三个“对象特性”：**

1. 对象的原型（prototype）指向另外一个对象，本对象的属性继承自它的原型对象
2. 对象的类，是一个标识对象类型的字符串
3. 对象的扩展标记，指明了是否可以向该对象添加新的属性


**JavaScript对象可分为三类:**

1. 内置对象(native object).数组，函数，日期，正则表达式这些又ECMAscript定义的
2. 宿主对象(host object)又javascript解释器嵌入的宿主和环境，比如浏览器定义的。
3. 自定义对象，又代码创建


**JavaScript对象属性可分为两类:**

1. 自有属性，直接在对象中定义的属性
2. 继承属性，从对象的原型对象中继承的

# 创建对象

创建对象可以通过：

1. 对象直接量
2. 关键字`new`
3. Object.create()

##对象直接量
对象直接量是由若干名／值低组成的映射表

属性名可以是标识符也可以说字符串直接量。

##通过new创建对象
```
var o=new Object();
var a=new Array();
var d=new Date();
var r=new RegExp("js");
```

## 原型
每一个对象都从原型继承属性，所有通过对象直接量创建的对象都有同一个原型对象，可通过`Object.prototype`获得对原型对象的引用。

## Object.create()

```
Object.create(prototype_object)
```
prototype_object 是原型对象，比如 {x:1,y:2}

```
var o=Object.create({x:1,y:2});
o.x =>1
o.y =>2
```


# 属性的查询和设置
通过点(`.`)或者方括号(`[]`)运算符来获取或者设置属性值

## 继承
JavaScript对象有自有属性(pwn property)，也有一些属性是从原型对象继承而来。

对象属性的查询是从对象本身开始，如果没有则从对象原型继续查询，直到原型是null为止

## 属性访问错误
查询一个对象的属性，从自有或者原型那里继承的都没查询到，那会返回undefined.

**以下场景给对象设置属性会失败：**

1. 对象的属性是只读的
2. 对象的属性是继承而来而且是只读的；不能覆盖和原型属性同名的只读继承属性
3. 对象的可扩展性是false


# 删除属性
detele 只能删除自有属性，不能删除继承属性


#检测属性

```
objectName.hasOwnProperty("propertyName")
```
自有属性可枚举:

```
objectName.propertyIsEnumerable("propertyName")
```


# 枚举属性

```
var o={x:1,y:2,z:3};
for(p in o)
console.log(p); 
```

# 属性getter和setter
由getter和setter定义的属性称作存取器属性（accessor property）
getter返回的值就是属性存取表达式的值，setter用来设置属性存取器的值


# 属性的特征

数据属性有4个特性：

```
value
writable
enumerable
configurable
```
存取器属性:

```
get
set
enumerable
configurable
```

# 对象的三个属性

1. prototype 原型
2. class 类型
3. extensible attribute 可扩展性

## 原型属性
对象的原型属性用来继承（原型对象）属性的
检测一个对象是否是另外一个对象的原型（或处于原型链中）
```
objectName.isPrototypeOf(anotherObjectName)
```

## 类属性

## 可扩展性
对象默认可以扩展，可以使用以下方法更改
```
Object.preventExtensions()
```
另外
```
Object.seal()
```
除了可以禁止对象扩展，还可以将对象的属性都设置为不可配置


如果想判断对象是否可以扩展:
```
Object.isEx张颖晴tensible()
```    

# 序列化对象
将对象的状态转化为字符串

```
//序列化对象
var s=JSON.stringify(objectName);

//还原对象
JSON.parse(s);
```

# 对象方法
## toString()方法
返回调用对象值的字符串

## toLocaleString()方法
对象的本地化字符串

## toJSON()方法
返回对象的序列化（字符串）

## valueOf()方法
对象转换为原始值
