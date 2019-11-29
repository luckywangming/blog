---
title: nuxt框架使用介绍
date: 2019-11-29 10:38:53
categories: NUXT
tags: 框架
---

## Nuxt为基于vue的SEO可选方案

与大家很熟练的vue项目相比，nuxt根本性的一个差异便是多了一层node层。
基于node层，代码的组织便和vue有了一些差异，比如全局变量在客户端、node端和服务端的互通有无。

#### Nuxt在服务端执行的接口

  服务端渲染利于SEO是指在爬虫爬取时已经拿到了渲染后的数据

+ NUXT框架支持服务端渲染的地方有：
  + asyncData 必须页面组件 即pages下的组件 components下的组件不可以
  + fetch 设置vuex数据变量
  + middleware 中间件 运行在组件渲染之前
  + nuxtServerInit 只在vuex且服务端执行 执行流程第一步
  + beforeCreate created这两个钩子在服务端和客户端被调用
  + 其他vue钩子只在客户端调用
  + 鉴别是否可被爬虫爬到请右键查看页面源代码 这是被爬虫获取的页面信息
  
#### 开发注意事项

1. 静态资源需要编译的放在assests文件夹里，会被webpack编译和打包，例如图片，小于1kb会被编译为base64，减少请求
2. 要善于使用中间件和nuxtServerInit处理node端的数据
3. 合理规范的使用vuex,可使项目更加清晰简洁
4. webpack压缩图片压缩率很低，可配合gulp对assets/images进行压缩[GULP压缩图片-配合VUE或NUXT](/2019/11/29/GULP压缩图片-配合VUE或NUXT)
5. nuxt.config.js里的配置项是很关键的参数，合理的配置会大大降低项目开发的难度和代码量
6. 在公共组件里尽量不要有接口请求，把具体业务暴露给父级组件执行