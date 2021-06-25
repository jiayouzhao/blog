# StrictMode 严格模式

做项目的时候，碰到一个很奇怪的bug。

在函数组件里，使用了 useState hook，它的初始值是从 localStorage 取到的。而 localStorage 里面有一个数字自增的id。比如，原本 id 应该是2, 但是渲染到页面上就变成了3。
debugger的时候，发现 useState 执行了两遍，就导致了 id 自增了两次。

React 文档里面很清楚的写着，` 这个初始 state 参数只有在第一次渲染时会被用到。 `那为什么会碰到执行两次的 bug 呢？

经过仔细检查代码，发现了这么个玩意。

```ts
ReactDOM.render(
	<React.StrictMode>
		<App />
	</React.StrictMode>,
	
	document.getElementById("root")
);
```

StrictMode 模式，其中的作用之一是 **检测意外的副作用**。

渲染阶段的生命周期包括以下 class 组件方法:

+ constructor
+ componentWillMount (or UNSAFE_componentWillMount)
+ componentWillReceiveProps (or UNSAFE_componentWillReceiveProps)
+ componentWillUpdate (or UNSAFE_componentWillUpdate)
+ getDerivedStateFromProps
+ shouldComponentUpdate
+ render
+ setState 更新函数（第一个参数）

因为上述方法可能会被多次调用，所以不要在它们内部编写副作用相关的代码，这点非常重要。

那么，这个 bug 也就不是 bug 了，是在严格模式下的工作方式，导致了 useState 执行了两次。用了俩天时间翻阅 react 文档解决了问题，看来文档还是要重头到尾仔细看。