# JS对象的基本用法

JS对象是无序的数据集合，也是键值对的集合

### 一、 声明对象的两种语法

1. 简单声明

    ```js
        let obj = {name:'jack',age:18}
    ```
2. 复杂且正规声明

    ```js
        let obj = new Object({name:'jack',age:18})
    ```    
3. 特殊
    
    在火狐浏览器里边，不写let，它是一个代码块
    ```js
        {
            name:'jack';
        }
    ```    
    输出为 `"jack"`

    在chrome浏览器，有无分号是区别

    ```js
    {
        name:'jack'
    }
    ```
    输出为 `{name:'jack'}`

    ```js
    {
        name:'jack';
    }
    ```
    输出为 `'jack'`

4. 键名是字符串，可以写任意字符串。
    
    当引号省略，只能写标识符，但它仍旧是字符串。

    也可以用数字做键名，但它还是字符串
    
    ```js
    let obj = {
        2 : '2222'
    }

    Object.keys(obj)

    //输出为 ["2"]
    ```

    如果用变量做属性名，需要加[]

    ```js
    let a = 'xxx';
    let obj =  {
        [a]:'yyy'
    }
    ```
    输出为 `{xxx:yyy}`

    ```js
    let obj =  {
        [1+2+3+4] :10
    }
    ```
    输出为 `{10:10}`,[ ]会变量求值

### 二、 删除对象属性

1. 语法

    delete obj.xxx 或者 delete obj['xxx']

    它不同于 obj.xxx = undefined;

    ```js
    let obj = {name:'jack',age:10}

    //delete
    delete obj.name
    // obj = {age:10}
    
    obj.age = undefined;
    // obj  ={age:undefined}
    ```

    delete是直接删掉属性，而 obj.xxx=undefined 是给属性赋值为undifined

2. 检测是否有属性名

    'xxx' in obj

    ```js
    let obj = {age:10}

    'age' in obj 
    
    //返回 true
    ```    
    含有属性名，且值为undefined

    ```js
    'age' in obj && obj.age === undefined
    ```
    但是 obj.age === undefined 不能判断 **'age'** 是否是obj的属性。
    ```js
    let obj = {name:'jack'}

    obj.age === undefined
    // true
    'age' in obj 
    // false

    let obj2 = {name:'jack',age:undefined}
    obj2.age === undefined
    // true
    'age' in obj
    // true
    ```

### 三、 查看对象属性

1. 语法

    `Object.keys(obj)` 查看属性名

    `Object.values(obj)` 查看属性值

    `Object.entries(obj)` 查看属性 

    ```js
    let obj = {name:'jack', age:10}

    Object.keys(obj);
    //返回 ["name","age"]

    Object.values(obj);
    //返回 ["jack",10]

    Object.entries(obj)
    //返回 [["name","jack"],["age",10]]
    ```
2. 写法区别

    obj.name 、obj['name'] 、obj[name]是有区别的。

    ```js
    let name  = 'jack';
    let obj = {name:'jack',age:19}

    console.log(obj.name);  // jack
    console.log(obj['name']);//jack
    console.log(obj[name]);// obj["jack"] undefined
    ```
    注意的是，obj.name的写法中，name始终是字符串。

### 四、 修改或增加对象的属性

1. 直接赋值

    ```js
    let name = 'username'
    let obj = {name:'jack'}
    obj.age = 10;
    obj['gender'] = 'man'

    // {name:'jack',age:10,gender:'man'}

    obj[name] =  'Bob'

    // {name:'jack',age:10,gender:'man',username:'Bob'}
    ```

2. 共有属性的修改增加

    无法通过自身修改或增加共有属性

    ```js
    let obj = {name:'jack'}
    let obj2 = {name:'Bob'}

    obj.toString = "xxx"
    obj2.toString() //[object Object]
    ```    
    obj修改的只是自己身上的属性，obj2.toString访问的仍然是原型上的属性

    因此，修改增加共有属性可以这样做：

    ```js
    obj.__proto__.toString = 'xxx' //不推荐

    Object.prototype.toString = 'xxxx' //可以使用
    ```
    但是，最好不要修改原型，以免发生问题。

3. 对象之间

    如果想要一个对象的原型拥有另一个对象的全部属性，使用Object.create(common)

    ```js
    //不推荐写法

    let obj = {name:'jack'}
    let obj2 = {name:'Bob'}
    let common = {'国籍':'英国'}

    obj.__proto__ = common
    obj2.__proto__ = common
    ```
    ```js
    //推荐

    let common = {'国籍':'英国'}
    let obj = Object.create(common);
    ```
    如果继续给obj对象添加大量属性，这里要用到**Object.assign()函数**,这是一个批量赋值的方法。
    ```js
    Object.assign(obj,{name:'jack',age:10,gender:'man'})
    ```
    当然，如果添加很少得属性，可以直接`obj.name = 'jack'`
    
    有一种情况，如果我们已经给obj对象设置了属性，再`obj = Object.create(common)`，就会清除obj自身的属性,在原型里添加common的属性。

    所以Object.create属性要一开始就使用。


### 五、 'name' in obj 和 obj.hasOwnProperty('name')的区别

1. 查看属性是 **自身属性** 还是 **共有属性**可以使用hasOwnProperty函数

    ```js
    let obj = {name:'jack'}

    obj.hasOwnProperty('toString');

    //返回 false

    obj.hasOwnProperty('name');

    //返回 true
    ```

2. 'name' in obj 是用来知道 obj 是否有name这个属性，不管是自身还是原型，只要有，那就是true。但是它不知道这个属性是来自自身还是原型，那么这就需要用到hasOwnProperty，如果是自身属性，返回true，反之，输出false。

