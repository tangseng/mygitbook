# flex

* **flex意为“弹性布局”，用来为盒装模型提供最大的灵活性。**
> 注意：设为flex布局以后，子元素的float、clear、vertical-align属性将失效。
        .xxx {
            display: flex;
        }


* **基本概念**
> 采用flex布局的元素称为flex容器(flex container)。
> 
> 它的所有子元素自动成为容器成员，称为flex项目(flex item)。
> 
> 容器默认存在两根轴：水平的主轴(main axis)和垂直的交叉轴(cross axis)。
> 
> 项目默认沿主轴排列。
> 
![flex](../assert/flex.png)

* **容器属性**
    * flex-direction: row | row-reverse | column | column-reverse; 决定主轴方向，即项目排列方向。
    * flex-wrap: nowrap | wrap | wrap-reverse; 如果一条轴线排不下，如何换行。
    * flex-flow: flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap。
    * justify-content: flex-start | flex-end | center | space-between | space-around; 定义了项目在主轴上的对齐方式。
    * align-items: flex-start | flex-end | center | baseline | stretch;定义了项目在交叉轴上如何对齐。
    * align-content: flex-start | flex-end | center | space-between | space-around | stretch;定义了多根轴的对齐方式。如果项目只有一根轴线，该属性不起作用。

* **项目的属性**
    * order: 定义项目的排列顺序。越小越靠前，默认为0。
    * flex-grow: 定义项目的放大比例，默认为0。
    * flex-shrink: 定义项目的缩小比例，默认为1。
    * flex-basis: 定义了在分配多余空间之前，项目占据的主轴空间。
    * flex: flex-grow、flex-shrink、flex-basis的简写，默认值：0 1 auto。后面两个属性可选。
    * align-self: auto | flex-start | flex-end | center | baseline | stretch;允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性，默认值为auto。

* **例子**
> 
![flex-lizi](../assert/flex-lizi.png)
        .parent {
            width: 200px;
            height: 150px;
            background-color: black;
            display: flex;
            flex-flow: row wrap;
            align-content: flex-start;
        }
        .child {
            box-sizing: border-box;
            background-color: white;
            flex: 0 0 25%;
            height: 50px;
            border: 1px solid red;
        }

**相关文章**
* [Flex 布局教程：语法篇](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)
* [Flex 布局教程：实例篇](http://www.ruanyifeng.com/blog/2015/07/flex-examples.html)