# 语法

## 元字符
1. \b 

    单词的开头或结尾

2. . 

    除了换行符以外的任意字符

3. \d

    一位数字（0、1、2、3、4....）

    ```js
    0\d\d-\d\d\d\d\d\d\d\d

    0\d{2}-\d{8}
    ```

4. \w

    字母或数字或下划线或汉字

5. \s 

    任意的空白符

6. ^

    匹配字符串的开始

7. $

    匹配字符串的结束

    ```js
    ^\d{5,12}$
    ```            
    重复的次数不低于5次，不得多于12次


## 字符转义

```js
\. \* \\
```    
如果查找. * \，前面要有\来转义。

## 重复

1. 星号*

    前边的内容可以连续重复使用任意次
2. 加号+

    重复1次或多次

3. ?

    重复零次或一次

4. {n} 

    重复n次

5. {n,}

    重复n次 或 更多次

6. {n,m}

    重复n次到m次


## 字符类

[aeiou]
    
匹配任何一个英文元音字母

[.?!]

匹配标点符号(.或?或!)

[0-9] 与 \d 完全一致

[a-z0-9A-Z_] 与 \w 相同

```js
\(?0\d{2}[) -]?\d{8}

//(010)88886666 或 022-22334455 或 02912345678
```

## 分支条件

| 分支条件
    
```js
0\d{2}-\d{8}|0\d{3}-\d{7}
```
匹配两种以连字号分隔的电话号码：一种是三位区号，8位本地号(如010-12345678)，一种是4位区号，7位本地号(0376-2233445)

## 分组

重复多个字符串用小括号来指定子表达式

```js
(\d{1,3}\.){3}\d{1,3}

(\d{1,3}\.){3} 括号里面的子表达式重复三次
```


## 反义

1. \W

    匹配任意不是字母，数字，下划线，汉字的字符

2. \S

    匹配任意不是空白符的字符

3. \D

    匹配任意非数字的字符

4. \B

    匹配不是单词开头或结束的位置

5. [^x]

    匹配除了x以外的任意字符

6. [^aeiou]	

    匹配除了aeiou这几个字母以外的任意字符

## 后向引用

```JS
(?<Word>\w+)
```
把\w+的组名指定为Word,也可以写成`(?'Word'\w+)`
```js
\k<Word>
```
反向引用这个分组捕获的内容


## 零宽断言

```js
(?=exp)
```
匹配exp前面的位置
```js
(?<=exp)
```
匹配exp后面的位置

## 负向零宽断言

```js
(?!exp)
```
匹配后面跟的不是exp的位置
```js
?<!exp)
```
匹配前面不是exp的位置

```js
(?<=<(\w+)>).*(?=<\/\1>)
```
匹配不包含属性的简单HTML标签内里的内容


(?<=<(\w+)>)指定了这样的前缀：被尖括号括起来的单词(比如可能是\<b>)，然后是.*(任意的字符串),最后是一个后缀(?=<\/\1>)。注意后缀里的\/，它用到了前面提过的字符转义；\1则是一个反向引用，引用的正是捕获的第一组，前面的(\w+)匹配的内容，这样如果前缀实际上是\<b>的话，后缀就是\</b>了。整个表达式匹配的是\<b>和\</b>之间的内容

## 懒惰
后面加上一个问号?


1. *?

    重复任意次，但尽可能少重复

2. +?

    重复1次或更多次，但尽可能少重复

3. ??

    重复0次或1次，但尽可能少重复
4. {n,m}?

    重复n到m次，但尽可能少重复
5. {n,}?

    重复n次以上，但尽可能少重复            


    