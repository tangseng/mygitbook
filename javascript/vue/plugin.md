# 插件

**开发插件：plugin**
*   为Vue添加全局功能，一般有几种：
    1.  为Vue添加全局属性和方法
    2.  为Vue添加全局资源：指令(directive)/过滤器/过渡等
    3.  为Vue全局混合对象，通过mixin方法为组件添加一些选项
    4.  通过向Vue.prototype添加一些方法来为组件实例增加方法
*   插件需要提供install方法，接受参数，1、Vue  2、配置参数
*   Vue.use(‘插件xxx’)


> 
    MyPlugin.install = function (Vue, options) {
        // 1. 添加全局方法或属性
        Vue.myGlobalMethod = function () {
            // 逻辑...
        }
        // 2. 添加全局资源
        Vue.directive('my-directive', {
            bind (el, binding, vnode, oldVnode) {
            // 逻辑...
            }
            ...
        })
        // 3. 注入组件
        Vue.mixin({
            created: function () {
                // 逻辑...
            }
            ...
        })
        // 4. 添加实例方法
        Vue.prototype.$myMethod = function (options) {
            // 逻辑...
        }
    }