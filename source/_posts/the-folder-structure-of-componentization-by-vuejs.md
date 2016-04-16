---
title: 基于Vue.js的组件化项目目录结构
date: 2016-04-16 20:59:26
author: yangxu
category: web开发
tags: [前端, 组件化, vuejs]
---

我们的项目最终采用了一套基于 [Vue.js](http://cn.vuejs.org/) 的组件化架构，轻量，高效，扩展性和维护性都不错，下面简单说明一下这套系统的目录结构。

```
webapp
│
├── dist
│   ├── app.min.js
│   ├── app.min.css
│   └── vender.min.js
│
├── src
│   ├── ceo.js
│   ├── operatingBillboard.js
│   ├── components
│   │   ├── ceoGrid
│   │   │   ├── index.js
│   │   │   └── index.sass
│   │   ├── operatingBillboardGrid
│   │   │   ├── index.js
│   │   │   └── index.sass
│   │   └── chart
│   │       ├── index.js
│   │       └── index.sass
│   ├── utils
│   │   ├── chart.js
│   │   ├── parse.js
│   │   └── native.js
│   ├── libs
│   │   ├── echarts.min.js
│   │   ├── iscroll.min.js
│   │   └── swiper.min.js
│   └── styles
│       ├── ceo.sass
│       ├── operatingBillboard.sass
│       ├── base.sass
│       └── themes
│           ├── white.sass
│           └── red.sass
│
├── jsp
│   ├── ceo.jsp
│   └── operatingBillboard.jsp
│
├── demo
│   ├── ceo.html
│   ├── operatingBillboard.html
│   └── mock
│       ├── ceo.json
│       └── operatingBillboard.json
│
├── node_modules
│   ├── babel
│   ├── vue
│   ├── webpack
│   └── eslint
│
├── package.json
│
└── webpack.config.js
```

