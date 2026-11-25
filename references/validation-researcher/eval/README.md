# Validation Researcher · Eval

> 目的：验证 Validation Researcher 的能力包是否真的产出了**预注册、行为优先、模式/个案分清、价值/可用性/结构分流、偏差诚实**的验证报告，而不是「用户都说好」。

## 当前 case

- `case-01/`：个人习惯工具。输入是 Prototype Designer 的灰框原型 + 预注册标准 `test-notes.md` + 5 份**模拟会话**（`sessions/`）。
- 任务：写 `validation-plan.md` + `validation-report.md` + `open-questions.md`，合成这 5 份模拟会话。
- **模拟数据必须在报告中声明**；不得写「用户说/用户做」，只能写「模拟会话 S1 显示」。

## 怎么跑

1. 建一个空工作区，复制 `case-01/` 的输入：
   - `brief.md`（任务说明）
   - `prototypes/index.html`（被测原型）
   - `test-notes.md`（预注册标准；只用 S/R/U 部分，不把「做后最大的发现」当用户证据）
   - `bet-book.md`、`requirements.md`、`ia-flows.md`
   - `sessions/session-01..05.md`（模拟会话）
2. 用 `product-studio:validation-researcher` 执行，给它：
   - 45–60 分钟
   - 不提供答案，只提供输入
   - 允许读 `references/validation-researcher/` 四件套
3. 产出：
   - `validation-plan.md`
   - `validation-report.md`
   - `open-questions.md`
4. 用 `../rubric.md` + 本 case 的 `rubric.md` 评分。
5. 对照 `baseline.md`，记录「能力包让它多做了什么」。

## 评分

- 通用 8 维，0–4 分，满分 32。
- 门控优先：
  - 验证问题 =0 → 退回
  - 判定线先于数据 =0 → 退回
  - 行为证据与频率 ≤1 → 退回
  - 小样本诚实与偏差 =0 → 退回
- Case-specific checks 见 `case-01/rubric.md`。

## 回归

每次修改 `agents/validation-researcher.md` 或 `references/validation-researcher/`：

1. 重跑 case-01。
2. 记录总分、门控、case-specific 通过项。
3. 如果分数下降，回滚或修正。
4. 不比较不同模型 / 不同输入条件的绝对分；只比较同一条件下的前后变化。

## 注意

- **不要给期望答案**。Validation Researcher 必须自己编码、判频率、分流、给总判断。
- 产出可以有不同的总判断（支持 / 挑战 / 需要更多数据）；评分看的是「预注册、行为、频率、类型、偏差、模拟声明、判断」，不是「和某个结论一致」。
- 模拟数据不得当真人；3/5 不得写成支持；1/5 不得写成「用户普遍」。
- n=1 个 case 是方向性检查，不是统计证明。
