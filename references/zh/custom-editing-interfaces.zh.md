# 自定义编辑界面

> "Sometimes it's hard to describe what you want in a text box. Ask for a
> throwaway editor for the exact thing you're working on — and always end with
> an export button that turns whatever you did in the UI back into something you
> can paste into the agent or commit. You stay in the loop; the loop gets
> tighter." — Thariq
>
> 「有时你很难在文本框里描述出你想要什么。为你正在做的那件具体的事，要一个一次性编辑器——并且
> 永远以一个导出按钮收尾，把你在界面里做的一切重新变成你能粘进智能体、或提交进去的东西。你始终
> 在闭环之中；而这个闭环会收得更紧。」—— Thariq

这是这种格式最具特色的用法。文本框是某些任务的错误形状——给 30 个工单分优先级、调一个正则、
重排一道流程。为那一个任务，构建一个专门打造的单文件编辑器。

## 直接入口 — 最近的原作示例

| 示例 | 何时使用 | 主导形态 | 关键读者动作 |
|---|---|---|---|
| [工单分流看板](../original-examples/18-editor-triage-board.html) · [在线](https://thariqs.github.io/html-effectiveness/18-editor-triage-board.html) | 把一批工单分配到优先级桶里 | 四列（当前/下一步/稍后/砍掉），拖拽，每桶计数，"复制为 Markdown"导出 | 调整 — 拖到感觉对，复制排序结果 |
| [功能开关编辑器](../original-examples/19-editor-feature-flags.html) · [在线](https://thariqs.github.io/html-effectiveness/19-editor-feature-flags.html) | 编辑一组有依赖关系的功能开关 | 分组开关 + 依赖警告 + 只导出改动键的"复制差异"按钮 | 调整 — 切换，看警告，只导出变化的部分 |
| [提示词调参器](../original-examples/20-editor-prompt-tuner.html) · [在线](https://thariqs.github.io/html-effectiveness/20-editor-prompt-tuner.html) | 针对多个样本输入迭代提示词模板 | 左侧可编辑模板，右侧三个实时预览随打字更新 | 试验 + 调整 — 编辑模板，观察三个样本同步更新 |

不可妥协的导出，正是编辑器与玩具的分水岭。先把导出加上，再加任何其他功能。

## 不可妥协的规则

**每个编辑器都以一次导出收尾。** 「复制为 Markdown / JSON / 提示词」「下载为 CSV」——无论哪种，
都把界面状态变成可粘回智能体、提交、或下一条提示词的东西。这就是 Thariq 说的「你始终在闭环之中」。
没有导出，编辑器只是个玩具；有了它，闭环才合上。若你发现自己在造一个没有导出路径的编辑器，
**先把导出加上**。

## Thariq 的三个 demo

- **工单分流看板** ——「把三十个工单在『当前 / 下一步 / 稍后 / 砍掉』之间拖动，然后把最终排序
  复制成 Markdown。」
- **功能开关编辑器** ——「按区域分组的开关，当前置条件关闭时给出依赖警告，以及一个只导出改动键
  的『复制差异』按钮。」
- **提示词调参器** ——「左边是可编辑的模板、变量槽高亮；右边三个样本输入随你打字实时重渲染。」

## 构建方法

- **工作区是绝对的焦点**；头部、控件和导出环绕在它周围。一句话头部说明这个编辑器是干什么的。
- **把数据预填进去。** 用户已在提示词里把数据给你了——别让他再打一遍。为*这*三十个真实工单
  构建分流看板，而非一个通用的「任务管理器」。
- 与数据相匹配的交互元件：排序用拖放，布尔用开关，枚举用下拉，范围用滑块。
- 一个实时的**当前状态读数**——每桶计数、字符数、即时可见的校验错误。在冲突*发生的那一刻*显示
  约束冲突，而非作为页脚的免责声明。
- 对重复动作提供**键盘支持**——当用户要给 100 个东西打标签时，给 `j`/`k` 或 `1`/`2`/`3`，
  而非只能点击。
- 会话内的状态持久化（没有文件系统的 agent：仅内存；写本地文件的 agent：`localStorage` 没问题且值得用）。
- 无设置、无后端、无认证。它是工具，不是产品。评判标准是用户能否完成并离开——把它做得快而直接。

## 草图 —— 分流看板

```html
<main>
  <header><h1>分流看板</h1>
    <p>三十个工单，已预排成初步猜测。拖到这刀切得顺手为止，然后把整块板复制为 Markdown。</p></header>
  <div class="board">
    <section data-bucket="now"><h2>当前</h2><ul></ul></section>
    <section data-bucket="next"><h2>下一步</h2><ul></ul></section>
    <section data-bucket="later"><h2>稍后</h2><ul></ul></section>
    <section data-bucket="cut"><h2>砍掉</h2><ul></ul></section>
  </div>
  <footer>
    <span id="tally"></span>
    <button id="reset">重置</button>
    <button id="export">复制为 Markdown</button>
  </footer>
  <script>
    const tickets = [/* 这三十个，从提示词预填 */];
    /* 渲染进各桶 · HTML5 拖放 · 状态存在 Map<id,bucket> */
    /* export → 每桶一个 ## 标题，每个工单一行 */
  </script>
</main>
```

---

## 何时引入 Unknowns 画廊

若任务存在尚未解决的偏好、假设或知识缺口——实施前选项仍未收敛、用户尚未做出某个决定、或有假设需要验证——请在生成最终产物前查阅 [`unknowns.zh.md`](unknowns.zh.md)，选择适当的探索、原型、澄清或理解检查。