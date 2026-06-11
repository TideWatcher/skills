# skills

外部接进来的 Claude Code Skills 集合。

每个一级目录是一个独立的 skill，包含一个 `SKILL.md`，遵循 Claude Code 的 Skill 格式（YAML frontmatter `name` + `description`，正文为该 skill 的人设/方法论/使用说明）。

## 当前已有的 Skills

| Skill | 说明 | 来源 |
|---|---|---|
| [`growth-hacker`](./growth-hacker/SKILL.md) | 增长黑客策略顾问：用于GTM诊断、漏斗/转化分析、病毒传播机制设计、增长实验清单与ICE优先级排序，内置行业基准KPI（激活率、留存率、K-factor、LTV:CAC等） | 改编自 [agency-agents](https://github.com/msitarzewski/agency-agents) 的 `marketing/marketing-growth-hacker.md`（MIT协议） |

## 如何使用

在 Claude Code 会话中，直接描述需求，Claude 会根据 `SKILL.md` 里的 `description` 自动判断是否调用对应 skill，例如：

> "帮我诊断一下这个项目的GTM现状，并给出6个月增长方案"

也可以显式引用 skill 名称，例如 `/growth-hacker`（取决于具体工具的调用方式）。

## 如何新增 / 修改 Skill

1. 基于 `main` 新建分支
2. 新增一个目录 `<skill-name>/SKILL.md`，或修改已有 skill 的内容
   - frontmatter 需包含 `name` 和 `description`
   - `description` 要写清楚"什么场景下应该使用这个skill"，方便自动匹配
3. 提交并推送分支，创建 PR 合并到 `main`

## License

各 skill 内容遵循其来源项目的协议（详见各 `SKILL.md` 末尾的 `Source` 说明）。
