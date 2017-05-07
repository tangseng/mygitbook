# 作用域

> 作用域本质是一套规则，就是程序如何存储变量，变量所影响的范围，以及之后如何可以方便的找到这些变量的一套机制规则。

**简单的说作用域就是根据名称查找变量的一套规则，用来规范引擎查找变量的过程的。**

JS引擎有两个帮手，一个是编译器，一个是作用域。
当代码中定义一个变量时候(var a = 2;)，实际上是会有两个阶段的处理，一是编译器编译时的处理，另外一个是引擎在运行时的处理。
编译时：编译器会询问作用域，是否有一个该名称的变量存在在当前作用域中，有则跳过，没有则要求作用域新建
运行时：也就是赋值操作，引擎会先找作用域询问，在当前的作用域集合中是否存在这样一个变量，如果有就直接使用，没有则继续查找。

**当然还有作用域嵌套或者说作用域链的概念**
> 当一个函数或者块嵌套在另外一个函数或者块中的时候，就发生了作用域嵌套。
在当前作用域中无法查找到某个变量时，引擎就会在外层嵌套的作用域中继续查找，直到最外层作用域即全局作用域为止。


**作用域有两种工作模型：词法作用域模型和动态作用域模型。**
**JS采用的是词法作用域模型。（词法分析，语法分析，生成代码）**
>词法作用域：简单的说，就是定义在词法阶段的作用域。词法分析器根据代码的变量以及块写在哪里，就定下作用域在哪里并保持不变。
在JS中的作用域由函数声明的位置决定的（当然es6引入块作用域，同理的）。词法分析阶段就确定了全部标识符，以及如何查找。