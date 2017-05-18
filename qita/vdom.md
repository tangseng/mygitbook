# 虚拟Dom

**virtual dom，通俗易懂的来说就是用一个简单的对象去代替复杂的dom对象。**

**diff算法**
* 只会在同级比较，不同级时可能的操作就是先删除再添加
    ![diff](../assert/virtual-diff.png)
* patch函数：打补丁一样修改真实dom。两个参数vnode、oldVnode：新旧两个虚拟节点。
    
        // body下的 &lt;div id="v" class="classA"&gt;&lt;div&gt; 对应的 oldVnode 就是
        {
            el:  div  //对真实的节点的引用，本例中就是document.querySelector('#id.classA')
            tagName: 'DIV',   //节点的标签
            sel: 'div#v.classA'  //节点的选择器
            data: null,       // 一个存储节点属性的对象，对应节点的el[prop]属性，例如onclick , style
            children: [], //存储子节点的数组，每个子节点也是vnode结构
            text: null,    //如果是文本节点，对应文本节点的textContent，否则为null
        }

* 设置key和不设置key的区别：不设key，newCh和oldCh只会进行头尾两端的相互比较，设key后，除了头尾两端的比较外，还会从用key生成的对象oldKeyToIdx中查找匹配的节点，所以为节点设置key可以更高效的利用dom。

**virtual dom的优化总结**
* 尽量不要跨层级的修改dom
* 设置key可以最大化的利用节点
* 不要盲目相信diff的效率，在必要时可以手工优化


最后，virtual dom的另外一个重大意义就是提供了一个中间层，js去写ui，客户端负责渲染，就是react native一样。


**相关文章**
* [解析vue2.0的diff算法](https://github.com/aooy/blog/issues/2)