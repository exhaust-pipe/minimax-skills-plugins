# Installing MiniMax Skills for OpenCode

[中文](./INSTALL_zh.md)

OpenCode installation for this pluginized repository has not been verified. The steps below are local symlink notes for OpenCode builds that support a local skill directory.

Issues and PRs that document a verified OpenCode install flow are welcome.

## Prerequisites

- [OpenCode.ai](https://opencode.ai) installed

## Installation

### macOS / Linux

```bash
git clone https://github.com/exhaust-pipe/minimax-skills-plugins.git ~/.minimax-skills-plugins

mkdir -p ~/.config/opencode/skill
for skill in ~/.minimax-skills-plugins/plugins/minimax-skills/skills/*/; do
    skill_name=$(basename "$skill")
    ln -s "$skill" ~/.config/opencode/skill/minimax-"$skill_name"
done
```

### Windows (PowerShell)

```powershell
git clone https://github.com/exhaust-pipe/minimax-skills-plugins.git "$env:USERPROFILE\.minimax-skills-plugins"

New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.config\opencode\skill"
Get-ChildItem "$env:USERPROFILE\.minimax-skills-plugins\plugins\minimax-skills\skills" -Directory | ForEach-Object {
    New-Item -ItemType SymbolicLink -Path "$env:USERPROFILE\.config\opencode\skill\minimax-$($_.Name)" -Target $_.FullName
}
```

> **Note:** Creating symbolic links on Windows may require administrator privileges or Developer Mode enabled.

Restart OpenCode to discover the skills.

Verify by asking: "List available skills"

## Available Skills

- **frontend-dev** — Frontend development with UI design, animations, AI-generated media assets
- **fullstack-dev** — Full-stack backend architecture and frontend-backend integration
- **android-native-dev** — Android native application development with Material Design 3
- **ios-application-dev** — iOS application development with UIKit, SnapKit, and SwiftUI
- **shader-dev** — GLSL shader techniques for stunning visual effects (ShaderToy-compatible)
- **gif-sticker-maker** — Convert photos into animated GIF stickers (Funko Pop / Pop Mart style)
- **minimax-pdf** — Generate, fill, and reformat PDF documents with a token-based design system
- **pptx-generator** — Generate, edit, and read PowerPoint presentations
- **minimax-xlsx** — Open, create, read, analyze, edit, or validate Excel/spreadsheet files
- **minimax-docx** — Professional DOCX document creation, editing, and formatting using OpenXML SDK
- **vision-analysis** — Analyze, describe, OCR, and extract information from images
- **minimax-multimodal-toolkit** — Generate voice, music, video, and image content via MiniMax APIs
- **minimax-music-gen** — Generate vocal songs, instrumentals, and covers with MiniMax Music API
- **buddy-sings** — Generate a personalized song for a Claude Code buddy
- **minimax-music-playlist** — Build music taste profiles and generate personalized playlists

## Updating

```bash
cd ~/.minimax-skills-plugins && git pull
```

Symlinks will automatically point to the updated content — no need to re-link.

## Uninstalling

### macOS / Linux

```bash
rm -f ~/.config/opencode/skill/minimax-*
rm -rf ~/.minimax-skills-plugins
```

### Windows (PowerShell)

```powershell
Get-ChildItem "$env:USERPROFILE\.config\opencode\skill\minimax-*" | Remove-Item -Force
Remove-Item -Recurse -Force "$env:USERPROFILE\.minimax-skills-plugins"
```

## Troubleshooting

### Skills not found

1. Verify symlinks exist: `ls -la ~/.config/opencode/skill/`
2. Each skill folder should contain a `SKILL.md` file
3. Restart OpenCode after installation

## Getting Help

- Report issues: https://github.com/exhaust-pipe/minimax-skills-plugins/issues
