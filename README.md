# skill-starter-kit

English | [中文](README.zh-CN.md)

[![CI](https://github.com/smiler488/skill-starter-kit/actions/workflows/validate.yml/badge.svg)](https://github.com/smiler488/skill-starter-kit/actions/workflows/validate.yml) [![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE) ![Agent Skill](https://img.shields.io/badge/Agent_Skill-informational)
A starter kit for writing an Agent Skill (the `SKILL.md` format used by Claude Code, Codex, WorkBuddy and others) and getting it published. It contains an annotated `SKILL.md` template, a release checklist for GitHub, SkillHub and SkillPay, and four prompts that walk an assistant through the whole chain. Installed as a skill, it also guides the assistant through drafting, testing and releasing a new one.

It accompanies my WeChat article 《Skill 发布完全指南：从创建标准 Skill 到 SkillPay 收费》 (account smiler488).

## Install

Tell your assistant:

```text
Install skill-starter-kit following https://raw.githubusercontent.com/smiler488/skill-starter-kit/main/install.md
```

Or by hand:

```bash
git clone --depth 1 https://github.com/smiler488/skill-starter-kit.git ~/.claude/skills/skill-starter-kit
```

Start a new session afterwards.

## Use

Ask for a new skill in plain words, e.g. "turn my weekly meeting-notes routine into a skill". The assistant will:

1. ask what the skill does, when it should trigger and where its limits are;
2. fill in `templates/SKILL.template.md`;
3. test that it triggers on relevant requests and stays quiet on unrelated ones;
4. go through `RELEASE-CHECKLIST.md` before anything is published.

Without the skill installed, copy the template and checklist yourself.

| File | Purpose |
| --- | --- |
| `SKILL.md` | the skill itself (workflow for creating and releasing a skill) |
| `templates/SKILL.template.md` | annotated template for a new skill, with SkillHub fields |
| `RELEASE-CHECKLIST.md` | GitHub / SkillHub / SkillPay checklist with common error codes |
| `PROMPTS.md` | four prompts: write a skill, publish to GitHub, list on SkillHub, set up SkillPay |
| `install.md` | install instructions written for an AI assistant |

## Notes

- `name` in SKILL.md must match the folder name, use lowercase letters, digits and hyphens, and the `description` must stay under 1024 characters.
- Payment platforms change their rules. Check SkillHub's and Alipay's / WeChat Pay's current documentation before charging for a skill.

## Changes in this revision

- The root `SKILL.md` was the blank template itself. Installing the kit therefore loaded a skill named `skill-starter-template` full of placeholders. The template now lives in `templates/`, and the root `SKILL.md` is a working skill named `skill-starter-kit`.
- `install.md` covers Claude Code, Codex, WorkBuddy, Cursor and Gemini CLI, works without git, and checks the result.

## License

MIT, see [LICENSE](LICENSE). Liangchao Deng (邓良超).
