# 编写良好的CL描述

*翻译自：https://github.com/google/eng-practices/blob/master/review/developer/cl-descriptions.md*

CL描述是对所做的更改以及更改原因的公开记录， 它是版本控制历史的永久组成部分，随着时间的推移，可能会被数百人阅读，不单单是reviewer。

未来的developer将根据您的CL的描述来检索。未来的某个人可能会寻找你的改变，因为他们对它的相关性有模糊的记忆，但却没有现成的细节。如果所有重要的信息都在代码中而不是描述中，那么他们要找到你的CL就会困难得多。

## 第一行

要点：

+ 对于改动的简介
+ 完整的句子，祈使句的形式
+ 跟一个空行

CL描述的简介是空行隔开的一行简短文字，用来描述CL具体做了什么改动。后续其他人在检索代码版本历史的时候，绝大部分都会看这部分内容，所以第一行需要提供足够多的信息，而不需要他们来阅读代码或者CL的完整描述来了解CL具体干了什么。

通常，第一行是一个完整的祈使句。例如，写成这样：“Delete the FizzBuzz RPC and replace it with the new system.”，而不是这样：“Deleting the FizzBuzz RPC and replacing it with the new system.”。不过，你不用把CL描述的其他部分都写成祈使句。

## 丰富的消息体

CL描述的消息体部分需要提供足够的信息量，描述解决了什么问题，为什么这是解决该问题的最好方式，如果该方式有什么不足之处，也应该提到。如果有的话，最好包括相关的背景信息，例如bug号，基准测试结果以及设计文档的链接等。

即使很小的CL也应该有一些细节需要注意，记得带上CL的上下文。

## 差的描述

“Fix bug”不是一个合适的描述，解决什么bug？通过什么方式修复的？其他不好的描述，包括但不限于一下：
+ “Fix build”
+ “Add patch”
+ “Moving code from A to B”
+ “Phase 1.”
+ “Add convenience functions.”
+ “Kill weird URLs”

其中一些是真实存在的CL描述。 他们的作者可能认为他们正在提供有用的信息，但它们并没有达到CL描述的目的。

## 好的描述

下面是一些好描述的例子。

### 功能变更

例如：
> rpc: remove size limit on RPC server message freelist.
>
> Servers like FizzBuzz have very large messages and would benefit from reuse.
> Make the freelist larger, and add a goroutine that frees the freelist entries
> slowly over time, so that idle servers eventually release all freelist
> entries.

第一行用少量词语说明CL具体做了什么。余下的内容提到解决了什么问题，为什么这是一个好的解法，还有一些具体实现的信息。

### 重构

例如：
> Construct a Task with a TimeKeeper to use its TimeStr and Now methods.
>
> Add a Now method to Task, so the borglet() getter method can be removed (which
> was only used by OOMCandidate to call borglet's Now method). This replaces the
> methods on Borglet that delegate to a TimeKeeper.
>
> Allowing Tasks to supply Now is a step toward eliminating the dependency on
> Borglet. Eventually, collaborators that depend on getting Now from the Task
> should be changed to use a TimeKeeper directly, but this has been an
> accommodation to refactoring in small steps.
>
> Continuing the long-range goal of refactoring the Borglet Hierarchy.

第一行描述了CL的功能以及这与过去的变化。 其余的描述讨论了具体的实现，CL的上下文，提到了该解决方案并不完美以及未来可能的改进方向。 还解释了为什么要做这个变更。

### 带上下文的小CL

例如：
> Create a Python3 build rule for status.py.
>
> This allows consumers who are already using this as in Python3 to depend on a
> rule that is next to the original status build rule instead of somewhere in
> their own tree. It encourages new consumers to use Python3 if they can,
> instead of Python2, and significantly simplifies some automated build file
> refactoring tools being worked on currently.

第一句话描述了实际正在做的事情。描述的其余部分解释了为什么要进行更改，并为审阅者提供了大量的上下文。

## 提交CL之前review一下描述

CL在review过程中可能会发生大的改变。在实际提交CL之前，记得review一下CL的描述，以确保其在经历了review并做了一些改动之后依然反应CL具体做的改动。

下一篇：[尽量提交小的CL](small-cls.md)
