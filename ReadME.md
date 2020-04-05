## RabbitMQ
*   [0、RabbitMQ教程](#RabbitMQ) 
*   [1、安装 ErLang](#ErLang) 
*   [2、安装 RabbitMQ](#RabbitMQ-install) 

> [github]( https://github.com/scott180/RabbitMQ-test ) &ensp; [dillinger]( https://dillinger.io/ )  &ensp;  [作业部落]( https://www.zybuluo.com/mdeditor )   


<h2 id="RabbitMQ"></h2>

### 0、RabbitMQ教程
>消息队列（Message Queue，简称MQ），从字面意思上看，本质是个队列，FIFO先入先出，只不过队列中存放的内容是message而已。
其主要用途：不同进程Process/线程Thread之间通信。

>[RabbitMQ教程]( https://blog.csdn.net/hellozpc/article/details/81436980 ) &ensp; [RabbitMQ 详解]( http://www.ityouknow.com/springboot/2016/11/30/spring-boot-rabbitMQ.html ) &ensp;[什么时候该使用MQ]( https://mp.weixin.qq.com/s?__biz=MjM5ODYxMDA5OQ==&mid=2651960012&idx=1&sn=c6af5c79ecead98daa4d742e5ad20ce5&chksm=bd2d07108a5a8e0624ae6ad95001c4efe09d7ba695f2ddb672064805d771f3f84bee8123b8a6&mpshare=1&scene=1&srcid=04054h4e90lz5Qc2YKnLNuvY )

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


参考
https://blog.csdn.net/lihua5419/article/details/93006834
https://blog.csdn.net/zhm3023/article/details/82217222


erlang官网  https://www.erlang.org/downloads
rabbitmq官网 https://www.rabbitmq.com/download.html

```
