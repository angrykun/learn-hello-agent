# Hello-Agents从零构建智能体 - Learning Progress

## Daily Logs

## Session 1 - 2026-05-12

**完成章节：** 第1-3章（智能体基础理论）

**核心收获：**
- 智能体 = LLM（推理）+ 工具（执行）+ 感知（反馈）
- 传统范式演进逻辑：问题复杂度倒逼设计演进
- LLM智能体本质变化：知识从显式编程 → 隐式预训练
- Function Calling = 决策与执行解耦
- requires_action = 模型决定需要工具结果，代码负责执行（≠用户批准）
- 三大能力边界：幻觉、长程推理失败、Token限制 → 催生Memory/RAG/上下文工程

**待复习概念：** 智能体定义、感知-行动闭环、传统范式演进、LLM智能体本质、Transformer原理、Function Calling机制、requires_action含义

## Session 2 - 2026-05-12

**完成章节：** 第4-7章（智能体范式构建+低代码平台+框架+HelloAgents设计）

**核心收获：**
- ReAct = 边想边做，适合多步开放任务
- Plan-and-Solve = 先规划再执行，适合步骤清晰的结构化任务
- Reflection = 行动后自审查，叠加在其他范式上使用
- 低代码平台分两类：Workflow式（n8n） vs AI Native（Dify/Coze）
- LangGraph用图建模Agent流程：Node = 每一步，Edge = 流转条件
- HelloAgents设计理念：万物皆为Tool，减少概念抽象层次
- 自建框架的价值：出问题了能自己修，想加功能自己能加

**待复习概念：** ReAct范式、Plan-and-Solve范式、Reflection范式、LangGraph节点边模型、Tool统一抽象
