# DOM 事件

## DOM 事件模型 或 DOM 事件机制

DOM 事件模型(DOM 事件机制)规定浏览器支持两种调用顺序，分别是事件捕获和事件冒泡。

从外向内寻找监听函数，叫事件捕获。

从内向外寻找监听函数，叫事件冒泡。

语法如下
```js
element.addEventListener('click',fn,false)

//element  监听对象
//click    事件名称
//fn       触发事件调用的函数
```
第三个参数可以 不写 或为 false，它表示事件冒泡，如果为true，则为事件捕获。

DOM 事件模型默认是先捕获，后冒泡。比如：
```html
<div id="level1">
    <div id="level2">
        <div id="level3">
            <div id="level4"></div>
        </div>
    </div>
</div>
```
```js
level1.addEventListener('click',()=>{console.log("事件冒泡")})
level1.addEventListener('click',()=>{console.log("事件捕获")},true)
```
在chrome浏览器里，当点击level4时，会先打印出`事件捕获`，再打印出`事件冒泡`。但是在Firefox浏览器里，哪个在前面，哪个先调用，先打印`事件冒泡`，再打印出`事件捕获`

如何看出事件是否冒泡呢？可以通过`bubbles`属性来查看。

```js
e.bubbles
```

如果要阻止事件捕获或者事件冒泡，添加`e.stopPropagation()`
```js
level1.addEventListener('click',(e)=>{console.log("事件捕获1")},true)
level2.addEventListener('click',()=>{console.log("事件捕获2")},true)
level3.addEventListener('click',(e)=>{
    e.stopPropagation();
    console.log("事件捕获3")},true)
level4.addEventListener('click',()=>{console.log("事件捕获4")},true)
```
只会打印出`事件捕获1`、`事件捕获2`、`事件捕获3`。level4就不在打印。

我们可以阻止默认事件的发生。
```js
e.preventDefault()
```
在阻止之前，需要检查 cancelable 属性的值
```js
e.cancelable
```

自定义事件

```html
<button id="btn">按钮</button>
```
```js

btn.addEventListener("click", (e) => {
	const event = new CustomEvent("cat", {
		"detail":{ name:"dog" }
	});
	btn.dispatchEvent(event);
});

btn.addEventListener("cat", (e) => {
	console.log(e.detail);
});
```
点击按钮以后，打印出 `{name:"dog"}` 。

## 事件委托

设想两种情况，第一种，当给100个按钮添加点击事件。第二种，给一个暂时不存在的元素添加点击事件。第一种情况会占内存，第二种元素都没有怎么添加事件呢？这就需要事件委托，即将事件监听设置在它的祖元素上。

```html
<div id="test">
        <button id="btn"><span>1</span></button>
        <button id="btn"><span>2</span></button>
        <button id="btn"><span>3</span></button>
        <button id="btn"><span>4</span></button>
        <button id="btn"><span>5</span></button>
        <button id="btn"><span>6</span></button>
        <button id="btn"><span>7</span></button>
        <button id="btn"><span>8</span></button>
        <button id="btn"><span>9</span></button>
        <button id="btn"><span>10</span></button>
    </div>
```
```js
let span2 = document.querySelectorAll("span")[1];

test.addEventListener("click", (e) => {
	if (e.target === span2) {
		console.log("2");
	}
});
```
当第二个按钮时，会打印出 `2` 。

```html
<div id="test"></div>
```
```js
setTimeout(() => {
	let button = document.createElement("button");
	let span = document.createElement("span");
	span.innerText = "按钮";
	button.appendChild(span);
	test.appendChild(button);
}, 2000);

test.addEventListener("click", (e) => {
	let span = document.querySelector("span");
	if (e.target === span) {
		console.log("点击了按钮");
	}
});
```
按钮在2秒后出现，点击按钮以后，输出`点击了按钮`

事件委托即省了内存，又可以监听动态元素。
