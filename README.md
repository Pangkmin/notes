# notes
个人笔记集

### ECMAScript 6
阮一峰书籍
http://jsrun.net/tutorial/dZKKp

### Web前端开发规范文档
[Webpack--管理资源](./specification.md)

### 图片无损压缩工具
[在线压缩](./compress.md)

### 在线字体格式转换
[在线字体转换](https://www.fontke.com/tool/convfont/)

### sublime text3
[sublime text 快捷键](./sublime.md)

[sublime 插件安装](./package.md)

### 粒子效果库
http://www.jq22.com/js/a10.html <br/>
http://www.jq22.com/js/a9.html

### CSS 布局
[多行文本溢出及对齐](./display.md)

### CSS 专业技巧
https://github.com/AllThingsSmitty/css-protips/blob/master/translations/zh-CN/README.md#%E4%BD%BF%E7%94%A8-%E5%BD%A2%E4%BC%BC%E7%8C%AB%E5%A4%B4%E9%B9%B0-%E7%9A%84%E9%80%89%E6%8B%A9%E5%99%A8 <br/>

[ 如何优雅的选择字体(font-family)](https://segmentfault.com/a/1190000006110417)

### CSS3 三次贝塞尔曲线(cubic-bezier)
[CSS3动画速度的控制通过三次贝塞尔曲线函数实现](./cubic.md)

### Discuz搭建论坛
[Discuz在Windows服务器上的环境搭建](./discuz.md) <br/>
[Discuz在CentOS服务器上的环境搭建](./discuz_centos.md)

### Web前端性能优化
[如何有效提升静态文件的加载速度](./jzsd.md)

### PHP手册
[PHP中文网](http://www.php.cn/toutiao-384729.html)

### HTML常用的特殊符号总结

[haorooms博客](http://www.haorooms.com/post/html_tsfh)

### vue项目

[iView admin是基于Vue.js，搭配使用iView UI组件库形成的一套后台集成解决方案](https://github.com/iview/iview-admin)

[基于 vue2 + vuex 构建一个具有 45 个页面的大型单页面应用](https://github.com/bailicangdu/vue2-elm)

[基于SOA架构的分布式电商购物商城 前后端分离 前台商城:Vue全家桶 后台管理系统](https://github.com/HurriedOn/xmall)

[Vue 全家桶 + axios 前端实现登录拦截、登出、拦截器等功能](https://github.com/superman66/vue-axios-github)

### 在线 .md 转换成 .pdf
http://www.mdtr2pdf.com/index_en.html

### 轻量级浏览器检测插件Feature.js

在页面中引入feature.js文件，不需要对其进行初始化，只需引入文件即可。
```html
<script src="js/feature.js"></script>
```
然后可以使用特性检测来检测浏览器是否支持某些特性，例如：
```js
if (feature.webGL) {
  console.log("你的浏览器支持WebGL");
} else {
  console.log("你的浏览器不支持WebGL");
}
```
也可以同时进行多选特性的检测：
```js
if (feature.webGL && feature.svg && feature.canvas) {
  console.log("你的浏览器支持Canvas、svg和WebGL")
}
```

### 网页动画效果库
1. GSAP  https://greensock.com/gsap  <br/>
2. Anime.js http://animejs.com/


### Live2D 卡通动画
live2D 卡通人物动画学习
http://www.live2d.com/usermanual/cubism2_cn/lets-do-it/quick-modeling.html
