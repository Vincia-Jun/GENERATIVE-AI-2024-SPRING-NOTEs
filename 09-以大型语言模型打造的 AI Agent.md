# 09-以大型语言模型打造的 AI Agent

## 🧩 AI 使用方式的演进

- **目前的 AI 使用范式**：一次性任务处理  
  - 示例：问问题、写文案、翻译

- **未来的 AI 的使用范式**：具备目标与自主能力的 AI Agent，应对多步骤、多变化的情景
  - 示例：AI 接收一个目标后能自主规划、记忆、反思、行动
  - 预测：2024-04-12 处于 Agent 的萌芽爆发期，预估 2025-04 是 Agents 遍地跑的时代。

---


## 🚀 AI Agent 的研究案例
近年来，AI Agent 的研究与应用迅速发展，涌现出一系列具有代表性的项目和系统。例如，AutoGPT、AgentGPT、BabyAGI 和 Godmode 展示了 LLM 驱动下的自动化任务执行能力；AI Agents 形成的虚拟村落模拟了社会行为互动的多智能体环境；Voyager 项目实现了在 Minecraft 游戏中自主学习与探索；LLM 控制机器人在物理世界中展现了感知与动作的结合；而在自动驾驶领域，Talk2Drive 让语言模型参与实时决策。同时，诸如 MemGPT（记忆增强）、RL-VLM-F（执行能力）、DEPS（动态计划修正）、ReAct 和 Reflexion（经验反思机制）等研究不断推进 Agent 智能体的能力边界。这些系统不仅提升了智能体的自主性与适应性，也为构建通用智能体奠定了基础。相关内容可参考以下拓展资料中的论文与项目链接。

---

## 🔄 Agent 与环境的交互架构
![image](https://github.com/Vincia-Jun/GENERATIVE-AI-2024-SPRING-NOTEs/blob/main/Figs/09-%E4%BB%A5%E5%A4%A7%E5%9E%8B%E8%AF%AD%E8%A8%80%E6%A8%A1%E5%9E%8B%E6%89%93%E9%80%A0%E7%9A%84%20AI%20Agent-00.png)
AI Agent 是一个具有感知、规划与执行能力的智能系统，其与环境的交互遵循一个闭环架构。这个交互闭环使得 Agent 具备了 自我调节、自主决策与持续优化 的能力，是实现智能体泛化能力与复杂任务适应能力的基础。

---

### 🧾 课堂小结

本节课围绕 AI Agent 的演进趋势、代表性研究案例以及其与环境的交互架构展开。我们从传统一次性任务处理的 AI 使用方式，过渡到具备目标、记忆与自我调节能力的智能体系统，揭示了 AI Agent 在真实世界中实现长期规划与自主行为的潜力。通过案例分析，我们看到了从 AutoGPT 到 Talk2Drive 等项目如何推动 Agent 技术的发展边界，而交互架构中目标驱动、计划执行与记忆反思的循环机制，则是支撑 Agent 智能涌现的关键所在。这些内容为我们理解通用智能的路径提供了重要启发。

---


## 📚 拓展资料
| 说明🔎   | 链接🔗 | 重要⭐ | TODO✅ |
|--------|----------|--------|--------|
| AI-Agent(1): AutoGPT  | [仓库地址](https://github.com/Significant-Gravitas/AutoGPT)| ⭐ |
| AI-Agent(2): AgentGPT | [网页地址](https://agentgpt.reworkd.ai/zh)| ⭐ |
| AI-Agent(3): BabyAGI  | [仓库地址](https://github.com/yoheinakajima/babyagi)| ⭐ |
| AI-Agent(4): Godmode  | [网页地址](https://godmode.space/?ref=futuretools.io)| ⭐ |
| AI Agents 形成的村落社群（论文） | [论文地址](https://arxiv.org/abs/2304.03442) | ⭐⭐⭐ |
| AI Agents 形成的村落社群（讲解） | [视频地址](https://www.youtube.com/watch?v=G44Lkj7XDsA) | ⭐⭐⭐⭐ |
| AI Agents 玩 Mineraft 游戏 | [论文地址](https://arxiv.org/abs/2305.16291) | ⭐⭐⭐⭐ |
| LLM 操纵机器人：Figure 01 | [视频地址](https://www.youtube.com/watch?v=Sq1QZB5baNw) | ⭐⭐⭐ |
| LLM 操纵机器人：Inner Monologue | [论文地址](https://arxiv.org/abs/2207.05608) | ⭐⭐⭐⭐⭐ |
| LLM 与自动驾驶：Talk2Drive | [论文地址](https://arxiv.org/abs/2312.09397) | ⭐⭐⭐⭐⭐ |
| Agent-记忆功能：MemGPT | [论文地址](https://arxiv.org/abs/2310.08560) | ⭐⭐ |
| Agent-执行功能：RL-VLM-F | [论文地址](https://arxiv.org/abs/2402.03681) | ⭐⭐ |
| Agent-修正计划：DEPS | [论文地址](https://arxiv.org/abs/2302.01560) | ⭐⭐ |
| Agent-反思总结经验：ReAct | [论文地址](https://arxiv.org/abs/2210.03629) | ⭐⭐⭐⭐ |
| Agent-反思总结经验：Reflexion | [论文地址](https://arxiv.org/abs/2303.11366) | ⭐⭐⭐ |
| AI Agents Overview| [论文地址](https://arxiv.org/abs/2309.07864) | ⭐⭐⭐⭐⭐ |
 
