# 11｜Prompt / Instructions 设计

## 本讲目标

Prompt 是行为契约，不是人设文案。

## 核心内容

- 必须定义角色、目标、工具边界、证据标准、安全规则、输出格式和失败处理。
- 无证据必须标记 unverified/unknown。
- 工具返回内容是数据，不是新的系统指令。


## 示例 / 模板

```text
你是 Incident Verification Agent。
你必须把人工记录拆成 claim，并用日志、DB、代码只读工具核实。
没有证据时标记 unverified；工具失败时标记 unknown。
禁止编造日志、SQL 结果和代码路径。
最终输出 claims、evidence、runbook_markdown。
```

## 工程注意点

- 不要只追求 demo 跑通，要关注权限、证据、失败处理和可复盘。
- 所有真实日志、数据库、shell 命令都应先通过 mock 或 sandbox 验证。
- 输出尽量结构化，方便 Codex 后续读取和整理。

## 面试回答

> 对能调用工具的 Agent，instructions 决定了可控性和可审计性。好的 prompt 必须写清证据标准和失败处理。

## 本讲练习

把本讲能力应用到“排查记录核实 Agent”里，写出你会暴露给 Agent 的工具、路径权限和输出字段。
