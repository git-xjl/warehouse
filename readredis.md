# Redis

## 定义

Redis是一个开源的使用ANSI C语言编写,支持网络,可基于内存亦可持久化的日志型,Key-Value数据库.也是一个软件.

## 特点和作用

1. 支持多种数据类型的存取数据
2. 支持持久化存储数据

# 应用场景

+ 数据缓存
+ 消息队列
+ 排行榜
+ 计数

## redis的安装

1. 下载
    wget `http://download.redis.io/releases/redis-3.2.8.tar.gz`
2. 解析
    `tar -zvxf redis-soft-3.2.8.tar.gz`
3. 进入目录
    `cd redis-3.2.8`
4. 编译安装
    `make  PREFIX=/usr/local/redis  install`
5. 移动配置文件
    `mv  redis.conf  /usr/local/redis`
6. 启动时载入配置文件 (前提是要先将配置文件放置到指定目录)
    `./redis-server /usr/local/redis/redis.conf`

## redis客户端连接

`./redis-cli  -h  localhost  -p  6379`
`./redis-cli --help`帮助

# redis的使用

命令行

php代码

## redis命令行使用

* 字符串
* 哈希
* 列表
* 集合
* 有序集合
* 其他

## redis字符串命令

### 1. 字符串

* set			存储一条数据
* get			获取一条数据 			
* incr			自增一个数据
* incrby		按照指定步进自增
* decr		自减一条数据
* decrby		按照指定步进自减
* setex		设置一条数据并设置声明周期
* strlen		获取数据的长度
* setbit		设置某一位上的数据
* getbit		获取某一位上的数据
* bitcount	统计值为1的位数
* setnx		不存在此key设置, 存在则不设置
* append	追加字符串
* getrange	截取字符串

### 2. 哈希

* hset			设置key中的某个字段
* hget			获取key中的某个字段
* hdel			删除key中的某个字段
* hexists		检测key中的某个字段是否存在
* hincrby		自增key中某个字段的值
* hgetall		获取key中所有的信息
* hkeys			获取key中所有的字段
* hvals			获取key中所有的值
* hmset		批量设置哈希中的数据
* hmget		批量获取哈希中的数据

### 3. 列表

* lpush			左侧插入列表一条数据
* lpushx			左侧插入一条数据, 如果列表不存在不插入
* rpush			右侧插入列表一条数据
* rpushx			右侧插入列表一条数据, 如果列表不存在不插入
* lindex			获取列表中指定索引的元素
* linsert			在列表中的某个位置插入一条数据
* llen				获取列表的长度
* lpop			在左侧弹出一条数据
* rpop			在右侧弹出一条数据
* lrange			获取列表中某个区间中的数据
* lrem			移出列表中的某个数据
* lset				修改列表中元素的值
* rpoplpush		将列表右侧的值弹出, 然后插入另一个列表中.

### 4. 集合

> 集合中的元素不能重复

* sadd					向集合中添加一个新的元素
* scard					返回集合中元素的个数
* sdiff					返回两个集合的差集
* sdiffstore				存储两个集合的差集结果
* sinter					返回两个集合的交集
* sinterstore				存储两个集合的交集结果
* sismember			检测一个元素是否在某个集合整那个
* smembers				获取一个集合中的所有元素
* smove					将一个元素从这个集合移动到另一个集合
* spop					随机弹出指定个数的元素	
* srandmember			随机获取集合中的一个元素
* srem					移出集合中元素
* sunion					返回两个集合的并集
* sunionstore			存储两个集合的并集结果

### 5. 有序

* zadd							向有序集合中添加一条数据
* zcard							返回有序集合的数据总数
* zcount							根据权重区间统计数据数量
* zincrby							按照步进增加数据的权重
* zrange							根据权重从低到高获取数据
* zrevrange						权重从高到低获取数据
* zrangebyscore				根据权重区间返回数据
* zrank							根据排名返回数据
* zrevrank						根据排名倒序返回数据
* zrem							删除数据
* zremrangebyrank				根据排名删除数据
* zremrangebyscore			根据权重删除数据
* zscore							返回一条数据的权重
* zunionstore					将集合并集存储到一个集合中

### 6. 其他

* del					删除某个key数据
* exists				检测某个key是否存在
* expire				为某个key设置生命周期
* ttl					返回key的生命时间
* keys				返回匹配到的key
* select				选择数据库
* move				将key移动到某个数据库
* type				获取key的类型
* rename			重命名key
* auth				密码
* multi				启动一个事务
* discard				取消时区
* exec				执行事务

# php代码使用

## 安装php-redis扩展

### php-redis的安装

1. 下载
    wget `http://pecl.php.net/get/redis-3.1.1.tgz`
2. 解压
    `tar -zvxf redis-3.1.1.tgz`
3. 进入目录
    `cd redis-3.1.1`
4. 运行phpize
    `/usr/local/php/bin/phpize`
5. 配置
    `./configure --with-php-config=/usr/local/php/bin/php-config`
6. 编译
    `make`
7. 安装
    `make install`
8. 修改php配置文件,添加扩展
    `extension=redis.so`
9. 重启apache
    `/usr/local/apache2/bin/apachectl  restart`

### php-redis扩展使用

* 缓存类的封装
* 用户管理
* 异步处理信息

## 使用php操作redis

> apache服务器不是只有浏览器才能访问

### php-redis使用

* 创建redis对象
* 连接redis服务器
* 写入数据/读取数据/删除数据

# redis在windows上的安装

## 软件的安装

