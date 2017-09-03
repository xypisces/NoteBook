---
title: 使用vue构建饿了么app前端
date: 2017/4/5
tags:
- WEB
- VUE
---

### vue.js语言
- 特性: 基于数据驱动和组件化的前端MVVM框架
- 应用场景: 复杂的交互页面,基础的架构抽象,Ajax数据持久化
- MVVM: view(DOM)<-->viewModel(通讯)<-->Model(js)

### 项目的构建
- npm install -g vue-cli
- vue init webpack project-name
- cd project-name
- npm install
- npm run dev

### 前期准备
- 图片素材的准备: icomoon.io将SVG文件上传制作成CSS文件
- MOCK数据: 使用json文件
- node编写接口:
```javascript
var appData = require('../data.json');
var seller = appData.seller;
var goods = appData.goods;
var ratings = appData.ratings

var apiRoutes = express.Router();

apiRoutes.get('/seller', function (req, res) {
    res.json({
        errno: 0,
        data: seller
    });
});
apiRoutes.get('/goods', function (req, res) {
    res.json({
        errno: 0,
        data: goods
    });
});

apiRoutes.get('/ratings', function (req, res) {
    res.json({
        errno: 0,
        data: ratings
    });
});

app.use('/api', apiRoutes);
```

### vue-router
- 安装vue-router:npm install vue-router --save-dev
- 目录:
```
src
 -components
  -goods
   -goods.vue
 app.vue
 main.js
index.html    
```
- main.js进行路由配置:创建组件->创建router->映射路由->v-Link指令->router-view标签->启动路由
```javascript
import Vue from 'vue';
import App from './App';
import VueRouter from 'vue-router';
import goods from 'components/goods/goods';
import ratings from 'components/ratings/ratings';
import seller from 'components/seller/seller';

Vue.use(VueRouter); //使用vue-router
let app = Vue.extend(App); //创建一个根组件,依赖于
let router = new VueRouter(); //调用构造器实例化vue-router
router.map({
    '/goods': {
        component: goods
    },
    '/ratings': {
        component: ratings
    },
    '/seller': {
        component: seller
    }
}); //进行路由映射
router.start(app, '#app'); //挂载在#app的元素上
router.go('/goods'); //默认路由

