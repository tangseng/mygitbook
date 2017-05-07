# Node

**Node（事件驱动、非阻塞IO，异步）**
1. global全局对象（相当于window）
2. require引入模块
3. module.exports导出模块，exports.xxx导出多个
4. 当应用程序需要处理大量并发的输入/输出时，而在向客户端输出响应之前，应用程序内部不需要做复杂得处理的这种情况下可以考虑node

**npm**
1. npm install
2. npm i —save、npm i —save-dev
3. npm info xxx
4. npm run xxx
5. npm init、npm publish

**dependencies 与 devDependencies区别：**
* dependencies是运行该包所需要的依赖，devDependencies是开发时用到的依赖项，像一些进行单元测试之类的包
* npm install 默认安装两种依赖，但是npm install —production只会安装dependencies中依赖
* npm install xxx -dev 才会安装devDependencies依赖