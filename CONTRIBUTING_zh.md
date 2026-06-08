# 为 MiniMax Skills Plugins 贡献

[English](./CONTRIBUTING.md)

感谢你有兴趣参与贡献！本文档涵盖 PR 要求、技能结构规范和开发指南。

## Pull Request 要求

### 标题格式

使用 [Conventional Commits](https://www.conventionalcommits.org/) 风格：

```
feat(<skill-name>): add new skill for X
fix(<skill-name>): fix YAML frontmatter parsing error
docs: update README skill table
chore: add CI workflow
```

常见前缀：`feat`（新技能或新功能）、`fix`（bug 修复）、`docs`（仅文档）、`refactor`（不改变行为的结构调整）、`chore`（工具、CI、配置）。

### 范围

**一个 PR，只做一件事。** 每个 PR 应只属于以下一种：

- 添加新技能
- 修复现有技能中的 bug
- 改进现有技能
- 更新插件打包、marketplace 元数据或安装文档

不要把无关改动打包到同一个 PR 中。

### PR 描述

每个 PR 必须包含：

1. **What** — 你添加或修改了什么
2. **Why** — 动机或使用场景

## 技能结构

技能现在位于插件根目录内。原仓库级别的 `skills/` 目录已移动到 `plugins/minimax-skills/skills/`。

### 目录布局

```
plugins/<plugin-name>/
├── .codex-plugin/
│   └── plugin.json          # Codex 插件安装所必需
├── README.md                # 插件概览和技能表
├── README_zh.md             # README.md 存在时对应的中文版本
└── skills/
    └── <skill-name>/
        ├── SKILL.md         # 必需 — 带 YAML frontmatter 的入口文件
        ├── references/      # 可选 — 详细参考文档
        │   └── *.md
        └── scripts/         # 可选 — 辅助脚本
            ├── *.py
            └── requirements.txt
```

- 目录名是技能标识符。使用小写 `kebab-case`（例如 `gif-sticker-maker`）。
- `SKILL.md` 是唯一必需文件。其他文件和目录都是可选的。
- Codex marketplace 入口是 `.agents/plugins/marketplace.json`。
- 主 MiniMax skills 插件是 `plugins/minimax-skills/`。
- PPTX 插件是 `plugins/pptx-plugin/`。

### SKILL.md Frontmatter

```yaml
---
name: my-skill                    # 必需 — 必须匹配目录名
description: >                    # 必需 — 说明技能功能和触发时机
  One-paragraph description. Include trigger conditions so the agent
  knows when to activate this skill (e.g., "Use when the user asks to
  create, edit, or format Excel files").
license: MIT                      # 推荐 — 省略时默认 MIT
metadata:                         # 推荐
  version: "1.0"
  category: productivity           # 例如 frontend, mobile, productivity, creative
  sources:
    - Relevant documentation or standards
---
```

**必需字段：** `name`、`description`

- `name` 必须与目录名完全一致
- `description` 必须清楚说明触发条件，这是 agent 判断是否加载技能的依据

**推荐字段：** `license`、`metadata`（version、category、sources）

### 不要硬编码密钥

**绝不要在任何文件中硬编码 API key、token 或凭据。**

如果你的技能需要调用外部 API，请指示 agent 从环境变量读取凭据。遵循现有技能建立的模式：

```python
API_KEY = os.getenv("MINIMAX_API_KEY")
if not API_KEY:
    raise SystemExit("ERROR: MINIMAX_API_KEY is not set.\n  export MINIMAX_API_KEY='your-key'")
```

你的 `SKILL.md` 应把所需环境变量写入前置条件。`frontend-dev/references/env-setup.md` 是一个很好的示例。

### README 同步

添加新技能时，请更新插件级别的 `README.md` 和 `README_zh.md`，将技能加入技能表。社区提交的技能应将 Source 列设置为 `Community`。只有在安装方式、仓库布局或插件打包发生变化时，才需要更新根目录 `README.md` 和 `README_zh.md`。

## 指南

以下规则不是硬性阻断项，但遵循这些指南的 PR 会更快被审阅和合并。

### 1. 技能范围 — 避免重叠

创建新技能前，请检查现有技能是否已有功能重叠。如果你的功能可以作为现有技能的扩展，优先扩展现有技能，而不是新建技能。

在 PR 描述中，简要说明你的技能与相关现有技能的差异。例如，如果你添加语音合成技能，请说明它与 `frontend-dev` 中已有 TTS 能力的关系。

### 2. 文件大小意识

技能会被加载进 agent 的上下文窗口。每个 token 都有成本。

- 保持单个 `.md` 文件聚焦且简洁
- 如果参考文档变得很长，请按逻辑拆分（例如 `minimax-docx/references/openxml_encyclopedia_part{1,2,3}.md`）
- 避免在 Markdown 中直接嵌入大数据块（base64 图片、完整 API 响应 dump）
- 优先链接外部资源，而不是内联大量内容

### 3. 脚本标准

如果技能包含辅助脚本（通常在 `scripts/` 目录中）：

- 包含 shebang 行（例如 `#!/usr/bin/env python3`）
- 提供 `requirements.txt` 列出所有依赖
- 优雅处理错误，输出清晰信息，而不是原始 traceback
- 在 `SKILL.md` 或参考文件中记录脚本用法

### 4. 语言和编码

- 技能名和文件名：仅 ASCII，使用 `kebab-case`
- SKILL.md 内容和代码应使用英文
- 推荐参考文档使用英文
- 所有文件必须使用 UTF-8 编码

## 审阅流程

提交前，你可以在本地运行验证脚本检查部分要求：

```bash
python .agents/skills/pr-review/scripts/validate_skills.py --path plugins/minimax-skills/skills
python .agents/skills/pr-review/scripts/validate_skills.py --path plugins/pptx-plugin/skills
```

也可以使用 [pr-review skill](./.agents/skills/pr-review/SKILL.md)，让你的 AI coding agent 辅助审阅。

1. 按上述要求提交 PR
2. 至少一位 maintainer 会进行审阅
3. 处理审阅反馈
4. 通过后由 maintainer 合并

## 有问题？

如果你对贡献流程有疑问，请打开 issue。我们很乐意提供帮助。
