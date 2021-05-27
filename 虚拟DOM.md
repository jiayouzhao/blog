# 虚拟 DOM 和 DOM diff

## 虚拟 DOM

虚拟 DOM 就是通过 JavaScript 对象来模拟真实的 DOM 树，它内部通常含有标签名、标签上的属性、事件监听和子元素，以及一些其他属性。

## 虚拟 DOM 的优点

1. 减少 DOM 操作
    
    * 虚拟 DOM 可以将多次操作合并为一次操作
    * 虚拟 DOM 借助 DOM diff 可以把多余的操作省掉

2. 跨平台

    虚拟 DOM 不仅可以变成 DOM ，还可以变成小程序、iOS应用、安卓应用，因为虚拟 DOM 本质上只是一个 JS 对象

## 虚拟 DOM 的缺点

需要额外的创建函数，如 createElement 或 h ，但可以通过 JSX 来简化成 XML 写法 

## DOM diff

DOM diff 是虚拟 DOM 的对比算法，该算法主要是对比两颗虚拟 DOM 的不同点。它其实就是一个函数，我们通常称为 patch ，通过函数内部的逻辑，patches = patch(oldVNode,newVNode) ，来找到虚拟 DOM 的区别，patches 就是需要更新的 DOM 操作。

大概分为以下几种逻辑

1. Tree diff

    将新旧两棵树逐层对比，找出哪些节点需要更新。如果节点是组件就走 Component diff，否则就走 Element diff

2. Component diff

    如果节点是组件，就先看组件类型，类型不同直接替换(删除旧的)，类型相同则只更新属性，然后深入组件做Tree diff (递归)

3. Element diff

    如果节点是原生标签，则看标签名。标签名不同直接替换，相同则只更新属性。然后进入标签后代做 Tree diff (递归)

## DOM diff 的优点

只更新需要修改的节点，不会大面积的渲染。

## DOM diff 的问题

同级节点对比会出现 bug，在 Vue 中，如果用 index 作为 key ，那么在删除第二项的时候，index 就会从1 2 3 变为 1 2 ，那么 Vue 依然会认为你删除的是第三项。因此，在列表渲染时，key 值的绑定对象最好不要使用 index 。