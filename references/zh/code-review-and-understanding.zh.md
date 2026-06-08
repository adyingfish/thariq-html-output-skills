# 代码审查与理解

> "Diffs and call-graphs are spatial information; markdown flattens them. Let
> the agent render the change as an annotated diff, draw the module as boxes and
> arrows, or write the PR description your reviewers actually want — so the shape
> of the code is visible at a glance." — Thariq
>
> 「差异与调用图是空间信息；Markdown 会把它们压平。让智能体把变更渲染成一份注释式差异，把模块
> 画成方框与箭头，或写出你的审查者真正想要的 PR 说明——好让代码的形状一目了然。」—— Thariq

按代码本身希望被阅读的方式来渲染它，而不是一面 `<pre>` 文字墙、每段之间夹着散文。

## Thariq 的三个 demo

- **注释式拉取请求** ——「一份带旁注、严重程度标签和跳转链接的差异——比滚动终端更易扫读。」
- **给审查者的 PR 说明** ——「作者这一侧：动机、前后对比、逐文件巡览并讲清*为什么*，以及审查
  该聚焦何处。」
- **模块地图** ——「把一个陌生的包画成方框与箭头，高亮热路径并列出入口点。」

## 构建注释式差异

- 差异是**主干**。给 `+`/`−` 行加样式，加语法高亮，再钉上**旁注**——挨着特定行的小编号注释。
  穿插式注释会打断视觉流；旁注既把代码作为代码保留，又把评注附着上去。
- 内联的严重程度标签，色彩编码：`🟥 阻塞`、`🟨 细枝末节`、`🟦 疑问`、`🟩 好评`。审查者先扫红色
  ——帮帮他们。
- 顶部设到注释区域的跳转链接；差异跨越约 3 个文件后，用可折叠的文件分节。
- 说清**审查该聚焦何处。** 审查者没时间看全部。

## 构建 PR 说明

- 祈使句标题。2–3 句动机。
- 若有视觉变化，**前后对比要做成真实的并排**——而非「之前：X，之后：Y」的散文。
- 一次逐文件巡览，按*主题*分组（「管道」/「核心逻辑」/「测试」），每处一两句讲*为什么*——
  变更的形状，而非每一行。
- 「聚焦何处」+ 风险 + 如何测试的。

## 构建模块地图

- 一句话概括这个包是做什么的，然后是一张**方框与箭头图**（内联 SVG），画出模块及其调用关系。
  （这伸进了「插图」——SVG 工艺去读那个参考文件。）
- 用一种醒目的颜色高亮**热路径**——常见的调用序列。
- 按使用场景点出入口点：「如果你想做 X，从 Y 开始。」
- 图下放每个模块的卡片；画一条「数据生命周期」轨迹，让一个真实输入流过。展示结构性关系，
  而非每一处文本引用——把每条边都画出来只会变成一团乱麻。

## 草图 —— 注释式差异

```html
<main class="diff-view">
  <header>
    <h1>给 GET /items 加键集分页</h1>
    <p>3 个文件 · +94 −12</p>
    <nav class="jump-links"><a href="#ann-1">🟥 #1 无界扫描</a></nav>
  </header>
  <section class="file">
    <h2>src/items/list.ts</h2>
    <div class="diff">
      <div class="line ctx">  const rows = await db.items</div>
      <div class="line add" data-annotation="1">+   .where('id', '>', cursor).all();</div>
      <div class="line add">+   return rows.slice(0, limit);</div>
    </div>
    <aside class="annotation" id="ann-1">
      <span class="severity blocking">🟥 阻塞</span>
      <p>这会把游标之后的每一行都拉出来，再在内存里切片。把 <code>limit</code>
         下推进查询，否则页大小毫无意义。</p>
    </aside>
  </section>
</main>
```
