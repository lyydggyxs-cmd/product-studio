# Prototype Designer · Eval

> 目的：验证 Prototype Designer 的能力包是否真的把「赌注 + IA」变成了**可被否定的原型仪器**，而不是提前做完整 App。

## 当前 case

- `case-01/`：个人习惯工具（习惯养成）。输入来自四维模型与 MVP 设计约束；要求选一个 B1/A1–A5 假设，用最低成本原型检验。
- 可接受的检验对象：A2（三级视觉平等）、A4（阶段标签可理解）、A5（中断不焦虑）、或 IA 的结构假设。

## 怎么跑

1. 建一个空工作区，复制 `case-01/` 的输入：
   - `brief.md`（任务说明）
   - `evidence-base.md`
   - `bet-book.md`
   - `prd.md`
   - `ia-flows.md`
   - `validation-toolkit.md`
2. 用 `product-studio:prototype-designer` 执行，给它：
   - 45–60 分钟
   - 不提供答案，只提供输入
   - 允许读 `references/prototype-designer/` 四件套
3. 产出：
   - `prototypes/`（探索：≥3 个结构性不同方向；验证：1 个聚焦可点击原型）
   - `test-notes.md`（问题 + 标准 + 保真度 + 学习日志 + 回灌）
   - `open-questions.md`（新问题分类）
4. 用 `../rubric.md` + 本 case 的 `rubric.md` 评分。
5. 对照 `baseline.md`，记录「能力包让它多做了什么」。

## 评分

- 通用 8 维，0–4 分，满分 32。
- 门控优先：
  - 检验问题 =0 → 退回
  - 支持/反驳标准 =0 → 退回
  - 保真度匹配 ≤1 → 退回
  - 学习日志 =0 → 退回
- Case-specific checks 见 `case-01/rubric.md`。

## 回归

每次修改 `agents/prototype-designer.md` 或 `references/prototype-designer/`：

1. 重跑 case-01。
2. 记录总分、门控、case-specific 通过项。
3. 如果分数下降，回滚或修正。
4. 不比较不同模型 / 不同输入条件的绝对分；只比较同一条件下的前后变化。

## 注意

- **不要给期望答案**。Prototype Designer 必须自己选检验问题、模式和保真度。
- 产出可以选不同假设；评分看的是「一个问题、先写标准、保真度匹配、可操作、有学习、有回灌、有边界」，不是「和某个方向一致」。
- 探索模式允许纸面/灰框；验证模式允许可点击 HTML；禁止生产代码。
- 如果证据不足以确定该测哪个假设，**写「先做 3 方向纸面探索」也是合格输出**。
- n=1 个 case 是方向性检查，不是统计证明。
