## 一、目标

文献调研的最终目的不是“读很多论文”，而是完成：

**了解领域 → 建立分类 → 掌握技术路线 → 判断研究价值 → 寻找 Research Gap → 产生 Idea → 收敛研究问题 → 设计可执行实验。**

最终应能够回答：

> 这个领域在研究什么？  
> 主流方法有哪些？  
> 当前 SOTA 做到了什么？  
> 现有工作的主要不足是什么？  
> 哪些问题仍值得研究？  
> 我的工作准备解决什么问题？  
> 与哪些 Baseline / SOTA 比较？  
> 用什么环境、数据集和指标验证？

---

# 1. 确定选题范围与关键词

## 1.1 定义研究范围

首先给出一个较宽泛的 Topic，例如：

> VLA + Dexterous Manipulation

此阶段不急于确定最终论文题目，而是确定需要调查的研究空间。

## 1.2 建立关键词树

不要只设置 2～3 个关键词，应从多个维度扩展。

```
研究对象
├── Robotic Manipulation
├── Dexterous Manipulation
└── Bimanual Manipulation

方法
├── Vision-Language-Action
├── Imitation Learning
├── Diffusion Policy
└── Reinforcement Learning

能力
├── Generalization
├── Zero-shot
├── Failure Recovery
└── Long-horizon

数据
├── Demonstration
├── Teleoperation
├── Synthetic Data
└── Human Video

环境 / Benchmark
├── LIBERO
├── RoboTwin
├── RLBench
└── RoboCasa
```

之后通过组合关键词进行检索，例如：

```
"VLA" AND "dexterous manipulation"

"vision language action" AND "zero-shot"

"bimanual manipulation" AND "failure recovery"

"dexterous manipulation" AND "generalization"
```

### 本阶段输出

**Topic + Keyword Tree + Search Queries**

---

# 2. 初步定位期刊 / 会议

建立目标领域的 Venue Pool。

优先调查：

**领域顶会 / 顶刊 → 相关领域顶会 → 高质量专业期刊 → 必要时进一步扩展。**

例如机器人研究：

```
Robotics
├── RSS
├── CoRL
├── ICRA
├── IROS
├── RA-L
├── T-RO
└── IJRR

AI / ML
├── NeurIPS
├── ICML
└── ICLR

Vision
├── CVPR
├── ICCV
└── ECCV
```

Venue 的作用主要是帮助控制文献质量，而不是限制检索范围。

### 本阶段输出

建立：

**Venue List**

记录：

```
Venue
领域
会议 / 期刊
与课题相关程度
重点关注年份
```

---

# 3. 第一轮检索：建立领域地图

此阶段目标不是寻找创新点，而是回答：

> **这个领域到底是怎么组织起来的？**

优先寻找三类论文：

### A. Survey / Review

作用：

- 理解领域历史
    
- 获得术语
    
- 获得分类体系
    
- 找经典论文
    
- 找代表性方法
    

### B. Benchmark / Dataset

作用：

- 理解领域任务设置
    
- 理解实验环境
    
- 理解评价指标
    
- 找 Baseline
    
- 找公开代码与数据
    

### C. Representative Work

重点寻找：

- 奠基工作
    
- 高引用工作
    
- 主流方法
    
- 最近 2～3 年代表工作
    
- SOTA 工作
    

不要一开始就精读。

首先建立一个初始论文池。

### 本阶段输出

**Paper Pool**

例如：

|Paper|Year|Venue|Category|Method|Benchmark|Code|
|---|---|---|---|---|---|---|
|Paper A|2025|CoRL|VLA|Method A|LIBERO|✓|
|Paper B|2026|RSS|IL|Method B|RoboTwin|✓|

---

# 4. 建立领域 Taxonomy

阅读综述和代表论文后，对领域进行分类。

例如：

```
Dexterous Manipulation
│
├── Learning Paradigm
│   ├── RL
│   ├── IL
│   ├── Diffusion
│   └── VLA
│
├── Embodiment
│   ├── Single Arm
│   ├── Bimanual
│   └── Dexterous Hand
│
├── Generalization
│   ├── Seen
│   ├── OOD Object
│   ├── OOD Scene
│   └── Zero-shot
│
└── Task
    ├── Grasp
    ├── Placement
    ├── Contact-rich
    └── Long-horizon
```

建立 Paper Matrix：

|Paper|Task|Method|Data|Generalization|Benchmark|Main Contribution|
|---|---|---|---|---|---|---|
|A|Grasp|VLA|Demo|OOD|X|xxx|
|B|Bimanual|IL|Demo|Seen|Y|xxx|

此时应该能够回答：

> 这个领域主要存在几条技术路线？

---

# 5. 略读论文并筛选核心论文

不要所有论文都精读。

每篇论文先快速回答六个问题：

### Problem

论文解决什么问题？

### Gap

以前的方法哪里不够？

### Method

作者用了什么核心方法？

### Contribution

真正新增了什么？

### Experiment

作者如何证明方法有效？

### Limitation

还存在哪些不足？

然后进行筛选：

```
Level 0：无关 → 删除

Level 1：相关 → 保留

Level 2：重要 → 重点阅读

Level 3：核心 → 精读 + 溯源
```

### 本阶段输出

**Core Paper List**

通常真正需要精读的论文远少于检索到的论文。

---

# 6. 精读 + 文献溯源

对 Level 2 / Level 3 论文进行精读。

重点理解：

```
Problem
↓
Motivation
↓
Method
↓
Architecture
↓
Training
↓
Dataset
↓
Experiment
↓
Baseline
↓
Metrics
↓
Ablation
↓
Limitations
```

同时进行三方向文献溯源。

## Backward Citation

看它引用了谁。

主要寻找：

> 经典工作 / 理论来源 / Baseline / 前置方法

## Forward Citation

看后来谁引用了它。

主要寻找：

> 后续改进 / 最新方法 / SOTA / 对该工作的批评与扩展

## Sibling Work

寻找同期解决相似问题的工作。

主要用于发现：

> 不同技术路线 / 竞争方法

最终形成：

```
Foundational Work
        ↓
    Baseline
        ↓
Representative Work
        ↓
 ┌──────┼──────┐
 ↓      ↓      ↓
SOTA A SOTA B SOTA C
        ↓
 Remaining Gap
```

### 本阶段重点学习

不仅学习算法，还需要学习：

**项目主流 Framework**

例如：

```
PyTorch
robosuite
MuJoCo
Isaac Lab
LeRobot
...
```

**主流实验设计**

例如：

```
Main Results
Generalization
Ablation
Robustness
Failure Analysis
Real-world Experiments
```

同时观察顶会论文：

> 到底需要做到什么程度，才能构成一篇完整 Contribution？

---

# 7. Research Gap Mining

这是从“读论文”进入“做研究”的关键阶段。

为每篇核心论文记录：

```
Assumption
Limitation
Failure Case
Future Work
Unsolved Problem
```

然后进行横向统计。

例如：

```
Paper A → OOD泛化差
Paper B → 长时序容易失败
Paper C → Failure后无法恢复
Paper D → 双臂依赖固定策略
Paper E → Real-world鲁棒性差
```

寻找反复出现的问题。

进一步分析：

```
现象
↓
共同问题
↓
根本原因
↓
Research Gap
```

注意：

**“作者说 Future Work” ≠ 自动成为好的创新点。**

还需要判断：

> 是否重要？  
> 是否尚未被解决？  
> 是否具有技术难度？  
> 是否可以实验验证？

### 本阶段输出

**Research Gap List**

---

# 8. Idea 发散

根据 Gap 产生多个候选 Idea。

例如：

```
Gap
Failure recovery能力不足

↓

Idea A
Failure-aware VLA

Idea B
Hierarchical Recovery Policy

Idea C
Bimanual Collaborative Recovery

Idea D
Online Failure Detection + Replanning
```

不要看到第一个 Idea 就立刻开始写代码。

每个 Idea 建立：

## Idea Card

```
Idea：

Problem：

Existing Limitation：

Research Question：

Hypothesis：

Proposed Method：

Expected Contribution：

Baseline：

Benchmark：

Metrics：

Required Hardware：

Expected Experiments：

Main Risk：
```

---

# 9. Idea 收敛

比较不同 Idea 时重点考虑：

### Novelty

有没有类似工作？

### Value

问题是否值得解决？

### Feasibility

现有设备、代码、时间是否允许？

### Experimentability

能否设计清晰实验验证？

### Contribution

即使成功，贡献是否足够形成论文？

### Engineering Cost

是否需要大量与核心创新无关的工程工作？

如果一个 Idea 无法回答：

> **和谁比？在哪里比？用什么指标？怎样证明有效？**

说明 Idea 还没有真正成熟。

此时返回第 3～7 步继续调研。

---

# 10. 将 Idea 转化为 Research Project

最终将选题写成一个明确 Research Question。

例如：

> Failure-aware recovery 是否能够提高 VLA 在长时序 OOD manipulation task 中的任务成功率？

然后形成完整实验逻辑：

```
Research Question
        ↓
Hypothesis
        ↓
Proposed Method
        ↓
Baseline / SOTA
        ↓
Dataset / Benchmark
        ↓
Metrics
        ↓
Main Experiment
        ↓
Ablation
        ↓
Generalization
        ↓
Robustness
        ↓
Failure Analysis
```

---

# 11. 最终调研产物

完成一次完整调研后，不应该只得到“一堆论文”。

至少应该留下以下成果：

### ① Keyword Tree

知道应该搜索什么。

### ② Venue List

知道这个领域主要在哪里发表。

### ③ Paper Library

建立结构化文献库。

### ④ Taxonomy

知道领域有哪些技术路线。

### ⑤ Research Graph

知道技术如何发展：

```
Foundation → Baseline → Representative → SOTA
```

### ⑥ Benchmark Table

明确：

```
Dataset
Environment
Task
Metric
Baseline
SOTA
```

### ⑦ Gap List

知道现有方法还缺什么。

### ⑧ Idea Pool

保留多个潜在研究方向。

### ⑨ Final Research Specification

最终确定：

```
Research Question
Hypothesis
Method
Contribution

Baseline
SOTA

Environment
Dataset
Task

Metrics

Main Experiment
Ablation
Generalization
Robustness
Failure Analysis
```

---

# 12. 整体流程图

```
确定研究范围
     ↓
建立关键词树
     ↓
定位 Venue
     ↓
Survey / Benchmark / Representative Work
     ↓
建立 Paper Pool
     ↓
建立 Taxonomy
     ↓
论文略读筛选
     ↓
核心论文精读
     ↓
Backward / Forward / Sibling Citation
     ↓
Baseline / SOTA / Framework / Experiment
     ↓
Research Gap Mining
     ↓
Idea 发散
     ↓
Idea Card
     ↓
Idea 收敛
     ↓
Research Question
     ↓
Method / Contribution
     ↓
Baseline / SOTA
     ↓
Environment / Dataset / Metrics
     ↓
Main / Ablation / OOD / Failure Experiments
     ↓
开始研究
```

## 核心原则

**调研不是线性的，而是循环收敛的。**

最常见的循环为：

```
搜索
 ↓
阅读
 ↓
发现新关键词
 ↓
重新搜索
 ↓
发现新方法
 ↓
重新分类
 ↓
发现Gap
 ↓
产生Idea
 ↓
搜索Idea是否已经有人做
 ↓
修改Idea
 ↓
再次验证
 ↓
最终收敛
```

因此真正的结束标准不是“我读了多少篇论文”，而是：

> **我已经能够清楚解释领域现状，并提出一个有依据、可验证、可执行的 Research Question，同时知道应该和谁比较、在哪里实验、怎样证明自己的贡献。**

达到这一状态，文献调研阶段才基本完成，随后进入项目实现与实验阶段。