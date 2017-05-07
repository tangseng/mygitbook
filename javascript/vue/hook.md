# 生命周期及钩子

**钩子：**
* beforeCreate  -> 绑定数据 -> 初始化事件
* created -> 是否有el设置（有就等$mounted事件触发，没有就如下一步） -> 是否有template值（有就编译模板进render函数，没有就前面的el的outHTML做为模板编译进render函数）
* beforeMount -> 建立vm.$el，并且用它来替换上面的el
* mounted -> 等待数据更新，如有进入update流程，该过程可能反复  ->  当有vm.$destroy()触发时候会进入destroy流程
* beforeUpdate -> virtual dom 会进行重新render，或者patch修补
* updated
* beforeDestroy -> 将卸载watchers、事件监听器，递归destroy子组件
* destroyed