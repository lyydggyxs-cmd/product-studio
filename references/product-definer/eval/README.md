# Product Definer · Eval

> 目的：验证 Product Definer 的能力包是否真的把「证据」变成「可证伪的赌注 + 活 PRD」，而不是写一份更完整的 PRD。

## 怎么跑

1. 建一个空工作区，复制 case 的 `brief.md` + `evidence-base.md`。
2. 用 `product-studio:product-definer` 执行，给它：
   - 30–45 分钟
   - 不提供答案，只提供 brief + evidence base
3. 产出：
   - `bet-book.md`（一个赌注 + 机制 + 证据 + 成功/kill + Plan B + Anti-Goals）
   - `prd.md`（v0.1，活文档）
   - `decision-log.md`（决策记录）
4. 用 `../rubric.md` + 本 case 的 `rubric.md` 评分。
5. 对照 `baseline.md`，记录「能力包让它多做了什么」。

## 评分

- 通用 8 维，0–4 分，满分 32。
- 门控优先：
  - 可证伪性 ≤1 → 退回
  - 证据追溯 ≤1 → 退回
  - 范围纪律 =0 → 退回
- Case-specific checks 见各 case 的 `rubric.md`。

## 回归

每次修改 `agents/product-definer.md` 或 `references/product-definer/`：

1. 重跑两个 case。
2. 记录总分、门控、case-specific 通过项。
3. 如果分数下降，回滚或修正。
4. 不比较不同模型/不同输入条件的绝对分；只比较同一条件下的前后变化。

## 结果记录

| Case | 场景 | 总分 | 门控 | Case-specific | 判断 | 日期 |
|---|---|---|---|---|---|---|
| case-01 | B2C 周末做饭 | 29/32 | 全过 | 8/8 | 可作模板（补两条反模式） | 2026-11-14 |
| case-02 | B2B 周报自动化 | **32/32** | 全过（4/4/4） | **8/8** | **可作模板**（4 条一致性小修已闭环） | 2026-11-25 |

- B2B case-02 是 Definer 的第二个回归基线；两个 case 都通过门控。
- 分数不跨 case 横比（输入不同）；只比较同一 case 的前后变化。

## 注意

- **不要给期望答案**。Product Definer 必须自己从证据里选赌注。
- 产出可以有不同的赌注方向；评分看的是「可证伪、有机制、有证据、有 kill 信号、有 Plan B」，不是「和答案一致」。
- 如果证据不足以支持一个赌注，**写「证据不足，先验证 X」也是合格输出**；假装确定才是失败。
- n=2 个 case 是方向性检查，不是统计证明。
