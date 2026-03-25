# Loop Skill

[中文](#中文) | [English](#english)

## 中文

### 概览

这个仓库提供一个可复用的 agent skill 包：`loop`。

它面向需要多轮推进任务的通用 agent。它的目标不是把 agent 变成刚性的流程机，而是给 agent 一个轻量的迭代思考结构，让多轮执行更贴近需求，也更不容易陷入低质量重复。

核心设计目标：

- 提高对用户真实意图的贴合度
- 降低单一路径依赖
- 让多轮执行产生累积认知收益，而不是空转

### 仓库结构

```text
repo/
  README.md
  skills/
    loop/
      SKILL.md
      references/
        patterns.md
        troubleshooting.md
```

文件职责：

- `skills/loop/SKILL.md`
  主 skill 定义，包含 loop 的基本约束、回合结构、报告格式和整体行为。
- `skills/loop/references/patterns.md`
  说明不同 loop 模式，包括 refinement、accumulation、exploration。
- `skills/loop/references/troubleshooting.md`
  处理 loop 常见失效模式，例如假进展、过早结束、跑偏和卡住。

### 设计模型

`loop` 更适合作为“思考支架”来理解，而不是任务编排器。

它鼓励 agent 在每一轮里走一遍轻量流程：

1. 执行
2. 反思
3. 视角切换
4. 与前一轮横向比较
5. 验证
6. 判断是否继续

重点不在流程感，而在于让回合之间真的发生认知修正。

### 设计动机

很多通用 agent 已经“会循环”，但默认循环常见三个问题：

- 只围绕当前答案打磨，却不重新看目标
- 沿着同一条推理路径小修小补
- 把“看起来很忙”误判成“真的有进展”

这个 skill 用三件事来对抗这些问题：

- 反思
  检查哪里可能误解了需求，哪里最薄弱。
- 视角切换
  在合适的时候换一个角度重新看问题。
- 横向比较
  判断这一轮是否真的比上一轮更好，而不只是形式不同。

### 安装方式

把 `skills/loop` 目录复制或软链接到你的 agent skills 目录中。

示例目标结构：

```text
<agent-skills-root>/
  loop/
    SKILL.md
    references/
      patterns.md
      troubleshooting.md
```

如果你的平台对 skills 根目录有不同要求，也建议保留 `loop/` 内部结构不变，这样相对引用文件还能正常工作。

### 调用建议

这个 skill 更适合显式调用，用在那些明显受益于多轮推进的任务上。

示例：

```text
Use the loop skill to refine this draft in 3 rounds.
```

```text
Use the loop skill to explore multiple approaches before choosing one.
```

```text
用 loop skill，分 4 轮从不同角度分析这个方案。
```

适合的任务包括：

- 对同一份内容逐轮打磨
- 分轮研究、整理、补全内容
- 从多个方向探索方案
- 一次性回答往往不够深的开放性任务

### 集成建议

如果你要把它接入更大的 skills 体系，建议把它当作“通用迭代层”，而不是领域 skill。

更合理的分工是：

- 领域 skill 决定“什么叫做好结果”
- `loop` 决定“多轮怎么推进才更有效”

也就是说，`loop` 更适合作为补充层，而不是替代任务本身。

### 维护建议

如果你后续继续演化这个 skill，建议保护下面这些特性：

- 保持轻量
- 不要把反思写成机械 ritual
- 不要让每轮视角切换都显得刻意
- 保留“真实进展”和“假进展”的区分

通常不建议的方向：

- 增加太多强制确认
- 把 skill 膨胀成完整状态机
- 强行要求每轮都演戏式切 persona
- 把它过度收窄到代码场景

### 扩展点

如果你要继续扩展这个仓库，比较安全的修改点包括：

- 调整每轮报告格式
- 在 `patterns.md` 里细化不同 loop 模式
- 在 `troubleshooting.md` 里补充恢复策略
- 在 `SKILL.md` 里微调触发描述

建议尽量保持 loop 的核心概念稳定，把变化放在外围指导层。

### 贡献建议

如果你准备继续公开维护这个仓库，比较好的提交说明方式是同时写清楚：

- 你观察到了什么失效模式
- 你改了 skill 的哪一部分
- 你预期 agent 会出现什么新行为

这样这个仓库会更贴近真实 agent 行为，而不是停留在抽象流程设计上。

### License

发布前补充适合你的开源协议，例如 MIT。

## English

### Overview

This repository contains a reusable agent skill package named `loop`.

The skill is designed for general-purpose agents that need to work in multiple rounds instead of producing a one-shot answer. Its goal is not to enforce a rigid workflow, but to give the agent a lightweight iterative thinking structure that improves task fit and reduces shallow repetition.

Core design goals:

- improve alignment with the user's actual intent
- reduce single-path dependence during iteration
- turn multiple rounds into accumulated learning instead of churn

### Repository Layout

```text
repo/
  README.md
  skills/
    loop/
      SKILL.md
      references/
        patterns.md
        troubleshooting.md
```

File roles:

- `skills/loop/SKILL.md`
  Main skill definition. Contains the loop contract, round structure, reporting format, and high-level behavior.
- `skills/loop/references/patterns.md`
  Describes the main loop styles: refinement, accumulation, and exploration.
- `skills/loop/references/troubleshooting.md`
  Covers failure modes such as false progress, premature pass, drift, and getting stuck.

### Mental Model

`loop` is best understood as a thinking scaffold, not an orchestrator.

The skill encourages each round to move through a lightweight sequence:

1. Execute
2. Reflect
3. Shift perspective
4. Compare against previous rounds
5. Verify
6. Judge whether to continue

The value comes from better thinking between rounds, not from ceremony.

### Why This Skill Exists

Many general agents can already iterate, but default iteration often has three weaknesses:

- it optimizes the current answer without revisiting the real goal
- it keeps following the same reasoning path with small wording changes
- it mistakes visible activity for real progress

This skill addresses those weaknesses with three built-in ideas:

- Reflection
  Ask what may be misread, weak, or underfit.
- Perspective shifting
  Revisit the same work from a different angle when useful.
- Cross-round comparison
  Check whether the new round is materially better, not merely different.

### Installation

Copy or symlink the `skills/loop` directory into your agent's skill directory.

Example target layout:

```text
<agent-skills-root>/
  loop/
    SKILL.md
    references/
      patterns.md
      troubleshooting.md
```

If your platform expects a different root structure, keep the internal `loop/` folder intact so the relative reference files still resolve correctly.

### Invocation

This skill is designed to be invoked explicitly when a task benefits from multi-round work.

Examples:

```text
Use the loop skill to refine this draft in 3 rounds.
```

```text
Use the loop skill to explore multiple approaches before choosing one.
```

```text
Use the loop skill to analyze this plan from different angles over 4 rounds.
```

Good fits:

- iterative refinement of one artifact
- research or synthesis done section by section
- exploration of alternatives
- open-ended tasks where one-shot output is usually too shallow

### Integration Notes

When integrating this skill into a broader skill ecosystem, treat it as a general iterative wrapper, not as a domain skill.

Recommended usage pattern:

- let domain-specific skills define what good work looks like
- let `loop` define how multi-round improvement happens

In other words, `loop` should usually complement another task or domain instruction rather than replace it.

### Maintenance Guidelines

If you evolve this skill, protect these properties:

- keep the loop lightweight
- avoid turning reflection into repetitive ritual
- avoid making perspective shifts feel forced in every round
- preserve the distinction between meaningful progress and false progress

Changes that often make the skill worse:

- adding too many mandatory confirmations
- expanding the skill into a full task state machine
- forcing dramatic persona-switching every round
- overfitting the skill to coding tasks only

### Extension Points

If you want to adapt this repository, the safest extension points are:

- adjusting the per-round report format
- refining pattern guidance in `patterns.md`
- improving recovery heuristics in `troubleshooting.md`
- tightening or loosening the invocation description in `SKILL.md`

Try to keep the core loop concept stable while evolving guidance around it.

### Contributing

If you publish improvements, it helps to include:

- what failure mode you observed
- what change you made to the skill
- what new behavior you expect from agents

This keeps the repository grounded in real agent behavior rather than abstract process theory.

### License

Add the license that matches your publishing plan before release, such as MIT.
