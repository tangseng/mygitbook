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


**webpack插件**
        function MyPlugin(options) {
        // Configure your plugin with options...
        }
        MyPlugin.prototype.apply = function(compiler) {
            compiler.plugin("compile", function(params) {
            console.log("The compiler is starting to compile...");
        });
        compiler.plugin("compilation", function(compilation) {
            console.log("The compiler is starting a new compilation...");
            compilation.plugin("optimize", function() {
                console.log("The compilation is starting to optimize files...");
            });
        });
        compiler.plugin("emit", function(compilation, callback) {
            console.log("The compilation is going to emit files...");
                callback();
            });
        };
        module.exports = MyPlugin;


**Compiler**
Compiler 是 webpack 的主要引擎,webpack 通过实例化 compiler，然后调用它的 run 方法来使用它。
既然他是主流程，那么我们来看下他的主要事件流，就能大致了解整个打包流程.（来自webpack2）：
* entry-option 参数处理
* after-plugins 设置插件的初始配置后
* after-resolvers 设置解析器后
* environment 环境配置
* after-environment 环境配置完成
* before-run 编译之前
* run 开始编译
* watch-run 监视后开始编译之前
* normal-module-factory 创建 NormalModuleFactory 后
* context-module-factory 创建 ContextModuleFactory 后
* before-compile 编译参数创建完成
* compile 创建新编译之前
* this-compilation 发射 compilation 事件之前
* compilation 编译创建完成
* make 从entry开始递归分析依赖，构建模块
* after-compile 编译之后
* should-emit 此时可以返回 true/false ，来判断是否生成文件
* emit 生成文件之前
* after-emit 生成文件结束
* done 整体流程结束

**Compilation**
Compilation实例继承于compiler,这个对象主要负责编译流程。在编译阶段，模块被加载，封闭，优化，分块，哈希和重建等。以下是这个对象的主要方法：
* templatesPlugin
* addModule
* getModule
* findModule
* buildModule
* processModuleDependencies
* addModuleDependencies
* _addModuleChain
* addEntry
* prefetch
* rebuildModule
* seal
* sortModules
* addChunk
* processDependenciesBlockForChunk
* removeChunkFromDependencies
* applyModuleIds
* applyChunkIds
* sortItems
* summarizeDependencies
* createHash
* modifyHash
* createModuleAssets
* createChunkAssets
* getPath
* getStats
* createChildCompiler

**流程大概是调用 addEntry 找到入口文件，然后调用_addModuleChain ，获得相应 moduleFactory ，开始构建模块,构建模块流程比较复杂，其中的步骤有**
* 调用各 loader 处理模块
* 使用 acorn 解析js文件，得到 AST 然后拿到依赖模块，调用addDependency方法添加
* 不断重复以上流程，来递归到构建模块

**流程中处理的的核心对象就是module**
    [
        'dependencies',
        'blocks',
        'variables',
        'context',
        'reasons',
        'debugId',
        'lastId','id','index','index2','chunks','warnings','dependenciesWarnings','errors','dependenciesErrors','request','userRequest','rawRequest','parser','resource','loaders','fileDependencies','contextDependencies','error','_source','meta','assets','built','_cachedSource','issuer','optional','building','buildTimestamp','cacheable'
    ]

其中几个关键的：
* dependencies 模块依赖
* context 模块文件的上下文
* chunks 此模块所在的chunks
* request 加载此模块的完整请求，包括loader及其参数
* resource 该模块对应的资源文件
* loaders 解析该模块的loader
* fileDependencies 文件依赖，包括自己
* issuer 模块调用方
* _source 模块内容



**相关文章**
* [官方中文文档](https://doc.webpack-china.org/concepts/)
* [webpack2 终极优化](https://github.com/gwuhaolin/blog/issues/2)
* [彻底解决Webpack打包慢的问题](https://segmentfault.com/a/1190000006087638)
* [开发工具心得：如何 10 倍提高你的 Webpack 构建效率](https://segmentfault.com/a/1190000005770042)
* [如何在 webpack 中引入未模块化的库](https://sebastianblade.com/how-to-import-unmodular-library-like-zepto/)
* [详解Webpack2的那些路径](http://www.qinshenxue.com/article/20170315092242.html)
* [Webpack 大法之 Code Splitting](https://zhuanlan.zhihu.com/p/26710831)
* [webpack2应用级构建配置方案](http://www.tangshuang.net/3573.html)
* [常用 webpack 配置统计结果](https://github.com/pigcan/blog/issues/5)