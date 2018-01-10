咱们的大致工作是： 

1. NodeJS 写 Backend （利用 [parse](http://parseplatform.org/) 来大大减少工作量）
2. 继承或覆写 Python 的日志模块，添加相关功能，兼容 2.7/3.x 
3. 使用 VueJs 实现前端 web app


这里我结合 Project 本身列出要用到的一些知识点，之后写一下我对这个 Project 的几个重要节点的展望。

> 这些知识点我基本都有一定了解， 有问题随时问我

## 知识点

### Python 相关

首先可以了解一下 Python logging 模块的工作方式， 因为咱们需要 Hack 到 logging 模块内部添加功能 （尤其 logger 还有继承关系，是否要处理待讨论）

> 我已经开始覆写其 Python logging 的代码

1. [logging 101](https://www.blog.pythonlibrary.org/2012/08/02/python-101-an-intro-to-logging/)
2. [Best Practice](https://atlee.ca/blog/posts/diving-into-python-logging.html)
3. [Python logging 模块源码](https://github.com/python/cpython/blob/2.7/Lib/logging/)


另外因为咱们需要从 Python 端向 NodeJS 服务器建立连接，异步发送日志数据，而以下这个库在 Python 中使用的比较多 （我建议咱们可以使用 WebSocket）

1. https://github.com/crossbario/autobahn-python 
2. [WebSocket 简介](http://www.ruanyifeng.com/blog/2017/05/websocket.html)
3. 关于 NodeJS 中使用 [µWebSocket](https://github.com/uNetworking/uWebSockets)


### 后端开发 

#### NodeJS 相关

Javascript 是一个门弱类型的语言， 弱类型带来的好处是书写简单，随时可run，而其缺点就是代码难以维护。随着 web 标准日新月异， 我们有了 Typescript 语言， 它与 Javascript 完全兼容， 同时加上了完备的类型系统，结合 [Webstorm](https://www.jetbrains.com/webstorm/) 强大的 IDE， 开发变得更加容易。 语言方面， 你可以看如下的资料： 

- [NodeJS 教程](https://www.gitbook.com/book/wizardforcel/yiqixue-nodejs/details) 
- 快速浏览一下 [Typescript 电子书](https://www.gitbook.com/book/zhongsp/typescript-handbook/details)， 目前 NodeJS 已经可以支持 Typescript。

另外推荐一个 NodeJS 包管理国内镜像： [阿里 NPM ](https://npm.taobao.org/)  （`npm` 类似 Python 的 `pip`）


#### 关于 Parse 

[Parse](http://parseplatform.org/) 曾经是 Facebook 的一款 BaaS (backend as a service) 云服务产品， 在 Facebook 关闭该业务后，开源社区用 NodeJS 重新实现了其框架和 SDK。 Parse 基于 Mongodb 提供了一套系统的数据存储，查询功能，并提供了在 client 端的 SDK，是一个后端的成熟解决方案。 

> 这块的架子已经基本搭好

你可以简单扫一眼他们的文档，有个印象： 

1.  https://github.com/parse-community/parse-server
2.  [Parse JS SDK](http://docs.parseplatform.org/js/guide/) 
3.  国内有一家公司，叫 Leancloud，他们的接口和 Parse 一致 (只不过前缀叫 `AV` 而不是 `Parse`)， 文档极为详尽易读，推荐看看：
	1. [Javascript 数据存储指南](https://leancloud.cn/docs/leanstorage_guide-js.html)
	2. [如何完成权限管理](https://leancloud.cn/docs/acl-start.html)


#### Javascript 语言相关

Javascript 在近几年增加了新的语法，和更多数据结构的原生支持， 使得开发更加的容易。 而且 Javascript 作为一个异步 IO 为主的语言， 新添加了专为异步处理而设计的 `async/await` 特性。  建议读一下下面的博客： 


1. [Javascript 新特性总览](http://javascript.ruanyifeng.com/advanced/ecmascript6.html) 
2. [Javascript 异步编程介绍及 Promise 解决方案](http://javascript.ruanyifeng.com/advanced/promise.html)
3. [Javascript 异步终极解决方案 async/await](http://www.ruanyifeng.com/blog/2015/05/async.html)




### 前端开发 

我们前端开发只需要使用一些现有的高层 library 来搭积木便可， 大部分情况不需要真正操作 DOM 树。 你先不用过多考虑， 到时候再去看不迟。 


上面我列了很多学习资料， 看起来很多， 但只需要有个大概了解就好， 我们是在实践中学习。 辛苦了！
