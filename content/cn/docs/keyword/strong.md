---
title: "Strong"
description: ""
lead: ""
date: 2022-07-10T21:43:17+08:00
lastmod: 2022-07-10T21:43:17+08:00
draft: false
images: []
menu:
  docs:
    parent: "keyword"
    identifier: "strong-5cd4dfd3e3166f22aa3ba89592782493"
weight: 101
toc: true
---


## 说明

strong 是强引用，会持有对象，引用计数器会+1，可用于属性的修饰

例如：

```objc
@property (strong) NSString *aString;
```

```swift
let a = 's';
```

{{< highlight objc >}}
@property (strong) NSString *aString;
{{< / highlight >}}

`strong` 是为了告诉编译器（xcode），被 `strong` 修饰的对象是强引用，需要 `retain` 操作，引用计数器会+1，默认情况下声明变量都是隐式 `strong` 申明。

## 举例

**下面的例子来说明实例变量默认使用 strong 进行修饰的**

```objectivec
// 默认情况下strArr引用testArr打印输出
NSArray *testArr = @[@"a", @"b"];
NSArray *strArr = testArr;

testArr = nil;
NSLog(@"print str is %@", strArr);
    
// 打印结果
2021-05-30 15:33:14.931372+0800 Strong&Weak[3480:197342] print str is (
    a,
    b
)

// __strong修饰情况下strArr引用testArr打印输出
NSArray *testArr = @[@"a", @"b"];
__strong NSArray * strongStrArr = testArr;

testArr = nil;
NSLog(@"print strongStr is %@", strongStrArr);

// 打印结果
2021-05-30 15:37:30.308564+0800 Strong&Weak[3551:201548] print strongStr is (
    a,
    b
)

// __weak修饰情况下strArr引用testArr打印输出
NSArray *testArr = @[@"a", @"b"];
__weak NSArray * weakStrArr = testArr;

testArr = nil;
NSLog(@"print weakStr is %@", weakStrArr);

// 打印结果
2021-05-30 15:39:38.772768+0800 Strong&Weak[3579:203646] print weakStr is (null)
```

## 小结

对比以上结果，可以看出不使用 `__strong` 修饰和使用 `__strong` 结果一样，说明 `oc` 默认情况下声明变量都是 `__strong` 因为 `weak` 修饰引用计数器不会+1，所修饰的对象可能随时被释放。