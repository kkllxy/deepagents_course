# 09｜Memory 记忆

## 本讲目标

DeepAgents 的 memory 更像可读写的长期文件系统。

## 核心内容

- Memory 保存项目事实、runbook、服务拓扑、用户偏好和工具经验。
- RAG 偏检索外部知识；memory 偏 Agent 自己沉淀可复用知识。
- 长期 memory 写入应审批，避免错误结论和敏感信息污染。


## 示例 / 模板

```markdown
# Service: order-api

## Common Incident: DB Pool Exhaustion
- Symptom: timeout spike
- Verification: logs + DB active connections
- Status: verified
- Evidence report: incidents/2026-06-10-order-timeout.report.md
```

## 工程注意点

- 不要只追求 demo 跑通，要关注权限、证据、失败处理和可复盘。
- 所有真实日志、数据库、shell 命令都应先通过 mock 或 sandbox 验证。
- 输出尽量结构化，方便 Codex 后续读取和整理。

## 面试回答

> Memory 不是聊天历史，也不是向量库本身。它是 Agent 可持续读写和复用的项目知识层。

## 本讲练习

把本讲能力应用到“排查记录核实 Agent”里，写出你会暴露给 Agent 的工具、路径权限和输出字段。
