# Node.js

## express框架 
express框架是有一个基于node.js平台的极简、灵活的web应用开发框架， 它提供一系列强大的特性，帮助你创建各种web和移动设备应该。<br/>
核心特性：可以设置中间件来相应http请求；定义了路由表用于执行不同的http请求动作；可以通过模板传递参数来动态渲染html页面。

express安装与使用<br/>
  1) 安装express-generator（快速生成一个基本的express开发框架）。<br/>
```base
$ cnpm i -g express-generator 
 ```
  2）创建项目 
```base
$ express -e 项目名称
```
  3） 安装依赖
```base
$ cnpm i
```
  4)  开启项目
```base
# 开启项目方式一：
$ node app 
# 开启项目方式二：
$ npm start
# 开启项目方式三：
$ node ./bin/www
```

项目结构：<br/>
|- app <br/>
   |- node_modules   # 依赖包的目录  <br/>
   |- bin   # 可执行文件目录  <br/>
     |- www <br/>
   |- public   # 静态文件根目录（静态html、css、js、图片、视频等）   <br/>
   |- routes   # 路由模板目录  <br/>
   |- views    # 视图目录，用于储存所有的ejs模板  <br/>
   |- app.js   # 项目的主文件   <br/>
   |- package.json  # 项目描述文件，声明项目的名称、版本、依赖等信息  <br/>


### 相应对象-send方法
响应对象res:
  1) 响应对象是指服务器向客户端相应数据的对象，包含了所有要响应的内容。 <br/>
  2）相应对象的方法  res.send();  <br/>
```js
 var express = require('express');
 var router = express.Router();
 
 router.get('/',function(req, res){
  // res.send('hell world'); //可以返回字符串
  // var data = {"name":"李白","age":18};
  // res.send(data);  //可以返回JSON数据
  
  // res.send('1');  // 如果一定要返回数字，必须加引号变成字符串，否则会报错。
  // send方法只能出现一次，重复无效还要报错。
  
  // 返回状态码+数据 链式调用
  res.status(404).send('<h1>没有找到内容</h1>'); 
 });
 
 module.express = router;
```
