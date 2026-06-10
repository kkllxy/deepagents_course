# 16｜实战一：代码仓库分析 Agent

## 项目目标

输入一个 Git 仓库路径，让 Agent 输出工程分析报告：项目类型、入口命令、构建方式、测试命令、关键模块、风险点、缺失文档、给 Codex 的下一步任务。

## 推荐工具

```python
def list_files(path: str) -> dict: ...
def read_file(path: str, start_line: int = 1, max_lines: int = 200) -> dict: ...
def grep_repo(pattern: str, include: str = "**/*") -> dict: ...
def run_readonly_command(command: str) -> dict: ...
def write_report(path: str, content: str) -> dict: ...
```

## 工作流程

```text
1. 读取根目录：README、pyproject、package、go.mod、pom.xml、Dockerfile 等。
2. 判断语言、框架、包管理器。
3. 找入口：main、cmd、app、server、routes。
4. 找构建和测试命令。
5. 找配置：env、yaml、toml、json、helm、k8s。
6. grep TODO、FIXME、panic、timeout、retry、deprecated。
7. 输出报告和 Codex 下一步任务。
```

## 输出模板

```markdown
# Repository Analysis Report

## Summary
## Project Type
## Entry Points
## Build Commands
## Test Commands
## Key Directories
## Configuration Files
## Risk Points
## Missing Documentation
## Recommended Codex Tasks

## Evidence
| Claim | Evidence Path | Confidence |
|---|---|---|
```

## Agent 指令

```text
你是代码仓库分析 Agent。你只能根据文件内容和只读命令输出下结论。不要修改仓库文件。每个判断都要引用文件路径或命令输出。
```

## 验收标准

- 至少列出 5 个关键文件或目录；
- 每个结论都有 evidence path；
- 不猜测不存在的构建命令；
- 输出可直接交给 Codex 继续干活。
