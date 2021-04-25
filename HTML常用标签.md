# a标签
## 属性
1. href
   * 网址
     ```
      <a href="https://baidu.com">百度</a>
      <a href="http://baidu.com">百度</a>
      <a href="//baidu.com">百度</a> 
     ```
     网址路径用//，//baidu.com是最高级，可以自动适应https或者http。
     
   * 路径
     ```
      <a href="/a/b/c">新页面</a>
      <a href="a/b/c">新页面</a>
     ```
     路径 /a/b/c 是以开启http服务的目录为根目录，区别于文件根目录
     ```
     <a href="index.html"></a>
     <a href="./index.html"></a>
     ```
     在当前目录打开index.html，两种方式效果相同
     
   * id
     ```
     <div>
        <p>1</p><p>2</p><p>3</p><p>4</p><p>5</p><p>6</p><p id="num7">7</p><p>8</p>
        <p>9</p><p>10</p><p>11</p><p>12</p><p>13</p><p>41</p>
     </div>
     ```
     ```
     <a href="#num7">点击查看标签7</a>
     ```
      点击a标签以后，页面滚动到数字7的位置
    
   * 伪协议
     ```
     <a href="javascript:;">点击</a>
     ```
     在点击之后，没有动作的a标签
     ```
     <a href="mailto:***@163.com">发邮件给某人</a>
     ```
     ```
     
     ```
