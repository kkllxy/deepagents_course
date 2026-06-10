# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **DeepAgents course materials** repository — a collection of Chinese-language lecture notes, labs, and prompts for learning to build production-grade AI agents using DeepAgents. It is **not** a software project with build/test/lint cycles; it is a knowledge base of Markdown documents.

## Repository Structure

- `deepagents_course_texts/` — 21 lecture files (`00` through `20`) covering agent engineering topics
- `deepagents_course_texts/labs/` — 3 hands-on lab exercises
- `deepagents_course_texts/prompts/` — Reusable prompt templates (Codex POC prompt, runbook output template)
- `claude-glm`, `claude-ds` — Shell launchers for Claude Code using GLM and DeepSeek as backend providers
- `agent-view-glm`, `agent-view-ds` — Shell launchers that run Claude Code in agent-view mode (multi-agent) with GLM and DeepSeek models

## Launchers & Provider Setup

### 支持的模型提供商

| 提供商 | API Key 环境变量 | API 端点 | 默认模型 |
|---|---|---|---|
| **GLM** (智谱 Coding Plan) | `GLM_PLAN_API_KEY` | `https://open.bigmodel.cn/api/anthropic` | `glm-5.1[1m]` |
| **DeepSeek** | `DEEPSEEK_API_KEY` | — (使用官方默认端点) | `deepseek-v4-pro[1m]` |

### GLM 模型映射

GLM 提供商兼容 Anthropic API 格式，默认映射：

```
ANTHROPIC_DEFAULT_OPUS_MODEL   → glm-5.1
ANTHROPIC_DEFAULT_SONNET_MODEL → glm-5-turbo
ANTHROPIC_DEFAULT_HAIKU_MODEL  → glm-4.5-air
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

首次使用时，在本机共享配置文件中填入有效 API Key 即可。快速验证：`bash ./claude-<provider> -p "Reply with exactly: hi" --output-format text`

## Course Content Map

The lectures follow a progression from fundamentals to production:

- **01–03**: Agent harness concept, DeepAgents/LangChain/LangGraph relationship, minimal runnable demo
- **04–07**: Default tools, context engineering, backend, filesystem context, sandbox
- **08–10**: Custom tool development, memory, subagents
- **11–15**: Prompt design, human-in-the-loop, permissions, trace/debug/eval, deployment & cost control
- **16–17**: Two capstone projects — code repo analysis agent, incident verification agent
- **18–20**: Interview Q&A, Codex workflow integration, official resource links

## Language

All course content is in **Chinese (中文)**. Maintain Chinese for any edits to existing lecture/lab files.
