# 本地存储

cookie、localStorage、sessionStorage 三者的异同

<table>
    <thead>
        <tr>
            <th>特性</th>
            <th>Cookie</th>
            <th>localStorage</th>
            <th>sessionStorage</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>数据的生命期</td>
            <td>可设置失效时间，默认是关闭浏览器后失效</td>
            <td>除非被清除，否则永久保存</td>
            <td>仅在当前会话下有效，关闭页面或浏览器后被清除</td>
        </tr>
        <tr>
            <td>存放数据大小</td>
            <td>4K左右</td>
            <td>一般为5MB</td>
            <td>一般为5MB</td>
        </tr>
        <tr>
            <td>与服务器端通信</td>
            <td>每次都会携带在HTTP头中，如果使用cookie保存过多数据会带来性能问题</td>
            <td>仅在客户端（即浏览器）中保存，不参与和服务器的通信</td>
            <td>仅在客户端（即浏览器）中保存，不参与和服务器的通信</td>
        </tr>
        <tr>
            <td>易用性</td>
            <td>需要程序员自己封装，源生的Cookie接口不友好</td>
            <td>源生接口可以接受，亦可再次封装来对Object和Array有更好的支持</td>
            <td>源生接口可以接受，亦可再次封装来对Object和Array有更好的支持</td>
        </tr>
    </tbody>
</table>

> 
    localStorage.setItem('cache', '皮皮虾，我们走~')
    localStorage.getItem('cache')
    localStorage.removeItem('cache')
    localStorage.clear()
    //StorageEvent
    window.addEventListener('storage', function(event){
        console.log(event)
    })