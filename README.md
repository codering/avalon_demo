# avalon_demo
mmrouter + dropdown 遇到的问题
* 重现步骤

1. 保证当前页是整页刷新过的
2. 点击"home.user"
3. 再点击"about"
4. 再点击"home.user"
5. 在dropdown搜索框输入任意字符，选择一个值

-------------
会看到console控制台出现错误"Uncaught TypeError: Cannot read property '$events' of null"
-------------

* 如果刷新整个页面后，先执行上面的步骤2、5, 则不论路由怎么切换，下拉框选择都不会有问题。
* 把下面代码中vm.dropdownlist 定义中的data去掉，也不会出现问题。


主要的代码逻辑
```js
           var data = [
                {
                    value: "default",
                    label: "default"
                },
                {
                    value: "name 1",
                    label: "name 1"
                }, {
                    value: "name 2",
                    label: "name 2"
                }, {
                    value: "name 3",
                    label: "name 3"
                }, {
                    value: "name 4",
                    label: "name 4"
                }, {
                    value: "name 5",
                    label: "name 5"
                }
            ]
            var dvm = null;
            // root ctrl
            avalon.define("app",function(vm){
                vm.$skipArray = ['dropdownlist']
                vm.dropdownlist = {
                   getRealTimeData: function(search, dropdownlist) {
                       dvm = dropdownlist;
                        setTimeout(function() {
                            dropdownlist.render(data)
                        }, 100)
                    },
                    data: [
                        {
                            value: "default",
                            label: "default"
                        }
                    ],
                    realTimeData: true
                   
                }
                 vm.vv = "default";
                 vm.reload = function(){
                    vm.vv="default";
                 }
            });

```


