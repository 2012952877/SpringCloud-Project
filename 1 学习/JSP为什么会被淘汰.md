https://baijiahao.baidu.com/s?id=1645273953613115391&wfr=spider&for=pc



这就是jsp的弊端，为什么呢？我们可以来总结一下：

（1）动态和静态资源放在一起，一旦服务器出现状况，前后台一起玩完，用户体验极差。

（2）一旦jsp出现了问题，就需要前端后端发开人员一块来分析解决，效率低。

（3）jsp无法使用nginx等。

（4）jsp页面复杂，难以修改。

（5）第一次加载jsp需要编译成servlet，时间久，而且业务量大的时候，jsp负担太大。

（6）jsp对于开发人员简直就是一个挥之不去的痛，太难了！！！

鉴于以上缺点，于是另外一套机制横空出世了，这就是前后端分离。什么是前后端分离呢？

前后端分离其实就是后端工程师只关注于后端页面的开发，不再处理前端问题。前端工程师只关注于自己的页面开发。需要数据交互的时候，两者会有一份接口文档。

就这样这种思想架构很快的流行开来，这也就是为什么jsp落寞的真正原因。从此java从jsp转向了restful结构，springMCV也开始流行开来，并逐渐占领了市场。前后端分离有什么优点呢？我们来总结一下：

（1）动态和静态资源分开存储。

（2）出现bug能很快定位是前端还是后端。

（3）支持nginx。在高并发状态下极其优秀。

（4）直接请求页面，不用编译，速度效率都提上来了。

（5）从此前端和后端是相亲相爱的一家人了！！！！