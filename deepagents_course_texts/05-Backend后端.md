# 05｜Backend 后端

## 本讲目标

Backend 决定文件、状态、memory 存在哪里，以及 execute 是否可用。

## 核心内容

- StateBackend 适合 demo 和临时任务。
- FilesystemBackend 适合本地项目分析。
- StoreBackend 适合跨会话和服务化。
- SandboxBackend 适合隔离执行命令。
- CompositeBackend 可以按路径路由不同存储和权限。


## 示例 / 模板

```text
/input    只读原始材料
/work     可写中间文件
/evidence 可写证据
/output   可写报告
/memory   长期记忆，写入需审批
```

## 工程注意点

- 不要只追求 demo 跑通，要关注权限、证据、失败处理和可复盘。
- 所有真实日志、数据库、shell 命令都应先通过 mock 或 sandbox 验证。
- 输出尽量结构化，方便 Codex 后续读取和整理。

## 面试回答

> Backend 是 DeepAgents 的工作台和边界层。生产里不能把整个宿主机目录暴露给 Agent，而要设计虚拟路径、读写权限和持久化策略。

## 本讲练习

把本讲能力应用到“排查记录核实 Agent”里，写出你会暴露给 Agent 的工具、路径权限和输出字段。
