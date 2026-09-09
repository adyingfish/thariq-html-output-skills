# 认知盲区（Know Your Unknowns）

> "The map is not the territory — the gap between them is your unknowns. Eleven
> self-contained `.html` artifacts for discovering them before, during, and
> after implementation." — Thariq, *Know your unknowns* gallery index
>
> 「地图不是疆域——两者之间的落差，就是你的未知。十一个自包含的 `.html` 产物，用来在实施前、
> 实施中、实施后把它们找出来。」—— Thariq，「Know your unknowns」画廊索引

这是一份跨类别参考。它不取代九个镜头——它为每个镜头增加一个补充问题：*读者还有什么不知道自己需要知道的事，而这份产物能帮他们发现吗？*

当存在尚未解决的偏好、假设或知识缺口，且这些缺口会影响最终结果时，进入本参考。任务清晰、读者已有所需信息时，跳过本参考。

## 何时进入本参考

以下任一条件成立时进入：

- 读者还没有看到设计空间，无法表达偏好，直到看到之后才能说（实施前：**探索**）
- 某个决定或交互只有通过体验才能判断，无法通过描述判断（实施前：**原型 / 试验**）
- 重要的约束或需求仍然模糊或隐含（实施前：**澄清**）
- 实现过程中偏离了计划，但偏差尚未被记录（实施中：**追踪偏差**）
- 读者需要在交接或合并前验证自己对已构建内容的理解（实施后：**理解检查**）

不要在每次实现前都默认先跑一个盲区访谈。不要收集已经给出的答案。使用已有信息；避免不必要的关卡。

## 三个阶段与 11 个示例

Thariq 将这组画廊按三个阶段组织。以下 11 个示例都是他的，保留他的原题；原样副本在 `../original-examples/unknowns/`（Apache-2.0，见 `source-and-examples.zh.md`）。「协作任务」与「自然组合的镜头」两列是技能层的概括，不是他的原话；他对每个示例的一句话描述在画廊索引页和文件本身里。

### 实施前 · 8 个示例

| # | 示例（Thariq 原题） | 协作任务 | 自然组合的镜头 |
|---|---|---|---|
| 01 | [盲区扫描 · Blindspot pass](../original-examples/unknowns/01-blindspot-pass.html) · [在线](https://thariqs.github.io/html-effectiveness/unknowns/01-blindspot-pass.html) | 发现计划遗漏的约束 | 代码审查、探索与规划 |
| 02 | [补齐领域知识 · Teach me my unknowns](../original-examples/unknowns/02-color-grading-explainer.html) · [在线](https://thariqs.github.io/html-effectiveness/unknowns/02-color-grading-explainer.html) | 学会用领域词汇精确描述需求 | 研究与学习、原型 |
| 03 | [四种设计方向 · Four design directions](../original-examples/unknowns/03-design-directions.html) · [在线](https://thariqs.github.io/html-effectiveness/unknowns/03-design-directions.html) | 从渲染出的选项中辨认偏好 | 探索与规划、设计、编辑 |
| 04 | [先做样机再接线 · Mock before you wire](../original-examples/unknowns/04-toolbar-mock.html) · [在线](https://thariqs.github.io/html-effectiveness/unknowns/04-toolbar-mock.html) | 在真正实现前先体验交互 | 原型、设计 |
| 05 | [干预方案脑暴 · Brainstorm the intervention](../original-examples/unknowns/05-churn-brainstorm.html) · [在线](https://thariqs.github.io/html-effectiveness/unknowns/05-churn-brainstorm.html) | 选择并收窄干预方向 | 探索与规划、编辑 |
| 06 | [需求访谈 · The interview](../original-examples/unknowns/06-interview.html) · [在线](https://thariqs.github.io/html-effectiveness/unknowns/06-interview.html) | 澄清模糊或有争议的决定 | 探索与规划、编辑 |
| 07 | [对照参考实现 · Point at a reference](../original-examples/unknowns/07-reference-port.html) · [在线](https://thariqs.github.io/html-effectiveness/unknowns/07-reference-port.html) | 核对与参考实现的语义对齐 | 代码审查、研究与学习 |
| 08 | [可调整的计划 · The tweakable plan](../original-examples/unknowns/08-implementation-plan.html) · [在线](https://thariqs.github.io/html-effectiveness/unknowns/08-implementation-plan.html) | 让仍可能变化的选择浮现并优先审阅 | 探索与规划、编辑 |

### 实施中 · 1 个示例

| # | 示例（Thariq 原题） | 协作任务 | 自然组合的镜头 |
|---|---|---|---|
| 09 | [实施笔记 · Implementation notes](../original-examples/unknowns/09-implementation-notes.html) · [在线](https://thariqs.github.io/html-effectiveness/unknowns/09-implementation-notes.html) | 记录计划与现实的偏离之处 | 报告、代码审查 |

### 实施后 · 2 个示例

| # | 示例（Thariq 原题） | 协作任务 | 自然组合的镜头 |
|---|---|---|---|
| 10 | [争取认同的文档 · The buy-in doc](../original-examples/unknowns/10-pitch-doc.html) · [在线](https://thariqs.github.io/html-effectiveness/unknowns/10-pitch-doc.html) | 帮助评审者理解并判断工作 | 报告、幻灯片、原型 |
| 11 | [合并前测验 · Quiz me before I merge](../original-examples/unknowns/11-change-quiz.html) · [在线](https://thariqs.github.io/html-effectiveness/unknowns/11-change-quiz.html) | 核对自己对改动的理解 | 代码审查、研究与学习 |

## 产物在各阶段欠读者的

**实施前——让未知的事变得可判断。** 把待判断的对象放在页面中心。若读者要在设计方向中选择，就把四个方向都渲染出来，而不是描述它们。若在澄清需求，就让歧义可见、让选项明确。保留假设、观察与读者自身决定之间的区别；不把推断呈现为已确认事实。

**实施中——让偏差清晰可见。** 记录原计划是什么、实际发现或构建了什么、因此作出了什么决定、还有什么悬而未决。已决定的事项和未决定的事项之间的区别，应在视觉上清楚呈现。导出应携带偏差记录，而不只是最终状态。

**实施后——让理解可被检验。** 把误解定位到具体的说明或证据上。给读者一个可以反驳的东西，而不只是一个可以同意的摘要。反馈应可携带——读者应能把检查的结果带入下一步。

## 每次使用 Unknowns 参考的三个判断

**识别。** 哪种不确定性实际上影响了这次任务？
- 使用已经提供的信息；不要重新收集已经给出的答案。
- 只有当某件事仍未解决且真正影响结果时，才考虑探索、原型、访谈或讲解。

**呈现。** 用什么能让不确定的事变得可判断？
- 读取相应阶段的示例，找到最接近的原作。
- 把待判断的对象放在页面的主导位置；解释、历史和上下文放入侧边栏、批注或按需展开区。

**带走。** 这次互动留下了什么？
- 提供偏好、决策、未决问题、偏差依据或理解检查结果的导出，让下一步得到新增信息。
- 点击一个按钮不等于风险已解决；说清楚它意味着什么。
- 原始答案、选择和批注应可恢复为清楚的文本。

## 使用边界

只有在协作确实需要发现或澄清某件事时，才进入本参考。清楚且可直接完成的任务应直接执行。

- 不要默认先进行访谈。
- 不要运行知识测验，除非用户的任务确实需要。
- 不要求所有项目都走完三个阶段。

把原作示例中的具体决策、保守处理和签署要求视为特定场景的行为，而非技能的通用权限规则。
