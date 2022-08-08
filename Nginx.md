#  `Nginx`

`Nginx`最重要的三个功能：**反向代理**、**负载均衡**、**动静分离**

- 一是反向代理
  - 【代理服务器接收请求然后分配到具体的服务器，正向代理就是代理客户端的比如说`VPN`，反向代理就是代理服务端的，客户端是感知不到的】
- 二是负载均衡
  - 【可以给不同服务器加权重，权重大的访问量更多】
    1. 轮询：一个个查询。
    2. 加权轮询：权重大的查询被分配的次数概率更大。
    3. `iphash`：对客户端请求的`ip`进行`hash`操作，然后根据`hash`结果将同一个`ip`客户端请求都分发给相同的一个服务端进行处理，这样就可以解决`session`不共享的问题。

- 三是动静分离
  - 一些静态资源如`js css html jpg`等不需要经过后台处理的，我们可以将其跟其它资源拆分开来，将其放到`Nginx`服务器上做缓存操作，这样做可以提高资源响应速度。

特点：占用内存小，并发能力强

略过`windows Linux`安装`Nginx` - `./configure && make && make install`然后访问`80`端口即可

`Linux`常用`Nginx`相关命令：

```shell
./nginx 启动
./nginx -s stop 停止
./nginx -s quit 安全退出
./nginx -s reload 重新加载配置文件
ps -au | grep nginx 查看 nginx 进程
```

配置反向代理：

![](https://img-blog.csdnimg.cn/6679b8d8a4eb40418834cfd89db12679.png)