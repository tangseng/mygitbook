# React

**React的核心思想：封装组件，各个组件维护自己的状态和UI，当状态更新时，自动重新渲染整个组件**

大概几个概念：组件、jsx、virturl dom、data flow
* *组件*：组件的两大核心概念：props(组件的配置，在组件内不变，调用组件时传入)、state（组件的状态机，不同状态显示不同UI，当改变这个数据时需要更新UI就可以认为这个数据是个状态），一个组件就是靠这两个值在render方法里面构建组件html的
* *jsx*：react提出的一种语法，可以将html直接写进js代码中
* *virturl dom*：virturl dom是一个纯粹的js数据结构，组件的真实dom结构会映射到virturl dom上，virturl dom实现了diff算法，当组件的state状态改变时，react会调用组件的render方法重新渲染UI
* *data flow*：单向数据绑定