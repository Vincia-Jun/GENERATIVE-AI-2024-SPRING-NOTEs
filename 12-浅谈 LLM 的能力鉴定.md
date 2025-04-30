# 12 浅谈 LLM 的能力鉴定


## 📝 标答的评估基准（选择题）
- Massive Multitask Language Understanding（MMLU）：[论文地址](https://arxiv.org/abs/2009.03300) & [排行榜单](https://huggingface.co/blog/zh/open-llm-leaderboard-mmlu)
  
- 《[Large Language Models Are Not Robust Multiple Choice Selectors](https://arxiv.org/abs/2309.03882)》 揭示了选择题评估基准的不足：
  - **随机的概率输出影响性能：** 模型每次输出的答案很可能不一致，导致不同论文的评估结果有差异。
  - **输出的规则约束影响性能：** 若只可以输出选项，不可以输出其他內容，那么模型会专注于指令跟随，而不是推理过程。
  - **题目的条件设置影响性能：** 将选项位置调换/改变选项的代号都会影响最终的性能。比如上文的实验将所有正确答案移至“A”选项，那么 Llama-30B 模型的性能会直接暴涨 15.2%，直接逆袭至 MMLU 数据集的冠军。
  
---


## 📖 非标的评估基准（翻译、摘要、写作...）
- 传统方法譬如使用 BLEU 评估翻译任务，使用 ROUGE 来评估摘要任务。
  
- 使用**人工**进行评估：
  - **[Chatbot-Arena](https://lmarena.ai/)**：大模型输出质量人类在线打分的平台。
  - **[Chatbot-Arena-Leaderboard](https://lmarena.ai/?leaderboard)**：公认的 LLM 性能排行榜。
    
- 使用**更强大的语言模型**进行评估：
  - 《[Can Large Language Models Be an Alternative to Human Evaluations?](https://arxiv.org/abs/2305.01937)》
  - 《[A Closer Look into Automatic Evaluation Using Large Language Models](https://arxiv.org/abs/2310.05657)》
  - 《[Judging LLM-as-a-Judge with MT-Bench and Chatbot Arena](https://arxiv.org/abs/2306.05685)》
    - 使用 GPT-4 评估，共有 80 道非标准答案的题目。
    - MT-Bench 与 Chatbot-Arena 的相关性很高，基本可以认为能够替代人类评估。
  - 《[Length-Controlled AlpacaEval: A Simple Way to Debias Automatic Evaluators](https://arxiv.org/abs/2404.04475)》
    - 大型语言模型评估过程可能偏袒更长的回答，AlpacaEval 基准针对此问题进行了优化。

---


## 🧪 通用基准：[BIG-bench](https://github.com/google/BIG-bench)

- 由 Google 主导，跨 132 个研究机构，444 位作者

- 涵盖多样化评测题型，Emoji Movie、ASCII识别、象棋一步将军等 

---



## 🧭 阅读与记忆能力：Needle in a Haystack
- 将特定信息放置超长文本不同位置 → 在超长文本中寻找一句话 → 考察语言模型的记忆能力

- Result：[GPT-4-128 Context Testing](https://github.com/gkamradt/LLMTest_NeedleInAHaystack/blob/main/img/GPT_4_testing.png)
  - 64K 能够处理很好，128K 放置文章前面会失效。

- Result：[Claude2.1-128 Context Testing](https://github.com/gkamradt/LLMTest_NeedleInAHaystack/blob/main/img/Claude_2_1_testing.png)
  - Claude 以长文著称，但测试结果很烂，官方出来辟谣，需要添加提示：
  - "Here is the most relevant sentence in the context:"
 
## 🦊 伦理导向的测试：MACHIAVELLI Benchmark
- 《[Measuring Trade-Offs Between Rewards and Ethical Behavior in the MACHIAVELLI Benchmark](https://arxiv.org/abs/2304.03279)》

- Reward VS Ethical Behavior，测试语言模型是否会“未达目的不择手段”？ 

- 经过奖励训练的模型会逐渐忽略道德的约束，为经过微调的 GPT-4 能够坚守道德底线。

---


## 🧠 心智理论的测试：Theory of Mind
- 心智理论（Theory of Mind）：揣测他人想法的能力，即 A 知道 B 知道的事情。

- 《[Sparks of Artificial General Intelligence: Early experiments with GPT-4](https://arxiv.org/abs/2303.12712)》

- 《[Evaluating Large Language Models in Theory of Mind Tasks](https://arxiv.org/abs/2302.02083)》

- 《[FANToM: A Benchmark for Stress-testing Machine Theory of Mind in Interactions](https://arxiv.org/abs/2310.15421)》
  - 设计 BenchMark 需要避免模型在预训练中接触过的训练资料
  - 设计收集的新的数据，发现大模型 FANToM 心智理论基准上表现极差，直接扑街。

---

## ⚠️ 不能完全相信 Benchmark 的结果

- 很多的 datasets 都是公开的，LLM 可能在预训练过程接触过测试题。
  
- 《[Rethinking Benchmark and Contamination for Language Models with Rephrased Samples](https://arxiv.org/abs/2311.04850)》
  - 将 MMLU 数据集换个问法进行训练，13B 模型效果直逼 GPT-4
 
- 《[Task Contamination: Language Models May Not Be Few-Shot Anymore](https://arxiv.org/abs/2312.16337)》
  - datasets prior >>> datasets post，预训练前提出的 dataset 效果明显好于预训练之后出现的 datasets
  - 为了更加严谨地说明，可以直接尝试让模型输出类似的训练资料，用于判断模型是否见过这些资料。

---



## 💸 其他考量：价格、速度、资源开销  

- [价格、速度、资源开销的比较平台](https://artificialanalysis.ai/)
  
---

## 🧾 课堂小结

本节课围绕“如何评估语言模型的能力”展开，深入探讨了从选择题测评到主观生成任务评估的挑战。通过 Chatbot Arena 与 MT-Bench 等方式引入人类和模型评审机制，同时引入伦理测试和心智认知测试，拓展语言模型评估的广度与深度，这些维度的测试还是蛮有意思的。最后提醒我们，Benchmark 结果可能不可靠，需警惕数据泄漏与测试集污染。

---
