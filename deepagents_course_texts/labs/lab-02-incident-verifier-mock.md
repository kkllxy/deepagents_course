# Lab 02｜Mock 版排查记录核实器

## 目标

不用真实日志/DB，只用 mock 数据跑通 claim 核实流程。

## 输入

`examples/incidents/order-timeout.md`

## 工具

- `search_logs` 返回 timeout 日志片段；
- `query_readonly_db` 返回连接池状态；
- `search_deploy_events` 返回重启事件。

## 输出

- `output/order-timeout.report.md`
- `output/order-timeout.evidence.json`

## 验收

- 至少 3 个 claim；
- 至少 2 条 evidence；
- 没证据的 claim 标记 unverified；
- 最终 runbook 不包含未核实事实。
