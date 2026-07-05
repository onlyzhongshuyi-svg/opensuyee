# 跨 Agent 使用说明

`ai-edu-video` 的核心说明是 `SKILL.md`。不同 Agent 对“技能”的命名和加载机制不同，所以本目录同时提供通用入口文件。

## 文件入口

| Agent/工具 | 推荐入口 | 说明 |
| --- | --- | --- |
| Codex | `SKILL.md` | 放到 `~/.codex/skills/ai-edu-video` 后由 Codex skills 机制加载。 |
| Claude Code | `SKILL.md` + `CLAUDE.md` | 放到 `~/.claude/skills/ai-edu-video` 后可作为 Claude Code skill 使用；作为项目打开时 `CLAUDE.md` 提供索引。 |
| opencode | `AGENTS.md` | opencode 会读取 `AGENTS.md` 作为项目规则；也可在 agent prompt 中引用该文件。 |
| OpenClaw | `AGENTS.md` 或 `SKILL.md` | 放入 workspace 后，把入口 Markdown 作为 bootstrap/context 文件使用。 |
| 其他 Agent | `AGENTS.md` -> `SKILL.md` | 先让 Agent 读通用入口，再读完整 skill 和模板文件。 |

## 安装到 Codex

```bash
mkdir -p ~/.codex/skills
cp -R skills/ai-edu-video ~/.codex/skills/ai-edu-video
```

## 安装到 Claude Code

```bash
mkdir -p ~/.claude/skills
cp -R skills/ai-edu-video ~/.claude/skills/ai-edu-video
```

安装后可以在 Claude Code 中尝试：

```text
/ai-edu-video 用 dark-kinetic-course-template，把这个口播视频做成 3:4 竖屏科普视频
```

## 用于 opencode

把 `skills/ai-edu-video/AGENTS.md` 复制或链接为项目的 `AGENTS.md`，也可以在 opencode 配置的 prompt 文件里引用它。

示例：

```bash
cp skills/ai-edu-video/AGENTS.md ./AGENTS.md
```

然后在 opencode 中说：

```text
根据 AGENTS.md 使用 ai-edu-video，读取 SKILL.md 和 dark-kinetic-course-template，生成视频方案。
```

## 用于 OpenClaw

把整个 `skills/ai-edu-video` 目录复制到 OpenClaw workspace 中，并把 `AGENTS.md` 或 `SKILL.md` 放入会被 workspace bootstrap/context 加载的位置。

建议启动语：

```text
读取 ai-edu-video/AGENTS.md，然后按 ai-edu-video/SKILL.md 的工作流执行。
```

## 维护原则

- `SKILL.md` 是唯一的核心规则源。
- `AGENTS.md`、`CLAUDE.md` 和本文档只做入口适配，不复制整套规则。
- 新增模板时只需要更新 `SKILL.md` 的模板列表和 `references/` 下的新模板文件；必要时再补充本文件的安装说明。
