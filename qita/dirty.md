# 脏数据检测

对脏数据的检查就是脏检查，比较UI和后台（scope）的数据是否一致。
当有UI事件，ajax请求和timeout延迟事件，才会触发脏检查。
一次脏检查就是调用一次$apply()或者$digest()，然后将数据中最新的值呈现到界面上。

**$watch对象**

Angular中每一个绑定到UI的数据，都会有一个 $watch 对象：

        //比如<span>{{user}}</span>
        watch = {
            name: '', //当前watch对象观测的数据名
            getNewValue: function($scope) { //得到$scope上的新值
                return newValue
            },
            listener: function(newValue, oldValue) {
                //比较新旧值，当数据发生改变时需要执行的操作
            }
        }

**双向数据绑定**

    对界面的操作能实时反应到后台($scope)数据，后台数据的更改也能在界面呈现。

**$scope的重要性能特征**
* 在作用域上添加数据本身并不会由性能折扣。如果没有监听器在监控某个属性，它在不在作用域上都无所谓。Angular并不会遍历作用域的属性，它遍历的是监听器。一旦将数据绑定到UI上，就会添加一个监听器。
* $digest里会调用每个getNewValue()，因此，最好关注监听器的数量，还有每个独立的监控函数或者表达式的性能。


        $scope.prototype.$watch = function(name,getNewValue,listener){
            var watch = {
                name:name,
                getNewValue : getNewValue,
                listener : listener || function(){}
            };
            this.$$watchList.push(watch);
        }
        $scope.prototype.$digest = function(){
            var list = this.$$watchList;
            for(var i = 0,l= list.length;i++){
                var watch = list[i];
                var newValue = watch.getNewValue(this);
                // 在第一次渲染界面,进行一个数据呈现.
                var oldValue = watch.last;
                if(newValue!=oldValue){
                    watch.listener(newValue,oldValue);
                }
                watch.last = newValue;
            }
        }


**相关文章**
* [AngularJS 脏检查深入分析](http://www.cnblogs.com/likeFlyingFish/p/6183630.html)