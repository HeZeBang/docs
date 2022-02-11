---
title: Synthesizer V Studio 脚本手册 | Synthesizer V Studio Scripting Manual
date: 2022-01-30 17:26:38
categories:
- SV - Scripting
tags:
- SynthV
- Scripting
---

[English](https://resource.dreamtonics.com/scripting/index.html) | [日本語](https://resource.dreamtonics.com/scripting/ja/index.html)

<!-- more -->

# Synthesizer V Studio 脚本手册

Synthesizer V Studio Pro 支持脚本。用户可以使用自己的脚本向编辑器添加新功能。

脚本的想法类似于插件系统，但不是加载动态链接的对象（例如 `.dll`），Synthesizer V Studio以源代码形式加载脚本。因此，需要一个文本编辑器进行脚本开发。编写完成后，这些脚本可以在Synsitorer V Studio支持的所有平台（Windows，Linux和macOS）上移植。

## 支持的语言

-   JavaScript (ECMAScript 5.1, powered by [Duktape](http://duktape.org/))
-   Lua 5.4 ([the official implementation](https://www.lua.org/))

## 功能

脚本可以做什么？

-	读取、添加、编辑和删除音符/音符组/参数/轨道...
-	访问和修改当前所选内容（包括音符和音符组）
-	在项目中导航（例如，滚动并缩放到某个范围）
-	控制播放
-	通过可自定义的对话框与用户交互
-	异步回调功能（例如，调用 [`SV#setTimeout`](../SV#setTimeout) 以延迟函数的执行） 
-	这意味着脚本可以在后台运行尽可能长时间。

## 如何开始

-	请看 [一个最小示例](../tutorial-A%20Minimal%20Example)。
-	下面是 [一个更高级的示例](https://github.com/Dreamtonics/svstudio-scripts/tree/master/HelloWorld)。
-	从 [测试脚本](https://github.com/Dreamtonics/svstudio-scripts/tree/master/Tests) 中学习。
-	如果您不理解，请查看 类（Classes）参考手册。
-	在脚本中使用 [本土化](../tutorial-Localization) 并走向国际。
-	高级用户：了解 [内存管理](../tutorial-Memory%20Management)。

## 编程概念

Synthesizer V Studio的脚本API是面向对象的。JavaScript 和 Lua 脚本共享相同的 API，尽管调用约定略有不同（请参阅下一节）。
用户可以与之交互两种类型的对象：数据对象和 UI 状态对象。

-	数据对象是项目的一部分，可以是跟踪，注释，参数......，如果您使用过类似的可编写脚本的软件，您可能已经熟悉这些内容。
-	UI 状态对象更有趣。它们是抽象的用户界面。例如， [`PlaybackControl`](../PlaybackControl) 对象管理播放、暂停、循环和查找行为。

### 与VOCALOID Job Plugins的区别

雅马哈的VOCALOID也支持Lua脚本 ("Job Plugin"). VOCALOID 的脚本与 Synthesizer V Studio 不兼容。主要区别在于

-	在 Job Plugin 中，所有API都公开为全局函数;在 Synthesizer V Studio API 中，唯一的全局对象是宿主对象 [`SV`](../SV) ，与数据结构的大多数交互都是通过数据类型的方法进行的。
-	Job Plugin API 使用基于事件的数据模型。例如，必须按顺序访问音符。Synthesizer V Studio API 提供对音符、参数、音符组和轨道的随机访问。

## JavaScript 和 Lua 之间的重要区别

### 索引

JavaScript 使用从0开始的索引，而 Lua 使用从1开始的索引。这也适用于脚本 API。

例如，JavaScript 中的 `NoteGroup.getNote(0)` 与 Lua 中的 `NoteGroup：getNote(1)` 相同。

### 调用方法

面向对象的编程在 JavaScript API 中是原型继承式的，这意味着调用约定是 `Class.Method(...)`。

Lua API 基于元表，调用约定为 `Class:Method(...)`。

但是，即使在Lua中，成员对象仍然可以使用点进行访问（例如 [`SV#QUARTER`](../SV#QUARTER)）。