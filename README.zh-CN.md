# skill-starter-kit

[English](README.md) | 中文

写 Agent Skill（Claude Code、Codex、WorkBuddy 等工具通用的 `SKILL.md` 格式）并把它发布出去的起步套件，里面有：

- 一份带注释的 `SKILL.md` 模板；
- 一份覆盖 GitHub、SkillHub、SkillPay 的发布检查清单；
- 四条提示词，可以带着智能体把整条流程走完。

把这个套件本身装成 skill 后，智能体会按流程帮你起草、测试并发布新的 skill。

它是我的公众号文章《Skill 发布完全指南：从创建标准 Skill 到 SkillPay 收费》（公众号 smiler488）的配套材料。

## 安装

对 AI 助手说：

```text
请根据 https://raw.githubusercontent.com/smiler488/skill-starter-kit/main/install.md，安装 skill-starter-kit。
```

也可以手动安装：

```bash
git clone --depth 1 https://github.com/smiler488/skill-starter-kit.git ~/.claude/skills/skill-starter-kit
```

装好后新开一个会话。

## 使用

直接用自然语言提需求，比如"帮我把每周整理组会纪要的流程做成一个 Skill"。智能体会依次：

1. 先问清这个 skill 做什么、什么时候触发、有哪些边界；
2. 按 `templates/SKILL.template.md` 填写；
3. 测试它在相关请求下会触发、在无关请求下不会误触发；
4. 发布前对照 `RELEASE-CHECKLIST.md` 逐项检查。

不装 skill 也可以，直接复制模板和清单自己用。

| 文件 | 用途 |
| --- | --- |
| `SKILL.md` | skill 本体（创建与发布 skill 的流程） |
| `templates/SKILL.template.md` | 新 skill 的带注释模板，含 SkillHub 字段说明 |
| `RELEASE-CHECKLIST.md` | GitHub / SkillHub / SkillPay 发布检查清单和常见报错 |
| `PROMPTS.md` | 四条提示词：写 skill、发布到 GitHub、上架 SkillHub、配置 SkillPay |
| `install.md` | 写给智能体看的安装说明 |

## 注意

- SKILL.md 中的 `name` 必须和文件夹名一致，只能用小写字母、数字和连字符；`description` 不能超过 1024 个字符。
- 支付平台的规则会变，给 skill 设置收费前，请先查看 SkillHub 和支付宝 / 微信支付的最新文档。

## 本次修订

- 原来根目录的 `SKILL.md` 就是空白模板本身，装上以后加载的是一个名叫 `skill-starter-template`、内容全是占位符的 skill。现在模板移到了 `templates/`，根目录的 `SKILL.md` 改成一个可以实际使用的 skill，名为 `skill-starter-kit`。
- `install.md` 覆盖 Claude Code、Codex、WorkBuddy、Cursor 和 Gemini CLI，没有 git 也能安装，装完会自动检查结果。

## 许可证

MIT，见 [LICENSE](LICENSE)。邓良超（Liangchao Deng）。
