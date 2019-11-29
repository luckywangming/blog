---
title: 'GULP压缩图片,配合VUE或NUXT'
date: 2019-11-29 11:17:07
categories: GULP
tags: 工具
---

## gulp处理图片资源压缩

项目中一般比较大的资源就是图片资源，所以一个项目的图片必须经过高压缩又高保真的处理。
webpack的插件压缩图片率都比较低，而且压缩图片是一个异步耗时的工作，
所以在项目中压缩图片一般会单独处理。
在这里推荐一个gulp压缩工具 `gulp-tinypng-nokey`

这个工具来源于[熊猫压缩](https://tinypng.com/),
是我接触过压缩率最高的工具了，png一般能压缩一半以上，jpg相对少些。

## gulp-tinypng-nokey

确保已全局安装gulp
```
npm i gulp -g
```

使用`gulp-tinypng-nokey`：
```
npm i gulp-tinypng-nokey -D
```

然后在根目录新建`gulpfile.js`

输入以下代码：
```
var gulp = require("gulp"),
  tinypng_nokey = require('gulp-tinypng-nokey');

gulp.task('min-imgs', async function () {
  await gulp.src('assets/images/*.{png,jpg,jpeg,gif,ico}')
    .pipe(tinypng_nokey())
    .pipe(gulp.dest('assets/images'));
})
```

执行`gulp min-imgs` 
也可以在`package.json`中配置新的指令：
```
"scripts": {
  "min-imgs": "gulp min-imgs"
}
```

这样便会将assets/images下的图片压缩后再输出覆盖到原文件夹.