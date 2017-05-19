# drag/drop

**相关事件及对象**
* DataTransfer 对象：退拽对象用来传递的媒介，使用一般为Event.dataTransfer。
* draggable 属性：就是标签元素要设置draggable=true，否则不会有效果，例如：
&lt;div title="拖拽我" draggable="true"&gt;列表1&lt;/div&gt;
* ondragstart 事件：当拖拽元素开始被拖拽的时候触发的事件，此事件作用在被拖曳元素上
* ondragenter 事件：当拖曳元素进入目标元素的时候触发的事件，此事件作用在目标元素上
* ondragover 事件：拖拽元素在目标元素上移动的时候触发的事件，此事件作用在目标元素上
* ondrop 事件：被拖拽的元素在目标元素上同时鼠标放开触发的事件，此事件作用在目标元素上
* ondragend 事件：当拖拽完成后触发的事件，此事件作用在被拖曳元素上
* Event.preventDefault() 方法：阻止默认的些事件方法等执行。在ondragover中一定要执行preventDefault()，否则ondrop事件不会被触发。另外，如果是从其他应用软件或是文件中拖东西进来，尤其是图片的时候，默认的动作是显示这个图片或是相关信息，并不是真的执行drop。此时需要用用document的ondragover事件把它直接干掉。
* Event.effectAllowed 属性：就是拖拽的效果


**相关文章**
* [HTML5 drag & drop 拖拽与拖放简介](http://www.zhangxinxu.com/wordpress/2011/02/html5-drag-drop-%E6%8B%96%E6%8B%BD%E4%B8%8E%E6%8B%96%E6%94%BE%E7%AE%80%E4%BB%8B/)