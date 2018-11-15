# Redis 安装完成之后的基本配置

1. 使 Redis 已后台进程的方式启动

```shell
daemonize no  --> daemonize yes
``` 

2. 桌面客户端软件可以连接 Redis 服务

找到如下内容，将其注释掉即可，或者配置指定客户端 IP 
```shell
bind 127.0.0.1

protected-mode yes
```

设置密码

```shell
requirepass 123456
```

3. 修改 Redis 默认端口

找到如下内容，修改成系统未使用的端口即可。

```shell
port 6379
```

4. 修改进程文件位置

找到如下内容，修改进程文件的位置

```shell
pidfile /var/run/redis_6379.pid
```

修改后

```shell
pidfile /usr/local/redis/data/redis_6379.pid
```

5. 存储本地数据库时，是否压缩，默认为 yes

```shell
rdbcompression yes
```

6. RDB 存储文件的名称 

```shell
dbfilename  dump.rdb
```

7. RDB 数据文件的存储位置，默认为 `./`，注意此处是目录，不是文件

```shell
dir ./
```

修改后：

```shell
dir /usr/local/redis/data
```

8. 设置 Redis 日志文件路径，注意此处是文件，不是目录

找到如下内容：

```shell
logfile ""
```

默认为 stdout 标准输出，若后台模式启动则会输出到 /dev/null 中，修改后如下：

```shell
logfile /usr/local/redis/log/redis.log
```

以上均是安装完 Redis 之后修改的一些简单配置，Redis 的配置可以修改 redis.conf 文件，也可以通过 config 命令实现。

```                                                                                                                         
    # 查看配置项                                                                                                                 
    redis 127.0.0.1:6379> config get loglevel                                                                               
    # 查看所有配置项                                                                                                               
    redis 127.0.0.1:6379> config get *                                                                                      
    # 设置配置项                                                                                                                 
    redis 127.0.0.1:6379> config set loglevel "notice"                                                                      
    OK                                                                                                                      
```                                                                                                                         
                                                                                                                            
**Redis.conf 配置参数说明**                                                                                                       
                                                                                                                            
参数名称           |  值                         |     说明                                                                          
-----------------|-----------------------------|-----------------------------------------------------                       
bind             | 127.0.0.1                   | 绑定的主机地址                                                                    
timeout          | 300                         | 客户端闲置多久后关闭链接，0:表示关闭该功能                                                     
loglevel         | debug/verbose/notice/warning| 日志级别                                                                       
database         | 10                          | 数据库数量                                                                      
save             | \<seconds\> \<changes\>     | save 900 10 表示指定多久内有多少次更新就将数据同步到数据文件                                   
slaveof			 | 	\<masterip\> \<masterport\>| 当本机为slaveof时，设置master的ip和port，redis启动时，自动从master上数据同步
masterauth 		 | \<master-password\>         | 如果master设置了密码，slav链接master的密码          