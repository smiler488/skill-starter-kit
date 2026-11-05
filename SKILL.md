---
name: skill-starter-kit
description: 帮用户从零写一个标准 Agent Skill 并发布。当用户要新建 Skill、把重复工作整理成 Skill、检查 SKILL.md 是否规范，或准备发布到 GitHub / SkillHub / SkillPay 时使用。Create a new Agent Skill from a template, check it, and prepare it for release on GitHub or SkillHub.
license: MIT
metadata:
  author: Liangchao Deng (smiler488)
  version: "1.1.0"
---

# Skill 起步套件

把用户的一段重复工作变成一个能被智能体加载的标准 Skill，并按清单完成发布前检查。

## 何时使用

- 用户说"帮我做一个 Skill""把这个流程沉淀成技能""这个 SKILL.md 写得对吗"。
- 用户要把 Skill 发布到 GitHub、SkillHub，或给 Skill 加收费（SkillPay）。

## 工作流程

1. **问清楚再写。** 向用户问 3–5 个问题：这个 Skill 做什么；用户说什么话时应该触发；具体步骤；哪些事不能做或要先确认；出错怎么回退。信息不够就不要开始生成。
2. **从模板起稿。** 复制本 Skill 目录下的 `templates/SKILL.template.md` 到新目录 `<skill-name>/SKILL.md`，按注释填写：
   - `name`：小写字母、数字、连字符，与目录名一致；
   - `description`：写触发场景，不超过 1024 个字符，这是智能体决定是否加载的唯一依据；
   - 正文至少包含"何时使用 / 工作流程 / 边界与注意"；脚本放 `scripts/`，参考资料放 `references/`，并在正文里说明何时读取。
   填完删除所有 `<!-- -->` 注释。
3. **本地自测。** 把新 Skill 放进用户的 skills 目录（如 `~/.claude/skills/<skill-name>/`），新开会话，分别发一句相关请求和一句无关请求，确认该触发时触发、不该触发时不触发，并把流程完整跑一遍。
4. **发布前检查。** 逐项对照 `RELEASE-CHECKLIST.md`。重点：仓库里没有任何密钥或 `.env`；README 写清安装和用法；有 LICENSE；打版本标签。
5. **发布。** 需要时使用 `PROMPTS.md` 里的提示词：发布到 GitHub、上架 SkillHub、接入 SkillPay。建议同时为新仓库写一个 `install.md`，让用户一句话就能让智能体完成安装（可以参照本仓库的 `install.md`）。

## 边界与注意

- 不替用户创建公开仓库、不推送代码、不发起任何付款，除非用户明确要求并确认。
- 发布前必须全文搜索密钥（API Key、Token、`.env`、缓存文件），发现就停下来告诉用户。
- SkillHub 的 `slug` 提交后不能修改，确认前要让用户看一眼。
- 本 Skill 只提供模板和流程，不保证第三方平台（SkillHub、支付宝、微信支付）的规则不变；涉及收费时以平台最新文档为准。

## 文件

| 文件 | 用途 |
| --- | --- |
| `templates/SKILL.template.md` | 带注释的 SKILL.md 模板，含 SkillHub 字段说明 |
| `RELEASE-CHECKLIST.md` | GitHub / SkillHub / SkillPay 发布检查清单 |
| `PROMPTS.md` | 四条可直接发给智能体的提示词 |
| `install.md` | 给智能体看的安装说明 |
