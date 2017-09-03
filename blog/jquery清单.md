---
title: jQuery应用清单(一)
date: 2016/12/20
tags:
- WEB
- jQuery
---
### 项目位置
[github.com/xypisces/JavaScript](https://github.com/xypisces/Javascript)中的jQuery应用中.
### 技术点
- 定时提醒功能的实现
- 最大限度重用数据
- 实现更强大的自定义alert()
- position属性的特殊用法

### 项目结构
- css
- js
- index.html
- node_modules
- package.json
使用npm安装jquery,添加到package.json依赖中,有利于项目的维护和迁移
js编写规范化
```js
// 自运行匿名函数,更加严谨
// 作用域限制,防止污染window全局环境,比如重写了consolo函数
// 前面的; 是用于在混淆压缩后别的文件没有结尾导致的出错
;(function(){
    'use strict'

})(); 
```
### 整体布局
基本布局
```html
<!-- 总容器 -->
<div class="container">  
    <!-- 添加任务 -->
    <div class="add-task">
        <input type="text">
        <button type="submit">submit</button>
    </div>
    <!-- 任务列表 -->
    <div class="task-list">
        <div class="task-item">
            <span><input type="checkbox"></span>
            <span class="task-content">item content 1</span>
            <span>delect</span>
            <span>detail</span>
        </div>
        <div class="task-item">
            <span><input type="checkbox"></span>
            <span class="task-content">item content 1</span>
            <span>delect</span>
            <span>detail</span>
        </div>      
    </div>
    <!-- 任务详情 -->
    <div class="task-detail">
        <div class="content"></div>
        <div>
            <div class="desc"></div>
        </div>
        <div class="remind">
            <input type="date">
            <button type="submit">submit</button>
        </div>
    </div>
</div>
```
### 基本样式

//使用npm install normalize.css安装样式重置表

`box-sizing:border-box 转换盒子模型`
盒子模型分margin,border,padding,content,当使用了box-sizing时,自动将padding和border计算在content中,即包含在宽度内,有利于布局.
`box-shadow:[inset] x-offset y-offset blur-radius spread-radius color`
- 阴影类型：可选；如省略，默认是外阴影；它有且只有一个值“inset”，表示为内阴影；
- x-offset：阴影水平偏移量，它可以是正负值。如为正值，则阴影在元素的右边；如其值为负值，则阴影在元素的左边；
- y-offset：阴影垂直偏移量，它可以是正负值。如为正值，则阴影在元素的底部；如其值为负值时，则阴影在元素的顶部；
- blur-radius：阴影模糊半径，可选，它只能是正值。如值为0，则阴影不具有模糊效果；它的值越大，阴影的边缘就越模糊；
- spread-radius：阴影扩展半径，可选，它可以是正负值。如为正值，则扩大阴影的尺寸；如为负值，则缩小阴影的尺寸；
- color：阴影颜色，可选，如不设定颜色，浏览器会取默认色，但各浏览器默认取色不一致。（经测试，在Safari上是半透明的，在chrome、firefox、ie上都是黑色的）。不推荐省略颜色值
- 例子:`box-shadow:5px 4px 4px #000;`相同大小的颜色为#000的色块表示向右移5px,向左移4px,高斯模糊4px,只留下背景交集部分.
`transition: <transition-property> || <transition-duration> || <transition-timing-function> || <transition-delay>`
- 过渡属性,过渡时间,过渡轨迹函数,过渡延迟时间
- ease: 开始和结束慢，中间快。相当于cubic-bezier(0.25,0.1,0.25,1)
- linear: 匀速。相当于cubic-bezier(0,0,1,1)
- ease-in: 开始慢。相当于cubic-bezier(0.42,0,1,1)
- ease-out: 结束慢。相当于cubic-bezier(0,0,0.58,1)
- ease-in-out: 和ease类似，但比ease幅度大。相当于cubic-bezier(0.42,0,0.58,1)
- step-start: 直接位于结束处。相当于steps(1,start)
- step-end: 位于开始处经过时间间隔后结束。相当于steps(1,end)
当transition-property的值的个数多于对应的transition-delay | transition-timing-function | transition-duration的属性值(属性值的个数大于1个)时，将按顺序开始取值
```
#test1{
    transition-property: width,background,opacity;
    transition-duration: 2s,500ms;
    transition-timing-function: linear,ease;
    transition-delay: 200ms,0s;
}
/*类似于*/
#test2{
    transition: width 2s linear 200ms,background 500ms ease 0s,opacity 2s linear 200ms;
}
```