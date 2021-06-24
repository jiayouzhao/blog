# 浅析 URL

## URL

* 组成部分

    URL包含 协议、域名或IP、端口号、路径、查询字符串、描点

    比如：https://www.baidu.com/s?wd=url#1

* 作用

    1. 协议(protocol) -> https
    
        指定使用的传输协议，通常使用的是 ***http*** 或者 ***https*** 协议

    2. 域名 -> www.baidu.com    

        对应IP的别称

    3. 端口号 -> :443 ( 默认端口 )

        不同的服务有不同的号码

        http 80端口

        https 443端口

        FTP 21端口

        一共有65535个端口

    4. 路径 -> /s

        请求不同的页面，此处请求的是百度的搜索功能

    5. 查询字符串 -> ?wd=url

        同一个页面展示不同的内容,展示的是搜寻url的页面             

    6. 锚点 -> #1

        同一个内容跳转到不同位置，锚点不会传给服务器         

## DNS

域名系统(Domain Name System),将 ***域名*** 和 ***IP*** 映射到一个分布式数据库，方便人们访问互联网，是互联网的一项服务。

用户通过浏览器输入网址，向电信/联通提供的DNS服务器询问域名对应的IP，电信/联通会回答一个IP。

浏览器会向这个IP的80/443端口发送请求，查看所需要的内容。

## nslookup 命令

nslookup 命令可以通过DNS查询域名对应的IP

`nslookup baidu.com` 

![结果](/images/nslookup.png)

baidu.com 对应的IP地址有2个：39.156.68.79 和 220.181.38.148

## IP

全称：Internet Protocal

* 作用

    1. 定位一台设备

        - 外网

            需要向网络运营商租用带宽，获得外网IP

        - 内网

            通过路由器[网关]给内网中的不同设备分配不同的内网IP

            127.0.0.1 自己
            
            localhost 通过host指向自己


    2. 封装数据报文，跟其他设备交流

## ping

* 使用

    获得域名对应的IP
    
    ```ping baidu.com```

    ![ping返回的结果](/images/ping.png)

## 域名

访问百度的时候，我们不会输入IP 220.181.38.148，而是 www.baidu.com

因此，域名就是对IP的别称。

一个域名可以对应不同的IP，防止一台机器扛不住叫均衡负载。一个IP对应不同域名，叫共享主机

www.xxxx.com 和 xxxx.com是同一个域名吗？

不是

com是顶级域名

xxxx.com是二级域名，俗称一级域名

www.xxxx.com是三级域名，俗称二级域名

两者是父子关系,但绝大多数www多余的。

