# 沉默的jQuery

jQuery要学吗？要学。它可以为其他高级框架的学习打好基础，也可以强化前端工程师的JS基础。正如官网所说，jQuery 是一个高效、精简并且功能丰富的 JavaScript 工具库。它提供的 API 易于使用且兼容众多浏览器，这让诸如 HTML 文档遍历和操作、事件处理、动画和 Ajax 操作更加简单。

## 获取元素
在使用jQuery之前，先想一想JS的用法，如果我们要操作一个元素，就要先获取到这个元素,经常会用到`document.querySelector`或者`document.querySelectorAll`等API，但是如果是jQuery的话，只需要`jQuery()`或者简写`$()`,括号里面是选择表达式。
```js
$(document) //选择整个文档对象

$('#myId') //选择ID为myId的网页元素

$('div.myClass') // 选择class为myClass的div元素

$('input[name=first]') // 选择name属性等于first的input元素

$('a:first') //选择网页中第一个a元素
```
## 链式操作

像自行车车链，一环扣一环。将所有的操作像链子一样链接起来。

```js
$("div").find("p").html('hello world')
```
找到div元素，选择其中的p元素，将它的内容改成'hello world'。

## 创建元素

可以直接写入要创建的标签，比如
```js
$("<div><p></p></div>")
```
这样就创建了一个div元素包含着p元素，但是要添加到文档里，就要使用元素的操作：移动。

## 移动元素

移动的操作方法一共有四对：
```js
.insertAfter()和.after()：在现存元素的外部，从后面插入元素

.insertBefore()和.before()：在现存元素的外部，从前面插入元素

.appendTo()和.append()：在现存元素的内部，从后面插入元素

.prependTo()和.prepend()：在现存元素的内部，从前面插入元素
```

## 修改元素的属性

为每个匹配的元素添加指定的样式类名

```js
.addClass('yellow')
```
给元素设置css属性,可以是一个或多个属性
```js
.css("background","yellow")
```
可以给匹配的元素指定文本内容
```js
.text("新内容")
```

####  jQuery还有很多API值得我们去探究，如果深入研究的话，比如像闭包、设计模式、封装等知识都值得我们去学习。

#### 推荐：

* [阮一峰的jQuery设计思想](http://www.ruanyifeng.com/blog/2011/07/jquery_fundamentals.html)

* [jQuery文档](https://www.jquery123.com/)






