# Redis 常用命令

### 1. 通用命令

-----------|--------------|---------------------------------------------------------|----------  
序号        | 命令          | 描述                                                    | 时间复杂度
1          |keys [pattern]| 列出系统中所有的 key                                       | O(n) 
2          |dbsize        | Redis 系统所有 key 的个数                                  | O(1) 
3          |exists key    | Redis 系统是否存在该 key，存在返回1，否则返回0                 | O(1) 
4          |del key...    | 删除 Redis 中的 key，删除不存在的key返回0，否则返回key个数      | O(1)
5          |expire key seconds | 设置 key 的过期时间，单位是秒                           | O(1)
6          |ttl key       | 显示 key 剩余的过期时间，返回 -1 表示没有设置过期时间，-2表示key已删除 | O(1)
7          |persist key   | 去掉 key 的过期时间                                        | O(1)
8          |type key      | 查看 key 的数据类型                                        | O(1)


### 2. 字符串

### 3. hash命令

### 4. list 命令

### 5. set

### 6. sorted set 命令