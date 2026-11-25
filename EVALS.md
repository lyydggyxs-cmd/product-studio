# Product Studio · Eval 回归基线

> 8 个岗位 eval 结果的统一登记处（2026-11-25 建立）。
> 评分细则在各 `references/<role>/eval/`；本文件只登记「跑过什么、得分多少、是否通过门控」。
> 运行产物（工作区、截图、`eval-report.md`）保存在本地 `../product-studio-evals/`，不随插件仓库发布。

---

## 1. 基线表

| 岗位 | Case | 场景 | 总分 | 门控 | Case-specific | 总判断 | 日期 |
|---|---|---|---|---|---|---|---|
| Research Analyst | case-01 | B2C 周末做饭 | 29/32 | 全过 | 8/8 | 可作模板 | 2026-11-13 |
| Research Analyst | case-02 | B2B 周报自动化 | 29/32 | 全过 | 8/8 | 可作模板 | 2026-11-14 |
| Product Definer | case-01 | B2C 周末做饭 | 29/32 | 全过 | 8/8 | 可作模板（有保留） | 2026-11-14 |
| Product Definer | case-02 | B2B 周报自动化 | **32/32** | 全过（4/4/4） | 8/8 | 可作模板 | 2026-11-25 |
| Product Architect | case-01 | B2C 习惯工具 | 30/32 | 全过 | 8/8 | 可作模板（有保留） | 2026-11-15 |
| Product Architect | case-02 | B2B 周报自动化 | **31/32** | 全过（4/4/4） | 8/8 | 可作模板 | 2026-11-25 |
| Prototype Designer | case-01 | B2C 习惯工具 | 31/32 | 全过 | 8/8 | 可作模板（三条非阻断建议） | 2026-11-18 |
| Requirements Analyst | case-01 | B2C 习惯工具 | 31/32 | 全过 | 8/8 | 可作模板（有保留） | 2026-11-18 |
| UI Designer | case-01 r1 | B2C 习惯工具（无 `requirements.md` 输入） | 30/32 | 全过 | 7/8 | 可进入下游 | 2026-11-18 |
| UI Designer | case-01 r2 | B2C 习惯工具（补 `requirements.md` 输入） | 29/32 | 全过 | 8/8 | 可作模板（附 2 项小修） | 2026-11-25 |
| Design Critic | case-01 | 评审习惯工具 UI | 30/32 | 全过 | 8/8 | 可作模板（有保留） | 2026-11-18 |
| Validation Researcher | case-01 | 5 份模拟会话合成 | 30/32 | 全过（4/4） | 8/8 | 可作模板（有保留） | 2026-11-18 |

> **不可横比的分数**：Research 的 B2C/B2B、Definer 的 case-01/02、Architect 的 case-01/02、UI 的 r1/r2 输入条件不同；只比较**同一 case、同一输入条件**的前后变化。
> **n=1/2 是方向性检查**，不是统计证明。

---

## 2. 可复跑流程

每个岗位的 `references/<role>/eval/README.md` 都有「怎么跑」。统一规则：

1. 建空工作区，只复制该 case 的输入；不复制评分材料、历史产出或 `eval-report.md`。
2. 用该岗位 Agent 执行，给 30–75 分钟；不提供答案。
3. 产出写到工作区。
4. 用 `references/<role>/rubric.md` + `eval/case-XX/rubric.md` 评分；门控优先于总分。
5. 对照 `eval/case-XX/baseline.md`，记录「能力包让它多做了什么」。
6. **评审者与产出者分离**；产出者不得读 `rubric.md` / `expected-output.md` / `baseline.md`。
7. 只比较同一 case、同一输入条件的前后变化；不跨 case 横比。

---

## 3. 已知残余（不阻断）

| 岗位 | 残余 |
|---|---|
| UI Designer | 回顾空/加载/失败、极端数据、暗色全量屏仍 spec-only；chip 选中态 `✓` 是文字；review 周切换仅视觉 |
| Product Architect | 维度 2 标签来源仍以日常语言/竞品惯例为主，未全部挂 evidence ID |
| Design Critic | 评审结论的严重度条件化依赖「requirements 晚于设计」的时序；换输入顺序时需重判 |
| 其余岗位 | 见各 `eval-report.md` 的「剩余未闭合」 |

---

## 4. 维护规则

- 每次修改 `agents/<role>.md` 或 `references/<role>/`，重跑该岗位的**全部** case。
- 重跑后在「基线表」追加或更新一行；保留日期，不删除旧记录。
- 分数下降 → 回滚或修正；不得为了保持分数放宽 rubric。
- 新增 case：先在 `references/<role>/eval/case-XX/` 建输入 + rubric + baseline，再跑。
- 修改了能力包但未重跑 → 在对应行标「待回归」，不要写成「已通过」。
