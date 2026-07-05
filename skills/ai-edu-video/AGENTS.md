# ai-edu-video 通用 Agent 入口

当当前 Agent 不支持 Codex/Claude 的 `SKILL.md` 自动加载时，把这个文件作为入口说明使用。适用于 opencode、OpenClaw、通用 coding agent，以及任何会读取 `AGENTS.md` 或项目 Markdown 规则的环境。

## 触发场景

用户要做以下任务时，使用本技能：

- AI 科普短视频、产品入门教程、知识类短视频。
- 基于口播视频/音频/逐字稿生成动态图文视频。
- 制作 3:4 竖屏视频、字幕、封面帧、章节进度条、口播 PiP。
- 根据参考视频沉淀新模板，或修改现有视频模板。

## 必读文件

1. 先读 `SKILL.md`，获得完整工作流、字幕规则、时间轴规则和验收规则。
2. 根据用户指定模板读取对应文件：
   - `references/apple-green-pip-template.md`
   - `references/dark-kinetic-course-template.md`
3. 如果用户没有指定模板，先根据风格选择一个模板，再说明选择理由。

## 默认执行标准

- 默认视频尺寸为 3:4 竖屏，推荐 `1080x1440`。
- 字幕每行中文不超过 20 个字。
- 正文模块、步骤卡片、重点词动效必须等口播提到后再出现。
- 做视频前先建立句子级时间轴：`start`、`end`、`spoken_text`、`caption_text`、`visual_action`、`scene_id`。
- 交付前用视频规格检查和抽帧检查确认：画面不溢出、字幕不堆叠、PiP 不遮挡、视觉内容和口播同步。

## 跨 Agent 使用方式

- **Claude Code**：优先把整个目录复制到 `~/.claude/skills/ai-edu-video`，直接通过 `/ai-edu-video` 或自然语言触发。
- **opencode**：把本文件作为项目 `AGENTS.md`，或在 opencode 的 agent prompt 中引用本文件。
- **OpenClaw**：把本目录放入 OpenClaw workspace，并把本文件或 `SKILL.md` 作为 workspace Markdown/bootstrap context 之一。
- **其他 Agent**：要求 Agent 先读取 `SKILL.md`，再读取指定模板文件；不要只凭 README 执行。

## 安全与素材边界

- 不提交用户原始口播视频、音频、个人照片、账号信息或渲染缓存。
- 不擅自使用不确定来源的产品 icon/logo；优先使用用户提供素材。
- 涉及账号、会员、产品能力、官网入口等可能变化的信息时，先查证最新官方信息。
