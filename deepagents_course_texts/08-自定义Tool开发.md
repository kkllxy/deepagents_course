# 08｜自定义 Tool 开发

## 本讲目标

Tool 是 Agent 接业务系统的入口。

## 核心内容

- Tool 名称和 docstring 要让 Agent 明白何时使用。
- 参数要有类型，返回要结构化。
- 生产 tool 应默认只读、有超时、有审计、有错误结构。
- Tool 返回证据，不直接替 Agent 下根因结论。


## 示例 / 模板

```python
def search_logs(service: str, start_time: str, end_time: str, keyword: str, limit: int = 50) -> dict:
    return {
        "status": "ok",
        "query": {"service": service, "start_time": start_time, "end_time": end_time, "keyword": keyword},
        "matches": [],
    }

def query_readonly_db(sql: str, max_rows: int = 100) -> dict:
    if not sql.strip().lower().startswith("select"):
        return {"status": "rejected", "reason": "only SELECT is allowed"}
    return {"status": "ok", "sql": sql, "columns": [], "rows": []}
```

## 工程注意点

- 不要只追求 demo 跑通，要关注权限、证据、失败处理和可复盘。
- 所有真实日志、数据库、shell 命令都应先通过 mock 或 sandbox 验证。
- 输出尽量结构化，方便 Codex 后续读取和整理。

## 面试回答

> 企业落地的关键不是会不会注册 tool，而是 tool 的权限、审计、结构化返回、超时、脱敏和错误处理。

## 本讲练习

把本讲能力应用到“排查记录核实 Agent”里，写出你会暴露给 Agent 的工具、路径权限和输出字段。
