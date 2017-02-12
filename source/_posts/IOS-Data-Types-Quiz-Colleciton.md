---
title: 'IOS: Data Types Quiz Colleciton'
date: 2016-05-04 20:49:01
tags: IOS
---
# 1. When to use NSInteger vs. int? #
** 结论： 尽量多用NSInteger **

***
You usually want to use NSInteger when you don't know what kind of processor architecture your code might run on, so you may for some reason want the largest possible  int type, which on 32 bit systems is just an int, while on a 64-bit system it's a long.

I'd stick with using NSInteger instead of int/long unless you specifically require them.

NSInteger/NSUInteger are defined as *dynamic typedef*s to one of these types, and they are defined like this:

```c++
#if __LP64__ || TARGET_OS_EMBEDDED || TARGET_OS_IPHONE || TARGET_OS_WIN32 || NS_BUILD_32_LIKE_64
typedef long NSInteger;
typedef unsigned long NSUInteger;
#else
typedef int NSInteger;
typedef unsigned int NSUInteger;
#endif
```

With regard to the correct format specifier you should use for each of these types, see the [String Programming Guide's section on Platform Dependencies](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/Strings/Articles/formatSpecifiers.html#//apple_ref/doc/uid/TP40004265-SW5)