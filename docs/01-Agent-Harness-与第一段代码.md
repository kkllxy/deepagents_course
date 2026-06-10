# 01｜Agent Harness 与第一段代码

## 本讲目标

DeepAgents 是什么，为什么它不是普通聊天 bot。

## 核心内容

- Agent harness 是把 Agent 跑起来的一整套支架：模型、工具、任务规划、文件系统、上下文管理、子任务、审批和状态。
- 普通 tool calling Agent 往往只有模型和工具，任务变长后容易忘记计划、塞爆上下文、无法复盘。
- DeepAgents 的定位是让长任务 Agent 开箱具备计划、文件系统、subagent、memory 等能力。


## 示例 / 模板

```python
from deepagents import create_deep_agent

def get_service_owner(service: str) -> str:
    owners = {"order-api": "team-order", "payment-api": "team-payment"}
    return owners.get(service, "unknown")

agent = create_deep_agent(
    model="openai:gpt-5.4",
    tools=[get_service_owner],
    system_prompt="你是工程排障助手。只能基于工具返回信息下结论。",
)

result = agent.invoke({
    "messages": [{"role": "user", "content": "order-api 是谁负责？"}]
})
print(result)
```

## 工程注意点

- 不要只追求 demo 跑通，要关注权限、证据、失败处理和可复盘。
- 所有真实日志、数据库、shell 命令都应先通过 mock 或 sandbox 验证。
- 输出尽量结构化，方便 Codex 后续读取和整理。

## 面试回答

> DeepAgents 是面向复杂长任务的 agent harness。它把计划、上下文管理、文件系统、subagent、memory 等通用能力封装好，让开发者专注业务工具和业务规则。

## 本讲练习

把本讲能力应用到“排查记录核实 Agent”里，写出你会暴露给 Agent 的工具、路径权限和输出字段。
