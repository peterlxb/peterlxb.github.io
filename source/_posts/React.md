---
title: React入门01-基本概念
date: 2018-08-27 22:12:40
categories: React学习笔记
tags: React fundamentals
---

# 1-React 出现的历史背景和特性介绍

Facebook 内部
![2018-06-22 10 50 45](https://user-images.githubusercontent.com/8121883/41755509-61833b66-760a-11e8-9ae6-ff9c4e27fb90.png)
如图片所示的功能:好友请求，消息列表，状态信息。
出现的问题:当到达一个新的消息时，图中的数字 3 并没有及时更新，或者明明点开了这个新消息，数字 3 也并没有消失。

## 问题出现的根源

![2018-06-22 10 57 00](https://user-images.githubusercontent.com/8121883/41755662-05390308-760b-11e8-8bda-12d28673e86a.png)
需要知道非常多的细节才能更新页面上的 UI
![2018-06-22 10 59 11](https://user-images.githubusercontent.com/8121883/41755727-59eab716-760b-11e8-860a-87b4b2782ed1.png)
以往做 web 开发的时候碰到需要局部更新页面上的状态，就需要去操作这个 DOM 节点，这时候就要用到 DOM API，只有熟练掌握了上图中的方法才能顺利完成页面的局部更新。
这也说明了一个问题，当要做比较复杂的页面操作，就需要关注很多的细节。

## React 提出的解决方案

![2018-06-22 11 02 10](https://user-images.githubusercontent.com/8121883/41755816-cd396c26-760b-11e8-9f43-092fca3265a8.png)
**用一个聊天应用的示例来说明**
这个聊天应用需要将新消息到达时展示在页面上。
首先是传统 web 开发的局部更新
![2018-06-22 11 03 20](https://user-images.githubusercontent.com/8121883/41755856-f1d223c0-760b-11e8-905a-619bdee9e507.png)
首先我们需要知道来的消息中，哪条是新的消息。然后针对新消息创建一个 DOM 节点，并且把这个节点更新到 UI 上。
![2018-06-22 11 06 40](https://user-images.githubusercontent.com/8121883/41755960-5dc72da0-760c-11e8-947c-197a211c49c6.png)
React 的思路:始终是整体刷新。
前后是两个状态，一个是两条消息，一个是三条消息。它并不关注哪条消息是新的。
**它的逻辑是把整个消息展示在 UI 上。**
React 并不关心细节，当 React 发现前后两个状态变了，相应的 UI 也会变化，React 自动完成 UI 更新的操作。
这样就把我们从细节操作的复杂度中解放出来，我们只需要关心状态及最终 UI 长什么样。

### 对比传统的 web 开发，React 的特点如下

![2018-06-22 11 11 24](https://user-images.githubusercontent.com/8121883/41756075-080a88e8-760d-11e8-8ca0-792f83a8f5c9.png)

## React 解决了 UI 细节问题。

数据模型的解决依赖 Flux 结构。

### 传统 MVC 难以扩展和维护

![2018-06-22 11 13 12](https://user-images.githubusercontent.com/8121883/41756118-49d0c616-760d-11e8-8351-45bc83ac34e2.png)
它有非常多的 model，非常多的 view，这些 model 和 view 之间的使用关心是错综复杂的，而且是双向绑定的。
这导致的问题就是:当应用程序复杂了以后，出现了一个问题，很难去追踪究竟是 model 出现了问题，还是 view 出现了问题。

## React 提出了 Flux 架构:单向数据流

![2018-06-22 11 13 53](https://user-images.githubusercontent.com/8121883/41756132-6008fbce-760d-11e8-9e69-20a765dc63e9.png)
Flux 架构并不是一个完整的技术实现，而是一种设计模式，它的核心思想就是单向数据流。
针对上图，一个完整的 Flux 架构流程就是:当 React Views 发生了一些用户操作，它会产生一个 action,这个 action 会通过 dispatcher 来 dispatch 出去，由 store 来进行处理，store 根据 action 来更新自己。
我们的 view 是绑定在 store 上的，所以 store 发生变化，view 也会更新。

# 2-以组件方式考虑构建 UI

React 中最核心的概念就是组件 component。组件可以让我们更直观地去描述我们的界面。

## 以构建一个下图所示的评论框为例

![2018-06-23 3 01 25](https://user-images.githubusercontent.com/8121883/41806761-55bbc734-76f6-11e8-8ff5-3e4493c4d441.png)

> 在传统模式下，我们可能需要定义一个 HTML 模版，然后通过 JavaScript 去获取一些数据，再把这些数据填充到模版中。下面会有一个 Form 表单，需要去绑定一些事件，去监听 submit 按钮去提交这个数据。

### 如果使用 React 组件化的方式 **将 UI 组织成组件树的形式**

![2018-06-23 3 07 47](https://user-images.githubusercontent.com/8121883/41806816-48fc385c-76f7-11e8-98c0-9f76c54c06a8.png)

> 可以把这个评论框分成几个部分:首先整个评论框就是一个大的组件，然后中间评论的 List 列表是一个组件，最后的 Form 又是一个组件，几个组件共同完成了一个功能。

通过这种方式可以很好很直观的描述我们的 UI，而且很自然的把 UI 拆分成比较小的独立的部分。

## 理解 React 组件

![2018-06-23 3 09 56](https://user-images.githubusercontent.com/8121883/41806831-8479b922-76f7-11e8-88f0-7706c16d5188.png)

> 1.React 组件一般不提供方法，而是某种状态机
> 2.React 组件可以理解为一个纯函数 3.单向数据绑定
> **由属性(props)和状态(state)最终得到一个 View。**

> React 组件的状态(state)由两种。一种是由外部传进来的属性(props)，一种是内部维持的状态(state)。
> 二者共同决定了 View 长什么样。

所以一个 React 组件可以理解为一个纯函数一样，它接受的参数是什么，输出的结果一定是确定的。
React 组件一般不会提供方法。
单向数据流:

> 外部要传数据进来，一定是通过 props 传进来。

如果组件外部要知道 View 内部发生了什么变化，那一定是 View 内部暴露了一个事件来让组件外部知道我们的组件内部发生了变化。

##创建一个简单的组件:TabSelect
![2018-06-23 3 18 55](https://user-images.githubusercontent.com/8121883/41806917-c60cc1e4-76f8-11e8-8e2b-fae265116941.png)

### React 组件的两种类型:受控组件和非受控组件

![2018-06-23 3 39 50](https://user-images.githubusercontent.com/8121883/41807087-b6ec14fa-76fb-11e8-9d2e-fc2b3a72c4df.png)

#### [受控组件](https://reactjs.org/docs/forms.html)

> 受控组件 Controlled Components 必须传递两个值，一个 value，一个 onChange。

它的值是什么取决于外部给它的属性而不是用户的输入，如果不指定 onChange 事件，输入任何值 value 都不会有变化。它的状态来自外部

#### [非受控组件](https://reactjs.org/docs/uncontrolled-components.html)

> Uncontrolled Components 非受控组件 它的状态由内部维护。
> 外部要用的时候是通过其它方式拿到它的值，这样的组件不需要传递 value 和 onChange 事件，但是一定要让外界知道这个原生 DOM node 是什么，从而才能够拿到它的值。

### 何时创建组件:单一职责原则

> 1.每个组件只做一件事 2.如果组件变得复杂，那么应该拆分成小组件
> 组件是构建 UI 的最小的元素，每个组件都应该尽量地小，这样才能使复杂度分散出去。

#### 拆分小组件有两个好处

第一可以让复杂度拆分到不同的地方，第二是性能问题：

> 当一个组件很大时，任何一个状态变化，整个组件都会进行刷新。如果拆分成小组件，这些小组件的状态可能没有变化，那它就不需要重新刷新，这样的化可以提高性能。

### 数据状态管理:DRY 原则

> 1.能计算得到的状态就不要单独存储 2.组件尽量无状态，所需数据通过 props 获取
> 能计算得到的状态在用的时候去计算它，而不是单独存储起来。
> 组件尽量无状态的好处是，可以让组件尽量是一个纯组件，他可以具有更好的性能，并且可以更容易被重用。

# 3-理解 JSX: 不是模板语言，只是一种语法糖

示例 JSX 语法
![2018-06-24 4 43 55](https://user-images.githubusercontent.com/8121883/41817441-d8b7c660-77cd-11e8-90ac-53a4553c9ae7.png)

## JSX 的本质:动态创建组件的语法糖

### JSX:在 JavaScript 代码中直接写 HTML 标记

![2018-06-24 4 44 38](https://user-images.githubusercontent.com/8121883/41817446-e8cb4e28-77cd-11e8-986b-e9b797720e9f.png)

### 组件的例子

![2018-06-24 4 44 55](https://user-images.githubusercontent.com/8121883/41817451-f9f48b92-77cd-11e8-9a32-aa1300ddc7c9.png)

## 在 JSX 中使用表达式

### 1. JSX 本身也是表达式

![2018-06-24 4 45 47](https://user-images.githubusercontent.com/8121883/41817459-132afa1a-77ce-11e8-87a4-35d907a552ad.png)

### 2. 在属性中使用表达式

![2018-06-24 4 46 13](https://user-images.githubusercontent.com/8121883/41817465-21b0e13a-77ce-11e8-845a-e463f8e138bb.png)

### 3. 延展属性

![2018-06-24 4 46 34](https://user-images.githubusercontent.com/8121883/41817467-2e9c5276-77ce-11e8-9b03-436b6d9b2599.png)

### 4. 表达式作为子元素

![2018-06-24 4 46 59](https://user-images.githubusercontent.com/8121883/41817469-3c3288e2-77ce-11e8-85d6-0295bb9437dd.png)

## 对比其它模板语言

![2018-06-24 4 47 13](https://user-images.githubusercontent.com/8121883/41817473-4b38c838-77ce-11e8-9835-2188dd88d958.png)

## JSX 优点

> 1.声明式创建界面的直观 2.代码动态创建界面的灵活 3.无需学习新的模板语言

## 约定:自定义组件以大写字母开头

> **1.React 认为小写的 tag 是原生 DOM 节点，如 div** > **2.大写字母开头为自定义组件** > **3.JSX 标记可以直接使用属性语法，例如<menu.Item />**

[原文 tips-to-learn-react-redux](https://www.robinwieruch.de/tips-to-learn-react-redux/)

1. **学习 React 的技巧**
2. **学习 Redux 的技巧**
3. **Testing 的技巧**
4. **一些建议**
