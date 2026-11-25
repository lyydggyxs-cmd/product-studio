# UI Designer · Eval

> 目的：验证 UI Designer 的能力包是否真的把「已验证的 IA + 赌注」变成了**有观点、可使用、可评审、视觉顶级**的个人工具界面，而不是把结构涂成通用模板。

## 当前 case

- `case-01/`：个人习惯工具（习惯养成）。输入来自四维模型与 MVP 设计约束；视觉方向 Apple 原生精致；要求参考板 + 视觉锚点 + 数据可视化。
- `_archive/cooking-case/`：旧的周末做饭 case，已废弃。保留作为失败样本——它证明了「只有纪律、没有参考板和视觉资产 = 带令牌的线框」。运行产出在 `product-studio-evals/ui-designer-case-00-cooking/`。

## 怎么跑

1. 建一个空工作区，复制 `case-01/` 的输入：
   - `brief.md`（任务说明）
   - `evidence-base.md`（Research Analyst）
   - `bet-book.md` + `prd.md`（Product Definer）
   - `requirements.md`（Requirements Analyst；必须包含，否则 R05 / C1–C3 无法被设计处理）
   - `ia-flows.md` + `validation-toolkit.md`（Product Architect）
2. 用 `product-studio:ui-designer` 执行，给它：
   - 60–75 分钟
   - 不提供答案，只提供输入
   - 允许读 `references/ui-designer/` 四件套 + `reference-board/`
3. 产出：
   - `reference-board.md`（参考拆解 + 本产品视觉语法）
   - `design-system.md`（意图 + 令牌 + 组件 + 视觉资产 + 页面清单 + 需人眼）
   - `ui-spec.md`（每页结构 / 状态 / 交互 / 文案 / 响应式）
   - `screens/`（≥4 屏高保真 HTML/CSS，设计件非生产代码）
   - `design-rationale.md`（关键决策理由 + 需人眼确认项）
4. 用 `../rubric.md` + 本 case 的 `rubric.md` 评分。
5. 对照 `baseline.md`，记录「能力包让它多做了什么」。

## 评分

- 通用 8 维，0–4 分，满分 32。
- 门控优先：
  - 非默认性与设计观点 ≤1 → 退回
  - 状态覆盖 =0 → 退回
  - 信心诚实与人类检查点 ≤1 → 退回
- **视觉表现力门**（独立 pass/fail）：
  - 核心屏没有任何视觉锚点 → FAIL
  - emoji 当图标 / 资产风格不统一 → FAIL
  - 所有屏都是同一种垂直堆叠 → FAIL
- Case-specific checks 见 `case-01/rubric.md`。

## 回归

每次修改 `agents/ui-designer.md` 或 `references/ui-designer/`：

1. 重跑 case-01。
2. 记录总分、门控、视觉表现力门、case-specific 通过项。
3. 如果分数下降，回滚或修正。
4. 不比较不同模型 / 不同输入条件的绝对分；只比较同一条件下的前后变化。

## 跨岗输入链（2026-11-18 发现，2026-11-25 修复并验证）

- 本 case 建于 Requirements Analyst 之前，首轮输入**不含 `requirements.md`**。
- Design Critic 用后来的 requirements 判了两条阻断：F1（R05 暂停路径不可达，AC5.1–5.2 无法执行）、F2（C1/C2/C3 未决冲突被设计写死）。这不是 UI Designer 的能力问题，是 eval 输入链不完整。
- **2026-11-25 修复**：`case-01/brief.md` 加入 `requirements.md`，并明确要求处理 R05 与 C1–C3；重跑 r2。
- **r2 独立评审结果**：29/32，门控全过，视觉表现力门 PASS，case-specific **8/8**，总判断**可作模板（附 2 项小修）**。
  - F1：**关闭**。R05 入口 → 暂停 sheet → 暂停后今天 → 已暂停列表 → 恢复，点击流实测通过；暂停保存失败可执行。
  - F2：**关闭**。C1–C3 默认 A/A/A、开关可切、裁决后重做表齐全；默认屏无预选档。
  - 4 项回归（S06→S10 断链、暂停保存失败未渲染、离线态丢失、暗色令牌丢失）复核 **4/4 CLOSED**。
  - 残余（spec-only，不阻断）：密度切换、回顾空/加载/失败、极端数据、暗色全量屏；chip 选中态 `✓` 仍是文字；review 周切换仅视觉。
- **分数口径**：首轮 30/32 与 r2 29/32 **不可横比**——输入条件不同，且 r2 按更严格的「非快乐路径需渲染证据」口径评分。
- 运行产物保存在本地 `product-studio-evals/ui-designer-habit-case-01-r2/`（不随插件仓库发布）。

## 注意

- **不要给期望答案**。UI Designer 必须自己选参考、拆参考、决定视觉方向。
- 产出可以有不同的视觉方向；评分看的是「参考板、意图可追溯、系统先于页面、非默认性、视觉锚点、状态覆盖、密度、工艺、信心诚实、交接」，不是「和某个参考设计一致」。
- 参考板是采样来源，不是拼贴；不抄品牌资产。
- 如果证据不足以确定视觉方向，**写「方向待验证，先做 2–3 个方向快照对比」也是合格输出**；假装确定才是失败。
- 允许 HTML/CSS 设计件；禁止生产代码（React / 后端 / 部署）。
- n=1 个 case 是方向性检查，不是统计证明。
