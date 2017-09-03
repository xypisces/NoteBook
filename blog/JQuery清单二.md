---
title: jQuery应用清单(二)
date: 2016/12/25
tags:
- WEB
- jQuery
---
### 项目位置
[github.com/xypisces/JavaScript](https://github.com/xypisces/Javascript)中的jQuery应用中.
### store.js
使用`store.js`插件进行localstore进行数据存储
### `base.js`中的各个函数流程
#### 添加删除功能函数实现
` init()` 初始化,如果localstore有数据就渲染出来
` render-task-list()` 渲染出所有数据
` render-task-item()` 渲染单挑数据tpl
` on-add-task-from-submit()` 绑定增加按钮
` add-task()` 将数据存入队列
` refresh-task-list()` 将队列更新到localstore中
` listen-task-detail()` 监听所有删除按钮
` delete-task()` 删除该条信息
初始化: `init()->render-task-list()->render-task-item()`
添加: `on-add-task-from-submit()->add-task()->refresh-task-list()->render-task-list()->render-task-item()`
删除: `listen-task-detail()->delete-task()->render-task-list()->render-task-item()`

