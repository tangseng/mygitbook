# EventSource

SSE（Server-Sent Event，服务端推送事件）是一种允许服务端向客户端推送新数据的HTML5技术。与由客户端每隔几秒从服务端轮询拉取新数据相比，这是一种更优的解决方案。

Server-sent Events 规范是 HTML 5 规范的一个组成部分，具体的规范文档见参考资源。该规范比较简单，主要由两个部分组成：第一个部分是服务器端与浏览器端之间的通讯协议，第二部分则是在浏览器端可供 JavaScript 使用的 EventSource 对象。通讯协议是基于纯文本的简单协议。服务器端的响应的内容类型是“text/event-stream”。响应文本的内容可以看成是一个事件流，由不同的事件所组成。每个事件由类型和数据两部分组成，同时每个事件可以有一个可选的标识符。不同事件的内容之间通过仅包含回车符和换行符的空行（“\r\n”）来分隔。每个事件的数据可能由多行组成。代码清单 1 给出了服务器端响应的示例。


        //浏览器端
        var evtSource = new EventSource("/sendMessage");
        //收到服务器发生的事件时触发
        evtSource.onmessage = function (e) {
            console.log(e.data);
        }
        //成功与服务器发生连接时触发
        evtSource.onopen = function () {
            console.log("Server open")
        } 
        //出现错误时触发
        evtSource.onerror = function () {
            console.log("Error")
        } 
        //自定义事件
        evtSource.addEventListener("myEvent", function (e) {
            console.log(e.data);
        }, false)

        ---------------------------------------------------
        
        //服务端
        var http = require('http');
        var fs = require('fs');

        http.createServer(function (req, res) {
            if(req.url === '/sendMessage') {
                res.writeHead(200, {
                    "Content-Type": "text/event-stream" //设置头信息
                });

                setInterval(function () {
                    res.write(
                        //事件一
                        "data:" + new Date().toLocaleTimeString() + "\n\n" + //必须“\n\n”结尾
                        //事件二
                        ": '这是注释！'" + "\n" +
                        "event: myEvent" + "\n" + 
                        "data:" + new Date().toLocaleString() + "\n\n"
                    );
                }, 1000);
            } else {
                fs.readFile('./index.html', function (err, content) {
                    res.writeHead(200, {'Content-Type': 'text/html'});
                    res.end(content, 'utf-8');
                });
            }

        }).listen(3000);

**相关文章**
* [SSE技术详解：一种全新的HTML5服务器推送事件技术](http://www.52im.net/thread-335-1-1.html)
* [HTML5—EventSource服务端推送事件](http://www.jianshu.com/p/622a3549728a)