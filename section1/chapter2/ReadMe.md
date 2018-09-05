第2章  词法结构

# 字符集
`Unicode`

## 区分大小写
在HTML中标签和属性名可以大写也可以小写，但是JavaScript中大写和小写是不一样的。


## 空格、换行符和格式控制符
JavaScript会忽略标识和换行符


## Unicode转义序列



## 标准化


# 注释
JavaScript支持两种格式注释:
```
//单行注释

/*
多行注释
 */
```
注意，多行注释不能有嵌套

# 直接量
直接使用的数据值就是直接量

# 标识符和保留字
标识符就是一个名字用来对变量和函数进行命名，或者作为循环语句中跳转位置的标记。

**标识符必须以`字母`、`下划线(_)`、或者`美元符号($)`开始，后续字符可以是字母、数字、下划线或者美元符号。**

**标识符不允许用数字做首字符出现**


## 保留字
某些标识符被JavaScript拿来作为关键字，所以不能再在程序中用这些关键字做标识符。

|  |  |  |  |  |
| :-: | :-: | :-: | :-: | :-: |
| break | delete | function | return | typeof |
| case | do | if | switch | var |
| continue | false | instanceof | throw | while |
| debugger | finally | new | true | with |
| default | for | null | try |

ECMAScript5中的保留字:

`class` `const` `enum` `export` `extends` `import` `super`

严格模式下的保留字:

`implements` `let` `private` `public` `yield` `interface` `package` `protected` `static`

严格模式下不能作为变量名、函数名或参数名:

`arguments` `eval`

ECMAScript 3将JAVA所有关键字列为自己的保留字：

| | | | | |
|:-:|:-:|:-:|:-:|:-:|
| abstract | double | goto | native | static |
| boolean | enum | implements | package | super |
| byte | export | import | private | synchronized | 
| char | extends | int | protected | throws |
| class | final | interface | public | transient |
| const | float | long | short | volatile |

另外，JavaScript预定义了很多全局变量和函数，不允许作为变量名或者函数名:

| | | | | |
|:-:|:-:|:-:|:-:|:-:|
| arguments | encodeURI | Infinity | Number | RegExp |
| Array | encodeURIComponent | isFinite | Object | String |
| Boolean | Error | isNaN | parseFloat | SyntaxError | 
| Date | eval | JSON | parseInt | TypeError |
| decodeURI | EvalError | Math | RangeError | undefined |
| decodeURIComponent | Function | NaN | ReferenceError | URIError |


# 可选的分号
JavaScript 使用(;)分号来将语句分隔开，JavaScript如果独占一行，通常分号可省略。 
