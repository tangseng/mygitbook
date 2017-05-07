# Vue

**概念：**
> 
1.  只关注视图层，自底向上增量开发
2.  响应的数据绑定、组合的视图组件

**标签：**
> 
* \{\{\}\}
* v-if
* v-else
* v-else-if
* v-for (in、key)
* v-show
* v-bind
* v-on
* v-model
* :
* @

**定义组件：**
>   
    Vue.component('my-zujian', {
        props: ['message'],
        template: ‘<span>{{message}}</span>'
    })


**例子：**
> 
    const vm = new Vue({
        el: 'xxx',
        components: {},
        data: {},
        computed: {
        },
        methods: {
        },
        watch: {
        }
    })


**自定义指令：directive**
> 
* v-demo，可以直接使用于原生dom
* 钩子函数：bind、inserted、update、componentUpdated、unbind。函数参数：el、binding、vnode、oldVnode

**混合：mixin**
> 
* 对于钩子函数，合并成数组，先执行混合对象的钩子，再执行组件的钩子
* 对于methods、components、directives，合并成一个对象，组件的对象中属性覆盖钩子函数里面的相同属性
* 可以定义全局混合，慎用，会影响所有vue组件，Vue.mixin

**专门增强：**
> 
* v-bind:class=“{‘class-a’: is-need-class-a, ‘class-b’: is-need-class-b}"
* v-bind:style=“{‘color’: redVar}"

**注意点：**
> 
1. 不能触发数据重新update的点: （可以使用Vue.set）
    * 直接this.items[index] = 'xxx'
    * this.items.length = n
2. 事件修饰符：（可以同时多个使用）
    * stop
    * prevent
    * capture
    * self
    * once
3. 按键修饰符：（keyup）
    * event
    * tab
    * delete
    * esc
    * space
    * up/left/down/right
    * 数字
    * ctrl/alt/shift/meta 这个可以联合数字按键修饰符
4. v-model修饰：
    语法糖：<xxx v-bind:value="var" v-on:input="var=arguments[0]"></xxx>
    * lazy (用于input，将事件放到change中触发)
    * trim
    * number
5. 使用v-on绑定自定义事件：
    * $on(eventName)监听事件 （即父组件的模板里面嵌入子组件时v-on:xxx="父组件的某个方法"）
    * $emit(eventName)触发事件（即子组件中的方法里面this.$emit('xxx')）
6. slot内容分发
    * 组件不知道自己的内容，内容由父组件决定，域在父级
    * slot有默认、具名
    * 作用于插槽 <template scope="props.子组件属性">
7. 可复用组件api：
    * props：允许外部环境传递数据进组件
    * events：允许组件触发外部环境（父组件或者挂载组件）方法
    * slots：允许外部环境组织内容进组件中
8. 子组件索引：ref
9. 组件包含大量静态内容时候可以考虑加v-once将渲染结果缓存起来   
10. 动态组件 &lt;component :is=“xxx” keep-alive&gt;&lt;component&gt;
     