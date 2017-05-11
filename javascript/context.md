#  执行上下文


当Javascript代码执行一段可执行代码时，会创建对应的执行上下文。
对于每个执行上下文，都有三个重要属性：
* 变量对象(variable object, VO)
* 作用域链(Scope chain)
* this

> 
    var scope = "global scope";
    function checkscope(){
        var scope = "local scope";
        function f(){
            return scope;
        }
        return f();
    }
    checkscope();
    //上下文栈
    ECStack = [
        fContext,
        checkscopeContext,
        globalContext
    ];
    //几个执行上下文
    globalContext = {
        VO: [global, scope, checkscope],
        Scope: [globalContext.VO],
        this: globalContext.VO
    }
    checkscopeContext = {
        AO: {
            arguments: {
                length: 0
            },
            scope: undefined,
            f: reference to function f(){}
        },
        Scope: [AO, globalContext.VO],
        this: undefined
    }
    fContext = {
        AO: {
            arguments: {
                length: 0
            }
        },
        Scope: [AO, checkscopeContext.AO, globalContext.VO],
        this: undefined
    }


**相关文章**
* [JavaScript深入之执行上下文](https://github.com/mqyqingfeng/Blog/issues/8)
* [一道js面试题引发的思考](https://github.com/kuitos/kuitos.github.io/issues/18)