---
title: transform-2d变形
date: 2018-08-28 21:52:09
categories: CSS
tags: CSS动画相关
---

## transform-2d 变形

### [参考网站-transform](https://css-tricks.com/almanac/properties/t/transform/)

在 CSS3 中，我们可以使用 transform 属性来实现文字或图像的的各种变形效果， 如位移、缩放、旋转、倾斜

![2018-06-22 10 50 45](https://peterlxb.gitbooks.io/front-end-study-notes/content/assets/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202018-04-10%20%E4%B8%8A%E5%8D%886.44.20.png)

### 旋转 rotate()方法

用 rotate()方法来将元素相对中心原点进行旋转。

![2018-06-22 10 50 45](https://peterlxb.gitbooks.io/front-end-study-notes/content/assets/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202018-04-10%20%E4%B8%8A%E5%8D%886.46.20.png)

> 语法:transform:rotate(度数);说明:度数指的是元素相对中心原点进行旋转的度数，单位为 deg。

其中，deg 是 degree(度数)的缩写。

它主要在二维空间内进行操作，设置一个角度值，用来指定旋转的幅度。如果这个值为正值，元素相对原
点中心顺时针旋转;如果这个值为负值，元素相对原点中心逆时针旋转。

### 位移 translate()方法

![2018-06-22 10 50 45](https://peterlxb.gitbooks.io/front-end-study-notes/content/assets/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202018-04-10%20%E4%B8%8A%E5%8D%886.48.32.png)

在 CSS3 中，我们可以使用 translate()方法将元素沿着水平方向(X 轴)和垂直方 向(Y 轴)移动.

### 缩放 scale()方法

缩放，指的是“缩小”和“放大”。在 CSS3 中，我们可以使用 scale()方法来将元 素根据中心原点进行缩放。

![2018-06-22 10 50 45](https://peterlxb.gitbooks.io/front-end-study-notes/content/assets/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202018-04-10%20%E4%B8%8A%E5%8D%886.48.32.png)

缩放 scale()方法也有 3 种情况:

#### (1)scaleX(x):元素仅水平方向缩放(X 轴缩放);

> 说明:x 表示元素沿着水平方向(X 轴)缩放的倍数，如果大于 1 就代表放大;如果小于 1 就代表缩小。

#### (2)scaleY(y):元素仅垂直方向缩放(Y 轴缩放);

#### (3)scale(x,y):元素水平方向和垂直方向同时缩放(X 轴和 Y 轴同时缩放);

### 倾斜 skew()方法

它可以将一个对象以其中心位置围绕着 X 轴和 Y 轴按照一定的角度倾斜。

这与 rotate()函 数的旋转不同，rotate()函数只是旋转，而不会改变元素的形状。skew()函数不会旋转，而 只会改变元素的形状。

skew()方法跟 translate()方法、scale()方法一样，也有 3 种情况:

> (1)skewX(x):使元素在水平方向倾斜(X 轴倾斜);transform:skewX(x);

> (2)skewY(y):使元素在垂直方向倾斜(Y 轴倾斜);transform:skewY(y);

skew 的默认原点 transform-origin 是这个物件的中心点

#### skewX(30deg) 如下图:(沿着 X 轴倾斜，沿着 Y 轴呈逆时针旋转 30 度。)

![2018-06-22 10 50 45](https://peterlxb.gitbooks.io/front-end-study-notes/content/assets/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202018-04-10%20%E4%B8%8A%E5%8D%886.59.52.png)

#### skewY(10deg)如下图:(沿着 y 轴倾斜，沿着 X 轴呈顺时针旋转 10 度。)

![2018-06-22 10 50 45](https://peterlxb.gitbooks.io/front-end-study-notes/content/assets/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202018-04-10%20%E4%B8%8A%E5%8D%887.01.04.png)

### transform-origin 属性

任何一个元素都有一个中心原点，默认情况下，元素的中心原点位于 X 轴和 Y 轴的 50%处,

如下图所示:
![2018-06-22 10 50 45](https://peterlxb.gitbooks.io/front-end-study-notes/content/assets/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202018-04-10%20%E4%B8%8A%E5%8D%887.02.28.png)

默认情况下，CSS3 变形进行的位移、缩放、旋转、倾斜都是以元素的中心原点(50%,50%)进行变形。

但很多时候，我们可以通过 transform-origin 属性来改变元素变形时的中心原点位置。

> 语法:
> transform-origin:[<percentage>|<length>|left|center1|right][<percentage> | <length> | top | center2 | bottom ]?

> 默认值:50% 50%，效果等同于 center center

![2018-06-22 10 50 45](https://peterlxb.gitbooks.io/front-end-study-notes/content/assets/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202018-04-10%20%E4%B8%8A%E5%8D%887.03.44.png)
