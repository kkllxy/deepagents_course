# 给 Codex 的 POC Prompt

```text
请在当前仓库里创建一个 DeepAgents POC，目标是做“排查记录核实 Agent”。

边界：
1. 先只用 mock 工具，不连接真实生产日志/DB。
2. 不修改现有业务代码。
3. 新增目录 tools/incident-verifier。
4. 输出必须是 Markdown 和 JSON 两份。
5. 所有 claim 必须有 verified / unverified / unknown 状态。
6. 未核实内容不能写入 verified runbook 区域。

最小功能：
- 读取 examples/incidents/*.md；
- 提取 claims；
- 调用 mock search_logs、query_readonly_db、grep_repo；
- 生成 output/<incident>.report.md；
- 生成 output/<incident>.evidence.json；
- 提供 README，说明如何运行。

请先给我实现计划和文件清单，不要直接大改。
```
