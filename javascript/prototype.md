# 原型及原型链

**JS中所有对象都有一个特殊的内部属性叫[[prototype]]，本质是对其他对象的引用。对象在创建时都为该属性赋予一个非空的值（当然是可以手动设置为空）。**
-   [[prototype]]的作用是：当我们使用对象的属性时，第一步引擎会查找该对象下是否有这个属性，如果没有，这个时候就会继续访问对象的[[prototype]]中是否有这个属性了，如果没有就继续查找[[prototype]]的[[prototype]]，这一过程也叫原型链查找。
-   [[prototype]]链的最终指向Object.prototype这个对象，这个对象包含很多通用的方法。
当我们new 一个构造函数生成一个变量a的时候，其中就有一步操作就是将a的内部属性[[prototype]]关联到构造函数的prototype上。
即：Object.getPrototypeOf(a) === 构造函数.prototype
-   如果刚才说的构造函数的prototype指向的是另外一个构造函数的实例对象，那么此时已经实现所谓了继承。
-   因为基于原型链的，所以在JS称为“原型继承”。跟其他语言的继承（复制机制）有很大区别的。

![原型图](../assert/prototype.png)

**相关文章**
* [JavaScript深入之从原型到原型链](https://github.com/mqyqingfeng/Blog/issues/2)
* [震惊！原来你是这样的原型继承。。。](http://www.jianshu.com/p/e858f729bf4c)