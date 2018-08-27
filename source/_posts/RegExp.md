---
title: 正则表达式参考手册
categories: Regexp
tags: 正则表达式
---

## 为什么要正则表达式？

### 使用正则表达式的一个小例子

```
// 来源： http://www.12306.cn/mormhweb/js/adKyfw.min.js, 访问日期： 2016-06-22
d = d.replace("'", "");
d = d.replace("%", "");
d = d.replace("#", "");
d = d.replace("&", "");
d = d.replace("*", "");
d = d.replace("(", "");
d = d.replace(")", "");
d = d.replace("@", "");
d = d.replace("`", "");
d = d.replace("/", "");
d = d.replace("\\", "");
d = d.replace(",", "");
d = d.replace(".", "");
d = d.replace("=", "");
d = d.replace("<", "");
d = d.replace(">", "");
```

上述代码是在过滤掉不合法的搜索字符，我们可以用一行正则替换来实现相同的功能：

```
d = d.replace(/'%#\&\*\(\)@`\/\\,\.=<>/g, '');
```

### 基本语法

定义正则表达式的方式在不同的工具中可能有所差别，但正则表达式内容的语法是一致的。 正则表达式有三类语法结构：

1. 串接（与操作）。相邻的字符默认为串接关系。例如 harttle 只能匹配 harttle， 不可匹配 hart。
2. 选择（或操作，|）。例如：harttle|serene 可以匹配 harttle 或者 serene。 选择的优先级级低于串接，因此很多情况下都可以省略括号。
3. 数量（限定符）。最常见的数量限定符包括+, ?, \*，分别表示左侧的字符出现一次或更多，不出现或出现一次，不出现或出现任意次。例如 harttle?可以匹配 harttl 和 harttle。
4. 组合（括号，()）。组合用来定义操作符的作用范围和优先级。例如 har(ttle)?可以匹配 harttle 和 har，h(a|u)rttle 可以匹配 harttle 和 hurttle。

### 表达式全集

More info: [参考](https://harttle.land/2016/07/18/intro-to-regexp.html)
