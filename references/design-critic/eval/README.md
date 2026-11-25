# Design Critic · Eval

> 目的：验证 Design Critic 的能力包是否真的产出了**有证据、有分级、有路由、不给方案**的评审，而不是「整体不错，建议优化」。

## 当前 case

- `case-01/`：评审 UI Designer 的「个人习惯工具」高保真产出（6 屏 + 状态页 + 设计系统），对照 B1 / PRD / IA / Requirements。
- 评审对象和上游都在 case 目录里；`screens/_shots/` 是真实截图，必须逐张看。

## 怎么跑

1. 建一个空工作区，复制 `case-01/` 的输入：
   - `brief.md`（任务说明）
   - `bet-book.md`、`prd.md`、`ia-flows.md`、`requirements.md`
   - `design-system.md`、`ui-spec.md`、`design-rationale.md`
   - `screens/`（HTML/CSS + `_shots/`）
2. 用 `product-studio:design-critic` 执行，给它：
   - 40–50 分钟
   - 不提供答案，只提供输入
   - 允许读 `references/design-critic/` 四件套
3. 产出：
   - `critique.md`（范围 + 意图对齐 + 分级问题 + 覆盖 + 路由 + 无法判断 + 总判断）
4. 用 `../rubric.md` + 本 case 的 `rubric.md` 评分。
5. 对照 `baseline.md`，记录「能力包让它多做了什么」。

## 评分

- 通用 8 维，0–4 分，满分 32。
- 门控优先：
  - 范围锁定 =0 → 退回
  - 证据质量 =0 → 退回
  - 严重度分级 ≤1 → 退回
  - 不给方案 =0 → 退回
- Case-specific checks 见 `case-01/rubric.md`。

## 回归

每次修改 `agents/design-critic.md` 或 `references/design-critic/`：

1. 重跑 case-01。
2. 记录总分、门控、case-specific 通过项。
3. 如果分数下降，回滚或修正。
4. 不比较不同模型 / 不同输入条件的绝对分；只比较同一条件下的前后变化。

## 注意

- **不要给期望答案**。Critic 必须自己找问题、分级、路由。
- 评审可以有不同的发现；评分看的是「范围、证据、分级、覆盖、不给方案、路由、判断」，不是「和某个问题清单一致」。
- 审美判断标 ⚪；不给方案；不越界评上游。
- 如果某个维度无法判断，标 ⚪ 并说明需要什么条件，不要假装能判断。
- n=1 个 case 是方向性检查，不是统计证明。
