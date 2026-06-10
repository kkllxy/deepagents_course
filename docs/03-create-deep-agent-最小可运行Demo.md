# 03｜`create_deep_agent` 最小 Demo

## 本讲目标

理解创建 Agent 的核心参数：model、tools、system_prompt、backend、memory。

## 核心内容

- `model` 决定使用哪个模型 provider。
- `tools` 是 Agent 连接真实世界的入口。
- `system_prompt` 是行为契约，不是随便写的人设。
- 后续再引入 backend、memory、checkpointer、interrupt。


## 示例 / 模板

```python
from deepagents import create_deep_agent

def calc_error_rate(total: int, errors: int) -> str:
    if total <= 0:
        return "total must be positive"
    return f"error_rate={errors / total:.4%}"

agent = create_deep_agent(
    model="openai:gpt-5.4",
    tools=[calc_error_rate],
    system_prompt="你是严谨的工程助手，必须说明计算依据。",
)

agent.invoke({"messages": [{"role": "user", "content": "总请求 120000，错误 360，错误率是多少？"}]})
```

## 工程注意点

- 不要只追求 demo 跑通，要关注权限、证据、失败处理和可复盘。
- 所有真实日志、数据库、shell 命令都应先通过 mock 或 sandbox 验证。
- 输出尽量结构化，方便 Codex 后续读取和整理。

## 面试回答

> 最小 demo 的重点不是模型回答，而是确认 tool 是否被正确调用、参数是否正确、输出是否绑定工具证据。

## 本讲练习

把本讲能力应用到“排查记录核实 Agent”里，写出你会暴露给 Agent 的工具、路径权限和输出字段。
