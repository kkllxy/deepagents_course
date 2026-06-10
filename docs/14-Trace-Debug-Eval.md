# 14｜Trace / Debug / Eval

## 本讲目标

没有 trace 和 eval，Agent 很难生产化。

## 核心内容

- Trace 要记录输入、工具调用、参数、返回、文件写入、子 Agent、审批和最终输出。
- Eval 不只看答案，还要看工具调用是否正确、证据是否充分、无证据时是否拒绝下结论。
- 排障 Agent 特别要测 prompt injection、证据矛盾、工具超时、无时间范围等情况。


## 示例 / 模板

```yaml
case: db_pool_timeout_verified
input: examples/incidents/db_pool_timeout.md
mock_tools:
  search_logs: examples/mocks/logs_timeout.json
  query_db: examples/mocks/db_pool_full.json
expect:
  claim_status: verified
  required_evidence_types: [log, db]
```

## 工程注意点

- 不要只追求 demo 跑通，要关注权限、证据、失败处理和可复盘。
- 所有真实日志、数据库、shell 命令都应先通过 mock 或 sandbox 验证。
- 输出尽量结构化，方便 Codex 后续读取和整理。

## 面试回答

> Agent Eval 的核心是验证过程，而不是只看最终回答。排障类 Agent 尤其要能在证据不足时说不知道。

## 本讲练习

把本讲能力应用到“排查记录核实 Agent”里，写出你会暴露给 Agent 的工具、路径权限和输出字段。
