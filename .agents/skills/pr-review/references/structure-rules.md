# Structure Rules (Hard Validation)

These rules are enforced by `scripts/validate_skills.py`. PRs that violate ERROR-level rules will not be merged.

## Directory Structure

Every skill must live under a plugin root and follow this layout:

```
plugins/<plugin-name>/
├── .codex-plugin/
│   └── plugin.json          # Required for Codex plugin installation
└── skills/
    └── <skill-name>/
        ├── SKILL.md         # Required
        ├── references/      # Optional
        │   └── *.md
        └── scripts/         # Optional
            ├── *.py
            └── requirements.txt
```

- Directory name must be lowercase `kebab-case` (e.g., `gif-sticker-maker`)
- `SKILL.md` is the only required file
- Validate skills by passing the plugin skill directory explicitly, for example `--path plugins/minimax-skills/skills`
- Do not review against legacy root-level `skills/`, `.claude/skills/`, or `.codex/skills/` paths

## SKILL.md Frontmatter

The file must begin with a valid YAML frontmatter block enclosed by `---` markers.

### Required Fields (ERROR if missing)

| Field | Rule |
|-------|------|
| `name` | Must exist and exactly match the directory name |
| `description` | Must exist and be non-empty |

### Recommended Fields (WARNING if missing)

| Field | Rule |
|-------|------|
| `license` | Should be `MIT` or a license declaration |
| `metadata` | Should include `version`, `category`, and optionally `sources` |

## Secret Scanning

No file in the skill directory may contain hardcoded secrets. The following high-confidence patterns are scanned:

- OpenAI-style API keys: `sk-` followed by 20+ alphanumeric characters
- AWS Access Key IDs: `AKIA` followed by 16 uppercase alphanumeric characters
- Hardcoded Bearer tokens: `Bearer` followed by 50+ characters (typical JWT length)

Other forms of hardcoded credentials (API key assignments, passwords, etc.) are not automatically blocked but should be flagged during manual review.

## Validation Severity Levels

- **ERROR** — PR must not be merged. Must be fixed before approval.
- **WARN** — Reviewer should flag. Not a merge blocker but should be addressed.
