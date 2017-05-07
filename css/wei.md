# 伪类/伪元素

**CSS3开始区分伪类和伪元素，伪类一个冒号:、伪元素两个冒号::**
**伪类：**
* :active
* :focus
* :visited
* :hover
* :first-child
* :nth-child
* :link
* :lang

**伪元素**
* ::before
* ::after
* ::first-letter
* ::first-line

> 
    举例：
    q:not(:lang(fr)):not(:lang(de)):not(:lang(en))::after{
        content:"(Unrecognized language)"; 
    }

**总结一下伪类与伪元素的特性及其区别：**

* 伪类本质上是为了弥补常规CSS选择器的不足，以便获取到更多信息；
* 伪元素本质上是创建了一个有内容的虚拟容器；
* CSS3中伪类和伪元素的语法不同；
* 可以同时使用多个伪类，而只能同时使用一个伪元素；