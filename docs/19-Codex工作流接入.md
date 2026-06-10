# 19｜接入 Codex 工作流

## 总体定位

```text
Codex：主操作者、代码修改、PR、审查、知识库合并
DeepAgents：长任务分析、证据查询、报告生成、子任务分派
```

## 推荐仓库结构

```text
repo/
  AGENTS.md
  docs/
    runbooks.md
    incidents/
    service-knowledge/
  tools/
    incident-verifier/
      pyproject.toml
      src/
        agent.py
        tools_logs.py
        tools_db.py
        tools_repo.py
        prompts.py
      examples/
      output/
```

## Codex 调用方式

```bash
uv run incident-verifier verify \
  --input docs/incidents/raw/2026-06-10-order-timeout.md \
  --out docs/incidents/verified/2026-06-10-order-timeout.report.md
```

## 分阶段路线

### 第 1 阶段：纯文本离线

- 不接真实日志；
- 使用 mock 数据；
- 跑通 claim -> evidence -> report。

### 第 2 阶段：只读真实工具

- 接日志只读；
- 接 DB SELECT；
- 接仓库只读 grep；
- 所有输出加 evidence。

### 第 3 阶段：Codex 合并知识库

- DeepAgents 只生成报告；
- Codex 审查并修改 Markdown；
- 人工确认后提交。

## 给 Codex 的规则

```text
当用户给出人工排查记录时：
1. 先调用 incident-verifier 生成核实报告。
2. 只把 verified claim 写入 runbook。
3. unknown/unverified 只能写入“待核实”区域。
4. 不得删除原始排查记录。
5. 任何涉及真实系统写操作都必须询问用户。
```
