# Lab 01｜最小 DeepAgents Agent

## 目标

创建一个只带 mock tool 的 Agent，让它回答服务负责人。

## 步骤

1. 创建 Python 项目；
2. 安装 deepagents 和模型 provider 包；
3. 写 `get_service_owner(service)`；
4. 用 `create_deep_agent` 注册工具；
5. 调用 `agent.invoke`；
6. 检查输出是否引用工具结果。

## 验收

- Agent 能调用工具；
- 未知服务不会编造负责人；
- 代码放在 `src/agent.py`。
