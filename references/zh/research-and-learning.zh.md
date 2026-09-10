# 研究与学习

> "An explainer with collapsible sections, tabbed code samples and a glossary in
> the margin reads very differently from the same words dumped linearly. The
> agent can build the scaffolding that makes a new topic navigable." — Thariq
>
> 「一份带可折叠分节、选项卡式代码示例、以及旁注词汇表的讲解，读起来与把同样的字线性堆出来
> 截然不同。智能体可以搭出那层脚手架，让一个新主题变得可浏览。」—— Thariq

这是用于*教学*的镜头——把一个主题变成读者可以非线性浏览的东西，而非从头读到尾。

## 直接入口 — 最近的原作示例

| 示例 | 何时使用 | 主导形态 | 关键读者动作 |
|---|---|---|---|
| [某功能如何运作](../original-examples/14-research-feature-explainer.html) · [在线](https://thariqs.github.io/html-effectiveness/14-research-feature-explainer.html) | 解释代码库中某个功能的工作原理 | TL;DR 框 → 可折叠生命周期步骤 → 选项卡式代码片段 → FAQ | 定位 — 只展开你需要的阶段或问题 |
| [概念讲解器](../original-examples/15-research-concept-explainer.html) · [在线](https://thariqs.github.io/html-effectiveness/15-research-concept-explainer.html) | 教授空间性或状态性概念（哈希、分片、调度、队列） | 活性交互演示作为核心解释，比较表，旁注词汇表 | 试验 — 改变参数，观察后果；不要跳过交互元素 |

这两个示例都是学习场景，却允许完全不同的主导形态。功能讲解器组织的是导航；概念讲解器围绕的是活性机制。让概念的性质决定哪种形状适用——空间机制适合演示；代码生命周期适合可折叠路径。选择结构前，先观察每个示例的信息分层和读者动作。

## Thariq 的两个 demo

- **某功能如何运作** ——「『解释这个仓库里的限速』——一个 TL;DR 框、可折叠的请求路径步骤、
  选项卡式配置片段，以及一个 FAQ。」
- **概念讲解** ——「用一个可增删节点的活性环来讲一致性哈希，配一张比较表，以及一个悬停链接的
  词汇表。」

## 构建功能讲解（仓库里的代码）

- 顶部一个 **TL;DR 框**：它做什么、它住在哪、关键文件。
- 生命周期每个阶段用**可折叠分节**——深的部分默认折叠，概览默认展开。代码讲解很密；让读者
  只展开他需要的。
- **选项卡式代码片段**——同一逻辑的 TypeScript、Python、测试、配置版本——以节省纵向空间。在
  有趣的行上加注释。
- 底部一个 **FAQ**；读者真正的问题就住在那里。再加上通向代码库的「接下来去哪看」链接。

## 构建概念讲解（一个新主题）

- 标题、副标题，以及**在任何技术内容之前的一段 TL;DR**——读者应在 15 秒内知道自己即将学到
  什么。别把妙处埋起来；TL;DR 就该把答案给出来。
- 核心洞见用一句话讲出，最要紧的词加重。
- 若概念是空间的或有状态的（哈希、分片、调度、排队），放一个**实时交互 demo**。五秒的交互
  胜过五段散文。别因为「读者能想象」就跳过它——他们想象不出，那正是他们来这儿的原因。（这伸进
  了「原型」/「插图」——交互与 SVG 工艺去读那两个文件。）
- 与朴素方案的比较要**用数字，而非形容词**——「移动 1/N 个键，而非 (N−1)/N 个」，而不是「更好」。
- 一个**旁注词汇表**，并从正文用悬停链接交叉引用。底部词汇表从不被读；旁注式的会被扫到。

## 草图 —— 带实时 demo 的概念讲解

```html
<main class="explainer">
  <header>
    <h1>一致性哈希，在一个环上</h1>
    <p class="tldr">把节点和键放上同一个圆；一个键归属于顺时针方向的下一个节点。增删一个节点，
       只有它那段弧会重排——约 K/N 个键移动，而非全部。</p>
  </header>
  <section>
    <h2>诀窍：一个圆，而非一条线</h2>
    <figure class="demo">
      <svg id="ring" viewBox="0 0 320 320"><!-- 圆上的节点 + 键 --></svg>
      <div class="controls">
        <label>节点 <input type="range" id="n" min="2" max="10" value="5"></label>
        <button data-act="drop">移除一个节点</button>
        <button data-act="add">加一个节点</button>
      </div>
      <output id="moved">上次变更移动了 — 个键</output>
    </figure>
  </section>
  <table class="vs"><caption>对比 hash mod N</caption>…</table>
  <aside class="glossary"><dl><dt>弧</dt><dd>一个节点所拥有的那段环。</dd></dl></aside>
</main>
```

---

## 何时引入 Unknowns 画廊

若任务存在尚未解决的偏好、假设或知识缺口——实施前选项仍未收敛、用户尚未做出某个决定、或有假设需要验证——请在生成最终产物前查阅 [`unknowns.zh.md`](unknowns.zh.md)，选择适当的探索、原型、澄清或理解检查。