# nodejs

## 定义:

nodejs是一个运行在服务端的软件

## 作用

1. 可以解析并运行JavaScript代码
2. 搭建http服务器

## 特点

1. 单线程

2. 异步非阻塞I/O

    阻塞按是按顺序执行的，而非阻塞是不需要按顺序的，所以如果需要处理回调函数的参数，我们就需要写在回调函数内 

   Node.js 回调函数

   Node.js 异步编程的直接体现就是回调。

   异步编程依托于回调来实现，但不能说使用了回调后程序就异步化了。

   回调函数在完成任务后就会被调用，Node 使用了大量的回调函数，Node 所有 API 都支持回调函数。

   例如，我们可以一边读取文件，一边执行其他命令，在文件读取完成后，我们将文件内容作为回调函数的参数返回。这样在执行代码时就没有阻塞或等待文件 I/O 操作。这就大大提高了 Node.js 的性能，可以处理大量的并发请求。
> 同步和异步：
>

>         同步和异步是一种“现象”，这种现象的表现在自己“编写的主程序”无停顿执行或有停顿执行，程序耗时是(m+n)还是max(m+n)。
   >    
   >     阻塞和非阻塞：
   >    
>         阻塞和非阻塞是一种“事实”，体现为一段主调用序是挂起还是一直等待另外的系统调用完成。
   >    
   >     总结:
   >    
>         阻塞的程序有可能体现外异步，也有可能体现为同步。非阻塞的程序已定体现为异步。nodejs所宣传的异步单线程程序也只是我们所写的代码看上去是异步单线程程序。真是情况是node的执行环境其实是多线程的，这个多线程的执行环境在保证我们代码的异步执行。
   > 

3. 事件驱动

4. npm包管理工具

5. 稳定性较差

## nodejs的学习目标

* 掌握nodejs的基本使用
* 掌握npm的基本使用
* 帮助了解web开发

# linux下的nodejs

## 源码安装

* 下载

* 解压

* 进入目录

* ./configure

* make && make install

  > 升级g++版本
  >
  > 1. wget http://people.centos.org/tru/devtools-2/devtools-2.repo -o  /etc/yum.repos.d/devtools-2.repo
  > 2. yum install devtoolset-2-gcc  devtoolset-2-binutils
  > 3. yum install devtoolset-2-gcc-c++  devtoolset-2-gcc-gfortran
  > 4. 查看版本
  >    1. /opt/rh/devtoolset-2/root/usr/bin/gcc  --version
  >    2. scl enable devtoolset-2 bash
  >    3. source /opt/rh/devtoolset-2/enable

## 安装

### 下载

* `https://nodejs.org/download/release/`
* `https://npm.taobao.org/mirrors/node/`

### 解压文件

`tar -xf node-vX.X.X-linux-x86.tar.xz`

### 移动目录

`mv node-vX.X.X-linux-x86 /usr/local/node`

### 配置环境变量

进入文件 `vim ~/bash_profile`

在末尾添加node命令所在的路径

### 启动生效

`source ~/bash_profile`

## 使用

### hello world

### 创建http服务

1. 引入node内置的http模块儿
   var http = require('http');
2. 创建服务
   var server = http.createServer(function(req, res){
   //逻辑代码 并给客户端返回结果
   res.end('hello world');
   });
3. 监听端口
   server.listen(8080);

### 请求

1. 请求方法 method
2. 请求路径 url
3. 协议版本 httpVersion
4. 请求头 headers
5. get参数 urlTool.parse(url,true).query

### 响应

1. 响应码 statusCode
2. 响应头 setHeader('name','value');
3. 响应体 write()
4. 结束(必加) end()

### 静态资源请求

### 页面处理

### 表单处理

* `req.addListener('data', function(chunk){});`
* `req.addListener('end', function(){});`

## npm

### 定义

npm是个软件

### 作用

它能安装工具包

> 类似软件
>
> 1. yum
> 2. apt-get
> 3. qq软件管家
> 4. app store
> 5. 手机助手

### 使用

#### 初始化npm

1. npm init
2. npm init --yes

#### 查找软件

1. 网址搜索 https://www.npmjs.com/
2. 命令搜索 `npm search formidable`

#### 安装软件

1. 记录安装信息 `npm install formidable  --save`
2. 不记录安装信息 `npm install formidable`

#### 移除软件

`npm uninstall fomidable`

#### 查看已安装的列表

`npm list`

#### 配置中文镜像

`npm install -g cnpm --registry=https://registry.npm.taobao.org`

## 模块儿化

* 每个文件被视为一个独立的模块
* 绝对路径 `/`
* 相对路径 `./`
* 文件夹
* module.exports
* node_modules安装包

# api手册地址

http://nodejs.cn/api/

# nodejs使用场景

* 聊天室
* 单页应用
* api
* 适合I/O密集型场景

# windows下的nodejs

## 介绍

一个主要运行在服务器端的软件

## 功能

1. 解析并运行 Javascript 代码
2. 创建 HTTP 服务

## 使用

### 1. 下载安装

1. 下载 http://nodejs.cn/download/
2. 安装 双击软件 -> 一路下一步
3. 测试 `win+r` 打开命令行 运行 `node -v`

### 2. 使用

#### 1. hello world

#### 2. HTTP服务

//引入 http 模块
var http = require('http');

//创建服务
var server = http.createServer(function(req, res){
	res.end('i love you');
});

//监听端口
server.listen(8080);

#### 3. HTTP请求协议

GET /login HTTP/1.1
Host: localhost
user-agent: firefox
referer: http://www.abc.com

username=admin&password=admin

#### 4. 请求

req.method
req.url
req.httpVersion
req.headers

#### 5. 响应

res.statusCode
res.setHeader
res.write
res.end

#### 6. fs 模块儿

##### 1. 文件操作

* 读取文件  readFile
* 写入文件  writeFile
* 追加文件  appendFile
* 删除文件  unlink

##### 2. 文件夹

* 创建文件夹   mkdir
* 删除文件夹   rmdir
* 读取文件夹   readdir

##### 3. 检测文件或者文件夹是否存在

`fs.access(file, fs.constants.F_OK, function(err){})`

`fs.existsSync(file)`

##### 4. 检测文件状态

`fs.stat('readme.md', function(err, stats){})`

##### 5. 复制文件

`fs.copyFile(src, dst, function(err){})`

##### 6. 修改名称

`fs.rename(old, new, function(err){})`

#### 7. 静态资源请求

#### 8. 静态页面

#### 9. 表单处理

`req.addListener('data', function(chunk){})`

`req.addListener('end', function(){})`

### 3. 模块儿

#### 分类

内置模块

第三方模块

自定义模块

#### 使用

##### 导出

`module.exports = {}`

`module.exports.xxx = {}`

`exports 和 module.exports 使用相同`

##### 导入

`require`

### 4. 文档  http://nodejs.cn/api/

## npm

> 具体用法和linu一样,详情请往上参照linux下的npm

## 特点

1. 单线程
2. 异步非阻塞
3. 事件驱动
4. npm 包管理工具

## 应用场景

* 网站
* API 接口
* IM 聊天室
* I/O 密集性的
* 不适合计算密集型的应用

## 长连接

### 轮询与长轮询

**轮询：**说白了就是客户端定时去请求服务端，  是客户端主动请求来促使数据更新；

**长轮询：**说白了 也是客户端请求服务端，但是服务端并不是即时返回，而是当有内容更新的时候才返回内容给客户端，从流程上讲，可以理解为服务器向客户端推送内容；

### SSE

### Server-Sent 事件 - 单向消息传递

Server-Sent 事件指的是网页自动获取来自服务器的更新。

以前也可能做到这一点，前提是网页不得不询问是否有可用的更新。通过服务器发送事件，更新能够自动到达。

例子：Facebook/Twitter 更新、股价更新、新的博文、赛事结果等。

### socket.io

 Socket.IO是一个WebSocket库，包括了客户端的js和服务器端的nodejs，它的目标是构建可以在不同浏览器和移动设备上使用的实时应用 

### socket.io的特点

易用性：socket.io封装了服务端和客户端，使用起来非常简单方便。

跨平台：socket.io支持跨平台，这就意味着你有了更多的选择，可以在自己喜欢的平台下开发实时应用。

自适应：它会自动根据浏览器从WebSocket、AJAX长轮询、Iframe流等等各种方式中选择最佳的方式来实现网络实时应用，非常方便和人性化，而且支持的浏览器最低达IE5.5。