# Claude Skills 通用指南

## 什么是 Skill

Skill 是一种可复用的"能力包"，用来扩展 Claude Code（或其他基于 Claude Agent SDK 的应用）的行为。
每个 Skill 本质上是一个目录，核心是一个 `SKILL.md` 文件，里面用 YAML frontmatter + Markdown
描述：

- 这个 Skill 是什么、解决什么问题
- 什么时候应该被触发使用
- Claude 应该按照什么角色 / 流程 / 知识来执行任务

Skill 可以是：
- **角色型（Persona）**：例如 `growth-hacker`，赋予 Claude 一个专家身份和方法论
- **流程型（Workflow）**：例如代码评审、PR 创建、研究报告生成等固定步骤的任务
- **工具型（Reference）**：提供某个领域的参考知识（API、配置、最佳实践等），供 Claude 查阅

## SKILL.md 的基本结构

```markdown
---
name: skill-name
description: 简要描述这个 skill 是做什么的，以及什么时候应该使用它（触发条件）。
---

# Skill 标题

## Role Definition / 角色定义
（如果是角色型 skill）描述 Claude 在这个 skill 下扮演的角色和专长

## Core Capabilities / 核心能力
列出该 skill 涵盖的主要能力点

## When to Use / 使用场景
列出适用的具体场景，帮助 Claude 判断何时调用此 skill

## Approach / 执行流程
描述具体的工作步骤、方法论或决策框架

## Success Metrics（可选）
如果是评估型/优化型任务，给出评判标准或基准值

## Source（可选）
注明该 skill 的来源出处和许可协议
```

### Frontmatter 字段说明

| 字段 | 说明 |
|------|------|
| `name` | Skill 的唯一标识，通常与目录名一致，使用小写连字符命名 |
| `description` | 非常关键：Claude 会根据这段描述判断"什么时候"应该使用该 skill。要写清楚触发场景和关键词 |

## 编写 Skill 的最佳实践

1. **description 要具体且包含触发关键词**：避免模糊描述，写明用户可能会怎么问、在什么场景下需要这个 skill。
2. **聚焦单一职责**：一个 skill 解决一类问题，不要把多个不相关的能力塞进同一个 skill。
3. **给出可执行的流程，而非空泛原则**：例如"先诊断现状 -> 再提出方案 -> 最后给出可执行的优先级列表"，比泛泛而谈"做好增长"更有用。
4. **量化的成功标准**：如果适用，给出基准数据（如转化率、留存率等），帮助 Claude 自我校准建议是否合理。
5. **注明来源和许可**：如果 skill 内容改编自他人开源项目，注明出处和 license，便于追溯和合规使用。

## 使用 Skill

在 Claude Code 中：
- 用户可以通过 `/skill-name` 显式调用某个 skill
- Claude 也会根据对话内容和 skill 的 `description` 自动判断是否需要调用某个 skill

## 如何收藏/管理 Skill 仓库

本仓库（`TideWatcher/skills`）的用法：
1. 看到他人开源的、有价值的 skill，先让 Claude 拆解其结构和内容
2. 确认内容有实质价值（非敷衍内容）后，将其整理为标准 `SKILL.md` 格式
3. 放入对应的目录（如 `growth-hacker/SKILL.md`），并在文件末尾保留 `Source` 出处
4. 后续可根据使用反馈对内容进行小幅迭代更新

## 参考示例

可参考本仓库中的 [`growth-hacker/SKILL.md`](../growth-hacker/SKILL.md)，
它展示了一个完整的角色型 skill 应该包含哪些部分（角色定义、核心能力、使用场景、
执行方法、成功指标、来源说明）。
