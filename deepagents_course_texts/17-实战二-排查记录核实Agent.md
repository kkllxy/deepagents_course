# 17｜实战二：排查记录核实 Agent

## 项目目标

把人工排查记录变成可核实、可引用、可沉淀的知识库条目。

## 输入示例

```markdown
服务：order-api
时间：2026-06-10 10:00-10:30
现象：接口大量超时。
人工判断：可能是数据库连接池耗尽导致。
处理：重启 order-api 后恢复。
```

## Claim 拆解

```json
[
  {"claim": "order-api 在 10:00-10:30 出现大量超时"},
  {"claim": "数据库连接池耗尽是主要原因"},
  {"claim": "重启 order-api 后恢复"}
]
```

## 核实状态

| 状态 | 含义 |
|---|---|
| verified | 有工具证据支持 |
| unverified | 查了但没找到证据 |
| unknown | 工具失败或输入不足 |
| contradicted | 证据与 claim 相反 |

## 输出模板

```markdown
# Incident Verification Report

## Incident
- Service:
- Time Range:
- Input Note:

## Claims
| ID | Claim | Status | Evidence | Reason |
|---|---|---|---|---|

## Evidence
### E001
- Type:
- Source:
- Query:
- Snippet:
- Supports:

## Runbook Entry
### Symptom
### Verification Steps
### Mitigation
### Follow-up Checks

## Unknowns
## Suggested Codex Tasks
```

## Codex 集成

```text
Codex 负责：读取报告、审查输出、把 verified 内容合并进 runbook。
DeepAgents 负责：拆 claim、调工具、生成证据链和报告。
```

## 验收标准

- 每个 claim 有 status；
- verified 必须有 evidence；
- unknown 必须说明缺什么；
- 未核实内容不能写成事实；
- 可直接进入 `docs/incidents/verified/`。
