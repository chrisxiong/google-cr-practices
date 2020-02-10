# google-cr-practices

谷歌有许多涵盖多种语言和多个项目的通用工程实践，并且维护了一个文档仓库：https://github.com/google/eng-practices 。
看仓库名字和其中的README描述，应该是打算把很多优秀的实践汇总到一处的，不过，当前（2020-02-10）该仓库下面只包含了关于谷歌如何做CodeReview的实践。

刚好团队内也在理CodeReview相关的工作，在看谷歌实践的过程中，就顺手把这些内容翻译一下：https://github.com/google/eng-practices/tree/master/review 。

## CodeReview的实践分为两个部分

+ 审查者（Reviewer）的指引
+ 修改者（Developer）的指引

## CodeReview相关术语

[来源仓库](https://github.com/google/eng-practices)的READEME里面是打算把所有相关，本仓库只针对CodeReview，摘一下相关的术语：
+ **CL**：即“changelist”，是指一个提交审查并纳入版本控制的自包含的代码改动。也有叫做“change”或者“patch”的，都是一个意思。
+ **LGTM**：英文“Look Good To Me.”的简写，表示Reviewer通过针对一个CL的审查。
