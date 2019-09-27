```bas
# 全局安装 vue-cli
$ npm install --global vue-cli
# 创建一个基于 webpack 模板的新项目
$ vue init webpack my-project
# 安装依赖
$ cd my-project
# 项目打包
$ npm run build
```

### vue项目拷贝到另一个地方启动不了的解决办法
造成这样的原因是当你在一台电脑上编译后npm会有cache缓存，到另外一台电脑上编译这个项目的缓存与原缓存不一致，导致编译报错。

解决办法：

1. 删掉node_modules文件夹，

2 .执行 npm cache clean 或者  cnpm cache clean 命令清除掉cache缓存，

若清除失败强制清除npm 的 cache. 
```base
$ npm cache clean --force  
```
然后再运行 npm install .

3.然后cnpm install 和npm run dev就可以在这台电脑运行你的项目

### webpack打包vue项目ie浏览器下报promise 未定义

解决办法 : 

步骤一: 安装 babel polyfill
```base
$ npm install --save babel-polyfill
```

步骤二: 配置build文件夹下webpack.base.conf.js文件添加 require('babel-polyfill') ,如下:
```js
'use strict'
const path = require('path')
const utils = require('./utils')
const config = require('../config')
const vueLoaderConfig = require('./vue-loader.conf')
const webpack = require('webpack')
require('babel-polyfill')         
```

步骤三: 配置main.js文件添加 import 'babel-polyfill',如下:
```js
import Vue from 'vue'
import App from './App'
import router from './router'
import 'babel-polyfill'
```
最后,重新运行项目就可以了
```base
$ npm run dev
```
