### 1. 表达式和语句

* 表达式一般都有值，比如

    1+2 表达式的值为3

    sun(1,2) 表达式 **值** 为函数的**返回值**

    console.log 表达式的值为函数本身

    console.log(3) 表达式的值为undefined

    ```js
        //console.log(3); 可以这么理解
        function fn(){
            return 
        }

        fn()  //undefined
    ```

* 语句可能有值也可能没有，一般会改变环境(声明、赋值)

    var a = 1 就是一个语句

* 但是他们并不是上面说的那么绝对。

### 2. 标识符的规则

* 第一个字符，可以是 **Unicode字母** 或 **$** 或 **_** 或 中文。

    ```js
        var a = 1;
        var ζ = 1;
        var $ = 1;
        var _ = 1;
        var 标识 = 1;
    ```

* 后面的字符，除了上面所说，还可以有数字

    ```js
        var $1 = 2;
    ```

### 3. if else 语句

* #### 语法

    ```js
        //标准
        if(表达式){
            语句1
        } else {
            语句2
        } 
        //省略
        if(表达式)
            语句1
    ```

* #### 其他情况

    1. 语句1里面可以嵌套if else ,同样语句2里面也可以嵌套 if else。

    2. ```js
            let a = 1;
            if(a ===2)
                console.log("a")
                console.log("a等于2")
        ```
        输出结果为`a等于2`。如果 if 语句省略了{},则它只执行离它最近的语句。
    
        上面的代码其实是这样的

        ```js
            if(a===2)
                console.log("a")
            console.log("a等于2");    
        ```

        当然还有特殊情况，比如

        ```js
            let a = 2;
            if(a === 2)
                console.log("a"),console.log("a等于2")
        ```
        输出结果为`a` `a等于2`，逗号不同于分号，它会继续执行逗号后面的内容。

* #### 推荐写法

    ```js
        let a = 1;
        if(a === 1){
            console.log("a是1");
        } else if ( a === 2) {
            console.log("a是2");
        } else {
            console.log("其他");
        }
    ```
    函数里面如果有多个if，则可以省略else

    ```js
        let a = 1
        function fn(){
            if(a === 1){
                return console.log("a是1");
            }
            if(a === 2){
                return console.log("a是2");
            }
            return console.log("其他")
        }
    ```
* #### switch 语句 

    if else 语句的升级版，认识它的写法即可。

    ```js
        let a = 1
        switch (a) {
            case "1":
                console.log("a是1");
                break;
            case "2":
                console.log("a是2");
                break;
            default:
                console.log('a是其他');        
        }
    ```
* #### 问好冒号表达式 (三目运算)

    ```js
        function num(a,b){
            if(a > b){
                return a
            } else {
                return b;
            }
        }
        
    ```
    以上 if else 语句可以写成:

    ```js
        function num(a,b){
            return a > b ?  a :  b;
        }
    ```

* #### &&运算符

    ```
        1 && 2 && 3 && 4
    ```
    输出结果为4
    ```
        1 && 0 && 2
    ```
    输出结果为 0    
    ```
        0 && 1 && 2
    ```
    输出结果0

    A && B && C && D 取第一个假的值或者D

* #### || 运算符
    
    ```
        0 || 1 || 2
    ```
    输出结果为 1
    ```
        2 || 1 || 0
    ```
    输出结果为 2
    ```
        0 || 0 || 3
    ```
    输出结果为 3

    A || B || C || D 取第一个为真的值 或者 D

### 4. while for 语句

* while 语法

    ```js
        let a = 1;
        while(a < 5){
            console.log(a);
            a = a + 1;
        }
    ```
    当 a < 5 时，会执行 `console.log(a)` `a = a + 1`,输出结果为 `1,2,3,4`

    当 a > 5 时，跳出 while语句，执行后面的语句

* for 语句

    while语句的方便写法

    ```js
        for(let a = 1; a < 5 ; a++){
            console.log(a);
        }
    ```    
    执行顺序是，先判断a是否小于5，如果小于5，执行console.log(a);然后执行 a = a + 1，再次判断是否进入循环，如果 a >= 5, 跳出循环。输出结果为 `1 2 3 4`

    但是如果将 **let** 改为 **var**

    ```js
        for(var a=1;a<5;a++){
            console.log(a);
        }
    ``` 
    输出结果与上面的结果还是一样的，`1 2 3 4` 。

    如果添加setTimeout

    ```js
        for(var i=0;i<5;i++){
            setTimeout(()=>{
                console.log(i);
            })
        }
    ```
    输出结果为 `5 5 5 5 5`
    
    为什么不是`0 1 2 3 4` ，因为setTimeout会在for语句执行完之后才会执行，当for语句执行完时，i=5，开始执行setTimeout，所以，输出结果成为`5 5 5 5 5`

    如果想输出`0 1 2 3 4`，代码如下

    ```js
        for(let a = 0;a<5;a++){
            setTimeout(()=>{
                console.log(a);
            })
        }
    ```
    当然 for语句 可以省略部分内容，如

    ```js
        let a = 0;
        for(;a<5;a++){
            console.log(a);
        }
    ```

    但要小心死循环

    ```js
        let a = 0;
        for(;;){
            console.log(a);
        }
    ```

### 5. break continue

* break 

    退出所有循环

    ```js
    for(var i =1;i<10;i++){
        if(i%2 === 1){
            console.log(i);
            break;
        } else {
            console.log(i);
        }
    }
    ```
    输出结果为 `1` 。

    ```js
    for(var i=1;i<10;i++){
        for(var j=100;j<200;j++){
            if(i === 5){
                break
            }
        }
        console.log(i);
    }
    ```
    输出结果为`1 2 3 4 5 6 7 8 9`，也就是说break只能**退出离它近**的for循环。

* continue

    退出当前一次循环

    ```js
    for(var i =1;i<10;i++){
        if(i%2 === 1){
        
            continue;
        } else {
            console.log(i);
        }
    }
    ```
    输出结果为 `2 4 6 8`
    
### 6. label

* 语法

    ```js
    foo: {
        console.log(1);
        break foo;
        console.log('本行不输出');
    }
    console.log(2);
    ```
    输出结果为 `1 2`

    ```js
    {
        foo:1;
    }
    ```
    chrome浏览器在有分号和无分号有区别
    
    有分号即为 label ,值为1。

    无分号为对象。
