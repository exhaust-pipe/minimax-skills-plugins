# 为 Cursor 安装 MiniMax Skills

[English](./INSTALL.md)

这个插件化仓库的 Cursor 安装流程尚未验证。如果你的 Cursor 版本支持本地 skills 路径，请克隆本仓库，并将 Cursor 指向 `plugins/minimax-skills/skills/`。

欢迎提交 issue 或 PR，补充经过验证的 Cursor 安装流程。

## 前置条件

- 已安装 Cursor
- Git

## 安装

### macOS / Linux

```bash
git clone https://github.com/exhaust-pipe/minimax-skills-plugins.git ~/.cursor/minimax-skills-plugins
```

将 Cursor 的 skills 路径设置为：

```text
~/.cursor/minimax-skills-plugins/plugins/minimax-skills/skills/
```

### Windows (PowerShell)

```powershell
git clone https://github.com/exhaust-pipe/minimax-skills-plugins.git "$env:USERPROFILE\.cursor\minimax-skills-plugins"
```

将 Cursor 的 skills 路径设置为：

```text
C:\Users\YOUR_USERNAME\.cursor\minimax-skills-plugins\plugins\minimax-skills\skills\
```

将 `YOUR_USERNAME` 替换为你的 Windows 账号名。

保存路径后，重启 Cursor 或重新加载窗口，让它重新扫描本地 skills。

## 验证

确认 clone 存在，并且包含 `SKILL.md` 文件：

### macOS / Linux

```bash
find ~/.cursor/minimax-skills-plugins/plugins/minimax-skills/skills -maxdepth 2 -name SKILL.md | head
```

### Windows (PowerShell)

```powershell
Get-ChildItem "$env:USERPROFILE\.cursor\minimax-skills-plugins\plugins\minimax-skills\skills" -Directory | ForEach-Object {
    Get-ChildItem $_.FullName -Filter SKILL.md
}
```

## 更新

### macOS / Linux

```bash
cd ~/.cursor/minimax-skills-plugins && git pull
```

### Windows (PowerShell)

```powershell
Set-Location "$env:USERPROFILE\.cursor\minimax-skills-plugins"
git pull
```

## 卸载

### macOS / Linux

```bash
rm -rf ~/.cursor/minimax-skills-plugins
```

### Windows (PowerShell)

```powershell
Remove-Item -Recurse -Force "$env:USERPROFILE\.cursor\minimax-skills-plugins"
```

## VS Code 说明

本仓库目前不提供独立的 VS Code 扩展。

如果你使用 VS Code，推荐选项是：
- 在 VS Code 集成终端中运行受支持的 CLI 工具，例如 Codex、Claude Code 或 OpenCode
- 如果你希望使用本仓库的原生本地 skills 配置，请使用 Cursor
