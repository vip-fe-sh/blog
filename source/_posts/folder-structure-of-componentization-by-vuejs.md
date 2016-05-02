---
title: 基于 Vue.js 的组件化项目目录结构
date: 2016-04-16 20:59:26
author: yangxu
category: web开发
tags: [前端, 组件化, vuejs]
---

经过了[前文](http://vip-fe-sh.com/2016/04/13/think-about-frontend-componentization-solution/)的一番讨论，我们的项目最终采用了一套基于 [Vue.js](http://cn.vuejs.org/) 和 [webpack](http://webpack.github.io/) 的前端组件化架构，参考了 Vue.js 的官方推荐结构 [vue-webpack-boilerplate](https://github.com/vuejs-templates/webpack)，轻量、高效，自动化、扩展性和维护性都不错，下面简单说明一下这套系统的目录结构.

## 目录结构

```
webapp
│
├── build
│   ├── webpack.base.conf.js
│   ├── webpack.dev.conf.js
│   └── webpack.prod.conf.js
│
├── src
│   ├── app.js
│   ├── components
│   │   ├── App
│   │   │   ├── index.html
│   │   │   ├── index.sass
│   │   │   └── index.js
│   │   └── Hello
│   │       ├── index.html
│   │       ├── index.sass
│   │       └── index.js
│   ├── vuex
│   │   ├── actions.js
│   │   ├── mutations.js
│   │   └── store.js
│   ├── utils
│   │   ├── filter.js
│   │   └── utils.js
│   └── styles
│       ├── app.sass
│       └── base.sass
│
├── dist
│   ├── app.min.js
│   ├── app.min.css
│   └── vendors.min.js
│
├── demo
│   ├── index.html
│   └── mock
│       └── mock.json
│
├── lib
│   └── spin.min.js
│
├── node_modules
│
├── .babelrc
│
├── .eslintrc
│
└── package.json
```

## webpack

build 目录下面是 webpack 的配置脚本，分为基础、开发和生产三个环境的配置，可以分别针对开发环境和生产环境执行打包操作。我们用到的 webpack 功能主要有 js 代码 eslint 检查、es6 代码 babel 编译、sass 编译、打包单独 css 文件、单独打包框架代码、sourceMap 输出、热替换、自动刷新、开发环境判断、开发服务器等，更多的功能可以参考 webpack [官方文档](http://webpack.github.io/docs/).

## 源码

实际开发代码都在 src 目录下，包括入口文件 `app.js`，组件目录 `components`，数据流转处理 `vuex`，工具函数目录 `utils`，以及样式文件目录 `styles`，每个组件由 html、sass，js 三个文件组成，`utils` 主要包括 Vue.js 的过滤器，以及一些通用工具函数，样式下有基础样式和应用入口样式，所有这些经由 webpack 打包，最后生成 `dist` 目录下的 `app.min.js`，`app.min.css`，这里的 `vendors.min.js` 是业务之外的代码打包出来的，主要包含 Vue.js 和其他一些依赖.

## vuex

对于比较简单的纯展示性页面，只要有单纯的 ui 组件组合就可以满足需求了，如果项目比较复杂，数据交互很频繁，那么就很有必要把数据流转的处理逻辑单独给拎出来，Vue.js 官方提供了类 flux 工具 [vuex](https://github.com/vuejs/vuex/)，用于简化组件和数据的交互，整体流程如下图所示：

![vuex](https://raw.githubusercontent.com/vuejs/vuex/master/docs/en/vuex.png)

## 本地demo

我们在webpack 开发服务器中支持了本地 demo 和数据 mock，这样可以方便在本地调试页面，另外，我们引入了 vue-resource，完成 http 请求.

## 非 npm 模块

对第三方非 npm 模块，我们统一放到 `lib` 目录下，在页面中直接引入.

## 其他

.babelrc 和 .eslintrc 分别是 [babel](https://babeljs.io/) 和 [eslint](http://eslint.org/) 的配置文件，需要了解具体功能的话可以查看它们的官方文档，此外，我们还用到了 [standard JS](https://github.com/feross/standard) 作为 eslint 的检查规则，配合编辑器的 linter 和 format 功能，可以很方便的统一代码规范.

## vip-cli

最后，我们把这一套目录结构提取出来，基于 Vue.js 官方的脚手架工具 [vue-cli](https://github.com/vuejs/vue-cli)，做了一个 [vip-cli](https://github.com/vip-fe-sh/vip-cli)，可以直接生成如上的目录结构，如果其他项目需要类似架构的话可以很方便的复用：）

> to be continued...

