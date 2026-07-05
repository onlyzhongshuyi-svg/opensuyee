# opensuyee
分享我日常沉淀的 AI Agent 技能、提示词以及自动化工作流脚本

## Skills

- [ai-edu-video](skills/ai-edu-video)：制作 AI 科普短视频和教程视频的跨 Agent skill，支持 Codex、Claude Code、opencode、OpenClaw 等工具通过 Markdown 入口读取，内置 `apple-green-pip-template` 和 `dark-kinetic-course-template` 两种视频模板。

## 安装 ai-edu-video

Codex:

```bash
mkdir -p ~/.codex/skills
cp -R skills/ai-edu-video ~/.codex/skills/ai-edu-video
```

Claude Code:

```bash
mkdir -p ~/.claude/skills
cp -R skills/ai-edu-video ~/.claude/skills/ai-edu-video
```

opencode / OpenClaw / 其他 Agent:

```bash
# 方式一：让 Agent 读取通用入口
skills/ai-edu-video/AGENTS.md

# 方式二：复制成当前项目的规则文件
cp skills/ai-edu-video/AGENTS.md ./AGENTS.md
```
