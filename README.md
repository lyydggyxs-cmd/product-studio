# Product Studio

一个由专业岗位组成的 AI 产品工作室：从调研到产品 UI 设计，共享同一套上下文，支持整队、配对、单岗、评审四种调用方式。

> **范围**：调研 → 需求分析 → 产品定义 → IA/结构 → 原型 → PRD → 产品 UI 设计。
> **不做**：开发、后端、部署、品牌识别、营销页。
> **状态**：Design-stage（v0.1.0）。先跑通设计链路，不承诺产品成功。

## 安装

这个仓库同时是 Claude Code marketplace。

从 GitHub 安装：

```bash
/plugin marketplace add lyydggyxs-cmd/product-studio
/plugin install product-studio@product-studio-marketplace
```

本地开发（不安装，直接加载；在仓库根目录执行）：

```bash
claude --plugin-dir .
```

验证清单（在仓库根目录执行）：

```bash
claude plugin validate .
```

## 使用

```text
/product-studio:team                     # 整队 Sprint
/product-studio:team pair research+definer   # 两岗配对
/product-studio:team role ui-designer        # 单岗调用
/product-studio:team review                  # 评审已有工件
```

> 具体路由以 `skills/team/SKILL.md` 为准。

## 先读这三个文件

| 文件 | 作用 |
|---|---|
| [`ROADMAP.md`](./ROADMAP.md) | **唯一事实源**：已确认决策、硬约束、Phase 1/2/3、当前进度 |
| [`ARCHITECTURE.md`](./ARCHITECTURE.md) | 团队架构：岗位、上下文总线、三个嵌套循环、调用模式 |
| [`EVALS.md`](./EVALS.md) | 8 个岗位的 eval 回归基线：分数、门控、case-specific、可复跑流程、已知残余 |

## 当前阵容

```
Studio Lead（skills/team）
├── Research Analyst
├── Requirements Analyst
├── Product Definer
├── Product Architect
├── Prototype Designer
├── UI Designer（产品 UI）
├── Design Critic
└── Validation Researcher
```

Phase 3：打磨能力包、eval、发布。**3.1 已完成**：Research Analyst 能力包 + 2 个 eval case。**3.2 已完成（8/8）**：8 个岗位能力包全部建成并跑 eval；UI Designer 含参考板与视觉表现力门。**3.5 已完成（流程）**：四种调用模式 + 完整 Sprint Loop 1–3 跑通；Loop 3 真人验证未执行（只出预注册计划），所以流程 ✅ / 产品 ⚠️。**3.3 已完成**：8 岗 eval 回归基线登记在 [`EVALS.md`](./EVALS.md)。下一步：3.4 可选岗位（Content Designer / Commercial Strategist）。

## 目录

```
.claude-plugin/   插件清单 + marketplace
skills/team/      Studio Lead 入口（主线程 skill）
agents/           8 个专业岗位（Claude Code subagent）
schemas/          上下文工件的 JSON Schema
templates/        工件模板
references/       各岗位能力包（Phase 3 填充）
```

## 硬约束

1. 不做开发。
2. 岗位之间传指针，不传全文。
3. 每个工件有 schema，每个结论带置信度。
4. PRD 是活文档。
5. Studio Lead 不干专业活。

详见 `ROADMAP.md` 第 2 节。

## 许可证

MIT。见 `LICENSE`。
