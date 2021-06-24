# css动画

css渲染过程依次包含布局、绘制、合成，其中布局和绘制有可能会被省略。

## 浏览器的渲染原理

* 步骤

    1. 根据HTML构建HTML树 (DOM)
    2. 根据CSS构建CSS树 (CSSOM)
    3. 将两颗树合并成一颗渲染树 (render tree)
    4. Layout布局 (文档流、盒模型、计算大小和位置)
    5. Paint绘制 (把边框颜色、文字颜色、阴影等画出来)
    6. Composite (根据层叠关系展示画面)

* 树

    ![效果](/images/tree.png)

* 三种更新方式

    1. js/css > 样式 > 布局 > 绘制 >  合成

        ![图示一](/images/one.png)

        比如：div.remove();

    2. js/css > 样式 > 绘制 > 合成

        ![图示二](/images/two.png)

        比如： 改变背景颜色

    3. Js/css > 样式 > 合成

        ![图示三](/images/3.png)

        比如： transform        

## transition

为一个元素在不同状态下定义不同的过渡效果

* 语法

    属性名 时长 过渡方式 延迟

    ```css
        transition:width 2s ease 2s; /*单个*/
        transition: width 2s, height 3s;/* 多个*/
    ```

* 过渡方式

    linear | ease | ease-in | ease-out | ease-in-out | cubic-bezier

* 属性过渡

    并非所有属性都能过渡，比如display:block和display:none;    
    
* transitionend 事件会在transition结束后发触发    

## animation

* 属性

    1. animation-name

        指定动画名称，由@keyframes定义动画

        ```css
        @keyframes move {
            from {
                transform:translateX(0px);
            }
            to {
                transform:translateX(200px);
            }
        }
        @keyframes move {
            0% {
                transform:translateX(0px);
            }
            50% {
                transform:translateX(100px);
            }
            100% {
                transform:translateX(200px);
            }
        }
        ```

    2. animation-duration 

        时长

    3. animation-timing-function

        同 transition 的过渡方式

    4. animation-delay 

        延迟

    5. animation-iteration-count

        动画结束前运行的次数

        ```css
        animation-iteration-count: infinite | <number>
        ```

    6. animation-direction

        动画是否方向播放

        - normal 动画结束后，重新回到起点开始
        - alternate 动画交替反向运行
        - reverse 反向运行动画，由尾到头运行
        - alternate-reverse 反向运行并交替

    7. animation-fill-mode

        动画运行后保留在哪一帧

        - forwards 最后一帧
        - backwards 第一帧

    8. animation-play-state

        动画运行或暂停

        - running
        - paused

* 语法

    ```css
    animation: move 3s infinite alternate ;
    ```


## css动画优化

参考地址：[谷歌优化](https://developers.google.com/web/fundamentals/performance/rendering/stick-to-compositor-only-properties-and-manage-layer-count)



