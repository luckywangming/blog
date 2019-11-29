---
title: flex布局下 css溢出隐藏 多行溢出隐藏
categories: CSS
tags: 样式
date: 2019-11-26 19:22:19
---

# 溢出隐藏

#### 单行溢出隐藏
```
text-overflow: ellipsis;
overflow: hidden;
white-space: nowrap;
```

#### 多行溢出隐藏
```
display: -webkit-box;
-webkit-box-orient: vertical;
-webkit-line-clamp: 3;
overflow: hidden;
/* -webkit-line-clamp 显示行数 */

```
#### FLEX布局中失效

在css规范中，一般默认`min-height`为`0`,但是在flex容器中，默认为`auto`

解决方案：
一般有两种

1. 设置flex元素 `min-width:0`
   + 给溢出元素添加父级，父级宽度设置为0 `width:0;overflow:hidden`
2. 设置属性`flex-shrink:0` 