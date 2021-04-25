# a标签
## 属性
### 1. href
* 网址

     ```html
      <a href="https://baidu.com">百度</a>
      <a href="http://baidu.com">百度</a>
      <a href="//baidu.com">百度</a> 
     ```
     网址路径用//，//baidu.com是最高级，可以自动适应https或者http。
     
* 路径
     ```html
      <a href="/a/b/c">新页面</a>
      <a href="a/b/c">新页面</a>
     ```
     路径 /a/b/c 是以开启http服务的目录为根目录，区别于文件根目录
     ```html
     <a href="index.html"></a>
     <a href="./index.html"></a>
     ```
     在当前目录打开index.html，两种方式效果相同
     
* id (跳转到内部锚点)

     ```html
     <div>
        <p>1</p><p>2</p><p>3</p><p>4</p><p>5</p><p>6</p><p id="num7">7</p><p>8</p>
        <p>9</p><p>10</p><p>11</p><p>12</p><p>13</p><p>14</p>
     </div>
     ```
     ```html
     <a href="#num7">点击查看标签7</a>
     ```
      点击a标签以后，页面滚动到数字7的位置
    
* 伪协议

     ```html
     <a href="javascript:;">点击</a>
     ```
     在点击之后，没有动作的a标签

     ```html
     <a href="mailto:***@163.com">发邮件给某人</a>
     ```
     ```html
     <a href="tel:1361111111">打电话给某人</a>
     ```

### 2. target

* _blank

    ```html
    <a href="//baidu.com" target="_blank">百度</a>
    ```
    跳转到新的页面

* _self

    在当前页面打开
   
* 自定义

    ```html
    <a href="//baidu.com" target="aaa">百度</a>
    <iframe src="" name="aaa"></iframe>
    ```

# img标签

* 属性

    alt　图像的文本描述，当无法加载图片时，浏览器会显示文本描述
    height/width 图像的宽/高，直接写数字
    src　图片的文件路径

* 事件
    onload  图片加载成功后立即执行

    onerror 图片加载发生错误时会触发

* 响应式

    ```css
    max-width:100%;
    ```

# table标签

* 完整示例

    ```html
    <table>
        <thead>
        <tr>
            <th>语文</th>
            <th>数学</th>
        </tr>
        </thead>
        <tbody>
        <tr>
            <th>小王</th>
            <td>99</td>
            <td>99 </td>
        </tr>
        <tr>
            <th>小刘</th>
            <td>100</td>
            <td>100</td>
        </tr>
        </tbody>
        <tfoot>
        <tr>
            <td></td>
            <td></td>
        </tr>
        </tfoot>
    </table>
    ```

* 相关样式    

    ```css
    table-layout: auto | fixed;
    ```
    auto 浏览器自动表格布局

    fixed 通过自定义宽度来布局
    
    ```css
    border-collapse:collapse | separate;
    ```
    collapse 相邻单元格共用一条边框

    separate 单元格有独立的边框

    ```css
    border-spacing: 0px;
    ```
    单元格边框之间的距离
