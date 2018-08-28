---
title: Transition过渡
date: 2018-08-28 22:15:26
categories: CSS
tags: CSS动画相关
---

## Transition 过渡

### [参考网站-transition](https://css-tricks.com/almanac/properties/t/transition/)

在 CSS3 中，我们可以使用 transition 属性来将元素的某一个属性从“一个属性值”在指定的时间内平滑地过渡到“另外一个属性值”来实现动画效果。

CSS transform 属性所实现的元素变形，呈现的仅仅是一个“结果”，而 CSS transition 呈现的是一种过渡“过程”，通俗点说就是一种动画转换过程，如渐显、渐隐、动画快慢等。

```
语法:transition:属性 持续时间 过渡方法 延迟时间;
```

CSS3 的过度 transition 属性是一个复合属性，主要包含 4 个子属性:

### transition-property:对元素的哪一个属性进行操作;

对于 CSS3 过渡动画，大多数情况下都是配合:hover 伪类来使用。其对应具有过渡的 CSS 属性主要有:
![2018-06-22 10 50 45](https://peterlxb.gitbooks.io/front-end-study-notes/content/assets/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202018-04-10%20%E4%B8%8A%E5%8D%887.36.13.png)

### transition-duration:过渡的持续时间;

> 说明:transition-duration 属性取值是一个时间，单位为 s(秒)，可以为小数如 0.5s。 如果提供多个属性值，以逗号进行分隔。

### transition-timing-function:过渡使用的方法(函数);

使用 transition-timing-function 属性来定义过渡方式。所谓的“过渡方式”主要用来指 定动画在过渡时间内的速率。

默认值:ease
transition-timing-function 属性取值共有 5 种，具体如下:

![2018-06-22 10 50 45](https://peterlxb.gitbooks.io/front-end-study-notes/content/assets/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202018-04-10%20%E4%B8%8A%E5%8D%887.38.54.png)

取值:

- linear: 线性过渡。等同于贝塞尔曲线(0.0, 0.0, 1.0, 1.0)
- ease: 平滑过渡。等同于贝塞尔曲线(0.25, 0.1, 0.25, 1.0)
- ease-in: 由慢到快。等同于贝塞尔曲线(0.42, 0, 1.0, 1.0)
- ease-out: 由快到慢。等同于贝塞尔曲线(0, 0, 0.58, 1.0)
- ease-in-out:由慢到快再到慢。等同于贝塞尔曲线(0.42, 0, 0.58, 1.0)

### transition-delay:可选属性，指定过渡开始出现的延迟时间;

transition-delay 属性取值是一个时间，单位为 s(秒)，可以为小数如 0.5s。

### transition

如果想要使用 transition 属性同时对多个属性进行实现平滑过渡效果，只需要在 transition-property 属性添加多个属性名即可，其中属性名之间用英文逗号隔开。然后各自可以有各自不同的延续时间和其时间的速率变换方式。

但需要值得注意的一点:第一个时间的值为 transition-duration，第二个为 transition-delay。
例如:

```
a{ transition: background 0.8s ease-in 0.3,color 0.6s ease-out 0.3;}
```
