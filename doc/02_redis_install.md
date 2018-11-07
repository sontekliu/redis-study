# Redis 安装

### 1. 下载Redis安装包

在 Redis [官方网站](https://redis.io)，下载stable version版本，编写此教程时，稳定版本为 5.0

### 2. 解压缩安装
使用 root 账号进行安装。
```shell
# tar -zxvf redis-5.0.0.tar.gz 
# cd redis-5.0.0
# make      # 官网下载完成之后就已经configure了，所以直接make
# make test
```
### 3. 创建安装目录并 COPY 相应的文件
一般情况下，我们第三方安装的软件一般放在 /usr/local 目录下，所以，此时需要在 /usr/local 目录下创建 redis 目录。
在 /usr/local/redis 目录下面，分别创建 bin 目录和 etc 目录，/usr/local/redis/bin 目录存放可执行文件，/usr/local/redis/etc 目录存放配置文件信息。
具体创建如下：

```shell
# mkdir -p /usr/local/redis/bin /usr/local/redis/etc
```
创建完安装目录之后，将第 2 步编译生成的可执行文件以及配置复制到指定的目录。操作如下：

```shell
# cd /usr/local/redis-5.0.0/src
# cp redis-sentinel redis-server redis-benchmark redis-cli redis-check-aof redis-check-rdb /usr/local/redis/bin
# cd ..
# cp redis.conf /usr/local/redis/etc
```

### 4. 启动 Redis 服务

默认情况下，Redis 的启动不是以后台服务器的形式启动的，若想让 Redis 以后台服务的形式启动，需修改如下配置，编辑 /usr/local/redis/etc/redis.conf
文件，找到如下内容：

```
# By default Redis does not run as a daemon. Use 'yes' if you need it.
# Note that Redis will write a pid file in /var/run/redis.pid when daemonized.
daemonize no
```
将 `daemonize no` 改成 `daemonize yes` 即可。启动命令如下：
```shell
# cd /usr/local/redis/bin
# ./redis-server /usr/local/redis/etc/redis.conf
```

附注：  
该目录下多了如下文件:  
redis-benchmark                 #redis性能测试工具,测试redis在当前系统的读写性能  
redis-check-aof                 #检查aof日志的工具  
redis-check-dump                #检查rdb日志的工具  
redis-cli                       #客户端链接工具  
redis-sentinel -> redis-server  
redis-server                    #redis启动服务工具  



