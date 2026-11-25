# Requirements Analyst · Eval

> 目的：验证 Requirements Analyst 的能力包是否真的把赌注拆成了**可执行、可验证、可追溯**的最小闭环，而不是功能 backlog。

## 当前 case

- `case-01/`：个人习惯工具（习惯养成）。输入来自 B1、四维模型与 MVP 设计约束；要求产出 P0 ≤5 的需求包。

## 怎么跑

1. 建一个空工作区，复制 `case-01/` 的输入：
   - `brief.md`（任务说明）
   - `evidence-base.md`
   - `bet-book.md`
   - `prd.md`
   - `open-questions.md`
2. 用 `product-studio:requirements-analyst` 执行，给它：
   - 40–50 分钟
   - 不提供答案，只提供输入
   - 允许读 `references/requirements-analyst/` 四件套
3. 产出：
   - `requirements.md`（核心 Job Story + 需求清单 + AC + 边界条件 + 不做清单 + 追溯矩阵 + 冲突标记）
4. 用 `../rubric.md` + 本 case 的 `rubric.md` 评分。
5. 对照 `baseline.md`，记录「能力包让它多做了什么」。

## 评分

- 通用 8 维，0–4 分，满分 32。
- 门控优先：
  - 赌注锁定与追溯 =0 → 退回
  - 最小闭环纪律 =0 → 退回
  - AC 可测 =0 → 退回
  - 歧义消除 ≤1 → 退回
- Case-specific checks 见 `case-01/rubric.md`。

## 回归

每次修改 `agents/requirements-analyst.md` 或 `references/requirements-analyst/`：

1. 重跑 case-01。
2. 记录总分、门控、case-specific 通过项。
3. 如果分数下降，回滚或修正。
4. 不比较不同模型 / 不同输入条件的绝对分；只比较同一条件下的前后变化。

## 注意

- **不要给期望答案**。Requirements Analyst 必须自己选 Job Story、P0 和边界。
- 产出可以有不同的需求切分；评分看的是「可追溯、有情境、最小闭环、可测、有边界、有取舍、有冲突检测」，不是「和某个需求清单一致」。
- 如果某条需求无法追溯到 B1，**写「暂不进入 P0，需要更多证据」也是合格输出**。
- n=1 个 case 是方向性检查，不是统计证明。
