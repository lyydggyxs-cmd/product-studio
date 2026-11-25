# Product Studio · 案例教训

> 案例：`../product-studio-cases/math-mistake-notebook/`（错题本；不在插件仓库内，避免公开个人数据）
> 状态：**PAUSED**（2026-11-13）。不继续跑，保留作为 Studio 的测试样本。
> 这份文件只记录「对 Studio 设计有用的教训」，不记录产品结论。

---

## 一、验证了的设计

1. **证据分级 + 竞争假说有用。** Research 主动找了反证；B1 被削窄，而不是被确认。这正是我们要的。
2. **「一个赌注」规则有用。** 从「故事/游戏让孩子更主动」缩到「新同构故事 + 家长只读不教」，变得可证伪。
3. **双工件结构是 X1 的结构解。** 纸给孩子（零评价）、屏给家长（步骤级证据），不是靠文案消解。
4. **预注册判定线有用。** R1–R7 / K1–K4 写死，堵住「故事输了一定是写得不好」这类事后解释。
5. **Critic 有价值。** 0 阻断、6 重要；抓住了 S 模板化、O 页真实性、A/B 位移、家长卡回应不匹配。
6. **证据变化时停止旧计划。** 孩子的真实错题（`4 = ( ) − 3`）推翻了「退位减」结构；Studio 没有强行继续，这是对的。

---

## 二、暴露的缺口

| # | 缺口 | 表现 | 对 Studio 的修改 |
|---|---|---|---|
| 1 | **没有 lite 模式** | 一个小案例跑了 Research/Definer/Architect/UI/Critic 五个角色，20+ 工件、数千行 | 增加 `lite`：小案例只跑 Research + Definer + Critic |
| 2 | **没有输出预算** | evidence 254 行、validation 583 行、packet spec 863 行 | 每个工件设行数上限，超出就拆或删 |
| 3 | **没有案例生命周期** | 用户改范围时，没有「暂停/归档/恢复」协议 | 增加 `CASE-STATUS.md`：active / paused / archived |
| 4 | **内容设计缺口** | UI Designer 写了故事题；S 六题同一模板换名词 | Phase 2 增加 Content Designer，或给 Architect 增加 content spec 子职责 |
| 5 | **角色边界模糊** | Architect 写了大量实验协议/家长脚本，接近 Definer/Research 的职责 | 明确 RACI：谁写实验协议、谁写家长脚本、谁写报告模板 |
| 6 | **上下文成本高** | 每个 agent 读大量上游文件 | 每个 handoff 附「最小读取集」，禁止默认读全文 |
| 7 | **没有「案例暂停」入口** | 用户说停时，只能临时处理 | Studio Lead 增加「park case」协议：保存状态、写恢复条件、不再自动继续 |

---

## 三、优先修的三件事

1. **Studio Lead 增加 `lite` 模式和 `park case` 协议。**
   - `lite`：Research → Definer → Critic；跳过完整 Architect/UI。
   - `park`：写 `CASE-STATUS.md`，记录停在哪、为什么、恢复需要什么。

2. **给每个工件设输出预算。**
   - evidence ≤120 行
   - validation plan ≤150 行
   - packet/spec ≤200 行
   - critique ≤120 行
   - 超出就拆成附录，不塞进主文件。

3. **补 Content Designer 责任（Phase 2 或 Architect 子职责）。**
   - 谁写故事/题目/界面文案？
   - 内容必须过「数学是解 / 无无关数字 / ≤2 句」三检查。
   - 不能默认让 UI Designer 兼。

---

## 四、一句话

**Studio 的架构是成立的；问题是它太「重」，而且角色边界还不够硬。** 下一轮系统的重点不是加更多岗位，而是加**刹车、预算、边界**。
