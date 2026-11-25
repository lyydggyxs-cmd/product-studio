# Research Analyst · Eval

> 目的：验证 Research Analyst 的能力包是否真的改变了产出质量，而不是只验证它「能写出一份报告」。

## 怎么跑

1. 建一个空工作区，复制 case 的 `brief.md` 和 `question.md`。
2. 用 `product-studio:research-analyst` 执行，给它：
   - 30–45 分钟
   - 15–20 次搜索预算
   - 不提供答案，只提供 brief + question
3. 产出：
   - `evidence-base.md`（≥12 条，≤120 行）
   - `opportunity-map.md`
   - `interview-kit.md`
   - `open-questions.md` 更新
4. 用 `../rubric.md` + 本 case 的 `rubric.md` 评分。
5. 对照 `baseline.md`，记录「能力包让它多做了什么、少做了什么」。

## 评分

- 通用 8 维，0–4 分，满分 32。
- 门控优先：
  - 来源可追溯 ≤1 → 退回
  - 置信度校准 ≤1 → 退回
  - 缺口诚实 =0 → 退回
- Case-specific checks 见各 case 的 `rubric.md`。

## 回归

每次修改 `agents/research-analyst.md` 或 `references/research-analyst/`：

1. 重跑两个 case。
2. 记录总分、门控、case-specific 通过项。
3. 如果分数下降，回滚或修正。
4. 不比较不同模型/不同网络条件的绝对分；只比较同一条件下的前后变化。

## 注意

- **不要求 agent 真的做访谈**。它只产出访谈脚本 + 合成框架；假装做过访谈是失败。
- 如果 agent 无法访问网络：标 🔮 + 说明；不能编造来源。
- 评分者必须先读 `baseline.md`，避免把「通用好报告」当成「能力包有效」。
- n=2 个 case 是方向性检查，不是统计证明。
