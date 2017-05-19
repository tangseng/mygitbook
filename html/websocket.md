# WebSocket

websocket是HTML5一种新的协议。它实现了浏览器与服务器的全双工通信，能更好的节省服务器资源和带宽并达到实时通讯，建立在TCP之上，同HTTP一样通过TCP来传输数据。
可以从头部字段可以看出与http的不同
> 
    Upgrade: websocket
    Connection: Upgrade

websocket客户端api：
> 
    const ws = new WebSocket('ws://websocket.com')
    ws.onopen = function() {
        ws.send('test')
    }
    ws.onmessage = function(event) {
        console.log(event.data)
        ws.close()
    }
    ws.onclose = function(event) {
        console.log('closed!')
    }
    ws.onerror = function(event) {
        console.log('error')
    }

![websocket与http](../assert/websocket.jpg)


**相关文章**
* [WebSocket 实战](https://www.ibm.com/developerworks/cn/java/j-lo-WebSocket/index.html)
* [WebSocket 教程](http://www.ruanyifeng.com/blog/2017/05/websocket.html)
* [Socket.IO介绍：支持WebSocket、用于WEB端的即时通讯的框架](http://www.52im.net/thread-190-1-1.html)