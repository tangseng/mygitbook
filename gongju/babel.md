# babel

**Babel是一个通用的多用途的Javascript编译器**
> Babel把用最新标准编写的Javascript代码向下编译成可以在今天随处可用的版本。本身这一过程叫做“源码到源码”的编译，也被称为转换编译。

* babel-cli
> 命令行使用babel方式
* babel-register
> 代码中引入babel的使用方式，类似即时编译，不适合正式产品使用
* babel-code
> 以编程的方式使用babel，const babel = require('babel-core'); babel.transformFile("filename.js", options, () => {})

**配置Babel**
最新版Babel本身只是个容器，本身不会做多少代码的转换编译工作，需要依赖插件(plugins)或者预设(presets，是一组预设的插件集合)完成更多的事情
通用做法需要为Babel提供.babelrc配置文件：
> 
    {
        "presets": [],
        "plugins": []
    }

** *关于presets，是一组预设的插件，官方提供了一些，也可以自定义。可以同时使用多个。* **
* babel-preset-es2015
* babel-preset-react
* babel-preset-stage-x (x有0,1,2,3，4就是标准es2015)
* babel-preset-env （最新）

当对代码进行转换编译后，有时并一定能直接运行。这时候还需要补充polyfill(代码填充，也称为兼容性补丁)。
babel-polyfill是官方提供的polyfill，使用了优秀的"core-js"，并且还有定制化的generator生成器"regenerator"和异步语法"async"。
使用时只需在工程文件的顶部导入就可以了
> 
    import "babel-polyfill";

Babel还会使用“助手”方法来保持生成代码的整洁，这些方法被统一到了“运行时”中了。
* babel-plugin-transform-runtime
* babel-runtime

使用如下：
> 
    {
        "plugins": [
            "transform-runtime"
        ]
    }

Babel会把
> 
    class Foo {
        method() {}
    }
    
编译成
> 
    import _classCallCheck from "babel-runtime/helpers/classCallCheck";
    import _createClass from "babel-runtime/helpers/createClass";
    let Foo = function () {
        function Foo() {
            _classCallCheck(this, Foo);
        }
        _createClass(Foo, [{
            key: "method",
            value: function method() {}
        }]);
        return Foo;
    }();

** *关于plugins，可以手动指定，跟使用预设几乎完全相同。* **
插件可以配置选项:
> 
    {
        "plugins": [
            ["transform-es2015-classes", {"loose": true}]
        ]
    }

可以基于环境自定义插件:
> 
    {
        "presets": ["es2015"],
        "plugins": [],
        "env": {
            "development": {
                "plugins": [...]
            },
            "production": {
                "plugins": [...]
            }
        }
    }
    当前环境可以使用 process.env.BABEL_ENV来获得。如果 BABEL_ENV 不可用，将会替换成 NODE_ENV，并且如果后者也没有设置，那么缺省值是 "development"。

另外Babel维护了一个官方的 babel-eslint 项目
> 
    npm i --save-dev eslint babel-eslint
    在.eslintrc中设置parser为"babel-eslint"
    {
        "parser": "babel-eslint",
        "rules": {
            ...
        }
    }


* [babel中文手册](https://github.com/thejameskyle/babel-handbook/tree/master/translations/zh-Hans)
* [babel初学者的一些常见误区](https://github.com/youngwind/blog/issues/68)