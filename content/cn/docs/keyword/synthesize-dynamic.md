---
title: "Synthesize Dynamic"
description: ""
lead: ""
date: 2022-07-14T21:53:20+08:00
lastmod: 2022-07-14T21:53:20+08:00
draft: false
images: []
menu:
  docs:
    parent: "keyword"
    identifier: "synthesize-dynamic-5b5ba3c58da518e9e0c1c09510cd6667"
weight: 106
toc: true
---

{{< alert icon="👉" context="" text="@synthesize是给属性添加别名，并生成get、set方法（默认使用）" />}}

```objc
@interface ViewController : UIViewController

@property (assign, nonatomic) int age;

@end

@implementation ViewController

// 此时在.m文件中属性age的引用方式就是__age, 或self.age;
@synthesize age = __age;
{
		NSLog(@"age is %d", __age);
}
// set
- (void)setAge:(int)age {
	__age = age;
}
// get
- (int)getAge {
	return __age;
}

// 不添加该语句，则系统默认生成
@synthesize age = _age;

// 提示 等同于 @synthesize age = age; 也就是该默认的 _age 为 age；
@synthesize age;

@end
```

{{< alert icon="👉" context="" text="@dynamic是告诉编译器不要生成getter、setter方法。" />}}

```objc
@interface ViewController : UIViewController

@property (assign, nonatomic) int height;

@end

@implementation ViewController

@dynamic height;

{
		self.height = 20;
    NSLog(@"height is %d", self.height);
}

@end

// 运行，直接报错
2021-06-01 14:11:01.503408+0800 Unit[3654:233676] *** Terminating app due to uncaught exception 'NSInvalidArgumentException', reason: '-[ViewController setHeight:]: unrecognized selector sent to instance 0x7fd827105730'
Terminating app due to uncaught exception 'NSInvalidArgumentException', reason: '-[ViewController height]: unrecognized selector sent to instance 0x7ff842309b40'
```