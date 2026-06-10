# 10｜Subagent 子智能体

## 本讲目标

把复杂任务拆给专业子 Agent。

## 核心内容

- 适合拆分日志分析、DB 核实、代码路径分析、报告整理。
- 主 Agent 负责计划和汇总，子 Agent 负责局部证据收集。
- 子 Agent 输出要压缩成结构化摘要，不要把原始大结果全塞回主上下文。


## 示例 / 模板

```text
主 Agent：Incident Verifier
  -> Log Analyst
  -> DB Analyst
  -> Code Analyst
  -> Runbook Writer
```

## 工程注意点

- 不要只追求 demo 跑通，要关注权限、证据、失败处理和可复盘。
- 所有真实日志、数据库、shell 命令都应先通过 mock 或 sandbox 验证。
- 输出尽量结构化，方便 Codex 后续读取和整理。

## 面试回答

> Subagent 适合多分支、可并行、需要角色隔离的任务；但要限制数量、递归深度、token 预算和输出格式。

## 本讲练习

把本讲能力应用到“排查记录核实 Agent”里，写出你会暴露给 Agent 的工具、路径权限和输出字段。
