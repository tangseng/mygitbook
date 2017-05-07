# HTML5

**html5是一堆新特性组合起来的集合**
> 
* doctype: <!DOCTYPE html>
* 新增了一些语义化标签：header、footer、nav、section、article
* 表单控件新增了一些类型：date、time、email、url、search、number、range，required、placeholder
* 标签添加自定义属性：data- 方便在js和css以属性的方式获取它们

**新增的能力**
> 
* canvas：上下文支持3D &lt;canvas&gt;标签 getContext('2d')
* svg：最外层&lt;svg&gt;标签，还有一些能力svg渐变
* MathML：&lt;math&gt;标签
* audio、video富媒体能力，controls，&lt;source&gt;
* 本地存储：localStorage、sessionStorage
* websocket：new WebSocket(url, [port])
* web workers：new Worker('xxx.js')、postMessage、worker.terminate()
* 服务器推送：&lt;eventsource&gt;
* 地理位置：navigator.geolocation.getCurrentPosition
* 拖放：drag、drop，dragstart...dragenter...dragmove...dragleave...drag...drop...dragend。event.dataTransfer