# DeepAgents 课程资料

本仓库是 **DeepAgents 课程**的配套文档站，包含 21 讲中文讲义、3 个实验练习，以及可复用的 Prompt 模板。课程内容面向希望构建生产级 AI Agent 的工程师。

> 本项目为纯文档仓库，不涉及构建/测试/lint 流程。

## 目录结构

```
deepagents_course/
├── deepagents_course_texts/        # 课程讲义 (00–20)
│   ├── labs/                       # 动手实验 (3 个)
│   └── prompts/                    # Prompt 模板
├── claude-glm                      # Claude Code 启动器 (GLM)
├── claude-ds                       # Claude Code 启动器 (DeepSeek)
├── agent-view-glm                  # Agent-View 多智能体模式 (GLM)
├── agent-view-ds                   # Agent-View 多智能体模式 (DeepSeek)
└── CLAUDE.md                       # Claude Code 项目指引
```

## 课程内容概览

讲义由浅入深，覆盖从基础到生产的完整链路：

| 范围 | 主题 |
|---|---|
| **01–03** | Agent Harness 概念、DeepAgents/LangChain/LangGraph 关系、最小可运行 Demo |
| **04–07** | 默认工具、上下文工程、后端、文件系统上下文、沙箱 |
| **08–10** | 自定义工具开发、记忆、子智能体 |
| **11–15** | Prompt 设计、Human-in-the-Loop、权限、Trace/Debug/Eval、部署与成本控制 |
| **16–17** | 两个毕业项目 — 代码仓库分析 Agent、事件验证 Agent |
| **18–20** | 面试 Q&A、Codex 工作流集成、官方资源链接 |

## 模型后端与启动器

本项目提供 4 个 Shell 启动器，可在 WSL 环境下通过不同模型后端运行 Claude Code：

### 支持的模型提供商

| 提供商 | API Key 环境变量 | API 端点 | 默认模型 |
|---|---|---|---|
| **GLM** (智谱 Coding Plan) | `GLM_PLAN_API_KEY` | `https://open.bigmodel.cn/api/anthropic` | `glm-5.1[1m]` |
| **DeepSeek** | `DEEPSEEK_API_KEY` | — (使用官方默认端点) | `deepseek-v4-pro[1m]` |

### GLM 模型映射

GLM 提供商兼容 Anthropic API 格式，模型映射关系如下：

```
ANTHROPIC_DEFAULT_OPUS_MODEL   → glm-5.1
ANTHROPIC_DEFAULT_SONNET_MODEL → glm-5-turbo
ANTHROPIC_DEFAULT_HAIKU_MODEL  → glm-4.5-air
```

如需切回更保守的 `glm-4.7`，可在共享配置中覆盖：

```bash
export ANTHROPIC_DEFAULT_OPUS_MODEL='glm-4.7'
export ANTHROPIC_DEFAULT_SONNET_MODEL='glm-4.7'
```

### 启动器一览

| 命令 | 用途 | 默认模型 |
|---|---|---|
| `bash ./claude-glm` | 交互式 Claude Code (GLM 后端) | `glm-5.1[1m]` |
| `bash ./claude-ds` | 交互式 Claude Code (DeepSeek 后端) | — |
| `bash ./agent-view-glm` | Agent-View 多智能体模式 (GLM) | `glm-4.7` (覆盖: `AGENT_VIEW_MODEL=glm-5.1`) |
| `bash ./agent-view-ds` | Agent-View 多智能体模式 (DeepSeek) | `deepseek-v4-pro[1m]` |

### 配置方式

所有启动器遵循相同模式：

1. **API Key 配置**：从项目级 `.claude/<provider>.local.env` 加载，该文件会自动 source 本机共享配置 `~/.config/ccinit/providers/<provider>.local.env`
2. **Setting 来源**：使用 `--setting-sources project,local`，避免全局 provider 配置干扰
3. **权限模式**：默认 `--permission-mode auto`；可通过 `CLAUDE_PERMISSION_MODE=default` 覆盖

首次使用时，在本机共享配置文件中填入有效 API Key：

```bash
# GLM
vim ~/.config/ccinit/providers/glm.local.env
# 填写: export GLM_PLAN_API_KEY='your_valid_key'

# DeepSeek
vim ~/.config/ccinit/providers/deepseek.local.env
# 填写: export DEEPSEEK_API_KEY='your_valid_key'
```

### 快速验证

```bash
bash ./claude-glm -p "Reply with exactly: hi" --output-format text
bash ./claude-ds  -p "Reply with exactly: hi" --output-format text
```

## 语言

所有课程内容均为**中文**。
