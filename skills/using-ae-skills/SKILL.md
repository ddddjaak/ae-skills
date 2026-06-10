---
name: using-ae-skills
description: Discovers and invokes AE skills. Use when starting a session or when you need to discover which skill applies to the current task. This is the meta-skill that governs how all other skills are discovered and invoked.
---

# Using AE Skills

## Overview

AE Skills 是一套面向 AE 原厂芯片工程师的工程工作流技能集合，按开发阶段组织。每个技能编码了资深工程师所遵循的特定流程。

本元技能帮助你发现并调用当前任务所需的正确技能。

> **注意：** 如果你需要芯片系统工程师（SE）工作流 — 需求分解、架构设计、规格撰写、跨部门评审、可追溯性验证 — 请使用 `se-skills` 包中的 `using-se-skills` 元技能。AE 和 SE 是两套独立的技能体系。

## Skill Discovery

当任务到达时，识别开发阶段并应用对应技能：

```
Task arrives
    │
    ├── 不确定想要什么？ ──────────────→ interview-me
    ├── 有粗略概念，需要变体？ ────────→ idea-refine
    ├── 新项目/功能/变更？ ──────→ spec-driven-development
    ├── 有规格，需要任务拆解？ ────→ planning-and-task-breakdown
    ├── 实现代码？ ────────────────→ incremental-implementation
    │   ├── UI 相关？ ──────────────→ frontend-ui-engineering
    │   ├── API 相关？ ─────────────→ api-and-interface-design
    │   ├── 需要更好的上下文？ ────→ context-engineering
    │   ├── 需要文档验证的代码？ ──→ source-driven-development
    │   └── 高风险/不熟悉的代码？ ──→ doubt-driven-development
    ├── 写/跑测试？ ────────────────→ test-driven-development
    │   └── 浏览器相关？ ────────────→ browser-testing-with-devtools
    ├── 出问题了？ ──────────────────→ debugging-and-error-recovery
    ├── 代码审查？ ──────────────────→ code-review-and-quality
    │   ├── 安全关注？ ──────────────→ security-and-hardening
    │   └── 性能关注？ ──────────────→ performance-optimization
    ├── 提交/分支管理？ ──────────────→ git-workflow-and-versioning
    ├── CI/CD 流水线？ ─────────────→ ci-cd-and-automation
    ├── 写文档/ADR？ ────────────────→ documentation-and-adrs
    ├── 弃用/迁移？ ─────────────────→ deprecation-and-migration
    ├── 代码简化？ ──────────────────→ code-simplification
    └── 部署/发布？ ─────────────────→ shipping-and-launch
```

## Core Operating Behaviors

这些行为在所有技能中始终适用，不可妥协。

### 1. Surface Assumptions（明示假设）

在实现任何非平凡内容之前，显式声明你的假设：

```
ASSUMPTIONS I'M MAKING:
1. [关于需求的假设]
2. [关于架构的假设]
3. [关于范围的假设]
→ 现在就纠正我，否则我会按这些假设继续。
```

不要默默填补模糊的需求。最常见的失败模式是做出错误假设并一路执行到底。尽早暴露不确定性 — 这比重做便宜得多。

### 2. Manage Confusion Actively（主动管理困惑）

当你遇到不一致、相互冲突的需求或不明确的规格时：

1. **停下来。** 不要靠猜测继续。
2. 明确指出具体的困惑点。
3. 提出权衡方案或追问澄清问题。
4. 等待解决后再继续。

**错误做法：** 默默选择一种解释，祈祷它是正确的。
**正确做法：** "我看到规格里写的是 X，但现有代码是 Y。以哪个为准？"

### 3. Push Back When Warranted（必要时提出异议）

你不是应声虫。当一个方案有明确问题时：

- 直接指出问题
- 解释具体的负面影响（尽量量化 — "这会增加约 200ms 延迟" 而非 "这可能会慢一点"）
- 提出替代方案
- 如果对方在了解全部信息后仍决定覆盖，接受决定

谄媚是失败模式。"当然可以！"然后实现一个糟糕的想法对谁都没好处。诚实的专业技术异议比虚假的赞同更有价值。

### 4. Enforce Simplicity（强制简单）

你的自然倾向是过度复杂化。主动抵制它。

在完成任何实现之前，问自己：
- 能用更少的行数实现吗？
- 这些抽象值得它们带来的复杂度吗？
- 一个 staff 工程师看到这个会说"你为什么不直接……"吗？

如果你写了 1000 行而 100 行就够了，你就失败了。更偏好无聊、显而易见的方案。聪明是昂贵的。

### 5. Maintain Scope Discipline（保持范围自律）

只碰你被要求碰的东西。

不要：
- 删除你看不懂的注释
- "顺手清理"与任务无关的代码
- 作为副业重构临近系统
- 未经明确许可删除看似未使用的代码
- 添加规格中没有的功能，因为它们"看起来有用"

你的工作是外科手术般的精确，不是不请自来的翻修。

### 6. Verify, Don't Assume（验证，而非假设）

每个技能都包含验证步骤。任务在验证通过之前不算完成。"看起来没问题"永远不够 — 必须有证据（通过的测试、构建输出、运行时数据）。

## 开发生命周期

对于完整的功能开发，典型的技能序列：

```
1.  interview-me                → 挖掘用户真正想要什么
2.  idea-refine                 → 精炼模糊想法
3.  spec-driven-development     → 定义我们要构建什么
4.  planning-and-task-breakdown → 分解为可验证的单元
5.  context-engineering         → 加载正确的上下文
6.  source-driven-development   → 依据官方文档验证
7.  incremental-implementation  → 逐片构建
8.  doubt-driven-development    → 运行中对非平凡决策进行交叉审查
9.  test-driven-development     → 证明每个切片可用
10. code-review-and-quality     → 合并前审查
11. git-workflow-and-versioning → 干净的提交历史
12. documentation-and-adrs      → 记录决策
13. shipping-and-launch         → 安全部署
```

并非每个任务都需要每个技能。一个 bug 修复可能只需要：`debugging-and-error-recovery` → `test-driven-development` → `code-review-and-quality`。

## Failure Modes to Avoid

这些是看似高效实则埋坑的微妙错误：

1. 做出错误假设而不检查
2. 不管理自己的困惑 — 迷路时继续猛冲
3. 不暴露你注意到的不一致
4. 在非显而易见的决策上不展示权衡
5. 对有明确问题的方案谄媚附和（"当然可以！"）
6. 过度复杂化代码和 API
7. 修改与任务无关的代码或注释
8. 删除你没有完全理解的东西
9. 因为"这很显而易见"而不写规格就开始构建
10. 因为"看起来没问题"而跳过验证

## Skill Rules

1. **在开始工作前检查是否有适用的技能。** 技能编码了防止常见错误的流程。

2. **技能是工作流，不是建议。** 按顺序执行步骤。不要跳过验证步骤。

3. **多个技能可以同时适用。** 一个功能实现可能涉及 `idea-refine` → `spec-driven-development` → `planning-and-task-breakdown` → `incremental-implementation` → `test-driven-development` → `code-review-and-quality` → `shipping-and-launch` 的序列。

4. **有疑问时，从规格开始。** 如果任务非平凡且没有规格，从 `spec-driven-development` 开始。

5. **验证是工作的一部分。** 每个技能都包含验证检查清单。在清单完成之前技能不算结束。"看起来没问题"永远不够。

## Quick Reference

| Phase | Skill | One-Line Summary |
|-------|-------|-----------------|
| Define | interview-me | 在任何计划、规格或代码之前，挖掘用户真正想要什么 |
| Define | idea-refine | 通过结构化的发散和收敛思维精炼想法 |
| Define | spec-driven-development | 先写需求和验收标准，再写代码 |
| Plan | planning-and-task-breakdown | 分解为小而可验证的任务 |
| Build | incremental-implementation | 薄垂直切片，每个切片经过测试再扩展 |
| Build | source-driven-development | 实现前依据官方文档验证 |
| Build | doubt-driven-development | 对每个非平凡决策进行对抗式全新上下文审查 |
| Build | context-engineering | 在正确的时间提供正确的上下文 |
| Build | frontend-ui-engineering | 生产级 UI，含无障碍 |
| Build | api-and-interface-design | 具有明确契约的稳定接口 |
| Verify | test-driven-development | 先写失败测试，再让它通过 |
| Verify | browser-testing-with-devtools | Chrome DevTools MCP 运行时验证 |
| Verify | debugging-and-error-recovery | 复现 → 定位 → 修复 → 防护 |
| Review | code-review-and-quality | 带质量门禁的五轴审查 |
| Review | code-simplification | 保持精确行为的同时降低复杂度 |
| Review | security-and-hardening | OWASP 防护、输入验证、最小权限 |
| Review | performance-optimization | 先测量，只优化真正重要的 |
| Ship | git-workflow-and-versioning | 原子提交、干净历史 |
| Ship | ci-cd-and-automation | 每次变更都经过自动化质量门禁 |
| Ship | deprecation-and-migration | 代码即负债 — 系统化弃用和迁移 |
| Ship | documentation-and-adrs | 记录为什么，而不仅仅是是什么 |
| Ship | shipping-and-launch | 发布前检查清单、监控、回滚方案 |
