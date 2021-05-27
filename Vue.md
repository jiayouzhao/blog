# Vue 两种版本

## 介绍 

Vue有两个版本，一个是完整版 (vue.js)，另外一个是非完整版 (vue.runtime.js)。

完整版有 compiler ，用来将模板字符串编译成为 JavaScript 渲染函数的代码，导致完整版的体积很大。

非完整版没有 compiler ，所以体积会比完整版小大概 30% 。

## template 和 render 的使用

* template 版本

    ```js
    new Vue({
        el:"#app",
        template:`
            <div @click="add">{{n}}<button>+1</button></div>
        `,
        data:{
            n:0
        },
        methods:{
            add(){
                this.n ++
            }
        }
    })
    ```

* render 版本

    ```js
    new Vue({
        el:"#app",
        render(h){
            return h('div',[this.n,h("button",{on:{click:this.add}}),"+1"])
        },
        data:{
            n:0
        },
        methods:{
            add(){
                this.n ++
            }
        }
    })
    ```

## codesandbox.io 使用

1. 进入 [codesandbox.io](https://codesandbox.io/) 网站。

2. 不要登录，直接点击右上角 create Sandbox

3. 选择 Vue 项目，即可操作。

