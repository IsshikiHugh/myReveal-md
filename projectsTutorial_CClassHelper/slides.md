---
title: C Class Helper Tutorial
separator: <!--s-->
verticalSeparator: <!--v-->
theme: night
highlightTheme: tomorrow-night-bright
revealOptions:
  width: 1520
  height: 950
  margin: 0.04
  transition: 'convex'
  slideNumber: true
---

# 𝓒 𝓒𝓵𝓪𝓼𝓼 𝓗𝓮𝓵𝓹𝓮𝓻

<font size="6"> < 面向 C 语言学习新手的日志打印工具 > </font>

<font size="16"> CCH 1.0 使用简明教程 </font>

<div align="right"><font size="6"> 

👉 GitHub [address](https://github.com/IsshikiHugh/C-Class-Helper)

</font></div>

<div align="right"><font size="6">

👉 Powered by [reveal.js](https://github.com/hakimel/reveal.js)

</font></div>

Note: Test note.


<!--s-->

## 目录

> 该 slides 仅包括 CCH 的部分基础功能

1. 导入
2. 设置
   1. 输出流
3. 打印日志
   1. 通用日志
   2. 变量监控
   3. 数组监控
4. 开关
   1. 显示开关
   2. 简洁模式开关

<!--s-->

# 导入 | import

> 您可以使用以下两种方法来将该工具应用与您的代码：

- 直接将 [ <font color="yellow">`CClassHelper.h`</font> ] 中的**所有**内容直接**复制**到您代码的**开头**
- 作为模块接口，使用 [ <font color="cyan">`#include "CClassHelper.h"`</font> ] 导入

<!--v-->

#### 直接将 [ <font color="yellow">`CClassHelper.h`</font> ] 中的**所有**内容直接**复制**到您代码的**开头**

```c[6-13|1-4|1-13]
#ifndef __C_CLASS_HELPER__
#define __C_CLASS_HELPER__
// 这些都是'CClassHelper.h'中的内容
#endif

#include <stdio.h>

int main(){
  printf("Hello World\n");
  return 0;
}
```

<!--v-->

#### 作为模块接口，使用 [ <font color="cyan">`#include "CClassHelper.h"`</font> ] 导入

```md[1-4|2-2]
# Make sure the files have the following structure.

┣   CClassHelper.h
┗   YourCode.c
```
  
```c[2-7|1-1|1-7]
#include "CClassHelper.h"
#include <stdio.h>

int main(){
  printf("Hello World\n");
  return 0;
}
```

<!--s-->

# 设置 | config

> 在这一个部分中，你需要<font color="orange">**检查**</font>/<font color="orange">**修改**</font>源代码中的部分参数

<!--v-->

## 输出流

```c[1-19|13-16]
#ifndef __C_CLASS_HELPER__
#define __C_CLASS_HELPER__

/****************************************************
 * C Class Helper 1.0                               *
 * ------------------------------------------------ *
 * Github Repository Address:                       *
 * - https://github.com/IsshikiHugh/C-Class-Helper  *
 ****************************************************/

/*** Config Part ************************************/

// MODE 0 : Logs will be write to 'CCH_log.txt' file.
// MODE 1 : Logs will be print to console (colorful for normal terminal).
// MODE 2 : Logs will be print to console (colorless but fine for CMD).
#define CCH_MODE 2

...

```

<font size="6">

- 如果你对命令行<font color="orange">毫无了解</font>，那么请检查 <font color="cyan">CCH_MODE</font> 被设置为 <font color="cyan">2</font> ；
- 如果你的日志将会被打印在常规的 <font color="orange">Terminal</font> 上，那么我们推荐你设置 <font color="cyan">CCH_MODE</font> 为 <font color="cyan">1</font> ；
- 如果你希望你的日志内容不被打印，而是输出到<font color="orange">文件</font>中，则可以设置 <font color="cyan">CCH_MODE</font> 为 <font color="cyan">0</font> ，但是请注意，CCH 无法清空输出文件，请在每次输出的时候手动清理 <font color="yellow">CCH_log.txt</font> ；

</font>

<!--s-->

# 打印日志 | print logs

> 在这一部分中，我们会着重介绍如何使用该工具的函数

请注意，虽然这些函数<font color="orange">本质上是宏函数</font>，但是它们的使用方法和普通函数类似

<!--v-->

## 通用日志 | LOG

- 使用 <font color="cyan">LOG(<font color="grey">*format...*</font>)</font> 来输出通用日志
- 该函数的使用方法和 <font color="cyan">`printf()`</font> 一模一样，但它会输出更详细与更具有辨识性的信息

```c[4,7|5,8|]
void foo(){
  double x = 1.14514;

  printf("This a normal 'printf' message.");
  LOG("This a normal log.");
  
  printf("x = %.2lf", x);
  LOG("x = %.2lf", x);
}

```
<!--v-->

![](https://raw.githubusercontent.com/IsshikiHugh/C-Class-Helper/main/img/img5.png)

<!--v-->

## 变量监控 | SHOW_VAR

- 使用 <font color="cyan">SHOW_VAR(<font color="grey">*CCH_TYPE*<font color="cyan">, </font>*CCH_VAR*</font>)</font> 来监控变量：

```c[5-7|8-9]
void foo(){
  int intX = 0;
  double doubleX = 1.14514;
  char charX = 'm';
  SHOW_VAR("%d", intX);
  SHOW_VAR("%.2lf", doubleX);
  SHOW_VAR("%c", charX);
  // It's ok to print pointer here!
  SHOW_VAR("%p", &intX);
}
```

<!--v-->

![](https://raw.githubusercontent.com/IsshikiHugh/C-Class-Helper/main/img/img6.png)

<!--v-->

## 数组监控 | SHOW_ARR

- 使用 <font color="cyan">SHOW_ARR(</font><font color="grey">*CCH_TYPE*</font><font color="cyan">, </font><font color="grey">*CCH_ARR_NAME*</font><font color="cyan">, </font><font color="grey">*CCH_ARR_BEGIN*</font><font color="cyan">, </font><font color="grey">*CCH_ARR_END*</font><font color="cyan">) </font>来监控数组：

```c[3-4|5-6]
void foo(){
  double doubleArrayY[5] = {1.2, 2.3, 3.4, 4.5, 5.6};
  // Print the whole array.
  SHOW_ARR("%.2lf", doubleArrayY, 0, 5);
  // You can also print part of it.
  SHOW_ARR("%.2lf", doubleArrayY, 2, 4);
}
```

<!--v-->

![](https://raw.githubusercontent.com/IsshikiHugh/C-Class-Helper/main/img/img7.png)

<!--s-->

# 开关 | Switch

> 这一部分中，我们将介绍一些具有文件全局效果的函数

- 受实现原理限制，在多模块编程时，这些开关只会在单一模块中生效！

<!--v-->

## 显示开关

- 使用 <font color="cyan">SET_CCH_SHOW(<font color="pink">*0*</font>);</font> 来关闭日志输出；
- 使用 <font color="cyan">SET_CCH_SHOW(<font color="pink">*1*</font>);</font> 来打开日志输出；
- 默认情况下，输出都是打开的；

```c[2|4-5|7-8]
void foo(){
  LOG("(QWQ) I can be seen!");

  SET_CCH_SHOW(0);
  LOG("(QAQ) I can't be seen!");

  SET_CCH_SHOW(1);
  LOG("(QWQ) I can be seen!");
}
```

<!--v-->

![](https://raw.githubusercontent.com/IsshikiHugh/C-Class-Helper/main/img/img3.png)

<!--v-->

## 简洁模式开关

- 使用 <font color="cyan">SET_CCH_BRIEF_MODE(<font color="pink">*1*</font>);</font> 来打开简洁模式；
- 使用 <font color="cyan">SET_CCH_BRIEF_MODE(<font color="pink">*0*</font>);</font> 来打开简洁模式；
- 默认情况下，简洁模式是关闭的；

```c[2|4-5|7-8]
void foo(){
  LOG("Normal mode here!");

  SET_CCH_BRIEF_MODE(1);
  LOG("Brief mode here!");

  SET_CCH_BRIEF_MODE(0);
  LOG("Normal mode here!");
}
```

<!--v-->

![](https://raw.githubusercontent.com/IsshikiHugh/C-Class-Helper/main/img/img4.png)
