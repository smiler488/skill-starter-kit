---
name: skill-starter-template
description: 创建标准 Agent Skill 的脚手架模板。当用户要新建一个 Skill、把重复工作沉淀成技能、或准备发布 Skill 到 GitHub / SkillHub 时使用。产出符合 Agent Skills 开放约定的目录结构与 SKILL.md，并附 SkillHub 发布所需的 frontmatter 字段。
---

# <你的 Skill 名称>

<!-- 正文标题：一句话说清这个 Skill 是干什么的 -->

## Overview

<!-- 两三句话：这个 Skill 解决什么问题、适合什么场景。
     description 决定 Agent 何时加载本 Skill，正文决定加载后怎么干活。 -->

## 何时使用

<!-- 触发条件：用户说什么话、做什么事时应该调用本 Skill。
     写得越明确，Agent 误触发/漏触发越少。 -->

## 工作流程

<!-- 按步骤写清操作顺序，能给命令就给命令，能给模板就给模板。
     Agent 是照章办事的"新同事"，SOP 写多细，它就做多细。 -->

1. 第一步……
2. 第二步……

## 边界与注意

<!-- 哪些事不要做、哪些操作需要先向用户确认、出错时怎么回退。 -->

## 目录说明

<!-- 如果本 Skill 带 scripts/、references/ 等子目录，在这里逐个说明用途。 -->

- `scripts/` — 可执行脚本，正文里写清调用方式
- `references/` — 参考资料，供 Agent 需要时查阅

---

<!-- ===== 以下为 SkillHub 发布专用字段说明，发布前替换/删除本注释 =====
发布到 SkillHub（https://skillhub.cn）时，在 frontmatter 中追加：

slug: your-skill-handle        # 全网唯一，kebab-case（小写字母/数字/连字符），2-128 字符
                               # 建议带上你的 handle，如 hello-skillhub-zhangsan；提交后不可修改
displayName: 你的技能展示名
version: 1.0.0                 # SemVer 格式（主.次.修订）
summary: 一句话简介，展示在技能列表
license: MIT                   # 开源许可证

校验命令：skillhub publish <本文件夹> --dry-run
正式发布：skillhub publish <本文件夹> --changelog "首次发布"
-->
