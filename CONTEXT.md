# Product Studio · 共享上下文

> 所有岗位的公共语言和路径约定。开工前读一遍。

## 路径约定

| 位置 | 路径 | 说明 |
|---|---|---|
| 插件根目录 | `product-studio/` | 本仓库；从 `skills/team/SKILL.md` 出发是 `../../` |
| 工作区 | `./product/`（当前用户项目） | 所有工件写这里，**不写进插件目录** |
| 模板 | 插件根目录 `templates/` | 从工作区看是插件路径；由 Studio Lead 在 handoff 中传绝对/相对路径 |
| Schema | 插件根目录 `schemas/` | 同上 |
| 岗位 | 插件根目录 `agents/` | Claude Code subagent |

## 术语

| 术语 | 定义 |
|---|---|
| **Evidence / 证据** | 一条可追溯的观察或数据，带来源和置信度 |
| **✅ verified** | 直接证据：用户行为/原话、同行评审、多个独立来源 |
| **⚠️ assumed** | 间接证据：类似场景、理论推理、小样本、单一来源 |
| **🔮 guess** | 未经实证的推断；必须标出来 |
| **Bet / 赌注** | 一个可证伪的产品假设：如果……那么……因为…… |
| **Kill signal** | 观察到什么就停止/转向；必须具体、可观察 |
| **Anti-goal** | 明确不做的范围，带理由和恢复条件 |
| **Handoff** | 岗位之间的交接：指针 + 问题 + 预期产出 |
| **Loop 1** | 证据 ↔ 定义（Research ⇄ Definer） |
| **Loop 2** | 定义 ↔ 结构（Definer ⇄ Architect） |
| **Loop 3** | 原型 ↔ 设计 ↔ 验证（Prototype ⇄ UI ⇄ Critic ⇄ Validation） |
| **Context bus** | 共享工作区里的工件集合；岗位按需读，不传全文 |

## 工件所有权

| 工件 | Owner | 读者 |
|---|---|---|
| `brief.md` | Studio Lead | 全员 |
| `evidence-base.md` | Research Analyst | 全员 |
| `opportunity-map.md` | Research Analyst + Product Definer | Architect、UI |
| `bet-book.md` | Product Definer | 全员 |
| `requirements.md` | Requirements Analyst | Architect、Prototype、UI、Validation |
| `ia-flows.md` | Product Architect | Prototype、UI、Critic |
| `prd.md` | Product Definer | 全员 |
| `prototypes/` | Prototype Designer | UI、Critic、Validation |
| `design-system.md` | UI Designer | Critic |
| `validation-plan.md` / `validation-report.md` | Validation Researcher | 全员 |
| `critique.md` | Design Critic | UI、Definer、Architect |
| `decision-log.md` | Studio Lead + 全员 | 全员 |
| `open-questions.md` | Studio Lead | 全员 |

## 硬约束

1. 不做开发。
2. 岗位之间传指针，不传全文。
3. 每个工件有 schema；每个结论带 ✅⚠️🔮。
4. PRD 是活文档。
5. Studio Lead 不干专业活。

## 反模式

- 把整篇 evidence-base 粘进下一个岗位的 prompt
- 把 🔮 写成 ✅
- 赌注没有 kill 信号
- UI 设计里出现品牌/营销内容
- Critic 给方案
- 为了"完整"而填充内容
