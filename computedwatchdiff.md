# computed 和 watch 的区别 

* computed 是计算属性，依赖数据进行计算并缓存。

    使用的时候，不需要加括号。
    ```js
    new Vue({
        data:{
            message:'message'
        },
        template:`
            <div>
                <p>{{message}}</p>
                <p>{{computedMessage}}</p>
            </div>
        `,
        computed:{
            computedMessage(){
                return this.message.split("").reverse().join("")
            }
        }
    })
    ```
    computedMessage 是根据 message 计算而来的，如果 message 不变的话，它就会变成缓存，computed 的值就不会重新计算。

* watch 是用来侦听的，当数据发生变化时，执行对应的函数。

    deep ：true/false。
    
    默认为 false ，在任何被侦听的对象的属性改变时被调用，不论对象的嵌套有多深。

    immediate : true 
    
    回调会在监听开始之后被立即调用。

    ```js
    const vm = new Vue({
        data:{
            a:1,
            b:2,
            c:{
                cc:3
            },
            d:{
                dd:5
            },
            e:4
        },
        watch:{
            a(newValue,oldValue){},
            b:{
                handler:function(val,oldVal){},
                immediate:true
            },
            c:{
                handler:function(val,oldVal){},
                deep:true
            },
            "d.dd":function(val,oldVal){}
        }
    })

    vm.$watch("e",function(val,oldVal){})
    ```
    谨慎在侦听的时候，在箭头函数里用 this ，因为 this 不是指向 vm 。

