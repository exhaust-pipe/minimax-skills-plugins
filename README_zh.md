# MiniMax Skills Plugins

[English](./README.md)

本仓库是原 MiniMax skills 仓库的插件化 fork，用于将该skills仓库以plugins的形式加载到你的AI工具中。

原 MiniMax 技能集现在位于：

```text
plugins/minimax-skills/skills/
```

Codex 插件根目录是：

```text
plugins/minimax-skills/
```

仓库还包含 `plugins/pptx-plugin/`，用于独立的 PPTX 专用插件。

## Fork

建议通过 fork 本仓库来自定义技能集、保留本地新增内容，或测试插件打包改动。请保持 `plugins/<plugin-name>/` 布局不变，这样 marketplace 条目和相对路径才能继续正确解析。

如果使用 fork，请用你的 fork URL 替换本仓库 URL 进行安装：

```bash
codex plugin marketplace add <your-org>/<your-fork>
codex plugin install minimax-skills
```

## 安装

### Codex CLI

```bash
codex plugin marketplace add exhaust-pipe/minimax-skills-plugins --ref main
```

或者，在本地安装：

```bash
git clone https://github.com/exhaust-pipe/minimax-skills-plugins -b main
codex plugin marketplace add path/to/local/repo
```

安装插件：

```bash
codex plugin install minimax-skills
```

```bash
codex plugin install pptx-plugin
```

### Codex App

在 Codex app 中，将本仓库添加为插件 marketplace 路径,使用main分支：

```text
exhaust-pipe/minimax-skills-plugins
```

或者，在本地安装：

```bash
git clone https://github.com/exhaust-pipe/minimax-skills-plugins -b main
```

```bash
path/to/local/repo
```

然后你可以在市场安装相应的skills。

### Claude Code

`.claude-plugin/` 中提供了 Claude Code 插件元数据，但这个插件化仓库的 Claude Code 安装流程尚未验证。如果你测试 Claude Code 安装，请确认它从以下路径解析技能：

```text
plugins/minimax-skills/skills/
```

欢迎提交 issue 或 PR，补充经过验证的 Claude Code 安装流程。

### Cursor

这个插件化仓库的 Cursor 安装流程尚未验证。本地 skills 路径应指向：

```text
plugins/minimax-skills/skills/
```

未验证的本地配置说明见 [`.cursor-plugin/INSTALL_zh.md`](./.cursor-plugin/INSTALL_zh.md)。欢迎提交 issue 或 PR，补充经过验证的 Cursor 行为。

### OpenCode

这个插件化仓库的 OpenCode 安装流程尚未验证。任何本地配置都应从以下路径链接技能：

```text
plugins/minimax-skills/skills/
```

未验证的本地符号链接配置说明见 [`.opencode/INSTALL_zh.md`](./.opencode/INSTALL_zh.md)。欢迎提交 issue 或 PR，补充经过验证的 OpenCode 行为。

Codex 的详细说明见 [`.codex/INSTALL_zh.md`](./.codex/INSTALL_zh.md)。

## MiniMax Skills

技能列表和单个技能说明见 [`plugins/minimax-skills/README_zh.md`](./plugins/minimax-skills/README_zh.md)。

### VS Code

本仓库目前不提供独立的 VS Code 扩展。

如果你使用 VS Code，受支持的方式是在集成终端中运行以下任一 CLI 工具：
- Codex
- Claude Code
- OpenCode

如果你希望从本仓库使用原生本地 skills 配置，请使用 Cursor，并参考 [`.cursor-plugin/INSTALL_zh.md`](./.cursor-plugin/INSTALL_zh.md) 中未经验证的说明。

## 原始项目

此 fork 从原 MiniMax skills 仓库重组而来：

```text
https://github.com/MiniMax-AI/skills
```

在当前插件化布局中，原顶层 `skills/` 目录已不再存在。

## 贡献

欢迎贡献！提交 PR 前请阅读：

- [CONTRIBUTING_zh.md](./CONTRIBUTING_zh.md) — PR 格式、技能结构要求和开发指南
- [PR Review Rules](./.agents/skills/pr-review/SKILL.md) — 自动化验证检查和质量审阅标准

新增或修改 MiniMax 技能时，请同步更新 `plugins/minimax-skills/` 下的英文和中文 README 文件。

提交前可在本地运行验证脚本：

```bash
python .agents/skills/pr-review/scripts/validate_skills.py --path plugins/minimax-skills/skills
```

## 许可证

MIT。见 [LICENSE](./LICENSE)。
