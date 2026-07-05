# ai-edu-video

`ai-edu-video` 是一个用于制作 AI 科普短视频、产品入门教程和口播动态图文视频的跨 Agent skill。

它适合把口播稿、口播视频、产品 icon、截图或录屏，整理成适合视频号、小红书等平台发布的 3:4 竖屏视频。核心目标是：画面和口播逐句对应，字幕短而清楚，重点信息通过动效被用户看见。

## 能做什么

- 拆分口播稿，并建立句子级精确时间轴。
- 生成 3:4 竖屏 AI 科普/教程视频。
- 添加封面帧、章节进度条、字幕、口播 PiP、产品 icon 和重点词动效。
- 根据用户反馈修正时间轴、字幕、排版、视觉重点和模板规则。
- 沉淀可复用的视频模板，方便后续扩展不同风格。

## 内置模板

- `apple-green-pip-template`：简洁、清晰、偏 Apple 官网教程感，适合干净克制的 AI 工具入门教程。
- `dark-kinetic-course-template`：深色高节奏课程感，适合需要强留存、强重点动效的知识切片。

## 目录结构

```text
ai-edu-video/
  AGENTS.md
  CLAUDE.md
  SKILL.md
  agents/
    openai.yaml
  references/
    apple-green-pip-template.md
    cross-agent-usage.md
    dark-kinetic-course-template.md
```

## 安装

从 `opensuyee` 仓库安装：

```bash
git clone https://github.com/onlyzhongshuyi-svg/opensuyee.git
cd opensuyee
```

安装到 Codex：

```bash
mkdir -p ~/.codex/skills
cp -R skills/ai-edu-video ~/.codex/skills/ai-edu-video
```

安装到 Claude Code：

```bash
mkdir -p ~/.claude/skills
cp -R skills/ai-edu-video ~/.claude/skills/ai-edu-video
```

用于 opencode / OpenClaw / 其他 Agent：

```bash
# 让 Agent 读取通用入口文件
skills/ai-edu-video/AGENTS.md

# 或复制到当前项目根目录
cp skills/ai-edu-video/AGENTS.md ./AGENTS.md
```

## 使用方式

在支持 skills 的 Agent 中点名使用这个 skill，并提供口播稿、口播视频、产品素材和目标模板，例如：

```text
[$ai-edu-video](~/.codex/skills/ai-edu-video/SKILL.md)
用 dark-kinetic-course-template，基于这个口播视频，做成一个 3:4 竖屏科普视频。
```

在不支持 skills 自动加载的 Agent 中，先让它读取入口文件：

```text
请读取 skills/ai-edu-video/AGENTS.md，然后按 ai-edu-video 的工作流处理这个口播视频。
```

更多跨 Agent 安装和入口说明见 `references/cross-agent-usage.md`。

## 扩展新模板

新增模板时：

1. 在 `references/` 下新增一个模板说明文件。
2. 在 `SKILL.md` 的模板列表里登记模板名、适用场景、版式规则和验收要求。
3. 明确字幕、时间轴、动效、PiP、产品 icon 和抽帧验收规则。

## 默认规格

- 默认画幅：3:4 竖屏，推荐 `1080x1440`。
- 字幕：每行中文不超过 20 个字。
- 口播同步：正文模块、步骤卡片、关键词动效必须等口播提到后再出现。
- 验收：导出后用 `ffprobe` 检查视频规格，并抽帧检查关键时间点。
