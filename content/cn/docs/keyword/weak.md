---
title: "Weak"
description: ""
lead: ""
date: 2022-07-11T20:41:53+08:00
lastmod: 2022-07-11T20:41:53+08:00
draft: false
images: []
menu:
  docs:
    parent: "keyword"
    identifier: "weak-ac561e605b7330bcf1ea80d95d2bce60"
weight: 102
toc: true
---

{{< alert icon="👉" context="" text="`weak` 是弱引用，不会持有对象，引用计数器不会+1" />}}

常用于修饰UI控件、delegate；声明为weak的指针，weak指针指向的对象一旦被释放，weak的指针都将被赋值为nil，防止野指针。