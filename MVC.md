# 浅析 MVC

## 概念

MVC (Model-View-Controller) 是一种软件设计模式，它强调分离软件的业务逻辑和显示。这种“分离”提供了更好的分工和改进的维护。

1. Model ：模型持有所有的数据、状态和程序逻辑

    ```js
    class Model{
        constructor(){
            //数据
        }
        //程序逻辑
        update(){}//修改数据
        get(){}//查看数据
    }
    ```

2. View ：负责界面的布局和显示

    ```js
    class View {
        constructor(el,html,init,render){
            this.el = el;//html放入的元素
            this.html = html;//html模板
            this.render = render;//刷新页面
            this.init = init;//初始化页面
        }
    }
    ```

3. Controller ：负责模型和界面之间的交互

    ```js
    class Controller{
        constructor(options){
            Object.assign(this,options)//事件函数添加到对象
            /*this.events=options.events*///事件哈希表
        }
        autoBindEvents(){}//绑定事件
    }
    ```
三个模块只专注做自己的事，不需要考虑其他模块，符合最小知识原则。

## EventBus

EventBus称为事件总线，用来负责对象之间的通信。jquery和vue都用到了EventBus，这里用jquery的API，如下：

1. EventBus.on() 
    
    用来监听事件

    ```js
    EventBus = ${"body"}
    EventBus.on(eventName,fn)

    /***/
    EventBus.on("m:update",()=>{
        console.log("1");
    })
    ```


2. EventBus.trigger()

    用来触发事件

    ```js
    EventBus.trigger(eventName)

    /***/
    EventBus.trigger("m:update")
    ```

3. EventBus.off()

    用来解绑事件  

    ```js
    EventBus.off(eventName,fn)

    /***/
    EventBus.off("m:update",()=>{
        console.log("1")
    })
    ```  

## 表驱动编程

> 表驱动法是一种可以在表中查找信息，而不必用很多逻辑语句来把它们找出来的方法。

多次使用的代码，我们可以用表驱动编程

```js
if(key === ".add"){
    add()
} else if(key === ".sub"){
    sub()
} else if(key === ".mul"){
    mul()
} else if(key ===".divide"){
    divide()
}
```
代码冗长，也不利于后期维护，可以改为表驱动

```js
let obj = {
    ".add":add,
    ".mul":mul,
    ".sub":sub,
    ".divide":divide
}
add(){}
mul(){}
for(let key in obj){
    $(key).on("click",obj.key)
}
```

## 模块化

模块化可以让我们对代码有更好的管理，只专注于当前模块，不需要考虑其他模块。

方便代码的可读性。在模块化之前，代码的可读性很差，需要我们去标记注释来辅助我们记忆，但是模块化之后，我们不用去查找代码的相关内容，直接在模块里获取信息。

模块化还可以代码解耦和代码的重复利用。

ES6语法

```js
// app1.js
let app1 = {
    init(){}
}

export default app1
```
```js
//main.js
import app1 from "./main.js"

app1.init()
```
