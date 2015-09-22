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

如果刷新整个页面后，只执行上面的步骤1、4, 则不论路由怎么切换，下拉框选择都不会有问题。


