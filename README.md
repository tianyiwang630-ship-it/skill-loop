# Loop Skill

中文 | English

## 中文简介

`loop` 是一个面向通用 agent 的多轮执行与思考 skill。

它的目标不是把 agent 变成死板的流程机，而是在需要多轮推进的任务里，帮助 agent：

- 更贴近用户真实意图
- 避免陷入单一路径依赖
- 把多轮迭代转化为真正的认知收益，而不是重复劳动

这个 skill 不绑定代码场景，也不依赖特定平台。它适用于写作、分析、研究、整理、规划、比较、翻译，以及其他适合多轮推进的任务。

## English Overview

`loop` is a multi-round execution and thinking skill for general-purpose agents.

Its purpose is not to turn an agent into a rigid workflow machine. Instead, it helps the agent during iterative tasks to:

- stay closer to the user's actual intent
- avoid getting trapped in a single path of reasoning
- turn multiple rounds into genuine learning instead of repetitive churn

This skill is not code-specific and is not tied to a single platform. It can be used for writing, analysis, research, planning, comparison, translation, and other tasks that benefit from iteration.

## 核心理念

这个 skill 的核心不是“多跑几轮”，而是让每一轮都更有价值。

它主要依赖三个机制：

- 强制反思：提升命中需求的概率
- 视角切换：避免单一路径依赖
- 横向比较：把多轮变成学习，而不是重复

在设计上，这三者被写成默认思考流程，而不是沉重的纪律约束。

## Core Ideas

The point of this skill is not merely to "run more rounds", but to make each round more useful.

It centers on three mechanisms:

- Reflection: increase the chance of matching the real need
- Perspective shifting: reduce single-path dependence
- Cross-round comparison: turn iteration into learning rather than repetition

These are implemented as a default thinking structure, not as heavy-handed discipline rules.

## Skill Flow

每一轮 loop 大致遵循以下结构：

1. Execute
2. Reflect
3. Shift Perspective
4. Compare Across Rounds
5. Verify
6. Judge

This structure is intentionally lightweight. The agent is encouraged to use it as a thinking scaffold, not as a theatrical ritual.

## 适用场景

- 打磨同一份内容，逐轮提升质量
- 分轮覆盖不同子主题，逐步补全内容
- 从不同角度探索多个方案，再进行比较
- 对复杂任务进行多轮推进，而不是一次性给出单一路径答案

## Good Fit

- refining the same artifact over multiple rounds
- accumulating coverage section by section
- exploring alternatives from different angles
- handling open-ended tasks that benefit from repeated improvement instead of one-shot output

## 仓库内容

当前仓库包含一个 skill 包：

- `skills/loop/SKILL.md`: 主 skill 定义
- `skills/loop/references/patterns.md`: 不同 loop 模式的说明
- `skills/loop/references/troubleshooting.md`: 当 loop 卡住、漂移或假进展时的处理方法

## Repository Contents

This repository currently contains one skill package:

- `skills/loop/SKILL.md`: main skill definition
- `skills/loop/references/patterns.md`: guidance for different loop patterns
- `skills/loop/references/troubleshooting.md`: recovery strategies for stuck loops, drift, and false progress

## 推荐目录结构

如果你准备把它发布到 GitHub 并作为可复用 skill 仓库维护，更推荐使用下面的结构：

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

如果仓库永远只包含这一个 skill，那么保持单 skill 的简洁结构也完全可以。

## Recommended Layout

If you plan to publish and maintain this as a reusable GitHub skill repository, this structure is recommended:

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

If the repository will always contain just this single skill, a simpler one-skill layout is also perfectly fine.

## 使用方式

把这个 skill 放到你的 agent skills 目录中，然后在需要时显式调用它，例如：

```text
Use the loop skill to refine this draft in 3 rounds.
```

```text
用 loop skill，分 4 轮从不同角度分析这个方案。
```

这个 skill 特别适合以下类型的请求：

- “请多轮优化这段内容”
- “试几个不同方向再比较”
- “不要只给一个答案，分轮推进”

## Usage

Place this skill in your agent's skills directory and invoke it explicitly when a task would benefit from iteration, for example:

```text
Use the loop skill to improve this draft in 3 rounds.
```

```text
Use the loop skill to explore three different directions for this idea.
```

It works especially well for requests like:

- "improve this over several rounds"
- "try different directions and compare them"
- "don't give a one-shot answer; iterate"

## 设计取向

这个项目更接近一种通用 agent 的思考增强层，而不是任务编排器。

它不追求：

- 复杂的状态机
- 沉重的交互确认
- 对所有任务一刀切的硬约束

它更重视：

- 在多轮任务中维持目标感
- 用轻量反思修正方向
- 用不同视角打开思路
- 用跨轮比较识别真实进展

## Design Philosophy

This project is closer to a thinking amplifier for general agents than to a strict task orchestrator.

It does not aim for:

- complex state machines
- heavy confirmation rituals
- rigid enforcement for every task

It does aim for:

- preserving task direction across rounds
- using lightweight reflection to self-correct
- widening thought through perspective shifts
- recognizing real progress through cross-round comparison

## License

You can add the license of your choice before publishing, such as MIT.
