# CSS知识总结

## 一、浏览器渲染原理

解析：是浏览器将通过网络接收的数据转换为DOM和CSSOM的步骤

渲染：渲染步骤包括样式、布局、绘制，在某些情况下还包括合成。在解析步骤中创建的CSSOM树和DOM树组合成一个Render树，然后用于计算每个可见元素的布局，然后将其绘制到屏幕上。在某些情况下，可以将内容提升到它们自己的层并进行合成，通过在GPU而不是CPU上绘制屏幕的一部分来提高性能，从而释放主线程。

浏览器的渲染步骤：

①根据HTML构建HTML树（DOM）；

②根据CSS构建CSS树（CSSOM）； 

③将HTML树和CSS树合成一个Render树；

④Layout布局，计算每个可见元素的布局（文档流、盒模型、计算大小和位置）；

⑤Paint绘制，将布局绘制到屏幕上（把边框、颜色和阴影等画出来）；

⑥Compose合成（根据层叠关系展示画面）。

## 二、CSS两种动画的方法

（一）transition 过渡

transition：可以为一个元素在不同状态之间切换的时候定义不同的过渡效果，即补充中间帧。

1、语法：

①transition： 属性名 时长 过渡方式 延迟

例如：transition：left 1000ms liner 200ms

②多个不同的属性用逗号隔开

例如：transition：left 200ms,top 400ms

③可以用all代表所有属性

例如：transition： all 200ms

2、过渡方式：

liner | ease | ease-in | ease-out | ease-in-out | cubic-bezier | step-start | step-end | steps 

3、注意：并不是所有属性都可以过渡。

①display：none =>block 没法过渡，一般改为：visibility：hidden =>visible

原因：display: none;是彻底消失，不在文档流中占位，浏览器也不会解析该元素；不会被子元素继承。visibility:hidden;是视觉上消失了，在文档流中占位，浏览器会解析该元素；会被子元素继承。

②background和opacity可以过渡。

（二）animation

animation：用来指定一组或多组动画，每组之间用逗号相隔。

* 语法：

缩写语法：

animation：时长 | 过渡方式 | 延迟 | 次数 | 方向 | 填充方式 | 是否暂停 | 动画名

时长：1s 或者 1000ms;

过渡方式：和transition一样，liner | ease | ease-in  | ease-out | ease-in-out等；




延迟：1s 或者 1000ms;

次数：3或者2 或者infinite（无限次）

方向：normal | reverse | alternate | alternate-reverse

填充方式：none | forwards | backwards | both

是否暂停：running | paused

以上属性都有对应的单独的属性。

（三）transition和animation的区别：

transition关注的是CSS属性的变化，property值和时间的关系是一个三次贝塞尔曲线，强调过渡属性。

animation作用于元素本身而不是样式属性，可以使用关键帧的概念，自由实现很多动画效果，需要绑定到选择器的 keyframe 名称，强调动画方式。
至于实现动画效果用哪一种，看应用场景。








