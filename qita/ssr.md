# 服务端渲染

SSR：三步走，举例Vue
1. 创建一个Vue实例
2. 创建一个渲染器
3. 将Vue实例渲染成HTML

        // 步骤 1:创建一个Vue实例
        var Vue = require('vue')
        var app = new Vue({
            render: function (h) {
                return h('p', 'hello world')
            }
        })
        // 步骤 2: 创建一个渲染器
        var renderer = require('vue-server-renderer').createRenderer()
        // 步骤 3: 将 Vue实例 渲染成 HTML
        renderer.renderToString(app, function (error, html) {
            if (error) throw error
            console.log(html)
            // => <p server-rendered="true">hello world</p>
        })

>SSR流程是这样的：

>客户端请求服务端， 服务端根据请求链接获得匹配到的组件， 再通过调用所有组件的某个返回Promise的埋点(官方是preFetch方法)来将需要的数据拿到， 最后再通过&lt;script&gt;window.__initial_state=blabla&lt;/script&gt;将其写入网页，最后将服务端渲染好的网页返回回去。

>接下来还没完，现在是客户端还要再跑： 它先用vuex将写入的__initial_state__替换为当前的全局状态树，再用这个状态树去检查服务端渲染好的数据有没有问题。遇到没被服务端渲染的组件，再去发异步请求拿数据。


**相关文章**
* [服务端渲染](https://vuefe.cn/v2/guide/ssr.html)
* [Vue2服务端渲染: 踩坑合集](https://smallpath.me/post/vue2-ssr-hardcore)