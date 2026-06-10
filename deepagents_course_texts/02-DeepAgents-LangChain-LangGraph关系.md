# 02｜DeepAgents / LangChain / LangGraph 关系

## 本讲目标

搞清三者分工，避免面试时混成一团。

## 核心内容

- LangGraph 像运行时内核，负责图、状态、checkpoint、streaming、human-in-the-loop 等底层能力。
- LangChain 提供模型、工具、消息、agent 基础接口等组件。
- DeepAgents 是上层 opinionated harness，在 LangChain/LangGraph 之上提供默认长任务能力。


## 示例 / 模板

```text
LangGraph：状态图运行时
LangChain：模型和工具组件层
DeepAgents：带默认能力的长任务 Agent harness
```

## 工程注意点

- 不要只追求 demo 跑通，要关注权限、证据、失败处理和可复盘。
- 所有真实日志、数据库、shell 命令都应先通过 mock 或 sandbox 验证。
- 输出尽量结构化，方便 Codex 后续读取和整理。

## 面试回答

> 如果要完全自定义状态机，用 LangGraph；如果只是轻量工具问答，用 LangChain create_agent；如果要快速做研究、代码分析、排障这类长任务，用 DeepAgents。

## 本讲练习

把本讲能力应用到“排查记录核实 Agent”里，写出你会暴露给 Agent 的工具、路径权限和输出字段。
