# Hello-Agents《从零开始构建智能体》学习大纲

> 项目来源：[Datawhale Hello-Agents](https://github.com/datawhalechina/Hello-Agents)
> 学习模式：理论 + 实践并重，动手贯穿始终
> 目标：从 LLM 的使用者蜕变为智能体系统的构建者

---

## Overview | 概述

本教程是 Datawhale 社区的系统性智能体学习教程，聚焦**真正的 AI Native Agent**（而非流程驱动的低代码平台类 Agent）。教程从智能体的核心原理出发，深入其架构，理解经典范式，并最终亲手构建起属于自己的多智能体应用。

全书 16 章分五部分：
- **第一部分**：智能体与语言模型基础（第 1-3 章）
- **第二部分**：构建你的大语言模型智能体（第 4-7 章）
- **第三部分**：高级知识扩展（第 8-12 章）
- **第四部分**：综合案例进阶（第 13-15 章）
- **第五部分**：毕业设计及未来展望（第 16 章）

---

## Prerequisites | 先修知识

- 基础 Python 编程能力
- 了解如何通过 API 调用 LLM（基本概念即可）
- 无需深厚的算法或模型训练背景

**环境准备：**
- Python 3.10+
- `openai` + `python-dotenv`（第四章起）
- 本地阅读：克隆 `https://github.com/datawhalechina/Hello-Agents`
- 在线阅读：https://hello-agents.datawhale.cc

---

## Learning Objectives | 学习目标

1. 理解智能体的概念、历史与经典范式（从反射智能体到 LLM 驱动的智能体）
2. 掌握主流低代码平台（Coze、Dify、n8n）和代码框架（AutoGen、AgentScope、LangGraph）的使用
3. 从零构建自己的智能体框架 HelloAgents，兼具"用轮子"与"造轮子"的能力
4. 掌握 Memory、RAG、上下文工程、MCP 协议、Agentic RL 等高级技术
5. 完成综合项目（智能旅行助手、DeepResearch Agent、赛博小镇）
6. 通过毕业设计构建完整的多智能体应用

---

## Learning Path | 学习路径

### Phase 1 · 理解智能体的"前世今生"（第 1-3 章）

**核心问题：智能体到底是什么？它为什么需要大语言模型？**

> 很多教程上来就讲 ReAct、Tool Calling，但不知道这些范式解决的是什么根本问题。这三章帮你建立对"智能体"本质的理解。

#### 第 1 章 · 初识智能体
- **根因起点**：为什么需要"智能体"这个概念？——从传感器/执行器的感知-行动闭环出发
- 传统智能体的演进路径：反射式 → 基于模型 → 基于目标 → 基于效用 → 学习型
- LLM 驱动的新范式：与传统智能体的本质区别在哪里？
- **工程要点**：LLM 作为"大脑"改变了什么？——知识来源从显式编程 → 隐式预训练
- **快速理解检测**：能否解释"智能体为什么要感知环境"这个问题的本质？
- **实践任务**：对照自己的使用经验，列出 LLM 出现前后，智能体能力的变化

#### 第 2 章 · 智能体发展史
- 从符号主义到连接主义：为什么最终是 LLM 带来了突破？
- 关键里程碑：ReAct、Toolformer、AutoGPT、ChatGPT Plugins、Agent 大爆发（2023-2025）
- **快速理解检测**：2023 年之前为什么没有真正的 LLM Agent？GPT-3/4 的什么特性使 Agent 成为可能？
- **思考问题**：如果下一代模型上下文窗口扩大到 100M Token，Agent 形态会发生什么根本性改变？

#### 第 3 章 · 大语言模型基础
- Transformer 架构的本质：为什么 attention 机制是关键？
- **根因讲解**：LLM 的"能力"从哪里来？——不是知识存储，是模式识别与推理
- 提示工程（Prompt Engineering）：不是技巧，是与"大脑"沟通的协议
- 主流 LLM 及选择策略：GPT-4o / Claude / Qwen / DeepSeek 等
- **工程要点**：Function Calling / Tool Use 机制 —— 模型"伸手"的原理（requires_action = 模型决定调函数，代码负责执行）
- LLM 的能力边界：幻觉、长程推理失败、Token 限制
- **快速理解检测**：能解释"为什么 LLM 无法直接操控你的文件系统"吗？
- **实践任务**：用 Function Calling 实现一个天气查询工具，对比书中示例代码与当前 OpenAI SDK 最新写法

---

### Phase 2 · 亲手实现经典范式（第 4-7 章）

**核心问题：智能体的"思考"和"行动"如何配合？**

> 这一阶段是全书动手密度最高的阶段。每一种范式都要亲手实现，理解背后的工程挑战。

#### 第 4 章 · 智能体经典范式构建
- **环境配置**：Python 3.10+ / openai / python-dotenv + `.env` 文件配置
- **基础封装**：HelloAgentsLLM 客户端类的实现（当前 OpenAI SDK 已变化，书中的 `openai` 包写法需更新）
- ReAct 范式：边想边做 —— "思考"（Thought）和"行动"（Action）如何交织
- Plan-and-Solve 范式：先规划再执行 —— 解决了什么问题？ReAct 的瓶颈在哪里？
- Reflection 范式：自我反思与修正
- **工程要点**：多轮对话的 Tool Calling 循环、解析模型输出格式、处理工具调用失败的重试机制
- **实践任务**：分别实现三种范式，对比它们在同一个复杂任务（如"帮我规划厦门三日游"）上的表现差异

#### 第 5 章 · 基于低代码平台的智能体搭建
- Coze / Dify / n8n 的设计理念对比：为什么说这些是"流程驱动"而非真正的 AI Native？
- Dify 保姆级操作流程
- **快速理解检测**：低代码平台的智能体和代码框架的智能体，本质区别是什么？
- **思考问题**：在实际项目中，什么场景选低代码平台，什么场景选代码框架？

#### 第 6 章 · 框架开发实践
- AutoGen：多智能体对话框架 —— 多 Agent 协作的通信模式
- AgentScope：国产多智能体平台的使用
- LangGraph：状态机驱动的 Agent 编排 —— 核心概念（State、Node、Edge）
- **工程要点**：框架选型依据：任务复杂度 vs. 灵活性 vs. 维护成本
- **实践任务**：用 LangGraph 实现一个带条件分支的任务路由 Agent

#### 第 7 章 · 构建你的 Agent 框架（HelloAgents）
- **核心理念**：为什么需要自建框架？—— "使用者" → "构建者"的能力跃迁
- HelloAgents 设计哲学：轻量级 + 教学友好 + 基于标准 API + "万物皆为工具"
- **渐进式开发**：每章迭代一个版本（V0.1 ~ V1.0）
- 核心类设计：Agent、Tool、Message、History
- **工程要点**：框架的模块化设计、接口抽象、错误处理
- **快速理解检测**：HelloAgents 为什么把 Memory、RAG、MCP 都抽象为"工具"？
- **实践任务**：基于第 4-6 章的范式代码，搭建 HelloAgents V0.1 基础框架

---

### Phase 3 · 让智能体"记得住、想得清"（第 8-12 章）

**核心问题：为什么智能体会"失忆"？如何让它具备持续学习和协作的能力？**

> 这一阶段使用 Phase 2 构建的 HelloAgents 框架进行扩展，每次扩展都对应一个真实工程问题。

#### 第 8 章 · 记忆与检索
- **根因起点**：LLM 为什么"无状态"？—— 每次 API 调用是独立的，没有连续记忆
- 人类记忆系统的启发：感官记忆 → 工作记忆 → 长期记忆
- 智能体的记忆分层：对话历史、实体知识、程序性经验
- RAG（检索增强生成）：让智能体"查阅资料"
- **工程要点**：向量数据库选型（ChromaDB / FAISS / Qdrant）、Embedding 模型选择、检索策略（密集/稀疏/混合）
- HelloAgents + Memory + RAG 扩展实现
- **快速理解检测**：能解释"为什么光靠上下文窗口无法解决智能体的长期记忆问题"吗？
- **实践任务**：为 HelloAgents 添加记忆模块，实现一个能记住用户偏好的对话 Agent

#### 第 9 章 · 上下文工程
- **根因起点**：为什么有时候模型"听不懂"？—— 不是模型笨，是上下文构造有问题
- 提示注入（Prompt Injection）攻防
- 上下文压缩与摘要策略
- **工程要点**：对话历史的截断策略（最近 N 轮 vs. 摘要压缩）、系统提示的层次设计
- **快速理解检测**：上下文工程的本质是解决什么问题？它和 RAG 的关系是什么？
- **实践任务**：实现一个带上下文摘要的对话 Agent，处理超过 50 轮的长对话场景

#### 第 10 章 · 智能体通信协议
- MCP（Model Context Protocol）：Anthropic 提出的工具调用协议 —— 为什么需要标准协议？
- A2A（Agent-to-Agent）：多智能体协作的通信协议
- ANP（Agent Network Protocol）
- HelloAgents + MCP Server 实战：构建一个天气 MCP Server 并发布
- **工程要点**：协议设计的权衡 —— 通用性 vs. 实现复杂度
- **快速理解检测**：MCP 解决的是什么问题？它和 Function Calling 有什么区别？
- **实践任务**：用 MCP 协议连接 HelloAgents 与外部工具生态

#### 第 11 章 · Agentic RL（智能体强化学习）
- **核心问题**：为什么 Agent 需要"训练"？—— SFT 的局限性在哪里？
- 从 SFT 到 GRPO：训练流程全解析
- 奖励模型设计、RLHF/DPO/GRPO 各自适用场景
- **工程要点**：训练成本、样本效率、稳定性问题
- **快速理解检测**：能解释"为什么 Agent 用 SFT 不够，还需要 RL"吗？
- **思考问题**：在真实业务中，什么场景值得投入去做 Agent 训练？

#### 第 12 章 · 智能体性能评估
- **核心问题**：如何衡量一个 Agent"好不好"？—— 准确率不够用了
- 核心指标：任务完成率、效率（Latency/Token）、稳定性、用户体验
- 基准测试：Benchmark 的设计挑战（Agent 在开放式环境中如何评估？）
- 评估框架：如何设计自动化评估流程
- **实践任务**：为 Phase 2 构建的 Agent 设计一套评估体系，包括指标定义和数据采集

---

### Phase 4 · 综合实战（第 13-16 章）

**核心问题：所有技术如何组合成一个真正能用的系统？**

#### 第 13 章 · 智能旅行助手
- **项目目标**：用 MCP 协议连接多个工具（天气、地图、酒店预订），构建多智能体协作的旅行规划系统
- HelloAgents 框架的综合应用：Memory + RAG + 工具调用 + 多 Agent 协作
- **核心挑战**：子 Agent 之间的任务划分与结果聚合
- **实践任务**：完成旅行助手项目，输出可演示的 Agent 系统

#### 第 14 章 · 自动化深度研究智能体（DeepResearch Agent）
- **核心问题**：如何让 Agent 真正"深度思考"而不是浅层搜索？
- Web 搜索 + LLM 推理的闭环设计
- 迭代式信息获取与验证
- **实践任务**：复现一个简化版 DeepResearch Agent

#### 第 15 章 · 构建赛博小镇
- **核心问题**：多 Agent 社会模拟的可能性——Agent 之间如何"对话"和"协作"？
- AI Town 架构解析：记忆系统、共情机制、对话日志
- **实践任务**：搭建赛博小镇，理解 Agent 社会动态

#### 第 16 章 · 毕业设计
- 构建一个完整的、属于你自己的多智能体应用
- 社区共创项目参考：数据分析 Agent、代码审查 Agent、学术研究 Agent 等（见 Co-creation-projects/）

---

## Extra Chapters | 扩展章节（可选）

| 章节 | 内容 | 优先级 |
|------|------|--------|
| Extra-01 | Agent 面试问题总结 & 参考答案 | 求职方向 |
| Extra-02 | 上下文工程补充知识 | 深化 Phase 3 |
| Extra-03 | Dify 保姆级操作流程 | 快速上手 |
| Extra-04 | Hello-Agents 课程常见问题 | FAQ |
| Extra-05 | Agent Skills 与 MCP 对比解读 | 协议深化 |
| Extra-06 | GUI Agent 科普与实战 | 前沿方向 |
| Extra-07 | 环境配置 | 环境准备 |
| Extra-08 | 如何写出好的 Skill.md | 工程实践 |
| Extra-09 | Agent 应用开发踩坑与经验 | 工程实践 |
| Extra-10 | Agent 自进化 | 前沿方向 |

---

## Success Criteria | 成功标准

- [ ] 能从原理层面解释 ReAct / Plan-and-Solve / Reflection 三种范式的本质差异和各自适用场景
- [ ] 独立实现 HelloAgents V0.1 ~ V1.0 框架，包含 Agent、Tool、Memory、MCP 核心模块
- [ ] 完成至少 1 个综合项目（旅行助手 / DeepResearch / 赛博小镇 / 毕业设计）
- [ ] 能从"构建者"视角评价 LangChain / LangGraph / AutoGen 等框架的设计权衡
- [ ] 理解 Agentic RL 的核心思想，能判断什么场景值得做训练微调
- [ ] 理解上下文工程、Memory、RAG 的关系，能设计智能体的知识架构

---

## Resources | 资源

- **教程主页**：https://github.com/datawhalechina/Hello-Agents
- **在线阅读**：https://hello-agents.datawhale.cc
- **PDF 下载**：https://github.com/datawhalechina/Hello-Agents/releases/latest
- **HelloAgents 框架**：https://github.com/jjyaoao/helloagents
- **配套代码**：项目内 `code/chapter{N}/` 目录