# Memcached

定义: 

1. memecached是一个开源免费的高性能的分布式内存对象`缓存系统`.

2. 就是一个软件.

作用:  缓存数据,提高动态网站的速度

安装: 

安装 lrzsz 可以直接把windows文件拖到linux目录下

`yum -y install lrzsz`

方法1. yum install memecached

方法2: 

1. 安装libevent

tar -zvxf libevent-release-1.4.15-stable.tar.gz

cd libevent-release-1.4.15-stable

./autogen.sh

./configure -prefix=/usr

make && make install

2. 安装memcache

tar -zvxf memcached-1.4.36.tar.gz

cd memcached-1.4.36

./configure --prefix=/usr/local/memcache

make && make install

3. memcached的启动和连接
   + 启动命令  ./memcached -u root -p 11211 -d
   + 连接命令  telnet 127.0.0.1 11211

# memcached命令行使用

* stats	查看当前状态
* set    四个参数     name(键名) 0(额外的数字标识,有特殊的写其他的,默认为0)  (生命周期的时间限定 (秒)s  0s时默认永久有效)10    当前写入的数据长度(字节)       往内存当中写入数据
* get     读取操作
* delete
* flush_all   清空memcached所存储的命令
* STORED 存储

> 存储数据时是以`key/value`的形式来存储的,有点像关联数组    `['key'=>"value"]`
>
> memcached所存储的数据再软件关闭/重启之后就销毁了

# php代码使用

## 安装php-memcache扩展

### php-memcache的安装

1. 下载
    wget https://github.com/websupport-sk/pecl-memcache/archive/php7.zip
2. 解压
    unzip pecl-memcache-php7.zip
3. 进入目录
    cd pecl-memcache-php7
4. 执行phpize
    /usr/local/php/bin/phpize
5. 配置
    ./configure --with-php-config=/usr/local/php/bin/php-config
6. 编译安装
    make && make install
7. 修改php配置文件
    vim /usr/local/php/etc/php.ini
    extension_dir = "/usr/local/php/lib/php/extensions/no-debug-zts-20151012/"
    extension="memcache.so";
8. 重启apache
    /usr/local/apache2/bin/apachectl  restart

> iptables -F 可以用来快速关闭防火墙
>
> ctrl+insert:复制
>
> shift+insert:粘贴
>
> `sftp`插件 sublime下面的插件

### php-memcache使用

1. 创建memcache对象 

   `$mem = new Memecache;`

2. 连接memcached服务器

   `$mem->connect('127.0.0.1',11211);`

3. 写入数据/读取数据/删除数据

   1. 写入

      `$mem->set('name','xiaoxu',MEMCACHE_COMPRESSED,0);`

   2. 读取

      `$res = $mem->get('name');`

   3. 删除

      `$res = $mem->delete('name');`

   4. 清除

      `$res = $mem->flush();`

4. 关闭连接

   `$mem->close();`

### php-memcache扩展使用

1. 数据缓存的实现

2. 缓存类的封装

   > 开启错误提醒,修改php.ini文件中的`display_errors = On`;

3. session数据的memcache存储

   session信息也是可以自定义存储的,比如可以将他们存入到mysql,memcache.redis中.

   原理: `session_set_save_handler`.

# memcached的安装



# php-memcache的安装