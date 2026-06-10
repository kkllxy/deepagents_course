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

All launchers share the same pattern:
1. Source API keys from `.claude/<provider>.local.env`, which in turn sources the shared config at `~/.config/ccinit/providers/<provider>.local.env`
2. Run Claude Code with `--setting-sources project,local` (ignores global provider config)
3. Default to `--permission-mode auto` (override with `CLAUDE_PERMISSION_MODE=default`)

| Command | Purpose | Default Model |
|---|---|---|
| `bash ./claude-glm` | Interactive Claude Code (GLM backend) | `glm-5.1[1m]` |
| `bash ./claude-ds` | Interactive Claude Code (DeepSeek backend) | — |
| `bash ./agent-view-glm` | Agent-view / multi-agent mode (GLM) | `glm-4.7` (override: `AGENT_VIEW_MODEL=glm-5.1`) |
| `bash ./agent-view-ds` | Agent-view / multi-agent mode (DeepSeek) | `deepseek-v4-pro[1m]` |

Quick smoke test for any launcher: `bash ./claude-<provider> -p "Reply with exactly: hi" --output-format text`

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
