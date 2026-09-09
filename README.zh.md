# 遵循 Thariq 的 Agent HTML 交互方式

[English](README.md) | **简体中文**

一个脱胎于 [Thariq Shihipar 的《HTML 的惊人有效性》](https://claude.com/blog/using-claude-code-the-unreasonable-effectiveness-of-html)
（及其[配套示例站](https://thariqs.github.io/html-effectiveness/)）的 Claude 技能。它试图接住原文里
最容易丢失的那部分：**判断力**——何时该用 HTML，何时该放手。

Thariq 在原文里就担心，有人会把这篇文章变成一个机械的「/html 技能」。这份顾虑，正是本技能的
设计任务书。一个把每条提示词都反射式地转成 HTML 的技能，会扔掉他真正在乎的东西。所以这一个，
是围绕识别与克制来构建的，而非围绕一本规则手册。

由此引出三条承诺：

- **识别，而非关键词匹配。** 全文围绕一个问题展开——*读者会扫一眼 Markdown 版，但会真正阅读
  HTML 版吗？* 技能触发于这种对*形状*的感知，并且同样清楚何时**不该**伸手去拿 HTML。
- **镜头，而非分桶。** 九个类别不是你把请求归档进去的格子，而是你透过去看的镜头，并且会叠加。
  一个产物可以同时透过几面镜头来构建——他自己的*实施计划* demo 就是「探索 + 插图 + 设计 +
  代码审查」于一个文件之中。把九种保持分开（而非揉成更少几类），本身就是一种判断：不同的形状
  值得不同的看法。
- **轻触。** 「你并不需要做太多，就能让 Claude 实现这一点。」所以技能宁可是最小的脚手架——给出
  框架和例子，然后让开，信任模型。各参考文件倚重 Thariq 那些一针见血的观察，不是把它们当作要
  供奉的遗物，而是因为它们是构建时认出形状最快的方式。

## 设计哲学

四条原则，每一条都是从原文、以及它收束于的那一份顾虑里反读出来的：

1. **触发是一种感知，而非关键词匹配。** 全文都围绕一个问题展开——*「读者会扫一眼 Markdown
   版，但会真正阅读 HTML 版吗？」* `SKILL.md` 的 `description` 描述的正是这种对*形状*的感知，
   并把九个类别作为给你所见形状命名的词汇表，而非一张你必须匹配其中一行的路由表。它对豁免同样
   直白：Markdown 是更好媒介的地方，就留在那里。

2. **类别是会叠加的镜头——由读者的动作来选。** `SKILL.md` 先问读者要对这份产物*做什么*
   ——比较、定位、追踪、试验、调整，还是跟随——让这个动作决定主导形态。然后才命名支持它的
   镜头、读取每个被点名的参考文件，并通过该参考文件的「直接入口」表打开最接近的原作示例。
   主导镜头确定骨架，其余镜头在其内贡献模式。各参考文件是为叠加而写的，且几个之间互相指向
   （模块地图借用「插图」；故障复盘借用「研究与学习」）。另有一份跨类别的 *Unknowns* 参考，
   处理「动手之前应先把尚未解决的偏好或假设浮现出来」的情形。

3. **信任模型。** 对这篇文章最深的领会，是*不*把它做成一本规则手册。所以各参考文件倚重少量
   举足轻重的要点加上 Thariq 自己的句子，而非详尽的「该做/不该做」清单。技能给出框架和例子，
   然后让开，让模型自己看出每个产物想要成为的样子。

4. **产物必须配得上被阅读。** 每个产物都守住一小组通用品质——自包含、离线可用、真实布局、
   五秒内可读、编辑器能导出回文本——因为正是这些把「你只会略读的文档」与「你会真正阅读的文档」
   区分开来。

## 结构

```
thariq-html-output-skills/
├── SKILL.md                                # 识别测试、读者动作表、九面镜头、组合、通用品质
├── SKILL.zh.md                             # 同上，简体中文
└── references/
    ├── exploration-and-planning.md         # 每份镜头参考都以一张「直接入口」表开头
    ├── code-review-and-understanding.md
    ├── design.md
    ├── prototyping.md
    ├── illustrations-and-diagrams.md
    ├── decks.md
    ├── research-and-learning.md
    ├── reports.md
    ├── custom-editing-interfaces.md
    ├── unknowns.md                         # 跨类别：浮现尚未解决的偏好与假设
    ├── source-and-examples.md              # 归属表、31 例原作索引、快照清单
    ├── zh/                                 # 以上所有参考文件的简体中文版（*.zh.md）
    └── original-examples/                  # Thariq 的 31 个示例文件，原样保留（Apache-2.0）
        ├── 01-exploration-code-approaches.html … 20-editor-prompt-tuner.html
        ├── unknowns/                       # 01-blindspot-pass.html … 11-change-quiz.html
        └── LICENSE
```

技能一旦触发，`SKILL.md` 始终在上下文中。各参考文件由请求所透过的镜头按需引入——通常一面，
有时几面。原作示例通过各参考文件的「直接入口」表每次只打开一两个——从不整座画廊一起读。

## 跑在更小的模型 / 子智能体上

各参考文件是自足的。要把生成任务路由给更便宜的模型或一个子智能体，交给它三样东西：(a) 用户的
原始请求，(b) `SKILL.md` 中「每个产物欠读者的」那三项义务，以及 (c) 每个被点名参考文件的全文。
这个包就是无需任何额外上下文即可构建产物的全部所需——见 `SKILL.md` 的「文件去哪」一节。

## 来源与许可

脱胎于 Thariq Shihipar 的[《HTML 的惊人有效性》](https://claude.com/blog/using-claude-code-the-unreasonable-effectiveness-of-html)及其[配套网站](https://thariqs.github.io/html-effectiveness/)。
九个类别及其 demo 描述、「略读 vs 真正阅读」的判断、示例画廊，出自他；把这些提炼成识别测试、组合模型、
三项义务、读者动作表和 Unknowns 跨类别参考，是本技能的扩展——一次尝试，去接住他的判断力，而不只是他的例子。

`references/original-examples/` 下的 31 个示例文件原样复制自
[ThariqS/html-effectiveness](https://github.com/ThariqS/html-effectiveness) 的提交 `1787245`，
保持其自身的 [Apache License 2.0](references/original-examples/LICENSE)，许可证文件随附。本仓库其余内容为 MIT。
