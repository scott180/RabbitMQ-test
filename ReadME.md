## RabbitMQ
*   [0、RabbitMQ教程](#RabbitMQ) 
*   [1、安装 ErLang](#ErLang) 
*   [2、安装 RabbitMQ](#RabbitMQ-install) 

> [github]( https://github.com/scott180/RabbitMQ-test ) &ensp; [dillinger]( https://dillinger.io/ )  &ensp;  [作业部落]( https://www.zybuluo.com/mdeditor )   


<h2 id="RabbitMQ"></h2>

### 0、RabbitMQ教程
>[RabbitMQ教程]( https://blog.csdn.net/hellozpc/article/details/81436980 ) &ensp; [RabbitMQ 详解]( http://www.ityouknow.com/springboot/2016/11/30/spring-boot-rabbitMQ.html ) &ensp;[什么时候该使用MQ]( https://mp.weixin.qq.com/s?__biz=MjM5ODYxMDA5OQ==&mid=2651960012&idx=1&sn=c6af5c79ecead98daa4d742e5ad20ce5&chksm=bd2d07108a5a8e0624ae6ad95001c4efe09d7ba695f2ddb672064805d771f3f84bee8123b8a6&mpshare=1&scene=1&srcid=04054h4e90lz5Qc2YKnLNuvY )

-----

>消息队列（Message Queue，简称MQ），从字面意思上看，本质是个队列，FIFO先入先出，只不过队列中存放的内容是message而已。
其主要用途：不同进程Process/线程Thread之间通信。

通常我们谈到队列服务, 会有三个概念： 发消息者、队列、收消息者，RabbitMQ 在这个基本概念之上, 多做了一层抽象, 在发消息者和 队列之间, 加入了交换机 (Exchange). 这样发消息者和队列就没有直接联系, 转而变成发消息者把消息给交换器, 交换器根据调度策略再把消息再给队列。

那么，其中比较重要的概念有 4 个，分别为：虚拟主机，交换机，队列，和绑定。

- 虚拟主机：一个虚拟主机持有一组交换机、队列和绑定。为什么需要多个虚拟主机呢？很简单， RabbitMQ 当中，用户只能在虚拟主机的粒度进行权限控制。 因此，如果需要禁止A组访问B组的交换机/队列/绑定，必须为A和B分别创建一个虚拟主机。每一个 RabbitMQ 服务器都有一个默认的虚拟主机“/”。
- 交换机：Exchange 用于转发消息，但是它不会做存储 ，如果没有 Queue bind 到 Exchange 的话，它会直接丢弃掉 Producer 发送过来的消息。 这里有一个比较重要的概念：路由键 。消息到交换机的时候，交互机会转发到对应的队列中，那么究竟转发到哪个队列，就要根据该路由键。
- 绑定：也就是交换机需要和队列相绑定，是多对多的关系。

#### 交换机(Exchange)
交换机的功能主要是接收消息并且转发到绑定的队列，交换机不存储消息，在启用ack模式后，交换机找不到队列会返回错误。交换机有四种类型：Direct, topic, Headers and Fanout

- Direct：direct 类型的行为是”先匹配, 再投送”. 即在绑定时设定一个 routing_key, 消息的routing_key 匹配时, 才会被交换器投送到绑定的队列中去.
```
简单模式：绑定queue，全文匹配routing_key
```
- Topic：按规则转发消息（最灵活） 
```
主题模式：绑定queue，routing_key，可以使用两个通配符:
*表示一个词   #表示零个或多个词
```
- Fanout：转发消息到所有绑定队列
```
广播模式（订阅模式）：绑定queue，忽略routing_key
```
- Headers：设置 header attribute 参数类型的交换机

<h2 id="ErLang"></h2>

### 1、安装 ErLang_otp_win64_22.2.exe 

- 设置环境变量，新建 ERLANG_HOME
- 修改环境变量path，增加Erlang变量至path，%ERLANG_HOME%\bin;
- 打开cmd命令框，输入 erl -version  验证



<h2 id="RabbitMQ-install"></h2>

### 2、安装 rabbitmq-server-3.8.2.exe 

- 设置环境变量，新建 RABBITMQ_SERVER
- 修改环境变量path，增加rabbitmq变量至path，%RABBITMQ_SERVER%\sbin;
- 打开cmd命令框，切换至...\sbin目录下，输入 rabbitmqctl status 验证
- 创建RabbitMQ服务并启动 rabbitmq-plugins.bat enable rabbitmq_management
- 登陆 http://127.0.0.1:15672/    账号密码 guest，guest

--------------



```
D:\>cd D:\ProgramFiles\rabbitmq-server-3.8.2\rabbitmq_server-3.8.2\sbin

D:\ProgramFiles\rabbitmq-server-3.8.2\rabbitmq_server-3.8.2\sbin>rabbitmqctl status

创建RabbitMQ服务并启动
D:\ProgramFiles\rabbitmq-server-3.8.2\rabbitmq_server-3.8.2\sbin>rabbitmq-plugins.bat enable rabbitmq_management
	停止：net stop RabbitMQ
	启动：net start RabbitMQ

	
启动命令	
D:\ProgramFiles\rabbitmq-server-3.8.2\rabbitmq_server-3.8.2\sbin>rabbitmq-server.bat

```

参考
https://blog.csdn.net/lihua5419/article/details/93006834
https://blog.csdn.net/zhm3023/article/details/82217222


erlang官网  https://www.erlang.org/downloads
rabbitmq官网 https://www.rabbitmq.com/download.html

