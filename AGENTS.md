# opensuyee Agent Instructions

这个仓库收集可复用的 AI Agent 技能、提示词和自动化工作流脚本。

## 使用 ai-edu-video

当用户要制作 AI 科普视频、产品入门教程、口播视频配动态图文、短视频字幕、封面帧、进度条、口播 PiP 或视频模板时，读取：

- `skills/ai-edu-video/SKILL.md`
- 按用户指定模板读取 `skills/ai-edu-video/references/*.md`

如果当前 Agent 不支持 Codex/Claude 的 `SKILL.md` 自动加载机制，把 `skills/ai-edu-video/AGENTS.md` 当作通用入口文件使用。

## 工作习惯

- 优先保留每个 skill 自己的目录结构，不要把模板和说明散落到仓库根目录。
- 修改 skill 时，同时更新对应目录里的 `README.md`、`AGENTS.md` 或 `CLAUDE.md`，确保跨 Agent 入口保持一致。
- 不提交生成的视频、音频、渲染缓存和私密素材。
