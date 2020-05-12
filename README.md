# 前端学习清单
## 一.css  [https://ashleynolan.co.uk/blog/frontend-tooling-survey-2018-results]
  ### 1.sass（功能强，使用范围广，可编辑性高）其他less postcss
  ### 2.css框架 Bootstrap Custom Framework （在vue中使用没那么高，现在需求不多）
  ### 3..BEM （css命名方案 block element modifier -- __ 前期使用不多，可读性好，后期利用率高）
  ### 4.Autoprefixer (相较于sass less那种预处理，它是后处理程序，可以将一些前缀补全，神器)
  ### 5.Modernizr （检测浏览器的css3和HTML5的属性而生，从而通过CSS来解决兼容性问题，加重css代码量，后期维护增加工作）
  ### 6.Stylelint （css代码检测工具）
  ### 7.Atomic Design （原子设计，element-ui与之类似，通过从小到大的排列，像原子-分子-细胞-组织这样一个方式组成页面结构，页面结构相似，功能相似，复合性能好）
  ### 8.css-in-js (react里面有用到，可以自定义样式，更能体现代码的编写功能)
  ### 9.css布局（flexbox弹性布局较为常见）
## 二.javascript
  ### 1.jquery 最受欢迎的js框架，使用率逐年降低
  ### 2.react 普遍使用的框架
  ### 3.vue 我目前使用的框架
  ### 4.webpack 使用最多的捆绑包，使用它进行模块打包
  ### 5.babel js编译器，通常将ES6译成ES5
  ### 6.ESLint js规范化工具
  ### 7.TypeScript 是js的超集，添加了可选的静态类型和基于类的面向对象编程
  ### 8.Yarn 架包的管理工具
  ### 9.Prettier 代码管理利器，能完美的将代码规范化
  ### 10.Yeoman 项目构建工具 可以试试构建一个react
## 三.javascript是如何工作的 [https://github.com/qq449245884/xiaozhi]
  ### 1.JS引擎 单线程 内置Api并非全部是由引擎提供，还有event loop和call queue （事件循环和呼叫队列）
    setTimeout、setInterval、I/O、UI交互事件   宏队列 执行完毕后会转到微队列，在主线程空了以后执行新一个线程时调用
    Promise，process.nextTick，且process.nextTick优先级大于promise.then   微队列 主线程最末尾执行 
  ### 2.V8引擎简介 复杂？简单？
  ### 3.内存管理与4中常见的泄漏  [https://github.com/qq449245884/xiaozhi/issues/3]
    引用计数垃圾收集算法  循环会产生问题  互相调用，产生超过0次引用，无法清除垃圾
    标记-清除(Mark-and-sweep)算法
    4个内存泄露  全局变量  setInterval或回调函数  闭包  脱离DOM的引用
  ### 4.从 Event Loop 规范探究 JavaScript 异步及浏览器更新渲染时机 [https://github.com/aooy/blog/issues/5] 

  (插入：vue的基本原理 object.defineProperty() 可以通过设置get和set的方法，来创造一个监听，每当对象数据改变时，必须经过set，此时可以监听到。
  通过监听observe可以获取改变的数据，然后在set时，将对象放置于订阅者处，统一管理，一旦监听到数据变化，遍历订阅者对象，通过{{}}等方式将储存的数据
  进行更改，即通过Compile将监听者和订阅者联系起来，将修改DOM上的ele的操作都写进Compile里面来，一旦数据改变，即去修改。双向绑定的简单化就是这样产生的
  后续就是不断完善对数据的监听方式（v-model v-if : {{}}等都是），而这些的共同点都是让Compile方法能够找到这个指令属性) 
  [https://github.com/DMQ/mvvm] [https://github.com/2686685661/SelfVue]
  ### 5.virtual DOM 
    页面中的element可以用js的对象代替，这样就可以直接用js对象的方式将整个页面表达出来，一旦哪里变更了，就是对象的改变，只要比较新旧两个对象就能找到变更的地方，从而快速改变
    virtual DOM 和页面上面的DOM就是一个映射的关系，显著提升效率
  ### 6.vue react这些框架更多的是对数据和状态的一种处理，不关心视图，或者说框架已经解决了数据状态对视图的影响，不需要去关注视图了（数据驱动 声明式的，性能全方位的提升）
    而jquery还是停留在对数据的处理和视图的变换上，（面向过程 命令式的，一步一动）
    两者对处理的点上就不一样，三大框架的流行则是因为用户在对web的要求发生了改变，对交互的需求更大了，对数据和状态这方面更加的注重了，单一的页面不能满足现在用户的要求
    jquery的时代已经过去了。。。
  ### 7.vue生命周期 
    beforeCreated 都为空 
    created 生成了data $el为空
    beforeMount $el为虚拟dom 
    Mounted 实例挂载，生成了html页面  
    beforeUpdate 监听数据，更新前 
    updated 更新数据后 
    beforeDestroy 页面销毁前 
    destroyed 都为空
## 四.浏览器
  ### 1.浏览器的工作原理 [https://www.html5rocks.com/zh/tutorials/internals/howbrowserswork/] 有点深奥，没真没看懂，有时间再看
  ### 2.跨越  同源策略  协议+域名+端口 其中域名  解决跨越的三个方法（1.配置代理proxy ，将跨域交给后端，需要后端转换，一些静态页面就不容易实现了，关键点在后端处理上 2. 在请求头中Access-Control-Allow-Origin 配置为* Access-Control-Allow-Credentials响应头为true 同事ajax请求中withCredentials=true 3. jsonp 通过script能够跨越来实现，只能使用在get上）
## 五.react
  ### 1.从零开始学react 安装react， facebook有一个脚手架可以快速安装，需要自己再添加一些额外的组件
  ### 2.react 更多的注重于代码本身,all in js 通过函数来将html css js等展现出来，更加的复合程序本身吧，vue则是html css js的有机结合，对web开发来讲更加的适应，旧系统转框架用vue更加的便捷
  ### 3.react自由度很高，很多都是需要自己来开发定义的，本身react很少，规定了基本框架，很多是依靠外力来实现，生态很广
## 六. Http
  ### 1.http协议和https
  ### 2.websocket
  ### 3.不同的code
    1XX 请求已接收 继续处理
    200 成功
    3XX 重定向 301 永久  302 临时
    4XX 客户端错误 400 语法错误，无法识别 401 请求未经授权 403 请求不被通过，拒绝提供服务 404 请求地址错误
    5XX 服务器错误 500 服务器出错 503 服务器临时有问题，一段时间可能恢复
  ### 4.https 加密的http 原理解析 [https://mp.weixin.qq.com/s/3NKOCOeIUF2SGJnY7II9hA]