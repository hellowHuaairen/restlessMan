
---
title: Vue + SpringCloud前后端分离项目3个月项目实战经验分享(下)
date: 2018-09-07 09:25:00
author: 不安分的猿人
img: /medias/featureimages/8.jpg
top: true
cover: true
coverImg: /medias/featureimages/8.jpg
password: 8d969eef6ecad3c29a3a629280e686cf0c3f5d5a86aff3ca12020c923adc6c92
toc: false
mathjax: false
summary: 上篇文章总结了三个月的后端开发。本篇主要对3个个月前端开发做个总结。
categories: Vue
tags:
  - SpringCloud
  - Vue
---

Vue + SpringCloud前后端分离项目3个月项目实战经验分享(下)



## 1.前言

上篇文章总结了三个月的后端开发。本篇主要对3个个月前端开发做个总结。最开始我想着我主要负责好后端的开发。没后端接口开发完成与前台的同事调接口。由于前端严重缺人，后端接口开发完成，没有可以和我调试接口的前端工作人员，于是我就想着不如自己来调前端页面吧！

Vue作为时下最流行的前端框架之一，我也想学习一下，于是开始一个人前后台的联调。（自己玩特别嗨哟！）

![](https://ae01.alicdn.com/kf/HTB1bAxsa1T2gK0jSZFvq6xnFXXaJ.jpg)

## 2.技术栈

![](https://ae01.alicdn.com/kf/HTB1bJ8Xbbr1gK0jSZFD7629yVXab.png)

1. Vue：是一套构建用户界面的渐进式框架。  数据驱动，组件化是Vue的两大核心思想。
2. Vue Router：是Vue的路由，根据不同的路径映射到不同的视图。
3. ElementUI：是一套基于 Vue 2.0 的组件库，提供了配套设计资源。由饿了么公司前端团队开源。 
4. Vuex： 是一个专为 Vue.js 应用程序开发的状态管理模式。它采用集中式存储管理应用的所有组件的状态，并以相应的规则保证状态以一种可预测的方式发生变化。 

## 3.前端项目总结

1. 组件的概念

组件就是可以扩展HTML元素，封装可重用的HTML代码，可以将组件看作自定义的HTML元素。 

2. 组件间的传值

​     父组件传参数给子组件，在子组件的自定义标签上写动态属性 :data = '数据'，子组件中定义props的选项['data']。

​     子组件传参数给父组件， 子组件中自定义绑定事件 <child-a @toParent="fn"></child-a>，触发事件 this.$emit('toParent', this.msg)，将子组件运算的结果通过emit事件传递回调函数toParent给父组件，this.msg为传递给父组件的参数。

​    更多组件之间的传值，可参考链接：<https://blog.csdn.net/lander_xiong/article/details/79018737> 

3. 正确使用Vue的声明周期函数

​       created： html加载完成之前执行。执行顺序，先父组件后子组件。

​       mounted： html加载完成后执行。执行顺序，先子组件后父组件。

​       watch： 监听一个值的变化，然后执行相对应的函数。

​       computed：computed是计算属性，也就是依赖其它的属性计算所得出最后的值。

![](https://ae01.alicdn.com/kf/HTB1FuxebbY1gK0jSZTEq6xDQVXaj.jpg)

4. vue.js支持打断点

和之前使用javascript一样，vue代码中也可打debugger,也可在Google Chrome浏览器安装vue插件vue devtools，插件可以查看组件的数据，插件特别好用。安装方法：https://blog.csdn.net/chenjiepds/article/details/80034956

5. 遇到的坑

​         1.定义scss样式时，需要添加scope来限制，表明样式只在本组件中起作用。通过scss定义elementUi组件内容的样式时需要添加/deep/，否则样式无效。

​        2.有时无法用“=”无法赋值的时候， 就需要使用set方法赋值，例如：this.$set(this.modelForm,'name','wangzg') 

​        3.恰当的使用插糟。定义一个名child子组件，为该子组件添加内容应该在子组件的template中定义，直接在父组件的<child>标签中定义的内容不会被渲染。使用插槽就能解决这个问题。在子组件template中加入<slot>元素占位，便能渲染父组件<child>标签下的内容。如果如果父组件没有为这个插槽提供了内容，会显示默认的内容。如果父组件为这个插槽提供了内容，则默认的内容会被替换掉。

​        4.结合elementUi中级联选择器v-model的选项中的值需要options的类型必须是数组，且是唯一标识。

​        5.事件绑定问题

修饰符native是用于自定义组件，也就是自定义的html标签。

修饰符self可以理解为跳过冒泡事件和捕获事件，只有直接作用在该元素上的事件才可以执行。

​         6.将ElementUi上传文件组件中的http-request的函数置成空函数，覆盖默认的上传行为，就可以自定义实现上传。

​         7.async与awit的使用，需要等待接口数据来渲染页面或者是避免页面出现闪屏的效果时使用。

async/await使用场景，是当前端接口调用需要后台等待接口返回值后才能渲染页面。

 async的用法，它作为一个关键字放到函数前面，用于表示函数是一个异步函数。

 await的含义为等待。意思就是代码需要等待await后面的函数运行完并且有了返回结果之后，代码继续向下执行。

## 4.结语

大部分的组件还是前端组开发的，我所做的工作就是前后台的接口对接和一些前台小功能的开发。虽然做的东西不算复杂，但是遇到的问题也挺多的。从最开始的举步维艰，到后来能独立解决问题，着实比较高兴。

人常说举一反三，我学习的Java编程语言，当然我会用Java写Hello World，那么我们也应该可以用Python，C++，Javascript，Vue等写Hello World。工作两年后，我渐渐地写过一些Bash脚本，查阅过Python的API，也开始写过jQuery。工作的需要让你跳出舒适区，只有不断地学习，才能让自己利于不败之地！

16岁的中学生都开发小程序了，再不加油，真的就被拍到沙滩上了！