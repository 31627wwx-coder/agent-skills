# agent-skills

钟意的 Agent Skills 合集：给 Claude Code、Codex、Cursor、OpenCode 等支持 Agent Skills / `SKILL.md` 的工具用。

每个 skill 是一份「先扫描汇报 → 你勾选 → 再执行」的说明书；**不是一键清盘脚本**。对方 Agent 需要能操作你的 Windows 本机（Shell / 文件 / 注册表等），纯聊天模型装了也只会照着念。

## 目录结构

```text
.agents/skills/<skill-id>/SKILL.md   # 主流约定（Cursor / Codex / 多家 CLI）
.claude/skills/<skill-id>            # 软链到同一份，方便 Claude Code
```

安装时可把整个仓库 clone 到本机 skills 目录，或只拷某一个子文件夹。

## 已收录

| Skill | 说明 |
|-------|------|
| [windows-pc-health-check](.agents/skills/windows-pc-health-check/) | **电脑大保健**：Windows 存储 / 软件更新 / 开机项 / 安全与磁盘健康 / 默认路径，先扫后批再执行 |

## 怎么用（简版）

1. Clone 本仓库，或只下载某个 `SKILL.md` 所在文件夹。
2. 放到你用的 Agent 会读的 skills 路径，例如：
   - Cursor / Codex：`~/.agents/skills/` 或项目内 `.agents/skills/`
   - Claude Code：`~/.claude/skills/` 或项目内 `.claude/skills/`
3. 对 Agent 说「跑电脑大保健」或调用 `windows-pc-health-check`（以各产品调用方式为准）。
4. **一定先看扫描清单再批准**；不要让 Agent 跳过确认直接删盘或升固件。

也可用社区安装器（如 [vercel-labs/skills](https://github.com/vercel-labs/skills)）按各客户端文档安装；本仓库以标准 `SKILL.md` 为准。

## 设计原则

- 默认只读扫描，用户勾选后才改系统
- 不做注册表「神优化」、不乱 debloat
- 不擅自关电源/睡眠；不擅自卸游戏；照片库删前必须确认
- 厂商固件与大型 Windows 功能更新默认跳过
- 代理日常用规则+系统代理；虚拟网卡（TUN）默认关

## 之后还会加

本仓库会继续放更多可复用 skill（同一套目录约定）。欢迎 Issue / PR。

## License

MIT
