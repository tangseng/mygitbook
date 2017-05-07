# cors

**cors**
> 支持CORS请求的浏览器一旦发现ajax跨域请求，会对请求做出一些特殊处理。
> 服务端如果实现了CORS接口，则会接受请求并进行回应。
> 浏览器对于跨域请求分为："简单请求" 和 "非简单请求"

**简单请求**
> 
    需要满足以下特征：
    1. 请求方法是以下三种之一：
        HEAD、GET、POST
    2. HTTP头信息不能超出以下几种字段：
        Accept
        Accept-Language
        Content-Language
        Last-Event-ID
        Content-Type: 
            application/x-www-form-urlencoded 
            multipart/form-data 
            text/plain

浏览器判断跨域为"简单请求"的时候，会在Request Header中添加 Origin （协议 + 域名 + 端口） 字段，用来表示请求的源，CORS服务端会将该字段作为跨源标志。
服务端接受到此次请求，首先判断Origin是否在允许源的范围内，如果通过验证，服务端会在Response Header中添加 Access-Control-Allow-Origin 、 Access-Control-Allow-Credentials 等字段

*必须字段*
<table>
    <tbody>
        <tr>
            <td>Access-Control-Allow-Origin</td>
            <td>表示服务端允许的请求源，* 代表全部，多个用逗号隔开</td>
        </tr>
        <tr>
            <td>Access-Control-Allow-Credentials</td>
            <td>表示是否允许发送cookie，默认值为 false。当设置为true时，并且ajax请求设置withCredentials = true，则浏览器就可以发送cookie到服务端</td>
        </tr>
        <tr>
            <td>Access-Control-Expose-Headers</td>
            <td>表示当使用getResponseHeader()方法时，能从header中获取到的参数</td>
        </tr>
    </tbody>
</table>

之后浏览器收到Response后也会判断自己的源是否在 Access-Control-Allow-Origin 允许的源中，如果不存在则会报"同源检测异常"。

> 总结：简单请求只需要CORS服务端在接收到携带Origin字段的跨域请求后，在Response Header中添加Access-Control-Allow-Origin等字段给浏览器做同源判断。


**非简单请求**
> 
    进行"非单请求"时，浏览器会首先发出类型为 OPTIONS 的"预检请求"，请求地址相同，CORS服务端对"预检请求"处理，并对Response Header添加验证字段，浏览器接收到"预检请求"的返回值进行一次请求预判断，验证通过后，主请求发起。

预检通过后，主请求和"简单请求"一致。

> 总结：非简单请求需要CORS服务端对OPTIONS类型的请求做处理，其他与简单请求一致。