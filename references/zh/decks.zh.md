# 幻灯片

> "A handful of `<section>` tags and twenty lines of JS is a slide deck. Point
> the agent at a Slack thread or a design doc and get something you can arrow-key
> through in a meeting — no Keynote, no export step." — Thariq
>
> 「几个 `<section>` 标签加二十行 JS 就是一套幻灯片。把智能体指向一段 Slack 对话或一份设计文档，
> 得到一个能在会议上用方向键翻阅的东西——无需 Keynote，无需导出步骤。」—— Thariq

适用于有人要对着房间讲解的简短演示。若内容是读者独自研读的密集参考材料，幻灯片就是错误的镜头
——改用「研究与学习」。

## 直接入口 — 最近的原作示例

| 示例 | 何时使用 | 主导形态 | 关键读者动作 |
|---|---|---|---|
| [方向键幻灯片](../original-examples/09-slide-deck.html) · [在线](https://thariqs.github.io/html-effectiveness/09-slide-deck.html) | 把一段 Slack 对话或设计文档变成一份简短演示 | 每张幻灯片一个 `<section>`，占满视口的演讲者视图，方向键导航，页码计数 | 跟随 — 按顺序翻阅；每个节拍一个想法 |

幻灯片示例让基础设施保持极简：二十行 JS，无需构建步骤，深色背景。每张一个想法是结构规则；视觉变化（图表、引言、代码块）跟随内容而来，而非来自模板。

## Thariq 的 demo

- **方向键幻灯片** ——「一份简短演示，作为一个 HTML 文件。左右键导航，无需构建步骤。」

## 构建方法

- 每张幻灯片一个 `<section>`。一个演讲者视图，只显示当前这张、占满视口——而非滚动。
- **方向键**（`←`/`→`，可选空格）前进与后退。没有键盘导航的幻灯片，只是个带幻灯片的网页。
- 角落一个小页码（`4 / 12`）。一个「按 F 全屏」的提示或按钮——浏览器边框在演示中令人分心。
- 默认 16:9，其他宽高比时加黑边，好让布局在各张之间不跳动。

## 每张幻灯片

- **每张一个想法。** 若它有两个，拆开。强制聚焦正是要点。
- **大字号**——从房间后排也能读清（正文 32–48px，标题更大）。
- **字越少越好**——一张幻灯片是讲者的视觉辅助，不是文档。幻灯片上有一段话，意味着讲者在和
  自己的幻灯片抢戏。
- 别千篇一律：一张是图表，下一张是引言，再下一张是代码块。跳过花哨的过渡——它们分散注意，且
  在快速点击时会出问题。确保浅色文字在深底上渲染干净；多数房间投影是暗的。

## 骨架 —— 全部底座

```html
<!doctype html><html lang="zh"><head><meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1"><title>幻灯片</title>
<style>
  :root{color-scheme:dark}
  body{margin:0;height:100vh;display:grid;place-items:center;
       background:#0c0d10;color:#f3f3ee;font:clamp(20px,3vw,34px)/1.4 system-ui}
  .slide{display:none;max-width:24ch;text-align:center;padding:0 6vw}
  .slide[data-on]{display:block}
  .page{position:fixed;bottom:1rem;right:1.1rem;font:13px ui-monospace;opacity:.55}
</style></head><body>
  <div class="slide" data-on><h1>形状先于格式</h1></div>
  <div class="slide"><h1>一个产物，多面镜头</h1></div>
  <div class="slide"><h1>信任那次阅读</h1></div>
  <div class="page"></div>
  <script>
    const deck=[...document.querySelectorAll('.slide')], page=document.querySelector('.page');
    let at=0;
    const show=n=>{at=(n+deck.length)%deck.length;
      deck.forEach((s,k)=>k===at?s.setAttribute('data-on',''):s.removeAttribute('data-on'));
      page.textContent=(at+1)+' / '+deck.length;};
    onkeydown=e=>({ArrowRight:()=>show(at+1),' ':()=>show(at+1),
      ArrowLeft:()=>show(at-1),f:()=>document.documentElement.requestFullscreen()}[e.key]?.());
    show(0);
  </script>
</body></html>
```

二十行 JS，无需构建步骤，直接在浏览器中打开。
