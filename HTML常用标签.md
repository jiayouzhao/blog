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
   
   * 伪协议
     ```
     <a href="javascript:;">点击</a>
     ```
     
