---
title: Interpreting Rewards from Inverse Reinforcement Learning
title_zh: 从逆向强化学习中解释奖励
authors: "Chow, J., Yang, Y., Laschowski, B."
date: 2026-07-13
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.08.736783v1.full.pdf"
tags: ["query:upa"]
score: 9.0
evidence: 逆向强化学习从观测行为中解释奖励函数
tldr: 逆强化学习虽能从行为中恢复奖励函数，但如何解读这些奖励仍是一大挑战。为此，论文提出一个结合奖励函数分析、潜在模式分配与短历史行为分析的新框架，用于推断潜在动机与行为动态。在大型多智能体社交互动数据集上实例化后，框架将学到的潜在模式解释为谨慎型与波动型动机，从而揭示了奖励函数反映出的行为动态差异。该工作为逆向解读智能行为与决策背后的隐藏奖励提供了可行途径。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-08-736783-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1854, \"height\": 299, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-08-736783-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1843, \"height\": 709, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-08-736783-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1768, \"height\": 768, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-08-736783-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1769, \"height\": 859, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-08-736783-v1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1781, \"height\": 627, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-08-736783-v1/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1821, \"height\": 867, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-08-736783-v1/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1779, \"height\": 1264, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-08-736783-v1/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1780, \"height\": 622, \"label\": \"Figure\"}]"
motivation: 逆强化学习恢复的奖励函数难以解读，制约了对智能行为与决策背后动机的理解。
method: 提出融合奖励函数分析、潜在模式分配和短历史行为分析的新框架，并采用switching IRL实例化。
result: 在社交互动数据中学到谨慎与波动两种动机模式，揭示了不同行为动态特征。
conclusion: 该框架能有效逆向工程并解读驱动智能行为的潜在奖励，具有重要应用前景。
---

## 摘要
逆向强化学习可以从观察到的行为中恢复奖励函数，但解释这些奖励仍然是理解智能行为和决策制定的根本挑战。为了应对这一挑战，我们引入了一个新颖的奖励解释框架，该框架结合了奖励函数分析、潜在模式分配和短时行为分析，以推断潜在的动机和行为动力学。作为概念验证，我们在大规模多智能体社交互动数据集上使用切换逆向强化学习实现了该框架。我们的框架将学习到的潜在模式解释为谨慎和易变的动机特征，表明恢复的奖励函数可以揭示行为动力学的独特模式。更广泛地说，这些发现表明所提出的框架为逆向工程和解释智能行为与决策制定背后的潜在奖励提供了一种有前景的方法。

## Abstract
Inverse reinforcement learning can recover reward functions from observed behavior, but interpreting those rewards remains a fundamental challenge for understanding intelligent behavior and decision-making. To address this challenge, we introduce a novel framework for reward interpretation that combines reward-function analysis, latent mode assignments, and short-history behavioral analysis to infer latent motivations and behavioral dynamics. As a proof-of-concept, we instantiated the framework using switching inverse reinforcement learning on a large-scale dataset of multi-agent social interactions. Our framework interpreted the learned latent modes as  cautious and  volatile motivational profiles, demonstrating that recovered reward functions can reveal distinct patterns of behavioral dynamics. More broadly, these findings suggest that the proposed framework provides a promising approach for reverse-engineering and interpreting latent rewards underlying intelligent behavior and decision-making.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义
- **核心问题**：逆强化学习可从观测行为恢复奖励函数，但如何**解读这些奖励**（即从奖励函数中推断潜在动机与行为模式）仍是一个根本挑战，特别在包含多种动机的动态社交互动中。
- **整体含义**：本研究旨在提出一种**奖励解释框架**，将恢复的奖励函数转化为可理解的动机特征与行为动力学，从而为“逆向工程”智能决策背后的隐藏奖励提供可行方法。

### 2. 论文提出的方法论
- **总体框架**：四步递进式解释流程，将逆强化学习的输出（潜在模式、奖励函数、策略）转化为可解释的动机概况。
  1. **奖励函数分析**：将恢复的奖励函数表示为状态‑动作奖励矩阵，通过对比矩阵结构识别不同潜在模式下的行为偏好。
  2. **潜在模式分配**：利用维特比解码恢复最可能的潜在模式序列，考察模式在行为轨迹上的时间一致性。
  3. **短历史行为分析**：基于L1正则化逻辑回归，筛选与目标行为高度相关的短行为序列，并结合奖励函数与策略计算偏好排名（式6‑10），从而揭示模式特有的时序行为模式。
- **底层逆强化学习模型**：框架实例化在 **切换逆强化学习**上，该模型将行为建模为多个离散潜在模式间的切换，每个模式拥有独立的奖励函数和历史依赖的控制策略；通过最大化证据下界（式5）进行期望最大化训练，同时恢复模式序列、奖励函数和策略。

### 3. 实验设计
- **数据集**：大规模多智能体社交互动数据集（小鼠的常驻-入侵者范式），共58条轨迹（46训练/12测试），每条轨迹2000帧，行为状态标注为攻击、探查、骑跨、其他四类。
- **预处理方案对比**：
  - **标准表示**：保留所有帧级转换（含大量自转换）。
  - **压缩表示**：移除连续自转换，仅保留行为间转换。
  - **状态编码**：一阶（当前行为）与二阶（当前与前一行为的外积编码）。
- **对比条件**：不同潜在模式数（K=1~4）、轨迹表示、编码阶数，以行为预测准确率为基准（随机基线25%）。
- **评价方式**：训练/测试预测准确率、奖励矩阵可视化、维特比模式分配图、短历史排序值的定性解释。

### 4. 资源与算力
- 文中**未明确说明**所使用的GPU型号、数量或训练时长，亦未提及算力消耗情况。

### 5. 实验数量与充分性
- **实验组合**：对K=1~4这4个值、两种轨迹表示、两种编码阶数进行了交叉评估，合计至少**16组核心对比实验**；此外还包括奖励矩阵分析、模式分配可视化、短历史分析及未压缩数据的附加实验。
- **充分性评价**：实验覆盖了主要的模型超参数和预处理策略，并通过预测性能、模式稳定性、行为序列解释等多角度验证框架。但由于仅在一个数据集（且行为类别粗糙）上验证，**方法泛化性的证据尚不充足**；对比基线也仅限于随机预测，缺乏与其他逆强化学习解释方法的直接对比。

### 6. 论文的主要结论与发现
- 该框架成功将恢复的奖励函数解读为两种可区分的**动机特征**：**谨慎型**（对攻击转换普遍赋予低奖励）与**易变型**（对攻击转换赋予高奖励）。
- 压缩轨迹表示（去除自转换）对稳定模式分配至关重要；未压缩数据会导致模型学习行为持续性而非切换动态，使模式分配碎片化。
- 短历史行为分析进一步揭示了两种动机在时序模式上的差异（如易变型偏好探查‑攻击循环），从而补充了奖励函数自身的局部偏好信息。
- 整体表明，**结合奖励函数、模式分配与短历史行为分析**的框架，能够为逆强化学习的解释性提供一种可操作且富有洞察力的方法。

### 7. 优点
- **框架创新性**：首次将逆强化学习的解释性提升为核心目标，提出多视角组合分析的统一范式。
- **强调预处理**：明确指出行为数据中自转换对模型学习的影响，并提出压缩轨迹方案以聚焦行为切换动态。
- **可解释性深度**：不仅解释“为什么”（奖励函数偏好），还通过短历史分析揭示“何时”（时序模式）发生特定动机行为。
- **实证证据丰富**：通过预测性能、模式一致性、行为序列排序等多种方式验证解释的合理性。

### 8. 不足与局限
- **数据集单一**：仅在小鼠社交行为的单一数据集上验证，行为类别有限（4类），结论的跨物种、跨场景迁移性未知。
- **对比基线薄弱**：主要与随机概率对比，未与其它奖励解释方法或动机推断模型（如动态IRL）进行定量比较。
- **模型表达能力受限**：使用有限阶状态编码，难以捕捉长程依赖；深层内部表示仍不透明。
- **解释仍存在黑箱成分**：虽然框架提供了动机标签和行为序列关联，但奖励函数和策略的**内部表征机制**未得到揭示。
- **计算开销未报告**，无法评估该方法在大规模应用下的可行性。

（完）
