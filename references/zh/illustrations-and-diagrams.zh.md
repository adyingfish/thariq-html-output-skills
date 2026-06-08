# 插图与图表

> "Inline SVG gives the agent a real pen. Ask for the figures for a post or a
> flowchart of a process and get vector art you can tweak by hand or paste
> straight into the final document." — Thariq
>
> 「内联 SVG 给了智能体一支真正的笔。要一篇文章的配图，或一道流程的流程图，得到的是矢量图——
> 你可以手动微调，或径直粘进最终文档。」—— Thariq

不要退回到 ASCII，或「想象有一张流程图……」这样的散文。把它画出来。产出的是用户可手动编辑、
可复制出去的矢量图。

## Thariq 的两个 demo

- **SVG 配图集** ——「一篇博文的各张图，内联绘制，好让它们能被逐一微调和复制出来。」
- **注释式流程图** ——「把一条部署流水线画成真正的流程图——点击任意步骤，看它运行什么、耗时、
  以及失败路径。」

## 构建配图集

- 每节一张图，每张是一个带图注的 `<figure>`，并配一个**「复制 SVG」**按钮——要点就是把它们逐一
  粘进真实文档。
- 整套图**视觉语言一致**：相同的线宽、箭头、配色、字体。一套散乱的图读起来很业余，哪怕每张
  单看都不错。
- 为复用而设尺寸——用在明暗背景下都成立的内联 `<svg>`，不硬编码会在目标处失效的颜色。

## 构建注释式流程图

- 流程图作内联 SVG，画得规范：带标签的节点、有方向的边（箭头——没有箭头它就只是张图）、分支与
  主路径在视觉上分明。
- **点击节点展开一个侧面板**，写明那里运行什么、预期耗时、失败长什么样、源码链接。图是导航，
  面板是内容。别把所有东西都塞进图里。
- 用醒目颜色高亮**正常路径**，失败/重试路径调暗。
- 同时用**形状*与*颜色**来区分状态，好让它在色盲查看与灰度打印下都存活。把罕见分支抽象成一个
  「错误处理」子图，而非画 40 个节点。

## SVG 工艺

- 用 `viewBox`，而非固定的 `width`/`height`，好让它可缩放。
- 墨色用 `currentColor`，好让它继承文字颜色、适应深色模式。
- 用整数（`x="120"`，而非 `x="119.7843"`），好让人能手动微调。
- 用 `<g>` 分组并加标签，好让编辑者按结构找到东西。
- 文字用真实的 `<text>`，而非路径——可选中、可复制、可访问。
- 不用位图回退。能画的就画出来。

## 草图 —— 带标签的流程

```html
<figure>
  <svg viewBox="0 0 640 160" role="img" aria-labelledby="t">
    <title id="t">部署流水线</title>
    <defs><marker id="tip" viewBox="0 0 10 10" refX="8" refY="5"
      markerWidth="6" markerHeight="6" orient="auto">
      <path d="M0,0 L10,5 L0,10 z" fill="currentColor"/></marker></defs>
    <g class="node" data-step="build">
      <rect x="20" y="60" width="110" height="40" rx="6" fill="none" stroke="currentColor"/>
      <text x="75" y="85" text-anchor="middle">build</text>
    </g>
    <g class="node" data-step="test">
      <rect x="180" y="60" width="110" height="40" rx="6" fill="none" stroke="currentColor"/>
      <text x="235" y="85" text-anchor="middle">test</text>
    </g>
    <line x1="130" y1="80" x2="180" y2="80" stroke="currentColor" marker-end="url(#tip)"/>
  </svg>
  <figcaption>正常路径用实线，回滚分支用虚线。点击某一步查看耗时。</figcaption>
  <button onclick="copyFigure(this)">复制 SVG</button>
</figure>
```
