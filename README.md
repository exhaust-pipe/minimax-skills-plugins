# MiniMax Skills Plugins

[中文版](./README_zh.md)

This repository is a pluginized fork of the original MiniMax skills repository, designed to integrate MiniMax skills as plugins into your AI tools.

The original MiniMax skill set now lives at:

```text
plugins/minimax-skills/skills/
```

The Codex plugin root is:

```text
plugins/minimax-skills/
```

The repository also contains `plugins/pptx-plugin/` for the separate PPTX-focused plugin.

## Forks

Forking this repository is the recommended way to customize the skill set, keep local additions, or test plugin packaging changes. Keep the `plugins/<plugin-name>/` layout intact so marketplace entries and relative paths continue to resolve.

For a fork, install from your fork URL instead of this repository URL:

```bash
codex plugin marketplace add https://github.com/<your-org>/<your-fork>
codex plugin install minimax-skills
```

## Installation

### Codex CLI

```bash
codex plugin marketplace add exhaust-pipe/minimax-skills-plugins --ref main
codex plugin install minimax-skills
```

or install locally:

```bash
git clone https://github.com/exhaust-pipe/minimax-skills-plugins -b main
codex plugin marketplace add path/to/local/repo
```

Install the plugin:

```bash
codex plugin install minimax-skills
```

```bash
codex plugin install pptx-plugin
```


### Codex App

In the Codex app, add this repository as a plugin marketplace path, use main branch:

```text
exhaust-pipe/minimax-skills-plugins
```

or install locally:

```bash
git clone https://github.com/exhaust-pipe/minimax-skills-plugins -b main
```

```bash
path/to/local/repo
```

Then you can install skills from the marketplace.

### Claude Code

Claude Code plugin metadata is provided in `.claude-plugin/`, but installation for this pluginized repository has not been verified. If you test Claude Code installation, make sure it resolves skills from:

```text
plugins/minimax-skills/skills/
```

Issues and PRs that document a verified Claude Code install flow are welcome.

### Cursor

Cursor installation is not verified for this pluginized repository. The local-skills path should point to:

```text
plugins/minimax-skills/skills/
```

See [`.cursor-plugin/INSTALL.md`](./.cursor-plugin/INSTALL.md) for the unverified local setup notes. Issues and PRs with verified Cursor behavior are welcome.

### OpenCode

OpenCode installation is not verified for this pluginized repository. Any local setup should link skills from:

```text
plugins/minimax-skills/skills/
```

See [`.opencode/INSTALL.md`](./.opencode/INSTALL.md) for the unverified local symlink setup notes. Issues and PRs with verified OpenCode behavior are welcome.

For Codex-specific details, see [`.codex/INSTALL.md`](./.codex/INSTALL.md).

### VS Code

This repository does not currently ship a standalone VS Code extension.

If you use VS Code, the supported approach is to run one of the supported CLI tools inside the integrated terminal:
- Codex
- Claude Code
- OpenCode

If you want native local-skills configuration from this repo, use Cursor and follow the unverified notes in [`.cursor-plugin/INSTALL.md`](./.cursor-plugin/INSTALL.md).

## MiniMax Skills

For the skill list and per-skill descriptions, see [`plugins/minimax-skills/README.md`](./plugins/minimax-skills/README.md).

## Original Project

This fork was reorganized from the original MiniMax skills repository:

```text
https://github.com/MiniMax-AI/skills
```

The original top-level `skills/` directory no longer exists in this pluginized layout.

## Contributing

We welcome contributions! Before submitting a PR, please read:

- [CONTRIBUTING.md](./CONTRIBUTING.md) — PR format, skill structure requirements, and development guidelines
- [PR Review Rules](./.agents/skills/pr-review/SKILL.md) — automated validation checks and quality review criteria

When adding or changing MiniMax skills, update the English and Chinese README files under `plugins/minimax-skills/`.

You can run the validation script locally before submitting:

```bash
python .agents/skills/pr-review/scripts/validate_skills.py --path plugins/minimax-skills/skills
```

## License

MIT. See [LICENSE](./LICENSE).
