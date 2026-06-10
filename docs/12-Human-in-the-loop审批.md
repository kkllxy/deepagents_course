# 12｜Human-in-the-loop 审批

## 本讲目标

高危动作必须可暂停、可审批、可拒绝。

## 核心内容

- 只读日志和 SELECT 可以自动执行，但写库、删除文件、写 memory、创建 PR、发送消息应审批。
- 审批信息要展示动作、参数、影响范围、原因和 fallback。
- 审批不是弹窗问一句，而是提供足够上下文给人判断。


## 示例 / 模板

```json
{
  "action": "write_memory",
  "target": "/memory/services/order-api.md",
  "reason": "Add verified DB pool exhaustion runbook",
  "evidence_ids": ["E001", "E002"],
  "risk": "medium"
}
```

## 工程注意点

- 不要只追求 demo 跑通，要关注权限、证据、失败处理和可复盘。
- 所有真实日志、数据库、shell 命令都应先通过 mock 或 sandbox 验证。
- 输出尽量结构化，方便 Codex 后续读取和整理。

## 面试回答

> Human-in-the-loop 是把高风险动作变成可检查节点。生产里按风险分层：只读自动，高危审批，不可逆默认禁止。

## 本讲练习

把本讲能力应用到“排查记录核实 Agent”里，写出你会暴露给 Agent 的工具、路径权限和输出字段。
