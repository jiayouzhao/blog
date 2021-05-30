# Vue 中的 .sync 修饰符

Vue 文档是这样描述的，我们可能需要对一个 prop 进行“双向绑定”。但是，真正的双向绑定会带来维护上的问题，因为子组件可以变更父组件，且在父组件和子组件两侧都没有明显的变更来源。

因此，推荐 update:myPropName 的模式取而代之。

```js
Vue.component("ButtonAdd",{
    props:["num"],
    template:`
        <div>
            {{num}}
            <button @click="$emit('update:addNum',num+1)">+1</button>
        </div>
    `
})


new Vue({
    data:{
        n:0
    },
    template:`
        <div>
            {{n}}
            <ButtonAdd :num="n" @update:addNum = "$event = n"/>
        </div>
    `,
    components:{
        ButtonAdd
    }
}).$mount("#app")
```

为了方便起见，Vue 提供了一个缩写，即 .sync 修饰符

```js
<ButtonAdd :num="n" :addNum.sync="n" />
```
需要注意的是，.sync 修饰符的 v-bind 不能和表达式一起使用 `v-bind:addNum.sync="n+'!'"` 。