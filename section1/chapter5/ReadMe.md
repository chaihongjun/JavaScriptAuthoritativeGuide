第5章 语句

# 表达式语句
赋值语句是一类表达式语句

# 复合语句和空语句
复合语句，多条语句用花括号括起来。
空语句只含分号


# 声明语句
## var
声明一个或者多个变量

通过var声明的变量无法通过detele删除，且没有指定初始值则是undefined。
变量的声明会被提前到函数体顶部，但是初始化还是在原来var语句的位置。

## function


# 条件语句

## if
```
if(expression) 
    statement1
else
    statement2  
```
## else if
```
if(expression1) 
    statement1
else if(expression2)
    statement2  
else if(expression3)
    statement3
else
    statement4              
```
## switch
```
switch(expression){
    case expression1:
     statement1;
     break;
     case expression2:
     statement2;
     break; 
     default:
     statement3;
}
```

# 循环

##　while

```
while(expression)
    statement
```
## do while
循环体至少执行一次


##　for
```
for(initialize;test;increment)
    statement
```
等价于
```
initialize;
while(test){
    statement;
    increment;
}
```

## for/in
```
for(variable in object)
    statement
```
for/in 循环方便遍历对象属性成员

# 跳转

```
identifier:statement
```

