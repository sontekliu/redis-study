# Redis 安装

### 1. 下载Redis安装包

在 Redis [官方网站](https://redis.io)，下载stable version版本，编写此教程时，稳定版本为 5.0

### 2. 安装之前的准备

首先要安装 tcl, make, gcc 

```shell
$ sudo apt install tcl make gcc 
```

### 3. 解压缩安装

使用 root 账号进行安装。

```shell
# tar -zxvf redis-5.0.0.tar.gz 
# cd redis-5.0.0
# make MALLOC=libc     # 官网下载完成之后就已经configure了，所以直接make
# make test
```
### 3. 创建安装目录并 COPY 相应的文件

一般情况下，我们第三方安装的软件一般放在 /usr/local 目录下，所以，此时需要在 /usr/local 目录下创建 redis 目录。
在 /usr/local/redis 目录下面，分别创建 bin 目录和 etc 目录，/usr/local/redis/bin 目录存放可执行文件，/usr/local/redis/etc 目录存放配置文件信息。
具体创建如下：

```shell
# cd /usr/local
# mkdir -p redis/bin redis/etc redis/data redis/log
```

创建完安装目录之后，将第 2 步编译生成的可执行文件以及配置复制到指定的目录。操作如下：

```shell
# cd /usr/local/redis-5.0.0/src
# cp redis-sentinel redis-server redis-benchmark redis-cli redis-check-aof redis-check-rdb /usr/local/redis/bin
# cd ..
# cp redis.conf /usr/local/redis/etc
```

### 4. 启动 Redis 服务

```shell
# cd /usr/local/redis/bin
# ./redis-server /usr/local/redis/etc/redis.conf
```
