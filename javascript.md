# JS的那点事儿

西游记唐僧每次介绍自己，都会说贫僧唐三藏，从东土大唐而来，去西天拜佛取经。这几句话包涵了三个问题，我是谁，从哪里来，到哪里去。那么，在学习JavaScript之前，这三个问题也可以帮助我们了解它。

## 一、我是谁

JavaScript是一种具有函数优先的轻量级，解释型或即时编译型的编程语言([百度百科](https://baike.baidu.com/item/javascript))。

它有曾用名吗？有的。当时的Java即是编程语言，也是一种咖啡，所以JS早期起名Mocha(摩卡)，再改为LiveScript，最后为了让它看起来像Java取名JavaScript。因此，Java跟JavaScript就如同老婆跟老婆饼，是不一样的。

## 二、从哪里来

JavaScript是谁发明的呢？布兰登(Brendan Eich)。

![布兰登](/images/people.png)

布兰登在1995年4月被网景公司录用，此前网景公司发布了第一个网络浏览器，

![浏览器](/images/web.png)


急需一种网页脚本语言，让浏览器可以与网页互动，而Sun公司大肆宣传Java，看起来有可能成为未来的主宰。

![Java](/images/java.png)

让网景公司动了心，决定未来的网页脚本语言看上去与Java足够相似，指定Brendan Eich为“简化版Java语言”的设计师。于是，为了应付公司的安排，他只用10天时间设计出了JavaScript的最初版本。(具体内容跳转[阮一峰博客](http://www.ruanyifeng.com/blog/2011/06/birth_of_javascript.html))


## 三、到哪里去

JavaScript到哪里去呢？它可以作为开发web页面的脚本语言，也可以作用到很多非浏览器环境中。

主要功能有嵌入动态文本于HTML页面、对浏览器事件做出响应、读写HTML元素、在数据被提交到服务器之前验证数据、检测访客的浏览器信息、控制cookies，包括创建和修改等、基于Node.js技术进行服务器端编程。

但是它也有设计缺陷，比如不适合开发大型程序、非常小的标准库、null和undefined、全局变量难以控制、动插入行尾分号、加号运算符、NaN、数组和对象的区分、== 和 ===、基本类型的包装对象。（参考[阮一峰博客](http://www.ruanyifeng.com/blog/2011/06/10_design_defects_in_javascript.html)）

虽然JavaScript设计的很仓促，有设计缺陷，但是最后也成功逆袭，成为如今很火的一门编程语言。
