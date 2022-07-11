---
title: "Copy"
description: ""
lead: ""
date: 2022-07-11T20:53:17+08:00
lastmod: 2022-07-11T20:53:17+08:00
draft: false
images: []
menu:
  docs:
    parent: "keyword"
    identifier: "copy-773cb29a89167c6738f1246aac15bee3"
weight: 103
toc: true
---

{{< alert icon="👉" context="" text="COPY 分为浅拷贝、深拷贝" />}}

修饰NSString、block；stackblock 如果不copy的话，stackblock 是存放在栈里面的，他的生命周期会随着函数的结束而出栈的，copy 之后会转变为 mallocblock 放在堆里面。

## 深拷贝和浅拷贝


1. copy 是复制出不可变对象
2. mutableCopy 是复制出可变对象
3. 复制出来的对象互不影响
4. copy 复制不可变对象属于浅拷贝（浅拷贝就只是地址拷贝）
5. copy 复制可变对象属于深拷贝（需要复制出一份不可变对象，以免之前可变对象变更影响复制出来的对象）
6. mutableCopy 属于深拷贝（重新申请一份内存和指针）

```objc
- (void)viewDidLoad {
    [super viewDidLoad];
    
    NSArray * arr = @[@1, @2];
    NSArray *arrCopy = [arr copy];
    NSMutableArray * arrMCopy = [arr mutableCopy];
    
    [arrMCopy addObject:@3];
    NSLog(@"%p, %p, %p", arr, arrCopy, arrMCopy);
    
    NSMutableArray * marr = [NSMutableArray arrayWithArray:arr];
    NSArray *marrCopy = [marr copy];
    NSMutableArray * marrMCopy = [marr mutableCopy];
    
    NSLog(@"%p, %p, %p", marr, marrCopy, marrMCopy);
}
```

{{< alert icon="👇" context="" text="Noraml Class Type Copy & mutableCopy results" />}}
||NSString|NSMutableStrong|
|---|---|---|
|copy|NSString <br>Pointer Copy|NSString <br>Object Copy|
|mutableCopy|NSMutableStrong <br>Object Copy|NSMutableStrong <br>Object Copy|
