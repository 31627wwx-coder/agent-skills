# wedding-script-gemini

给 Grok Bot / Composio Instant 使用的婚礼写稿 Skill：把钟意的**创作铁律**和**自有语料学习点**打成可喂给 Gemini 4 Argon 的 `system_instruction`，避免每次口头复述方法论，也禁止「只塞问卷」的裸跑。

## 这个仓库有什么

- `SKILL.md` — Agent skill 入口（frontmatter + 调用约定）
- `system_instruction.txt` — **直接**作为 Gemini `system_instruction` 的压缩版（优先用这个）
- `references/方法论摘要.md` — 可展开的方法论
- `references/语料学习点.md` — 001… 最新 + 徐岩/赵轩宇结构学习点（**无完整口播、无客户隐私原文**）

完整成稿与可识别经历只在主持人本地「钟意婚礼主持自有语料库」，**不进本仓库**。

## Grok Bot 怎么用

1. 写台词任务触发时加载本 skill（或 Composio org Skill 同文）。
2. 调用 `GEMINI_GENERATE_CONTENT`（模型 `gemini-4-argon`）时：
   - `system_instruction` = 本仓库 `system_instruction.txt` 全文
   - `prompt` = 本场档案事实 + 流程硬约束 + 环节与时长要求
3. 默认：跳过对外三方向，直出约 2 分钟开场；用户明确要求诊断时再输出七项+三方向。
4. 返回后按铁律做事实/口语审计，再交给主持人改定。

## 与本地语料库的关系

| 层级 | 内容 | 是否公开进 GitHub skill |
| --- | --- | --- |
| 铁律 + 结构学习点 | 本仓库 | 是 |
| 索引条目（母题/路径/学习点） | 本仓库（已脱敏姓名经历） | 是 |
| 完整口播成稿 | 本地自有语料库 | **否** |
| 徐岩/赵轩宇全文校正稿 | 本地项目资料包 | **否**（只学结构标签） |

## 更新约定

- 自有语料新增编号后：先更新本地索引与成稿，再把**学习点摘要**（无全文）补进 `references/语料学习点.md`，并视需要刷新 `system_instruction.txt`。
- 不要把问卷原文、客户隐私、他场成句推进本仓库。

## 许可与边界

仅供钟意婚礼主持工作流内部使用。参考校正语料只学方法，不复制标志句式。
