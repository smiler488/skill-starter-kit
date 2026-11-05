# skill-starter-kit

创建标准 Agent Skill 的起步套件：带注释的 `SKILL.md` 模板 + Skill 发布避坑清单。

配套公众号文章《Skill 发布完全指南：从创建标准 Skill 到 SkillPay 收费》（公众号 smiler488）。

## 内容

| 文件 | 用途 |
|---|---|
| `SKILL.md` | 标准 Skill 模板（带注释），含 SkillHub 发布字段说明 |
| `RELEASE-CHECKLIST.md` | GitHub / SkillHub / SkillPay 三段发布避坑清单 |
| `install.md` | Agent 一句话安装协议 |
| `PROMPTS.md` | 四条智能体提示词：总结成 Skill / 发布 GitHub / 上架 SkillHub / 配置 SkillPay |

## 用法

1. 复制 `SKILL.md` 到你的 Skill 文件夹，按注释改写正文与 frontmatter；
2. 发布前对照 `RELEASE-CHECKLIST.md` 逐项过一遍；
3. 发布到 SkillHub：`skillhub publish <你的文件夹> --dry-run` 预检后正式发布。

## 给 AI 助理的安装方式

在支持 Skill 的 AI 助理（如 WorkBuddy）里发一句话：

```
请根据 https://raw.githubusercontent.com/smiler488/skill-starter-kit/main/install.md，安装 skill-starter-kit
```

## License

MIT
