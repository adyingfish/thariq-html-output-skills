# 原型

> "Motion and interaction can't be described, only felt. A throwaway page with
> the real easing curve or the real click-through tells you in five seconds what
> a paragraph of prose never could." — Thariq
>
> 「动效与交互无法被描述，只能被感受。一个一次性页面，带着真实的缓动曲线或真实的点击流程，
> 五秒之内告诉你的东西，是一整段散文永远做不到的。」—— Thariq

这是散文败得最惨的一面镜头。你写不出一条缓动曲线；你得让它动起来。把真东西做出来，聚焦于
所讨论的那一个交互。

## 直接入口 — 最近的原作示例

| 示例 | 何时使用 | 主导形态 | 关键读者动作 |
|---|---|---|---|
| [动效沙盒](../original-examples/07-prototype-animation.html) · [在线](https://thariqs.github.io/html-effectiveness/07-prototype-animation.html) | 在接入真实代码前把过渡调好 | 被动画对象居中放大；时长、缓动、延迟的滑块；实时 CSS 输出与复制按钮 | 试验 — 拖动滑块，观察结果；调好后复制 |
| [可点击流程](../original-examples/08-prototype-interaction.html) · [在线](https://thariqs.github.io/html-effectiveness/08-prototype-interaction.html) | 在构建前检查多屏交互是否感觉对 | 四五个相连的屏幕，足够感受流程的保真度，可前进/后退的点击目标 | 跟随 + 试验 — 点击走过交互，判断是否符合预期 |

动效沙盒适合活性演示；可点击流程适合相连的屏幕。用最简单的形式让读者*感受*交互，而非描述它。

## Thariq 的两个 demo

- **动效沙盒** ——「把过渡单独拿出来，配上时长和缓动的滑块，让你在接线之前先调好它。」
- **可点击流程** ——「四个屏幕串联起来——足够的保真度，让你感受这个交互对不对。」

## 构建动效沙盒

- 被动画化的对象，单独拿出来，放大居中。
- 每个要紧的参数都配一个滑块/开关——时长、延迟、缓动、距离、颜色变化——随用户拖动实时更新。
- 一个**重新触发 / 重放按钮**，免得用户等一个自然触发时机。一次性的动画对调试毫无用处。
- 底部一个**实时代码块**，把当前参数显示为 CSS / JS / framer-motion 配置，随滑块更新，再加一个
  复制按钮。这正是这个页面存在的全部理由——调好数值，粘进真实代码库。没有复制这一步，它就只是
  个演示。
- 一张缓动曲线图胜过一个名称下拉框；人是靠视觉来调曲线的。
- 聚焦于用户问到的那一个过渡——而非一个通用的「动效游乐场」。

## 构建可点击流程

- 3–6 个屏幕，按自然顺序串联。真实的按钮：「下一步」真的前进，「返回」真的后退。
- 一条**屏幕托盘**缩略图带，高亮当前屏幕，好让用户跳到任意一处，直接拿第 1 屏对比第 4 屏。
- 恰好足够测试流程*形状*的保真度——渲染流程会用到的字段，而非每一个字段。像素级完美是另一种产物。

## 草图 —— 动效沙盒

```html
<main>
  <section class="stage"><div id="toast" class="toast">已保存</div></section>
  <aside class="controls">
    <label>滑入距离 <input type="range" id="dist" min="0" max="80" value="24"><output>24px</output></label>
    <label>时长 <input type="range" id="dur" min="80" max="1200" value="320"><output>320ms</output></label>
    <label>缓动 <select id="ease"><option>cubic-bezier(.2,.9,.3,1)</option><option>ease-out</option></select></label>
    <button id="play">▶ 重放</button>
  </aside>
  <pre id="out">/* transform + transition，随拖动实时更新 */</pre>
  <button id="copy">复制 CSS</button>
</main>
```
