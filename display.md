## 多行文本溢出显示省略号(…)：

在WebKit浏览器或移动端（绝大部分是WebKit内核的浏览器）的页面实现比较简单，可以直接使用WebKit的CSS扩展属性(WebKit是私有属性)-webkit-line-clamp ；

注意：这是一个 不规范的属性（unsupported WebKit property），它没有出现在 CSS 规范草案中。

`-webkit-line-clamp`用来限制在一个块元素显示的文本的行数。 为了实现该效果，它需要组合其他的WebKit属性。

常见结合属性：

  * `display: -webkit-box;` 必须结合的属性 ，将对象作为弹性伸缩盒子模型显示 。
  * `-webkit-box-orient` 必须结合的属性 ，设置或检索伸缩盒对象的子元素的排列方式 。
  * `text-overflow: ellipsis;`，可以用来多行文本的情况下，用省略号“…”隐藏超出范围的文本 
  
CSS代码：
```css
overflow : hidden;
text-overflow: ellipsis;
display: -webkit-box;
-webkit-line-clamp: 2;
-webkit-box-orient: vertical;
```
这个属性比较合适WebKit浏览器或移动端（绝大部分是WebKit内核的）浏览器。

#### 跨浏览器兼容的方案:

比较靠谱简单的做法就是设置相对定位的容器高度，用包含省略号(…)的元素模拟实现；

CSS代码：
```css
p {
    position:relative;
    line-height:1.4em;
    /* 3 times the line-height to show 3 lines */
    height:4.2em;
    overflow:hidden;
}
p::after {
    content:"...";
    font-weight:bold;
    position:absolute;
    bottom:0;
    right:0;
    padding:0 20px 1px 45px;
    background:url(http://newimg88.b0.upaiyun.com/newimg88/2014/09/ellipsis_bg.png) repeat-y;
}
```

## display:table-cell与大小不固定元素的垂直居中
display:table-cell属性指让标签元素以表格单元格的形式呈现，类似于td标签。

CSS代码：
```css
div{
 display:table-cell; 
 width:1em; height:1em; 
 border:1px solid #beceeb; 
 font-size:144px; 
 text-align:center; 
 vertical-align:middle;
} 
div img{vertical-align:middle;}
```
效果：

![](img/user02.jpg)

## 通过使用 box-align and box-pack 属性，居中 div 框的子元素：

```html
<style>
div
{
width:350px;
height:100px;
border:1px solid black;
  
/* Firefox */
display:-moz-box;
-moz-box-pack:center;
-moz-box-align:center;

/* Safari, Chrome, and Opera */
display:-webkit-box;
-webkit-box-pack:center;
-webkit-box-align:center;

/* W3C */
display:box;
box-pack:center;
box-align:center;
}
</style>

<div>
 <p>我是居中对齐的。</p>
</div>
```

