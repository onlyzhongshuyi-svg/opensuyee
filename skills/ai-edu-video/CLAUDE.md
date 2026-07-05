# ai-edu-video for Claude Code

这是 `ai-edu-video` 的 Claude Code 入口文件。Claude Code 支持将技能放在 `.claude/skills/*/SKILL.md` 或 `~/.claude/skills/*/SKILL.md` 下；如果本目录被作为项目打开，本文件也会作为项目说明帮助 Claude 找到正确的 skill。

## 使用规则

当用户要制作 AI 科普视频、教程视频、口播动态图文视频，或要维护视频模板时：

1. 读取 `SKILL.md`。
2. 根据用户指定模板读取 `references/` 下的模板文件。
3. 按 `SKILL.md` 的工作流先拆稿和建立时间轴，再制作视频。
4. 交付前按 `SKILL.md` 的验收清单检查视频规格、字幕、PiP、抽帧和音画同步。

## 快速触发语

用户可能这样调用：

- `/ai-edu-video 用 dark-kinetic-course-template 做一个科普视频`
- `用 ai-edu-video，根据这个口播视频生成 3:4 竖屏教程视频`
- `把这个参考视频风格沉淀成 ai-edu-video 的新模板`

## 不要跳过

- 不要只看 README 就开始制作。
- 不要把整段口播堆到一帧字幕里。
- 不要让正文模块在口播提到之前提前出现。
- 不要提交源视频、源音频、隐私素材或渲染缓存。
