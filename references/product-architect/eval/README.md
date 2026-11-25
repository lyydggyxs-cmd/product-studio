# Product Architect · Eval

> 目的：验证 Product Architect 的能力包是否真的把「赌注 + 需求」变成了「可验证的 IA + 流 + 状态 + 验证工具」，而不是画了一棵更完整的 IA 树。

## 怎么跑

1. 建一个空工作区，复制 case 的输入：
   - `brief.md`
   - `bet-book.md` + `prd.md`（case-01）或 `given-bet.md`（case-02）
   - `evidence-base.md`
2. 用 `product-studio:product-architect` 执行，给它：
   - 30–45 分钟
   - 不提供答案，只提供输入
3. 产出：
   - `ia-flows.md`（心智模型 + 骨架 IA + 完整 IA + 用户流 + 状态矩阵 + 信心地图 + 致命假设）
   - `validation-toolkit.md`（Card Sorting / Tree Testing / 陌生人测试工具包）
4. 用 `../rubric.md` + 本 case 的 `rubric.md` 评分。
5. 对照 `baseline.md`，记录「能力包让它多做了什么」。

## 评分

- 通用 8 维，0–4 分，满分 32。
- 门控优先：
  - 心智模型假说 ≤1 → 退回
  - 验证工具 =0 → 退回
  - 信心诚实 ≤1 → 退回
- Case-specific checks 见各 case 的 `rubric.md`。

## 回归

每次修改 `agents/product-architect.md` 或 `references/product-architect/`：

1. 重跑两个 case。
2. 记录总分、门控、case-specific 通过项。
3. 如果分数下降，回滚或修正。
4. 不比较不同模型/不同输入条件的绝对分；只比较同一条件下的前后变化。

## 注意

- **不要给期望答案**。Architect 必须自己做竞争性心智模型。
- 产出可以有不同的组织方式；评分看的是「竞争假说、标签语言、结构纪律、流/状态完整、验证工具可执行、信心诚实」，不是「和答案一致」。
- 如果证据不足以确定 IA，**写「骨架待验证，先做 card sorting」也是合格输出**；假装确定才是失败。
- n=2 个 case 是方向性检查，不是统计证明。
