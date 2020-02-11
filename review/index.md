# CodeReview指引

*翻译自：https://github.com/google/eng-practices/blob/master/review/index.md*

## 简介

CodeReview是指作者以外的其他人对一段代码进行检查的过程。

在谷歌，用CodeReview来保证代码和产品的质量。

本文档是对谷歌代码审查流程和策略的规范描述。

本页面概述了整个代码审查过程。本指南还包含其他两部分：
+ [审查者（Reviewer）的指引](reviewer/index.md)
+ [修改者（Developer）的指引](developer/index.md)

## Reviewer应该关注什么？

需要关注这些点：

+ **设计**：代码是否经过良好设计并且和系统契合？
+ **功能**：代码是否如预期工作？是否对用户有益？
+ **复杂度**：代码是否还可以变得更简单？是否可以很容易就被未来的开发者理解和使用？
+ **测试**：代码是否有正确且经过良好设计的自动化测试？
+ **命名**：Developer对于变量、类、方法等的命名是否清晰易于理解？
+ **风格**：代码是否符合 [谷歌代码风格指南](http://google.github.io/styleguide/))?
+ **文档**：Developer是否同时更新了相关的文档？

[CodeReview的关注点](./reviewer/looking-for.md)有更详细的描述。

## 选择最佳Reviewer

一般来说，您希望找到能够在合理的时间内对您的评审做出响应的最佳Reviewer。

最好的Reviewer是能够对您正在编写的代码段进行最全面、最正确的审查的人。一般是代码的所有者，通常是OWNERS文件里的人，当然也可能不在里面。有时候，可能需要由不同的人review CL的不同部分。

如果你的最佳reviwer没空，也最好抄送下他。

## 现场评审

如果你采用的是结对编程，且伴侣（嗯，是的，伴侣。。。😄）能力足够，那么，你们的爱情结晶可以被认为是经过了review的。

你还可以选择面对面评审，reveiwer和developer一问一答，developer只在被问到的时候才回答问题。




