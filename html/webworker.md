# web worker

Javascript是单线程，提出web worker（工作线程）是为了解决处理一些比较耗时的计算。
它允许开发人员编写能够长时间运行而不被用户中断的后台程序，去执行事务或者逻辑，并同时保证页面对用户的响应不受影响。
> 总结：就是允许Javascript创建多个线程，但是这些线程完全受主线程控制，且不能操作DOM。

**web worker常用API**
* postMessage(data)：子线程与主线程之间互相通信的方法，data可以为任意值。
> 
        //主线程
        const worker = new Worker('xxx.js')
        worker.postMessage({shuju: '数据'})
        //子进程 xxx.js
        onmessage = function(event) {
            postMessage(event.data.shuju + '收到并返回')
        }
    
* terminate：主进程终止worker。一旦terminate后，无法重启启用，只能另外创建。
* message事件： onmessage
* error事件：onerror

**web worker上下文**
> worker执行的上下文，与主页面html执行时的上下文并不相同。没有window，而是WorkerGlobalScope。

WorkerGlobalScope作用域的常用属性和方法如下：
* self
* location (初始化当前工作线程的js的绝对URI，即使页面发生重定向等，这个URI也不会改变)
* close (子线程自己关闭，与terminate功能类似)
* importScripts (在子线程中加载其他js资源)
* XMLHttpRequest
* setTimeout/setInterval
* addEventListener
* postMessage

**web worker局限性**
* 不能跨域加载js资源
* 不能访问DOM
* 目前浏览器的实现不太一致


**相关文章**
* [浅谈webWorker](http://www.cnblogs.com/giggle/p/5350288.html)