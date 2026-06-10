# DeepAgents 快速开发入门

> 原创课程文本讲义包 · 版本 v0.1

欢迎来到 **DeepAgents 快速开发入门** 课程！本课程从零带你掌握生产级 AI Agent 工程开发。

## 学习路线

### 基础篇（01–07）

| 讲次 | 主题 |
|------|------|
| [00｜课程总览](00-课程总览.md) | 课程目标与学习路线 |
| [01｜Agent Harness 与第一段代码](01-Agent-Harness-与第一段代码.md) | DeepAgents 核心概念 |
| [02｜DeepAgents / LangChain / LangGraph 关系](02-DeepAgents-LangChain-LangGraph关系.md) | 框架对比与选型 |
| [03｜create_deep_agent 最小 Demo](03-create-deep-agent-最小可运行Demo.md) | 最小可运行示例 |
| [04｜默认工具与上下文工程](04-默认工具与上下文工程.md) | 工具链与上下文管理 |
| [05｜Backend 后端](05-Backend后端.md) | 后端模型接入 |
| [06｜文件系统上下文](06-文件系统上下文.md) | 文件系统交互 |
| [07｜Sandbox 沙箱](07-Sandbox沙箱.md) | 安全沙箱机制 |

### 进阶篇（08–15）

| 讲次 | 主题 |
|------|------|
| [08｜自定义 Tool 开发](08-自定义Tool开发.md) | 工具开发实战 |
| [09｜Memory 记忆](09-Memory记忆.md) | 记忆与状态管理 |
| [10｜Subagent 子智能体](10-Subagent子智能体.md) | 多 Agent 协作 |
| [11｜Prompt / Instructions 设计](11-Prompt-Instructions设计.md) | 提示词工程 |
| [12｜Human-in-the-loop 审批](12-Human-in-the-loop审批.md) | 人机协作 |
| [13｜权限模型与安全边界](13-权限模型与安全边界.md) | 安全架构 |
| [14｜Trace / Debug / Eval](14-Trace-Debug-Eval.md) | 调试与评估 |
| [15｜部署与成本控制](15-部署与成本控制.md) | 生产部署 |

### 实战篇（16–20）

| 讲次 | 主题 |
|------|------|
| [16｜实战一：代码仓库分析 Agent](16-实战一-代码仓库分析Agent.md) | 项目实战 |
| [17｜实战二：排查记录核实 Agent](17-实战二-排查记录核实Agent.md) | 项目实战 |
| [18｜面试题速查](18-面试题速查.md) | 面试准备 |
| [19｜接入 Codex 工作流](19-Codex工作流接入.md) | Codex 集成 |
| [20｜官方资料链接](20-官方资料链接.md) | 延伸阅读 |

### 实验与模板

| 文件 | 说明 |
|------|------|
| [Lab 01：最小 Agent](labs/lab-01-minimal-agent.md) | 动手实验 |
| [Lab 02：事件核实 Mock](labs/lab-02-incident-verifier-mock.md) | 动手实验 |
| [Lab 03：沙箱检查清单](labs/lab-03-sandbox-checklist.md) | 检查清单 |
| [Codex POC Prompt](prompts/codex-poc-prompt.md) | 可复用 Prompt 模板 |
| [Runbook 输出模板](prompts/runbook-output-template.md) | Runbook 模板 |

## 安全边界

所有涉及日志、数据库、shell、生产系统的示例，都应该先用 mock 数据或 sandbox 验证。真实系统接入时遵守：**只读优先、最小权限、高危操作审批、证据链输出**。
