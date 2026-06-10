# AE Skills

**面向 AE 原厂芯片工程师的生产级工程技能。**

Skills 将资深工程师在构建软件时所遵循的工作流、质量门禁和最佳实践进行编码封装，使 AI 助手能够在开发的每个阶段一致地遵循这些规范。

---

## 命令

提供 7 个斜杠命令，映射到开发生命周期的各个阶段。每个命令会自动激活相应的技能。

| 你在做什么 | 命令 | 核心原则 |
|-------------------|---------|---------------|
| 定义要构建什么 | `/spec` | 先写规格，再写代码 |
| 规划如何构建 | `/plan` | 小而原子化的任务 |
| 增量式构建 | `/build` | 一次一个切片 |
| 证明它能用 | `/test` | 测试即证明 |
| 合并前审查 | `/review` | 提升代码健康度 |
| 简化代码 | `/code-simplify` | 清晰优于聪明 |
| 发布到生产环境 | `/ship` | 越快越安全 |

技能也会根据你正在做的事情自动激活 — 设计 API 会触发 `api-and-interface-design`，构建 UI 会触发 `frontend-ui-engineering`，以此类推。

---

## 快速开始

<details>
<summary><b>Claude Code（推荐）</b></summary>

**通过 Marketplace 安装：**

```
/plugin marketplace add ddddjaak/ae-skills
/plugin install ae-skills@ddddjaak-ae-skills
```

> **遇到 SSH 错误？** Marketplace 通过 SSH 克隆仓库。如果你没有在 GitHub 上设置 SSH 密钥，请先[添加 SSH 密钥](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)，或使用完整的 HTTPS URL 强制走 HTTPS 克隆：
> ```bash
> /plugin marketplace add https://github.com/ddddjaak/ae-skills.git
> /plugin install ae-skills@ddddjaak-ae-skills
> ```

**本地 / 开发环境：**

```bash
git clone https://github.com/ddddjaak/ae-skills.git
claude --plugin-dir /path/to/ae-skills
```

</details>

<details>
<summary><b>Cursor</b></summary>

将任意 `SKILL.md` 复制到 `.cursor/rules/` 目录下，或引用整个 `skills/` 目录。详见 [docs/cursor-setup.md](docs/cursor-setup.md)。

</details>

<details>
<summary><b>Gemini CLI</b></summary>

以原生技能方式安装，实现自动发现；或添加到 `GEMINI.md` 中以获得持久上下文。详见 [docs/gemini-cli-setup.md](docs/gemini-cli-setup.md)。

**从仓库安装：**

```bash
gemini skills install https://github.com/ddddjaak/ae-skills.git --path skills
```

**从本地克隆安装：**

```bash
gemini skills install ./ae-skills/skills/
```

</details>

<details>
<summary><b>Windsurf</b></summary>

将技能内容添加到你的 Windsurf 规则配置中。详见 [docs/windsurf-setup.md](docs/windsurf-setup.md)。

</details>

<details>
<summary><b>OpenCode</b></summary>

通过 AGENTS.md 和 `skill` 工具使用基于 agent 驱动的技能执行模式。

详见 [docs/opencode-setup.md](docs/opencode-setup.md)。

</details>

<details>
<summary><b>GitHub Copilot</b></summary>

将 `agents/` 中的 agent 定义用作 Copilot 角色，并将技能内容放入 `.github/copilot-instructions.md`。详见 [docs/copilot-setup.md](docs/copilot-setup.md)。

</details>

<details>
  <summary><b>Kiro IDE & CLI</b></summary>
  Kiro 的技能存放在 ".kiro/skills/" 下，可配置在项目级别或全局级别。Kiro 也支持 Agents.md。详见 Kiro 文档：https://kiro.dev/docs/skills/
</details>

<details>
<summary><b>Codex / 其他 Agent</b></summary>

技能是纯 Markdown 格式 — 可以与任何接受系统提示或指令文件的 agent 配合使用。详见 [docs/getting-started.md](docs/getting-started.md)。

</details>



---

## 全部 23 个技能

上述命令是入口点。本包包含 23 个技能 — 22 个生命周期技能加 1 个 `using-ae-skills` 元技能。每个技能都是一个结构化的工作流，包含步骤、验证门禁和反合理化表。你也可以直接引用任何技能。

### 元技能 - 发现该用哪个技能

| 技能 | 功能 | 使用场景 |
|-------|-------------|----------|
| [using-ae-skills](skills/using-ae-skills/SKILL.md) | 将任务映射到正确的技能工作流，并定义共享操作规则 | 开始一个会话，或不确定该用哪个技能时 |

### 定义 - 明确要构建什么

| 技能 | 功能 | 使用场景 |
|-------|-------------|----------|
| [interview-me](skills/interview-me/SKILL.md) | 一次一个问题地访谈，挖掘用户真正想要的东西，而非他们以为想要的，直到达到约 95% 的置信度 | 需求描述不够明确，或用户说 "interview me" / "grill me" |
| [idea-refine](skills/idea-refine/SKILL.md) | 结构化的发散/收敛思维，将模糊的想法转化为具体的方案 | 有一个需要探索的粗略概念 |
| [spec-driven-development](skills/spec-driven-development/SKILL.md) | 在写任何代码之前，撰写涵盖目标、命令、结构、代码风格、测试和边界的 PRD | 开始一个新项目、新功能或重大变更 |

### 规划 - 拆解任务

| 技能 | 功能 | 使用场景 |
|-------|-------------|----------|
| [planning-and-task-breakdown](skills/planning-and-task-breakdown/SKILL.md) | 将规格分解为小而可验证的任务，包含验收标准和依赖排序 | 已有一份规格，需要可实施的单元 |

### 构建 - 编写代码

| 技能 | 功能 | 使用场景 |
|-------|-------------|----------|
| [incremental-implementation](skills/incremental-implementation/SKILL.md) | 薄垂直切片 — 实现、测试、验证、提交。功能开关、安全默认值、易于回滚的变更 | 任何涉及多个文件的变更 |
| [test-driven-development](skills/test-driven-development/SKILL.md) | 红-绿-重构，测试金字塔（80/15/5），测试规模，DAMP 优于 DRY，Beyonce 法则，浏览器测试 | 实现逻辑、修复 bug 或变更行为 |
| [context-engineering](skills/context-engineering/SKILL.md) | 在正确的时间向 agent 提供正确的信息 — 规则文件、上下文打包、MCP 集成 | 开始一个会话、切换任务，或输出质量下降时 |
| [source-driven-development](skills/source-driven-development/SKILL.md) | 将每个框架决策建立在官方文档之上 — 验证、引用来源、标记未经验证的内容 | 希望为任何框架或库生成权威的、有来源引用的代码 |
| [doubt-driven-development](skills/doubt-driven-development/SKILL.md) | 运行中对每个非平凡决策进行对抗式全新上下文审查 — CLAIM → EXTRACT → DOUBT → RECONCILE → STOP，可选经用户授权的跨模型升级 | 高风险场景（生产环境、安全、不可逆操作），在不熟悉的代码中工作，或一个自信的输出现在验证比以后调试更划算 |
| [frontend-ui-engineering](skills/frontend-ui-engineering/SKILL.md) | 组件架构、设计系统、状态管理、响应式设计、WCAG 2.1 AA 无障碍 | 构建或修改用户界面 |
| [api-and-interface-design](skills/api-and-interface-design/SKILL.md) | 契约优先设计、Hyrum 定律、单版本规则、错误语义、边界验证 | 设计 API、模块边界或公共接口 |

### 验证 - 证明它能用

| 技能 | 功能 | 使用场景 |
|-------|-------------|----------|
| [browser-testing-with-devtools](skills/browser-testing-with-devtools/SKILL.md) | Chrome DevTools MCP 获取实时运行时数据 — DOM 检查、控制台日志、网络追踪、性能分析 | 构建或调试任何在浏览器中运行的内容 |
| [debugging-and-error-recovery](skills/debugging-and-error-recovery/SKILL.md) | 五步排查法：复现、定位、归约、修复、防护。停线规则，安全回退 | 测试失败、构建中断或行为异常 |

### 审查 - 合并前的质量门禁

| 技能 | 功能 | 使用场景 |
|-------|-------------|----------|
| [code-review-and-quality](skills/code-review-and-quality/SKILL.md) | 五轴审查、变更规模（约 100 行）、严重性标签（Nit/Optional/FYI）、审查速度规范、拆分策略 | 合并任何变更之前 |
| [code-simplification](skills/code-simplification/SKILL.md) | Chesterton 栅栏、500 行规则，在保持精确行为的同时降低复杂度 | 代码能用，但比应有的更难读或更难维护 |
| [security-and-hardening](skills/security-and-hardening/SKILL.md) | OWASP Top 10 防护、认证模式、密钥管理、依赖审计、三级边界系统 | 处理用户输入、认证、数据存储或外部集成 |
| [performance-optimization](skills/performance-optimization/SKILL.md) | 先测量再优化 — Core Web Vitals 目标、性能分析流程、打包分析、反模式检测 | 存在性能要求，或怀疑性能退化 |

### 发布 - 自信地部署

| 技能 | 功能 | 使用场景 |
|-------|-------------|----------|
| [git-workflow-and-versioning](skills/git-workflow-and-versioning/SKILL.md) | 主干开发、原子提交、变更规模（约 100 行）、提交作为保存点模式 | 进行任何代码变更（始终适用） |
| [ci-cd-and-automation](skills/ci-cd-and-automation/SKILL.md) | Shift Left、越快速越安全、功能开关、质量门禁流水线、故障反馈循环 | 设置或修改构建和部署流水线 |
| [deprecation-and-migration](skills/deprecation-and-migration/SKILL.md) | 代码即负债思维、强制 vs 建议弃用、迁移模式、僵尸代码清除 | 移除旧系统、迁移用户或下线功能 |
| [documentation-and-adrs](skills/documentation-and-adrs/SKILL.md) | 架构决策记录、API 文档、内联文档标准 — 记录*为什么* | 做架构决策、变更 API 或发布功能 |
| [shipping-and-launch](skills/shipping-and-launch/SKILL.md) | 发布前检查清单、功能开关生命周期、分阶段推出、回滚流程、监控设置 | 准备部署到生产环境 |

---

## Agent 角色

用于针对性审查的预配置专业角色：

| Agent | 角色 | 视角 |
|-------|------|-------------|
| [code-reviewer](agents/code-reviewer.md) | 高级 Staff 工程师 | 五轴代码审查，以 "staff 工程师会批准吗？" 为标准 |
| [test-engineer](agents/test-engineer.md) | QA 专家 | 测试策略、覆盖率分析、Prove-It 模式 |
| [security-auditor](agents/security-auditor.md) | 安全工程师 | 漏洞检测、威胁建模、OWASP 评估 |

---

## 参考检查清单

技能在需要时引用的快速参考材料：

| 参考 | 涵盖内容 |
|-----------|--------|
| [testing-patterns.md](references/testing-patterns.md) | 测试结构、命名、Mock、React/API/E2E 示例、反模式 |
| [security-checklist.md](references/security-checklist.md) | 提交前检查、认证、输入验证、Headers、CORS、OWASP Top 10 |
| [performance-checklist.md](references/performance-checklist.md) | Core Web Vitals 目标、前端/后端检查清单、测量命令 |
| [accessibility-checklist.md](references/accessibility-checklist.md) | 键盘导航、屏幕阅读器、视觉设计、ARIA、测试工具 |

---

## 技能的工作原理

每个技能都遵循一致的结构：

```
┌─────────────────────────────────────────────────┐
│  SKILL.md                                       │
│                                                 │
│  ┌─ 前置元数据 ──────────────────────────────┐  │
│  │ name: 小写连字符命名                      │  │
│  │ description: 引导 agent 完成 [任务]。     │  │
│  │              使用场景：…                  │  │
│  └───────────────────────────────────────────┘  │
│  概览             → 这个技能做什么              │
│  使用场景         → 触发条件                    │
│  流程             → 逐步工作流                  │
│  常见合理化借口   → 借口 + 反驳                 │
│  红旗信号         → 出问题的迹象                │
│  验证             → 证据要求                    │
└─────────────────────────────────────────────────┘
```

**核心设计选择：**

- **是流程，不是散文。** 技能是 agent 遵循的工作流，不是让他们阅读的参考文档。每个技能都有步骤、检查点和退出标准。
- **反合理化。** 每个技能都包含一个常见借口表，列出 agent 用来跳过步骤的借口（例如 "我之后再补测试"），并附有文档化的反驳。
- **验证不容妥协。** 每个技能都以证据要求结尾 — 测试通过、构建输出、运行时数据。"看起来没问题" 永远不够。
- **渐进式披露。** `SKILL.md` 是入口点。支撑性参考材料仅在需要时加载，最大限度地减少 token 消耗。

---

## 项目结构

```
ae-skills/
├── skills/                            # 23 个技能（22 个生命周期 + 1 个元技能）
│   ├── interview-me/                  #   定义
│   ├── idea-refine/                   #   定义
│   ├── spec-driven-development/       #   定义
│   ├── planning-and-task-breakdown/   #   规划
│   ├── incremental-implementation/    #   构建
│   ├── context-engineering/           #   构建
│   ├── source-driven-development/     #   构建
│   ├── doubt-driven-development/      #   构建
│   ├── frontend-ui-engineering/       #   构建
│   ├── test-driven-development/       #   构建
│   ├── api-and-interface-design/      #   构建
│   ├── browser-testing-with-devtools/ #   验证
│   ├── debugging-and-error-recovery/  #   验证
│   ├── code-review-and-quality/       #   审查
│   ├── code-simplification/          #   审查
│   ├── security-and-hardening/        #   审查
│   ├── performance-optimization/      #   审查
│   ├── git-workflow-and-versioning/   #   发布
│   ├── ci-cd-and-automation/          #   发布
│   ├── deprecation-and-migration/     #   发布
│   ├── documentation-and-adrs/        #   发布
│   ├── shipping-and-launch/           #   发布
│   └── using-ae-skills/            #   元技能：如何使用本包
├── agents/                            # 3 个专业角色
├── references/                        # 4 个补充检查清单
├── hooks/                             # 会话生命周期钩子
├── .claude/commands/                  # 7 个斜杠命令（Claude Code）
├── .gemini/commands/                  # 7 个斜杠命令（Gemini CLI）
└── docs/                              # 各工具的设置指南
```

---

## 为什么需要 AE Skills？

AI 编程助手默认走最短路径 — 这往往意味着跳过规格、测试、安全审查以及让软件可靠的工程实践。AE Skills 为 agent 提供了结构化的工作流，强制贯彻资深工程师在生产代码中所秉持的规范。

每个技能都编码了来之不易的工程判断：*何时*写规格、*测什么*、*如何审查*以及*何时发布*。这些不是泛泛的提示词 — 它们是那种有见地的、以流程为导向的工作流，能够区分生产质量的工作和原型质量的工作。

---

## 贡献

技能应该 **具体**（可操作的步骤，而非模糊的建议）、**可验证**（明确的退出标准和证据要求）、**经过实战检验**（基于真实工作流）以及 **精简**（只包含引导 agent 所需的内容）。

详见 [docs/skill-anatomy.md](docs/skill-anatomy.md) 了解格式规范，以及 [CONTRIBUTING.md](CONTRIBUTING.md) 了解贡献指南。

---

## 许可证

MIT — 在你的项目、团队和工具中自由使用这些技能。
