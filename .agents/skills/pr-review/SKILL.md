---
name: pr-review
description: >
  Review pull requests for the MiniMax Skills plugin repository. Use when
  reviewing PRs, validating new plugin skill submissions, checking existing
  skills for compliance, or verifying Codex plugin packaging under .agents/.
  Run the validation script first for hard checks, then apply plugin-structure
  and quality guidelines for content review. Triggers: PR review, pull request,
  validate skill, validate plugin, check skill, check plugin.
license: MIT
metadata:
  version: "1.0"
  category: tooling
---

# PR Review Skill

Review pull requests against the current plugin repository structure. Three-phase process: automated validation, plugin structure review, then manual content review.

## Repository Layout

Use these paths from the repository root:

- `.agents/plugins/marketplace.json` — Codex plugin marketplace entrypoint.
- `.agents/skills/pr-review/` — this reviewer skill, including scripts and references.
- `plugins/<plugin-name>/.codex-plugin/plugin.json` — Codex plugin manifest.
- `plugins/<plugin-name>/skills/<skill-name>/SKILL.md` — actual skill definitions.
- `plugins/<plugin-name>/README.md` and optional localized README files — plugin-level skill catalog and install docs.

Do not use legacy root-level `skills/`, `.Codex/skills/`, `.codex/skills/`, or `.claude/skills/` paths when reviewing this repository. They are from the pre-plugin layout and can produce false positives or miss the actual plugin skills.

## Phase 1: Automated Validation (Hard Rules)

Run the validation script from the repository root and pass the plugin skill directory explicitly:

```bash
python .agents/skills/pr-review/scripts/validate_skills.py --path plugins/minimax-skills/skills
python .agents/skills/pr-review/scripts/validate_skills.py --path plugins/pptx-plugin/skills
```

For a PR that adds or renames a plugin, inspect `plugins/<plugin-name>/.codex-plugin/plugin.json`, read its `skills` field, then validate that resolved directory with `--path`. Running the script without `--path` uses the legacy default `skills/` and is not valid for this repository.

The script checks:
- `SKILL.md` exists in every skill directory
- YAML frontmatter is parseable
- Required fields present: `name`, `description`
- `name` matches directory name
- No hardcoded secrets detected

All ERROR-level checks must pass. WARNING-level items (missing `license`, `metadata`) should be flagged but are not blockers.

See [references/structure-rules.md](references/structure-rules.md) for the complete hard rules specification.

## Phase 2: Plugin Structure Review

When the PR changes plugin packaging or skill locations, manually verify:

1. **Marketplace wiring** — `.agents/plugins/marketplace.json` points to each plugin root under `./plugins/<plugin-name>`.
2. **Codex manifest** — `plugins/<plugin-name>/.codex-plugin/plugin.json` has a correct `skills` path, normally `./skills/`.
3. **Skill placement** — new or updated skills live under the manifest's skills directory, not under old root-level skill folders.
4. **Plugin README sync** — plugin README files list new skills, renamed skills, and removed skills accurately.
5. **No stale install paths** — docs and scripts should not instruct Codex reviewers to symlink or validate old root `skills/` paths.

## Phase 3: Content Review (Soft Guidelines)

After automated checks pass, review the PR against quality guidelines:

1. **Skill scope** — Does it overlap with existing skills? Is the boundary clear?
2. **Description quality** — Does the `description` include clear trigger conditions?
3. **File size** — Are reference docs reasonably sized for context window consumption?
4. **API key handling** — If external APIs are used, are credentials read from environment variables?
5. **Script quality** — Do scripts have shebang, requirements.txt, and error handling?
6. **Language** — Are SKILL.md and code written in English?
7. **README sync** — Are plugin-level `README.md` and localized README files updated for new skills?

See [references/quality-guidelines.md](references/quality-guidelines.md) for soft guidelines details.

## Review Checklist Summary

### Must Pass (Blockers)
- [ ] `validate_skills.py --path plugins/<plugin-name>/skills` exits with code 0 for each changed plugin
- [ ] PR title follows conventional commit format
- [ ] One PR, one purpose
- [ ] Codex plugin manifests resolve to real skill directories

### Should Pass (Flagged in Review)
- [ ] No functional overlap with existing skills
- [ ] Description includes trigger conditions
- [ ] Files are reasonably sized
- [ ] API keys via environment variables
- [ ] Plugin README tables updated for new skills (Source column set to `Community` for community submissions)
- [ ] `.agents/plugins/marketplace.json` is updated when plugins are added, removed, or renamed
