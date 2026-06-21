---
type: rejected
status: archived
decided_by: Claude (CTO agent review)
verdict: 多 Agent 网络永久禁止；MBclaw 不是 Agent 框架
date: 2026-06-21
---

# Agent 网络与多 Agent 协作 — 永久放弃

## 假想方案核心
将 MBclaw 演化为多 Agent 平台：
- ExtractorAgent + ClassifierAgent + SchedulerAgent + ReviewerAgent + CoordinatorAgent
- Planner/Executor 双层
- Agent 之间通过 pub/sub 协作
- 每个 Agent 持自己的状态/存储
- "循环博弈"提升质量

## 否决理由
1. **角色错位**：MBclaw 是**被 Agent 调用的记忆服务**，不是 Agent 框架
2. **多 Agent = 复杂度指数增长**：通信、状态、一致性、调试成本全部爆炸
3. **循环博弈无收益证据**：同模型互评有系统性偏见，已在 dual-key 否决
4. **违反 R0 三大限制**：复杂 Agent 网络 / 循环博弈结构 / 分布式
5. **Agent 框架赛道有 OpenHands/LangGraph/Letta**：MBclaw 重复造轮子无意义

## 替代方案（R0 落地）
**MBclaw 不跑 Agent**。所有"代理"由外部框架完成：
```
OpenHands / Claude Code / 自写 App
        │ HTTP REST
        ▼
   MBclaw（纯记忆服务）
```

R2 中后期最多 **1 个 ReflectionAgent**：
- 单步循环（max_steps=1）
- 3 个工具（2 读 1 写）
- 用户主动触发，无后台运行
- 详见 Design `agent/AGENT-r0.md`

## 教训
> "多 Agent 协作"是 2024-2025 年最被高估的架构模式。
> 多数任务用单 Agent + 好的工具就能完成。
> 多 Agent 增加的是协调复杂度，不是解题能力。
> MVP 阶段引入 = 用复杂度交换"看起来很 AI"。

## 关联
- 设计：[[architecture/ARCH-r0]] §6
- 详细 Agent 评审：MBclaw `design/agent/AGENT-r0.md`
- 同类否决：[[2026-06-21_dual-key-and-subagent]] [[2026-06-21_auto-mode]] [[2026-06-21_collision-engine]]
