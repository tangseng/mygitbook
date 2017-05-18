# 响应式原理

![响应式原理](../../assert/vue-watcher.png)

**原理：**
*   所有传入data中的数据都会被Vue通过Object.definePorperty进行getter/setter设置。组件实例化时都会有相应的watcher对象，组件中的所有属性都会被watcher记录为依赖项，当依赖项被调用setter时，watcher会进行重新计算，进而重新渲染组件。
*   受限于js的限制，vue不能监测到属性的动态添加和删除。因此Vue不支持动态添加根级属性，所有的属性必须在组件初始化的时候添加进data并进行getter/setter。但是可以对属性的子属性进行添加/修改。并且需要使用Vue.set或者vm.$set，或者替换属性引用来让watcher检测到更新。
*   Vue检测到数据的更新，会开启一个队列，并缓存同一个事件里面的所有修改，同一个watcher被多次触发，只会有一个进入队列，这样合并计算所有的修改，然后在下一个tick里面对DOM进行异步更新。MutationObserver->setTimeout(fn,0)。如果业务逻辑中需要获得数据变化后的dom内容或者对dom做点什么，可以使用Vue.nextTick(fn)，(或者vm.nextTick)在回调里面处理。