---
title: CSS布局-居中布局
date: 2018-08-21 19:26:33
categories: CSS
tags: CSS布局
---

# 居中布局

# 水平居中布局\(子容器和父容器宽度不定情况\)

![](/images/center.png)

## inline-block + text-align

{% codeblock inline-block + text-align %}

<div class="parent">
  <div class="child">DEMO</div>
</div>

.child {
display: inline-block;
}
.parent {
text-align-center;
}
{% endcodeblock %}

> 兼容性好，兼容 IE6-7;
>
> 需要额外代码来修复 text-align 造成问题。

## table + margin

{% codeblock table + margin %}

<div class="parent">
  <div class="child">DEMO</div>
</div>

.child {
display:table;
margin: 0 auto;
}
{% endcodeblock %}

## absolute + transform

{% codeblock table + margin %}

<div class="parent">
  <div class="child">DEMO</div>
</div>

.parent {
position: relative;
}
.child {
position:absolute;
left:50%;
transform: translateX(-50%);
}
{% endcodeblock %}

> 居中元素不会对其他元素产生影响
>
> 兼容性较差

## flex + justify-content

{% codeblock table + margin %}

<div class="parent">
  <div class="child">DEMO</div>
</div>

.parent {
display: flex;
justify-content: center;
}

{% endcodeblock %}

{% codeblock table + margin %}

<div class="parent">
  <div class="child">DEMO</div>
</div>

.parent {
display: flex;
}
.child {
margin: 0 auto;
}

{% endcodeblock %}

> 只需设置父元素即可实现居中布局
>
> 低版本不支持
