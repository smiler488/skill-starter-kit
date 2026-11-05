# skill-starter-kit 安装说明（给 AI 助手）

> 用户只需对 AI 助手说：
> `请根据 https://raw.githubusercontent.com/smiler488/skill-starter-kit/main/install.md，安装 skill-starter-kit。`

你是收到安装请求的 AI 助手。按下面的步骤把 Agent Skill `skill-starter-kit` 装到本机，用默认值直接执行，不需要每一步都征求确认。只有一种情况要先问用户：目标目录已经存在、而且不是本仓库的 git 克隆（可能是用户自己改过的版本）。装完用一两句话告诉用户结果。

## 1. 确定安装目录

按当前运行的工具选择 skills 目录；如果目录还不存在就创建它：

| 工具 | 用户级 skills 目录 |
| --- | --- |
| Claude Code | `~/.claude/skills/` |
| Codex | `~/.codex/skills/` |
| WorkBuddy / CodeBuddy | `~/.workbuddy/skills/` |
| Cursor | `~/.cursor/skills/` |
| Gemini CLI | `~/.gemini/skills/` |

- 用户说只在当前项目里用时，改用项目内的目录，例如 `<项目>/.claude/skills/`。
- Windows 上 `~` 指 `C:\Users\<用户名>`。
- 目标目录记为 `TARGET = <skills 目录>/skill-starter-kit`。目录名必须是 `skill-starter-kit`，和 SKILL.md 里的 `name` 一致。

## 2. 下载

**有 git 时（推荐，方便以后更新）**

```bash
git clone --depth 1 https://github.com/smiler488/skill-starter-kit.git "$TARGET"
```

如果 `TARGET` 已经是本仓库的克隆，改为更新：

```bash
git -C "$TARGET" pull --ff-only
```

**没有 git，macOS / Linux：**

```bash
mkdir -p "$TARGET"
curl -fsSL https://codeload.github.com/smiler488/skill-starter-kit/tar.gz/refs/heads/main \
  | tar -xz --strip-components=1 -C "$TARGET"
```

**没有 git，Windows PowerShell：**

```powershell
$Target = "$HOME\.claude\skills\skill-starter-kit"   # 按第 1 步换成实际目录
$Zip = "$env:TEMP\skill-starter-kit.zip"
Invoke-WebRequest https://codeload.github.com/smiler488/skill-starter-kit/zip/refs/heads/main -OutFile $Zip
Expand-Archive $Zip -DestinationPath "$env:TEMP\skill-starter-kit-src" -Force
New-Item -ItemType Directory -Force $Target | Out-Null
Copy-Item "$env:TEMP\skill-starter-kit-src\skill-starter-kit-main\*" $Target -Recurse -Force
```

## 3. 依赖

无需安装额外依赖。

## 4. 检查

- `TARGET/SKILL.md` 存在，开头的 frontmatter 里有 `name: skill-starter-kit`。
- 这些文件也在：`templates/SKILL.template.md`、`RELEASE-CHECKLIST.md`、`PROMPTS.md`。

缺文件就说明下载不完整，删掉 `TARGET` 后重新执行第 2 步。

## 5. 告诉用户

报告安装路径，并提醒用户：**新开一个会话（或重启工具）后 skill 才会生效**。

用法示例："帮我把每周整理组会纪要的流程做成一个 Skill"、"检查一下这个 SKILL.md 写得规不规范"、"把这个 Skill 发布到 GitHub"。

## 网页版助手（没有本地文件系统）

跳过安装。把 https://raw.githubusercontent.com/smiler488/skill-starter-kit/main/SKILL.md 和 https://raw.githubusercontent.com/smiler488/skill-starter-kit/main/templates/SKILL.template.md 读进对话，按 SKILL.md 的流程帮用户写 Skill。

## 卸载

删除 `TARGET` 目录即可。

---

## English

Tell your assistant: `Install skill-starter-kit following https://raw.githubusercontent.com/smiler488/skill-starter-kit/main/install.md`

1. Pick the skills folder of the running tool (table above), e.g. `~/.claude/skills/`. Set `TARGET=<folder>/skill-starter-kit`. The folder name must equal the `name` in SKILL.md.
2. `git clone --depth 1 https://github.com/smiler488/skill-starter-kit.git "$TARGET"`. If it already exists as a clone, run `git -C "$TARGET" pull --ff-only` instead. Without git, use the curl or PowerShell commands above.
3. Check that `TARGET/SKILL.md` has `name: skill-starter-kit` and that `templates/SKILL.template.md`, `RELEASE-CHECKLIST.md`, `PROMPTS.md` exist.
4. Tell the user where it was installed and that a new session is needed. Example requests: "turn my weekly meeting-notes routine into a skill", "check whether this SKILL.md is valid".

Chat-only assistants: read SKILL.md and templates/SKILL.template.md from the raw URLs and follow SKILL.md.

Uninstall: delete `TARGET`.
