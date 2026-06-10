# .

这个目录已经初始化成可在 WSL 里运行的 Claude Code 项目环境。

模式：`both`

Claude Code 建议启动方式：

```bash
bash ./claude-<provider> --version
```

## DeepSeek

只需要一次性配置这份本机共享文件：

```bash
/home/yy834/.config/ccinit/providers/deepseek.local.env
```

如果你还没填过 key，把这行占位符改掉：

```bash
export DEEPSEEK_API_KEY='REPLACE_WITH_YOUR_VALID_DEEPSEEK_KEY'
```

新项目里的：

```bash
.claude/deepseek.local.env
```

会自动 source 上面的共享配置，所以你以后再跑 `ccinit`，默认就能直接 `bash ./claude-ds`。
只有这个项目想单独覆盖时，才需要改项目里的这个文件。

常用命令：

```bash
bash ./claude-ds -p "Reply with exactly: hi" --output-format text
bash ./claude-ds
bash ./agent-view-ds --json
bash ./agent-view-ds
```

## GLM Coding Plan

只需要一次性配置这份本机共享文件：

```bash
/home/yy834/.config/ccinit/providers/glm.local.env
```

如果你还没填过 key，把这行占位符改掉：

```bash
export GLM_PLAN_API_KEY='REPLACE_WITH_YOUR_VALID_GLM_CODING_PLAN_KEY'
```

新项目里的：

```bash
.claude/glm.local.env
```

会自动 source 上面的共享配置，所以你以后再跑 `ccinit`，默认就能直接 `bash ./claude-glm`。
只有这个项目想单独覆盖时，才需要改项目里的这个文件。

固定端点：

```text
https://open.bigmodel.cn/api/anthropic
```

当前默认模型映射：

```text
ANTHROPIC_DEFAULT_OPUS_MODEL=glm-5.1
ANTHROPIC_DEFAULT_SONNET_MODEL=glm-5-turbo
ANTHROPIC_DEFAULT_HAIKU_MODEL=glm-4.5-air
```

如果你想切回更保守的 4.7，去共享配置里手动改：

```bash
export ANTHROPIC_DEFAULT_OPUS_MODEL='glm-4.7'
export ANTHROPIC_DEFAULT_SONNET_MODEL='glm-4.7'
```

常用命令：

```bash
bash ./claude-glm -p "Reply with exactly: hi" --output-format text
bash ./claude-glm
bash ./agent-view-glm --json
bash ./agent-view-glm
AGENT_VIEW_MODEL='glm-5.1' bash ./agent-view-glm
```

## 备注

- 这里固定使用 `--setting-sources project,local`，避免误吃全局 provider 配置。
- launcher 默认使用 `--permission-mode auto`；如果某次想改回别的模式，可以临时加环境变量：`CLAUDE_PERMISSION_MODE=default bash ./claude-glm`
- 如果当前目录已有 `README.md`，初始化脚本会改写到 `CC-README.md`，避免覆盖原 README。
- 默认共享 key 文件在 `/home/yy834/.config/ccinit/providers/`，只要这里配好一次，后续新项目会直接复用。
- 项目里的 `.claude/*.local.env` 仍然加入了 `.gitignore`，可以安全写项目级覆盖。
