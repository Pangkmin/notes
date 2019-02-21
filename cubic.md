# CSS3 三次贝塞尔曲线(cubic-bezier)

animation-timing-function 和 transition-timing-function两个属性来控制动画速度分别提供了ease，liner，ease-in，ease-out，ease-in-out几个预设速度，还可以同过cubic-bezier来自定义速度。<br/>
CSS3动画速度的控制通过三次贝塞尔曲线函数实现，定义规则为 `cubic-bezier (x1,y1,x2,y2)`

### 原理：
-------------------
看一下什么是三次贝塞尔曲线，以及这几个参数的含义：
![](img/after.jpg)
