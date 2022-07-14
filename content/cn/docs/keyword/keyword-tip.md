---
title: "Tips"
description: ""
lead: ""
date: 2022-07-11T20:59:23+08:00
lastmod: 2022-07-11T20:59:23+08:00
draft: false
images: []
menu:
  docs:
    parent: "keyword"
    identifier: "keyword-tip-4cb9d5b30010ccf7c542afb2d2da1e3a"
weight: 105
toc: true
---

|声明变量的修饰符写法|
|---|
|`__strong`|
|`__weak`|
|`__unsafe_unretained`|
|`__autoreleasing`|

例：

```objc
__strong NSArray * strongStrArr = testArr; // 默认不需要写
__weak NSArray * weakStrArr = testArr;
```

|声明属性的修饰符写法|
|---|
|`__strong`|
|`__weak`|
|`__unsafe_unretained`|
|`__autoreleasing`|