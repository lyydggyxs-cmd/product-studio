# Product Studio · 团队架构

> 详细设计文档。决策与实施进度见 `ROADMAP.md`。
> 一句话：**岗位是产品，团队是组合，上下文是 API。**

---

## 1. 为什么是工作室，不是流水线

流水线假设：产品工作可以被切成 8 个阶段，每个阶段做完交棒，上一阶段的输出是下一阶段的输入。

工作室假设：产品工作是**一群人围绕同一面墙上的工件，反复看、反复改**。每个人有自己的专业判断，也都能看到别人写了什么。

两者的差别不在「有没有分工」，而在：

| | 流水线 | 工作室 |
|---|---|---|
| 上下文 | 交接时传全文 | 共享工作区，按需读 |
| 反馈 | 上一站→下一站 | 任意两岗可以互看、互怼 |
| 节奏 | 串行 | 嵌套循环，可并行 |
| 质量 | 每站质量门 | 持续 critique |
| 单岗 | 难以独立调用 | 可独立调用 |
| 失败模式 | 交接丢失、上下文爆炸 | 需要强 schema 和版本管理 |

**结论**：工作室更适合 AI，因为每个岗位可以有独立上下文、独立工具、独立能力包；但前提是**共享上下文层**必须存在。

---

## 2. 三层结构

```
┌──────────────────────────────────────────────────────────────┐
│                         STUDIO LEAD                          │
│   上下文路由 · 检查点 · 漂移检测 · 决策记录 · 不干专业活       │
└───────────────────────────┬──────────────────────────────────┘
                            │
        ┌───────────────────┼───────────────────┐
        │                   │                   │
   ┌────▼─────┐        ┌────▼─────┐        ┌────▼─────┐
   │  LOOP 1  │        │  LOOP 2  │        │  LOOP 3  │
   │ 发现与定义 │◄──────►│ 定义与结构 │◄──────►│ 设计与验证 │
   └────┬─────┘        └────┬─────┘        └────┬─────┘
        │                   │                   │
  Research ⇄ Definer   Requirements ⇄ Architect  Prototype ⇄ UI
        │                   │                   │
        └───────────┬───────┴───────┬───────────┘
                    │               │
              ┌─────▼─────┐   ┌─────▼──────┐
              │ Design    │   │ Validation │
              │ Critic    │   │ Researcher │
              └─────┬─────┘   └─────┬──────┘
                    └───────┬───────┘
                            │
              ┌─────────────▼──────────────────────────────┐
              │              CONTEXT BUS                   │
              │ brief · evidence · bet · requirements      │
              │ IA · prototypes · design system · PRD      │
              │ decision log · open questions              │
              └────────────────────────────────────────────┘
```

---

## 3. 岗位

### 3.1 Phase 1 核心岗位

| 岗位 | 一句话 | 不做什么 |
|---|---|---|
| **Studio Lead** | 管上下文、节奏、检查点、漂移 | 不做调研、不写 PRD、不做设计 |
| **Research Analyst** | 找证据，区分事实/推断/猜测 | 不替产品做取舍 |
| **Product Definer** | 把证据变成可证伪的赌注和活 PRD | 不做 IA、不做视觉 |
| **Product Architect** | 把赌注变成可验证的结构（IA/flows/states） | 不做视觉、不做技术架构 |
| **UI Designer** | 把结构变成产品 UI：设计系统、高保真界面、可点击原型 | 不做品牌识别、不做营销页、不写生产代码 |
| **Design Critic** | 找问题、分级、给证据，不给方案 | 不审美裁判、不改稿 |

### 3.2 Phase 2 专业岗位（已加入）

| 岗位 | 一句话 | 与 Phase 1 的关系 |
|---|---|---|
| **Requirements Analyst** | 把赌注拆成 Job Stories / AC / 边界条件 | 从 Product Definer 拆出；Definer 不再兼需求 |
| **Prototype Designer** | 用最低成本让赌注可被否定 | 与 UI Designer 分工：原型验结构，UI 做视觉 |
| **Validation Researcher** | 拿原型找真人测，区分价值/可用性/结构问题 | 接 Loop 3 的验证；问题按类型路由 |

### 3.3 Phase 3 可选岗位

| 岗位 | 一句话 |
|---|---|
| **Content Designer** | UX writing、语气、微文案 |
| **Commercial Strategist** | 商业模式、定价、单位经济 |

---

## 4. 上下文总线

### 4.1 工件表

| 工件 | 所有者 | 主要读者 | 更新规则 |
|---|---|---|---|
| `brief.md` | Studio Lead | 全员 | 项目开始；方向大改时 |
| `evidence-base.md` | Research | 全员 | 每次研究发现后追加 |
| `opportunity-map.md` | Research + Definer | Requirements、Architect | 每周 |
| `bet-book.md` | Product Definer | 全员 | 赌注变化时 |
| `requirements.md` | Requirements Analyst | Architect、Prototype、UI、Validation | 需求变化时 |
| `ia-flows.md` | Product Architect | Prototype、UI、Critic | 结构变化时 |
| `prd.md` | Product Definer | 全员 | 活文档，版本化 |
| `prototypes/` | Prototype Designer | UI、Critic、Validation | 每轮新增版本 |
| `design-system.md` | UI Designer | Critic、Prototype | 设计系统变化时 |
| `decision-log.md` | Studio Lead（唯一写入者；其他岗位只在产出里写「建议决策 / 需要裁决」） | 全员 | 每个决策追加，不删除 |
| `checkpoints.md` | Studio Lead | 全员 | 每个岗位交付后、每个循环出口追加 |
| `open-questions.md` | Studio Lead | 全员 | 每周 |
| `critique.md` | Design Critic | UI、Definer、Architect | 每次评审 |

### 4.2 传指针，不传全文

**错误做法**：
```
把 A1 的 3 万字报告全文贴进 A2 的 prompt
```

**正确做法**：
```
handoff:
  from: research-analyst
  to: product-definer
  task: "判断哪个因果假说最强"
  read:
    - file: evidence-base.md
      sections: ["E12-E18", "缺口"]
    - file: opportunity-map.md
      sections: ["矛盾区"]
  question: "哪条因果链有区分性证据？如果没有，缺什么？"
  expected_output: "bet-book.md 的候选赌注 2-3 个"
```

### 4.3 工件契约

- 核心契约有 **schema**（见 `schemas/`）：`brief`、`evidence`、`bet`、`decision`、`handoff`；其余工件由 `templates/` 约束。
- 每个结论带 **置信度**（✅/⚠️/🔮）。
- 每个决策带 **理由 + 替代方案 + 重新评估条件**。
- 版本化：不覆盖旧版本，追加新版本号。

---

## 5. 三个嵌套循环

### Loop 1：证据 ↔ 定义

```
Research 收集 → Definer 框定赌注 → Research 找区分性证据 → Definer 修正
```

**出口标准**：
- 赌注可证伪（有成功信号和 kill 信号）
- 关键不确定性排了序
- 至少一条区分性证据计划

**反哺**：
- Research 可以用反证推翻 Definer 的赌注
- Definer 可以要求 Research 去找能区分两个假说的证据

### Loop 2：定义 ↔ 需求 ↔ 结构

```
Definer 给赌注 → Requirements 拆 Job Stories / AC / 边界
                      ↓
              Architect 做 IA/flows/states
                      ↓
       ↑──────── 结构矛盾 / 需求不可行 ────────┘
```

**出口标准**：
- 每个核心 Job 有完整用户流
- 每条 P0 需求有 AC 且能追溯到赌注
- 每个一级界面有状态矩阵
- 关键 IA 假设有验证工具

**反哺**：
- Requirements 发现「这个赌注拆不出可验证的需求」→ 回 Definer
- Architect 发现「结构上行不通」→ 回 Requirements / Definer
- Definer 重新划范围 → Requirements 重写需求 → Architect 重做结构

### Loop 3：原型 ↔ 设计 ↔ 验证

```
Prototype Designer 做最低成本原型 → 验结构/赌注
       ↓
UI Designer 做设计系统 + 高保真 UI
       ↓
Design Critic 审 → 问题分级
       ↓
Validation Researcher 找真人测
       ↓
价值问题 → Definer / 结构问题 → Architect
交互视觉 → Prototype / UI / 需求不可测 → Requirements
```

**出口标准**：
- 原型验证过核心结构/赌注
- UI 设计意图与 bet/IA 对齐
- 关键状态覆盖完整
- Critic 的 🔴 问题清零
- 至少一轮真人验证，且判定线先于数据

---

## 6. 调用模式

| 模式 | 入口 | 行为 |
|---|---|---|
| **整队 Sprint** | `/product-studio:team` | Studio Lead 跑一个或多个 Loop，带检查点 |
| **配对 Pair** | `/product-studio:team pair research+definer` | 两个岗位围绕一个具体问题协作；如 `requirements+architect`、`prototype+ui`、`ui+critic`、`validation+definer` |
| **单岗 Role** | `/product-studio:team role ui-designer` | 只叫一个岗位做 bounded task |
| **评审 Review** | `/product-studio:team review` | Critic + Lead 审已有工件 |

**单岗模式的关键**：每个岗位必须能独立读取上下文总线、独立产出、独立交付——不依赖整条流水线先跑完。

---

## 7. 每个岗位的能力包

每个岗位文件必须包含：

1. **身份**：它是什么、不是什么
2. **专业能力**：知识、方法、工具
3. **标准**：什么算顶级输出
4. **品味**（设计岗）：参考库、taste vector、人类检查点
5. **反模式**：最容易犯的错
6. **输入契约**：读什么、读到什么程度
7. **工作流**：步骤 + 退出标准
8. **输出契约**：写什么文件、什么 schema、谁消费
9. **接口**：向谁反哺、接收谁的反哺
10. **自检**：交付前逐条检查

---

## 8. 和 A0–A7 的差异

| 维度 | A0–A7 | Product Studio |
|---|---|---|
| 拓扑 | 8 站串行 | 3 个嵌套循环 |
| 上下文 | handoff prompt 传全文 | 共享工作区 + 指针 |
| 角色 | 一个 Agent 一个阶段 | 一个岗位一个专业能力 |
| 需求 | A2 兼 | Phase 1 Definer 兼；Phase 2 独立 |
| UI | A6 写 React | UI Designer 只做设计 |
| PRD | 跨阶段版本链 | 活文档，由赌注书 + 决策日志 + 需求包合成 |
| 质量 | 每站质量门 | 持续 critique + kill 标准 |
| 单岗 | 难独立 | 可独立调用 |
| 开发 | 有交接包 | 明确不做 |

---

## 9. 范围边界

**做**：
- 调研、需求分析、产品定义、IA/结构、原型、PRD、产品 UI 设计

**不做**：
- 生产代码、后端、数据库、部署、运维
- 品牌识别、logo、营销页（UI Designer 只做产品 UI）
- 商业模式/定价（Phase 3 可选 Commercial Strategist，不在本期）
- 上线后增长/留存测量（不在本期）
