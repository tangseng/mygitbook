# webpack

> 
webpack是一个在开发阶段所使用的模块打包工具，本身可以将前端各种资源统一打包成js文件和资源文件，其中需要配合一些loader加载器（如css、js预编译方案）

前端几大模块系统：commonjs(node)，amd(requirejs)，cmd(sea.js)，还有umd
本身兼容amd，commonjs，甚至非模块化写法，可以同时用3种，无比“酸爽”

> webpack 是一个Javascript应用程序的*模块打包器*

**webpack四个核心概念**
* 入口(entry)
* 输出(output)
* 加载器(loaders)
* 插件(plugins)

**什么是 webpack 模块**
> 对比 Node.js 模块，webpack 模块能够以各种方式表达它们的依赖关系，几个例子如下：

* ES2015 import 语句
* CommonJS require() 语句
* AMD define 和 require 语句
* css/sass/less 文件中的 @import 语句。
* 样式(url(...))或 HTML 文件(&lt;img src=...&gt;)中的图片链接(image url)

> webpack 1 需要特定的 loader 来转换 ES 2015 import，然而通过 webpack 2 可以开箱即用。

**依赖图表**
> webpack 从命令行或配置文件中定义的一个模块列表开始，处理你的应用程序。 从这些入口起点开始，webpack 递归地构建一个依赖图表，这个依赖图表包含着应用程序所需的每个模块，然后将所有这些模块打包为少量的 bundle - 通常只有一个 - 可由浏览器加载。


**webpack几大重要概念：**
* 入口文件：简单的说入口文件就是在html里面直接引入的，由浏览器触发执行的js文件。其他文件都是由入口文件直接或间接引入的
* loader：webpack本身只能处理js文件，所以需要loader将一些非js文件转换成js，再require进来。loader可以串联，并且接受参数

> 
    module.exports = {
        entry:['', ''],
        output: {
            filename: '',
            path:'',
            publicPath: ''
        },
        resolve: ['', '.js'],
        module: {
            preLoaders: [],
            loaders: [
                {test: '', loader:'vue-loader'}
            ],
            postLoaders: []
        },
        plugins: [],
        devtool: 'source-map',
        devServer: {
            hot: true,
            proxy: {}
        }
    }

> 
* webpack-dev-server 
* 如果用express，可以直接用webpack-dev-middleware


**相关文章**
* [官方中文文档](https://doc.webpack-china.org/concepts/)
* [webpack2 终极优化](https://github.com/gwuhaolin/blog/issues/2)
* [彻底解决Webpack打包慢的问题](https://segmentfault.com/a/1190000006087638)
* [开发工具心得：如何 10 倍提高你的 Webpack 构建效率](https://segmentfault.com/a/1190000005770042)
* [如何在 webpack 中引入未模块化的库](https://sebastianblade.com/how-to-import-unmodular-library-like-zepto/)
* [详解Webpack2的那些路径](http://www.qinshenxue.com/article/20170315092242.html)
* [Webpack 大法之 Code Splitting](https://zhuanlan.zhihu.com/p/26710831)