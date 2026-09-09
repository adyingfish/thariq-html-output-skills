# 探索与规划

> "When you're not sure what you want yet. Ask the agent to fan out across
> several directions and lay them next to each other so you can point at one —
> instead of reading three sequential walls of text and trying to hold them all
> in your head. And once you've picked, turn the pick into a plan the
> implementer can actually read." — Thariq
>
> 「当你还不确定自己想要什么的时候。让智能体向几个方向铺开，把它们并排摆放，这样你可以指着
> 其中一个——而不是顺次读三面文字墙，还得把它们全都装进脑子里。一旦你选定了，就把选择变成一份
> 实现者真能读下去的计划。」—— Thariq

这面镜头里住着两个时刻：*决定之前*（铺开、比较）与*决定之后*（一份你交接出去的计划）。两者
都关乎让某个形状变得可见——选择的形状，或变更的形状。

## 直接入口 — 最近的原作示例

| 示例 | 何时使用 | 主导形态 | 关键读者动作 |
|---|---|---|---|
| [三种代码方案](../original-examples/01-exploration-code-approaches.html) · [在线](https://thariqs.github.io/html-effectiveness/01-exploration-code-approaches.html) | 并排比较 2–4 个具体解法 | 三列，内部结构完全一致，硬性指标强制推荐 | 比较 — 目光横向扫过各列 |
| [实施计划](../original-examples/16-implementation-plan.html) · [在线](https://thariqs.github.io/html-effectiveness/16-implementation-plan.html) | 交接一个需要时间轴、图表和风险表的决定 | 里程碑条 + 数据流 SVG + 风险表 + 注释式片段 | 跟随 — 读者按阶段依次推进 |
| [视觉设计方向](../original-examples/02-exploration-visual-designs.html) · [在线](https://thariqs.github.io/html-effectiveness/02-exploration-visual-designs.html) | 渲染 3–4 个设计选项以便直接指出偏好 | 并排实时渲染的选项，而非描述性文字 | 比较 + 试验 — 对渲染出的东西作出反应，而非想象它 |

观察最接近示例的空间关系和信息层级；按本次材料重新设计，而非复制其外壳。

## Thariq 的三个 demo

- **三种代码方案** ——「并排比较解决同一问题的三种方式，把权衡就地标注出来。」
- **视觉设计方向** ——「把若干布局与配色选项实时渲染出来，让你对它们作出反应，而非凭空想象。」
- **实施计划** ——「时间轴上的里程碑、一张数据流图、内联原型、关键代码，以及一张风险表——你
  交接出去的计划。」

## 构建并排比较

这是 HTML 在此处最大的胜场。三种方案在 Markdown 里是三个顺次排列的章节，读者得一次性装进
脑子里；在 HTML 里则是三列，读者横向扫视即可比较。

- 每个选项一列（选项超过约 4 个时，用响应式卡片网格）。
- 每列**内部结构完全一致**——相同的标题、相同的子章节——好让目光横向比较。某个指标在一列里
  有、另一列里没有，会被读成弱点，哪怕你只是忘了填。
- 每列内含：一句框架语句、真实的内容（代码 / 原型 / 草图）、一张优缺点**表格**（表格读起来
  是比较，项目符号读起来是序列），以及一行硬指标，逼着推荐结论站得住脚。
- 结尾**真的选出一个**并说明理由。「给我看三种方式」意味着读者想要你帮他选。

## 构建实施计划

注意这是典型的复合体——它伸进了「插图」（数据流图）、「设计」（内联原型）和「代码审查」
（注释式的关键片段）。若计划需要，也去读那几个参考文件。

- 一段问题陈述，然后是一条**里程碑带**，呈现为真实的可视化时间轴——而非编号列表。
- 若系统有两个以上部件，画一张**数据流图**（内联 SVG）。读者无法仅凭散文在脑中保持拓扑结构；
  别为难他们。
- 那 2–3 段举足轻重的代码片段，在棘手的行上加注释。
- 一张**风险表**（风险 / 可能性 / 缓解措施）——表格里的风险会被处理；段落里的风险会消失。
- 一小节**「我们明确不做的事」**。它能在范围蔓延开始之前将其扼杀。

## 草图 —— 三种方案

```html
<main>
  <header>
    <h1>给 /items 分页的三种方式</h1>
    <p>产生本文的提示词 · 我会上线的那个</p>
  </header>
  <section class="grid grid-cols-3">
    <article>
      <h2>01 · Offset / limit</h2>
      <p>按行数翻页。</p>
      <pre><code>…查询…</code></pre>
      <table class="pros-cons"><tr><th>优点</th><th>缺点</th></tr>
        <tr><td>写起来极简</td><td>行变动时会漂移</td></tr></table>
      <dl class="metrics"><dt>深翻页代价</dt><dd>O(n)</dd><dt>稳定？</dt><dd>否</dd></dl>
    </article>
    <article>…02 · 游标…</article>
    <article>…03 · 键集…</article>
  </section>
  <footer><h2>推荐</h2><p>选 03（键集）——原因如下……</p></footer>
</main>
```
