# JS函数的执行时机

* 先来看一段代码

    ```js
    let i = 0
    for(i = 0; i<6; i++){
        setTimeout(()=>{
            console.log(i)
        },0)
    }
    ```
    打印出来的是`6 6 6 6 6 6`,为什么不是`0 1 2 3 4 5 `呢？

    先从setTimeout说起，它是一个定时器，在定时器到期后执行里面的函数。也就是说当i=0时，i<6，setTimeout里面的函数不立即执行，等到i=6时，i等于6，不符合for循环条件，这时执行setTimeout里面的函数,这里要说一下变量 **i**。

    变量 **i** 是一个全局变量，当for循环走完以后，全局变量 **i** 的值变为6，所以，console.log(i)就只能打印6个6.

* 一定要打印`0 1 2 3 4 5`,可以将`let i=0`放进for循环的括号里,如下

    ```js
    for(let i = 0; i<6; i++){
        setTimeout(()=>{
            console.log(i)
        },0)
    }
    ```

* 还有其他解决办法吗？

    1. 闭包

        ```js
        for (var i = 0; i < 6; i++) {
            !function(j) {
                setTimeout( () => {
                    console.log(j);
                }, 0 );
            }(i);
        }
        ```
        
    2. 将setTimeout提出来另外放在函数里

        ```js
        function setTime(i) {
            setTimeout( () => {
                console.log(i);
            },0);
        }
        for (var i = 0; i < 6; i++) {
            setTime(i);
        }
        ```    

