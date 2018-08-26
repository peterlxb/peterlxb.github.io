---
title: Float
date: 2018-08-26 10:53:39
tags: CSS相关
---

# 深入理解 CSS 浮动

## 定义

> MDN：
> float CSS 属性指定一个元素应沿其容器的左侧或右侧放置，允许文本和内联元素环绕它。该元素从网页的正常流动中移除，尽管仍然保持部分的流动性

浮动元素脱离普通流，然后按照指定方向，向左或者向右移动，碰到父级边界或者另外一个浮动元素停止。

> 值: left | right | none | inherit

> 初始值: none

> 应用于: 所有元素

> 继承性: 无

## 特性

### 1.浮动流

正常流中元素一个接一个排列；浮动元素也构成浮动流

![](/images/float1.png)

### 2.块级框

浮动元素自身会生成一个块级框，而不论这个元素本身是什么，使浮动元素周围的外边距不会合并
![](/images/float2.png)

### 3.包裹性

浮动元素的包含块是指其最近的块级祖先元素，后代浮动元素不应该超出包含块的上、左、右边界。若不设置包含块的高度，包含块若浮动，则包含块会延伸，进而包含其所有后代浮动元素；若不设置包含块的宽度，包含块若浮动，则包含块宽度由后代浮动元素撑开

![](/images/float3.png)

### 4.破坏性

浮动元素脱离正常流，并破坏了自身的行框属性，使其包含块元素的高度塌陷，使浮动框旁边的行框被缩短，从而给浮动框留出空间，行框围绕浮动框重新排列

![](/images/float4.png)

# 清除浮动

## 定义

clear 清除

> 值: left | right | both | none | inherit

> 初始值: none

> 应用于: 块级元素(块级元素指 block 元素，不包括 inline-block 元素)

> 继承性: 无

_设置 clear 属性的元素并不能改变浮动元素，而只能改变自身_

## 方法

清浮动其实就两种方法，一种是在浮动元素下面添加新元素设置 clear 属性；另一种是触发包含块的 BFC，使其包含浮动元素。

在除 IE7-以外的其他浏览器都可以将 clear 属性应用于<br>元素

为浮动元素的 after 伪元素设置 clear 属性

除了清除浮动外，常常也需要解决外边距 margin 重叠的问题。这时，清除浮动和解决 margin 重叠的代码如下

```
.clear:before,.clear:after{content:"";display:table;}
.clear:after{clear:both;}
.clear{zoom:1}
```

#### 参考文章

[深入理解 CSS 浮动](https://xiaohuochai.site/CSS/layout/float/float.html)
[深入理解 CSS 清除浮动](https://xiaohuochai.site/CSS/layout/float/clear.html)
[MDN-float](https://developer.mozilla.org/zh-CN/docs/CSS/float)
[MDN-clear 清除浮动](https://developer.mozilla.org/zh-CN/docs/Web/CSS/clear)
