# Product Studio · 实施路线图

> **这是本项目的唯一事实源（source of truth）。**
> 任何后续设计、命名、范围、角色调整，先改这里，再改实现。
> 如果实现和本文件冲突，以本文件为准；如果本文件需要变，先记变更日志。

- 项目启动：2026-11-10
- 当前阶段：**Phase 3（能力包 + eval + 模式实测）**
- 分发准备：插件打包已完成，但不属于原 Phase 3；见 Phase 4
- 范围终点：**产品 UI 设计**（不做开发）
- 案例状态：错题本 PAUSED（2026-11-13），不继续；教训只作观察，不作为改设计依据

---

## 1. 已确认决策

| # | 决策 | 确认日期 | 备注 |
|---|---|---|---|
| D1 | 采用「工作室团队」架构，不是单体 Agent，也不是线性流水线 | 2026-11-10 | 岗位专业化 + 上下文总线 + 嵌套循环 |
| D2 | 按 Phase 1 → Phase 2 → Phase 3 实施 | 2026-11-10 | 不一次性做全部岗位 |
| D3 | UI Designer **只做产品 UI**（界面、设计系统、高保真 UI） | 2026-11-10 | 不做品牌识别、不做营销页 |
| D4 | PRD 采用**活文档**形态：由赌注书 + 决策日志 + 需求包合成 | 2026-11-10 | 不单独写一份一次性 10 节大文档 |
| D5 | 团队支持四种调用：整队 Sprint / 配对 Pair / 单岗 Role / 评审 Review | 2026-11-10 | 单岗可独立调用是核心价值 |
| D6 | 上下文通过**共享工作区 + 指针**传递，不通过 prompt 传全文 | 2026-11-10 | 这是团队模式成立的前提 |

---

## 2. 不可漂移的硬约束

以下六条是红线。任何后续改动如果违反其中一条，**停下来，先问用户**，不要自行放宽。

1. **不做开发**：不产出生产代码、后端、数据库、部署、运维。UI Designer 只做设计，不写 React 生产代码。
2. **岗位不做全文转述**：不把一个岗位的整篇输出粘进另一个岗位的 prompt。只传「读哪个文件、读哪几节、回答哪个问题」。
3. **每个工件有 schema**：证据、赌注、决策、交接必须有结构化字段，不能是自由散文。
4. **每个结论带置信度**：✅ 已验证 / ⚠️ 推断 / 🔮 猜测。下游不得把 ⚠️ 当 ✅ 用。
5. **PRD 是活文档**：由 Product Definer 持有，随证据和决策更新；不是某一阶段的终点产物。
6. **Studio Lead 不干专业活**：只做上下文路由、检查点、漂移检测、决策记录。不替 Research 做调研，不替 UI 做设计。

---

## 3. 实施路径

### Phase 1：骨架 + 核心 6 岗（已完成）

**目标**：跑通「调研 → 赌注 → IA → UI 设计」一条最小链路。

| # | 交付 | 形态 | 状态 |
|---|---|---|---|
| 1 | Studio Lead | `skills/team/SKILL.md` | ✅ 完成 |
| 2 | Research Analyst | `agents/research-analyst.md` | ✅ 完成 |
| 3 | Product Definer（含最小需求分析） | `agents/product-definer.md` | ✅ 完成 |
| 4 | Product Architect | `agents/product-architect.md` | ✅ 完成 |
| 5 | UI Designer（产品 UI） | `agents/ui-designer.md` | ✅ 完成 |
| 6 | Design Critic | `agents/design-critic.md` | ✅ 完成 |
| 7 | 上下文总线 schema | `schemas/*.schema.json` | ✅ 完成 |
| 8 | 工件模板 | `templates/*.md` | ✅ 完成 |
| 9 | 冒烟测试 | 错题本案例跑通 Loop 1–3 后暂停（2026-11-13） | 🟡 部分完成 |

> 案例教训见 `LESSONS.md`；案例状态见 `../product-studio-cases/math-mistake-notebook/CASE-STATUS.md`（案例已移出插件仓库，避免公开个人数据）。
> **注意**：`LESSONS.md` 里的硬化建议只作观察记录，不作为改设计依据——用户判断「半个案例不足以改架构」。等跑过几个完整案例再决定是否采纳。

**Phase 1 刻意不做（Phase 2 已补齐前三项）**：
- 独立的 Requirements Analyst（Phase 1 由 Product Definer 兼；Phase 2 已拆出）
- 独立的 Prototype Designer（Phase 1 由 UI Designer 出高保真原型作过渡；Phase 2 已拆出）
- Validation Researcher（Phase 2 已加入）
- 能力包 references 的深度填充（Phase 3）

### Phase 2：补齐专业分工（当前）

| # | 交付 | 说明 | 状态 |
|---|---|---|---|
| 1 | Requirements Analyst | 从 Product Definer 拆出：JTBD、Job Stories、AC、边界条件 | ✅ 完成 |
| 2 | Prototype Designer | 低保真/中保真原型，专做赌注检验，不追求视觉 | ✅ 完成 |
| 3 | Validation Researcher | 原型测试、访谈、行为分析、价值/可用性分流 | ✅ 完成 |
| 4 | 三角协作 | Research ↔ Requirements ↔ Definer；Architect ↔ Prototype ↔ UI ↔ Validation | ⬜ 待实测 |

### Phase 3：打磨与扩展（当前）

| # | 交付 | 说明 | 状态 |
|---|---|---|---|
| 1 | 每岗能力包 | `references/<role>/`：方法、案例、评分标准、反模式 | ✅ **8/8 岗位完成**（Research / Definer / Architect / UI / Prototype / Requirements / Critic / Validation）；UI 含参考板 + 视觉表现力门；Prototype 含原型仪器 + 顺序/措辞纪律；Requirements 含 AC 灰区 + 证伪优先；Critic 含证据/分级/路由/不给方案；Validation 含预注册/行为优先/小样本诚实 |
| 2 | 每岗 eval | golden task + rubric + 回归 | ✅ **8/8 岗完成**：8 岗均有 eval；Research / Definer / Architect 双 case（B2C+B2B）；UI 跨岗输入链已补并重跑 r2；**回归基线统一登记在 [`EVALS.md`](./EVALS.md)**（2026-11-25） |
| 3 | 可选岗位 | Content Designer、Commercial Strategist | ⬜ 待做 |
| 4 | 配对/单岗/评审模式实测 | 验证四种调用模式 | ✅ **四模式 + 完整 Sprint Loop 1–3 流程已跑通**；Pair / Role / Review / Sprint 全部验证；Loop 3 真人验证未执行（只出预注册计划）；SKILL.md 三处修复已写回 |

> **3.1 模板已验证（B2C + B2B）**：`references/research-analyst/`。两个 case 都是 29/32、门控全过、case-specific 8/8；补了反模式「合并项拆解」「单源主结论」。下一步按这个结构复制到其余 7 个岗位，先做 **Product Definer**。

> **插件打包不属于原始 Phase 3**。它是我后来加的分发准备，已放在 Phase 4；Phase 3 没完成前不发布。

### Phase 4：分发（已发布）

| # | 交付 | 说明 | 状态 |
|---|---|---|---|
| 1 | 插件清单 | `.claude-plugin/plugin.json` + `marketplace.json`；插件名 `product-studio`，入口 `product-studio:team` | ✅ 完成 |
| 2 | 本地加载验证 | `claude --plugin-dir`：8 agents + 1 skill | ✅ 完成 |
| 3 | 发布 GitHub / 安装说明 | 公开仓库 `lyydggyxs-cmd/product-studio`；v0.1.0 tag；安装命令见 README | ✅ 完成（2026-11-25） |

---

## 4. 目录结构（插件态）

```
product-studio/                  ← 插件根目录（repo root）
├── .claude-plugin/
│   ├── plugin.json              ← 插件清单
│   └── marketplace.json         ← 仓库即市场
├── ROADMAP.md                   ← 本文件（唯一事实源）
├── ARCHITECTURE.md              ← 团队架构
├── CONTEXT.md                   ← 共享术语 / 路径 / 工件所有权
├── README.md                    ← 安装 + 使用
├── LESSONS.md                   ← 案例观察记录（不改设计）
├── LICENSE                      ← MIT
├── skills/
│   └── team/
│       └── SKILL.md             ← Studio Lead（主线程入口）
├── agents/
│   ├── research-analyst.md
│   ├── requirements-analyst.md
│   ├── product-definer.md
│   ├── product-architect.md
│   ├── prototype-designer.md
│   ├── ui-designer.md
│   ├── design-critic.md
│   └── validation-researcher.md
├── schemas/
│   ├── brief.schema.json
│   ├── evidence.schema.json
│   ├── bet.schema.json
│   ├── decision.schema.json
│   └── handoff.schema.json
├── templates/
│   ├── brief.md
│   ├── evidence-base.md
│   ├── bet-book.md
│   ├── requirements.md
│   ├── prd.md
│   ├── decision-log.md
│   ├── open-questions.md
│   ├── ia-flows.md
│   ├── prototype-notes.md
│   ├── design-system.md
│   ├── critique.md
│   ├── validation-plan.md
│   └── validation-report.md
└── references/                  ← Phase 3 填充
    ├── research/
    ├── definition/
    ├── architecture/
    ├── ui/
    └── critique/
```

> 案例不放在插件仓库内：`../product-studio-cases/`（避免公开个人数据）。

---

## 5. 变更日志

| 日期 | 变更 | 原因 | 影响 |
|---|---|---|---|
| 2026-11-10 | 项目启动；确认 D1–D6 | 用户确认工作室团队方向 | 新建本项目 |
| 2026-11-10 | Phase 1 暂不设独立 Requirements Analyst / Prototype Designer | 控制首版复杂度；Definer 兼最小需求分析，UI Designer 兼高保真原型 | Phase 2 补齐 |
| 2026-11-13 | Phase 2 完成：Requirements Analyst / Prototype Designer / Validation Researcher | 用户选择先补齐专业分工 | 8 个岗位到位 |
| 2026-11-13 | 错题本案例 PAUSED | 用户决定回到 Studio 系统设计；半个案例不足以改架构 | 案例移出插件仓库，保留为观察样本 |
| 2026-11-13 | 插件打包完成（分发准备） | 用户选择打包；本地加载验证通过 | 插件清单 + marketplace + LICENSE 就绪 |
| 2026-11-13 | **纠正路径**：Phase 3 未完成，插件打包不属于原始 Phase 3 | 用户指出跳步；原始 Phase 3 是能力包 + eval + 可选岗位 + 模式实测 | 插件打包移到 Phase 4；恢复 Phase 3 顺序 |
| 2026-11-13 | Phase 3.1 完成：Research Analyst 能力包 + 2 个 eval case | 用户选 A：Research Analyst 作为参考岗位 | 建立能力包模板，下一步复制到其余岗位 |
| 2026-11-13 | Phase 3.1 eval 通过：case-01 独立评分 29/32，门控全过，case-specific 8/8 | 验证模板是否真的改变产出质量 | 模板验证通过；补反模式「合并项拆解」；产出可进 Product Definer |
| 2026-11-14 | Phase 3.1 双案例验证：case-02（B2B）同样 29/32、门控全过、case-specific 8/8 | 检查模板是否只对 B2C 有效 | B2C/B2B 都通过；补反模式「单源主结论」；进入 Phase 3.2 |
| 2026-11-14 | Phase 3.2 Product Definer 能力包已建 | 按 Research Analyst 模板复制；复用 B2C/B2B 证据库做 eval 输入 | 待跑 eval；通过后继续下一岗位 |
| 2026-11-14 | Product Definer case-01 eval 通过：29/32，门控全过，case-specific 8/8 | 验证「一个赌注 + 活 PRD」能力包 | 补「单变量假象」「Kill 阈值不一致」；case-02 待跑 |
| 2026-11-14 | Product Definer case-02 推迟；进入 Product Architect | 用户选择先做下一岗位，不继续 B2B eval | 记为「推迟」，不是跳过；当前做 Architect 能力包 |
| 2026-11-14 | Product Architect 能力包已建 | 按同一模板复制；case-01 复用 Definer 输出，case-02 用给定 bet | 待跑 eval；通过后继续下一岗位 |
| 2026-11-15 | Product Architect case-01 eval 通过：30/32，门控全过，case-specific 8/8 | 验证「竞争心智模型 + 可执行验证工具」能力包 | 补「合并项推导标 ✅」；case-02 待定 |
| 2026-11-17 | Phase 3.2 UI Designer 能力包 + 参考板 + eval case-01（习惯养成） | 用户要求「视觉顶级个人工具」；旧做饭 case 归档为失败样本 | eval 31/32，门控全过，视觉表现力门 PASS，case-specific 8/8，**可作模板（附暗色未出图）**；修对勾徽章 + 补 07-states 三态 + 清 07 引入的 5 处回归 |
| 2026-11-17 | 能力包硬化：参考板硬步骤 + 视觉资产要求 + 视觉表现力门 + 状态必须渲染 | 做饭 case 产出「带令牌的线框」；eval 抓到状态只写不渲染 | UI Designer 从「纪律」升级为「参考驱动 + 视觉执行」 |
| 2026-11-18 | Phase 3.2 Prototype Designer 能力包 + eval case-01（A2 三级平等） | 验证「原型仪器」能力包；eval 抓到顺序未平衡、追问污染两个方法学缺陷 | eval 31/32，门控全过，case-specific 8/8，**可作模板（三条非阻断建议已闭合）**；补顺序平衡 / 中性追问 / 被试模式 / 复合对照臂归因四条纪律 |
| 2026-11-18 | Phase 3.2 Requirements Analyst 能力包 + eval case-01（习惯养成） | 验证「赌注 → 最小闭环需求」能力包；eval 三轮抓到 AC 中间带缺失、比较命题用单臂阈值、AC2.4 引错 kill、种子数据等 | eval 31/32，门控全过，case-specific 8/8，**可作模板（有保留）**；补 AC 灰区/证伪优先、比较命题 vs 设计前提、产品级信号不归因三条纪律；维度 3 仍 3（R01 承载 A1/A2/A4） |
| 2026-11-18 | Phase 3.2 Design Critic 能力包 + eval case-01（评审习惯工具 UI） | 验证「证据/分级/路由/不给方案」能力包；critic 抓到 R05 暂停不可达、C1/C2/C3 写死两条跨岗位阻断 | eval 30/32，门控全过，case-specific 8/8，**可作模板（有保留）**；阻断按「requirements 晚于 UI 设计」条件化；暴露 UI eval 输入缺 requirements.md，已记入 UI eval README |
| 2026-11-18 | Phase 3.2 Validation Researcher 能力包 + eval case-01（5 份模拟会话合成） | 验证「预注册/行为优先/模式 vs 个案/小样本诚实」能力包；eval 抓到 S5 编码误计会翻转 R1、R3/R4 未测被写成未触发 | eval 30/32，门控 4/4，case-specific 8/8，**可作模板（有保留）**；行为证据 67% < 70% 为方法限制；**Phase 3.2 完成（8/8）** |
| 2026-11-19 | Phase 3.5 四种调用模式实测（个人读书笔记小案例） | 验证 Studio Lead 的路由、handoff 指针、上下文总线、检查点、决策记录 | Pair / Role / Review / Sprint-lite 全部跑通；指针纪律成立；发现决策日志归属不清、回灌段格式不统一、检查点无固定文件；SKILL.md 已写回三处 |
| 2026-11-20 | 完整 Sprint Loop 1–3 流程实测（同一案例） | 补上 3.5 唯一没测的端到端协同；验证 Loop 3 的原型/UI/复审/验证计划 | 流程 ✅ / 产品 ⚠️；F2 升级为载体所有权；N-1 为结构门 G2；K1–K4 缺「入口不可发现」；Loop 3 真人验证未执行（只出 742 行计划）；D08/D09 记录 |
| 2026-11-25 | Phase 4.3 完成：公开发布 `lyydggyxs-cmd/product-studio`（`v0.1.0` tag） | 用户确认公开仓库、仓库名、包含 eval；明确要求先发布，覆盖先前「Phase 3 完成后再发布」的顺序约束 | 插件可通过 marketplace 安装；README 已改为实际 owner/repo；清理了本机绝对路径并新增 `.gitignore` |
| 2026-11-25 | Phase 3.3 ① 完成：UI Designer eval 补 `requirements.md` 并重跑 r2 | 修复 Critic 暴露的跨岗输入链缺口；验证 R05 / C1–C3 能否被设计处理 | r2 独立复核 29/32、门控全过、视觉门 PASS、case-specific 8/8、可作模板（附 2 项小修）；F1/F2 关闭；4 项回归复核 4/4 CLOSED；首轮与 r2 分数不可横比 |
| 2026-11-25 | Phase 3.3 ② 完成：Definer / Architect case-02（B2B） | 建立 B2B 回归基线；验证两个岗位在第二个案例上是否仍通过门控 | Definer **32/32**、Architect **31/32**，均门控全过、case-specific 8/8、可作模板；Architect 最大结构问题（改期请求无归宿）已修并复核 6/6 CLOSED；Definer 4 条一致性小修已闭环；剩余为 Architect 维度 2 标签来源颗粒度 |
| 2026-11-25 | Phase 3.3 ③ 完成：建立 8 岗 eval 回归基线（[`EVALS.md`](./EVALS.md)） | 统一登记各岗位 case、分数、门控、case-specific、残余；确认每个岗位的 eval README 都有可复跑流程 | **Phase 3.3 完成**；基线：Research 29/29、Definer 29/32、Architect 30/31、Prototype 31、Requirements 31、UI r1 30/r2 29、Critic 30、Validation 30；下一步 Phase 3.4 可选岗位 |

> 以后每次变更追加一行。不要删除旧行。

---

## 6. 下一步

> **2026-11-13 纠正**：Phase 3 未完成。插件打包是我后来加的分发准备，不属于原始 Phase 3；先做 Phase 3，再谈发布。
> `LESSONS.md` 里的硬化建议只作观察记录，等跑过几个完整案例后再决定是否采纳。

> **当前暂停点（2026-11-25）**：Phase 3.1 ✅ / 3.2 ✅（8/8）/ 3.3 ✅（① UI 输入链 ② B2B case-02 ③ 回归基线）/ 3.5 ✅（流程；产品 ⚠️）。下次从 **Phase 3.4** 开始：
> 3.4 可选岗位（Content Designer / Commercial Strategist）；Phase 4 发布已提前完成，之后只剩维护。
> 然后 Phase 3.4 可选岗位（Content Designer / Commercial Strategist），最后 Phase 4 发布。
> 完整 Sprint 流程测试的产物在 `../product-studio-evals/mode-test/`（`mode-test-report.md` + `sprint-report.md`）。

1. **Phase 1 完成；Phase 2 完成。**
2. **Phase 3 按顺序做**：
   - **3.1 ✅ 能力包模板 + 参考岗位**：Research Analyst（`references/research-analyst/`）；case-01（B2C）+ case-02（B2B）均 29/32，门控全过；补了「合并项拆解」「单源主结论」两条反模式。
   - **3.2 🟡 复制到其余 7 个岗位**：**Product Definer 能力包已建**；case-01 eval **29/32**，门控全过，case-specific 8/8；补了「单变量假象」「Kill 阈值不一致」两条反模式；case-02 推迟。**Product Architect 能力包已建**；case-01 eval **30/32**，门控全过，case-specific 8/8；补了「合并项推导标 ✅」反模式；case-02 待跑或推迟。**UI Designer 能力包已建**（含参考板 + 视觉表现力门）；eval case-01（习惯养成）**31/32**，门控全过，视觉表现力门 PASS，case-specific 8/8，判断**可作模板（附暗色未出图）**；补了「没有参考板 = 带令牌线框」「状态只写不渲染」两条教训；旧做饭 case 归档为失败样本。**Prototype Designer 能力包已建**；eval case-01（习惯养成，A2 三级平等）**31/32**，门控全过，case-specific 8/8，判断**可作模板（三条非阻断建议已闭合）**；补了「顺序平衡」「追问不提供词」「被试模式」「复合对照臂不归因单一变量」四条纪律。**Requirements Analyst 能力包已建**；eval case-01（习惯养成）**31/32**，门控全过，case-specific 8/8，判断**可作模板（有保留）**；补了「AC 灰区/证伪优先」「比较命题 vs 设计前提」「产品级信号不归因于假设」三条纪律；维度 3 仍 3（R01 一个 ID 承载 A1/A2/A4）；压缩 825→650–700 行列为模板质量项。**Design Critic 能力包已建**；eval case-01（评审习惯工具 UI）**30/32**，门控全过，case-specific 8/8，判断**可作模板（有保留）**；抓到两条跨岗位阻断（R05 暂停不可达、C1/C2/C3 写死），并暴露 UI eval 输入缺 `requirements.md` 的链路缺口（已记入 `references/ui-designer/eval/README.md`）。**Validation Researcher 能力包已建**；eval case-01（5 份模拟会话合成）**30/32**，门控全过，case-specific 8/8，判断**可作模板（有保留）**；补了「预注册/行为优先/模式 vs 个案/模拟数据声明」纪律；行为证据 67% < 70% 列为方法限制。**Phase 3.2 完成（8/8）**。
   - **3.3 ✅ 每岗 eval**：8 岗 eval 全部建立；Research Analyst case-02 已通过（29/32）；**UI Designer 跨岗输入链已补（r2：29/32、门控全过、视觉门 PASS、case-specific 8/8、可作模板附 2 项小修；F1/F2 关闭，4 项回归复核 CLOSED）**；**Definer case-02（B2B）32/32、Architect case-02（B2B）31/32，均门控全过、case-specific 8/8、可作模板**；**回归基线统一登记在 [`EVALS.md`](./EVALS.md)**。
   - **3.4 ⬜ 可选岗位**：Content Designer、Commercial Strategist。
   - **3.5 ✅ 四种调用模式 + 完整 Sprint Loop 1–3 流程实测**：个人读书笔记小案例；Pair / Role / Review / Sprint 全部跑通；指针纪律、检查点、角色反哺成立。完整 Sprint 走完 Loop 1（Research→Definer）、Loop 2（Requirements→Architect）、Loop 3（Prototype→UI→Critic→Validation plan）；**Loop 3 的「至少一轮真人验证」未执行**，只出 742 行预注册计划，所以流程 ✅ / 产品 ⚠️。关键跨 Loop 发现：F2 是载体所有权（不是入口按钮位置）、N-1 是结构门 G2、K1–K4 缺「入口不可发现」。详见 `../product-studio-evals/mode-test/mode-test-report.md` 与 `sprint-report.md`。
3. **Phase 4 分发**：已完成——公开仓库 `lyydggyxs-cmd/product-studio`，`v0.1.0` tag（2026-11-25）。原始顺序要求「Phase 3 完成后再发布」，用户明确要求先发布，已记录在变更日志。
4. 错题本案例保持 PAUSED；恢复条件见 `../product-studio-cases/math-mistake-notebook/CASE-STATUS.md`。
5. 硬化建议（lite 模式、输出预算、park case）暂不实施，等更多完整案例的证据。
