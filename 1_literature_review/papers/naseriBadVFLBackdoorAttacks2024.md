---
title: "BadVFL: Backdoor Attacks in Vertical Federated Learning"
authors: Mohammad Naseri, Yufei Han, Emiliano De Cristofaro
year: "2024"
tags:
  - Security
  - Training
  - Backdoor
  - Finance
  - Privacy
  - Robustness
  - backdoor
  - federated-learning
  - ds
source: https://doi.org/10.1109/SP54263.2024.00008
---
**Read:** [Open in Zotero](zotero://select/items/2_YZFBYVC9)

# 🧠 Summary
This paper presents BadVFL, the first clean-label backdoor attack specifically designed for Vertical Federated Learning (VFL) systems. Unlike traditional backdoor attacks, BadVFL operates without access to training labels by using a two-phase approach: first inferring labels through an auxiliary dataset, then strategically injecting triggers into feature embeddings. The attack achieves 85% Attack Success Rate (ASR) on CIFAR-10 with only 4% utility drop, demonstrating significant security vulnerabilities in VFL deployments.



---

# 🎯 Problem Statement
VFL systems are vulnerable to backdoor attacks, but existing attack methods from Horizontal FL (HFL) cannot be directly applied due to two critical constraints: (1) malicious participants cannot access or modify training labels held by the server, and (2) attackers can only manipulate their own feature subsets, not the complete feature space. This creates a need for novel attack strategies tailored to VFL's unique architecture.

---

# ⚙️ Method / Approach
> BadVFL employs a two-stage clean-label backdoor attack methodology specifically designed for VFL's split-learning architecture.

- **Technique used:** Clean-label backdoor attack with label inference and feature embedding manipulation
- **Framework type:** Two-phase attack pipeline (Model Extraction + Backdoor Trigger Insertion)
- **Dataset:** CIFAR-10, CIFAR-100, CINIC-10 (images), Criteo (tabular)
- **Evaluation metrics:** Attack Success Rate (ASR), Main Task Accuracy (MTA), Precision, Recall
- **Key approach:**
    1. **Phase 1 - Model Extraction:** Use auxiliary labeled data to train surrogate classifier and infer training labels
    2. **Phase 2 - Trigger Injection:** Select source/target classes, compute saliency maps, inject triggers using optimization objective to minimize distance between triggered source samples and target class embeddings
    3. **Optimization:** Minimize ||B_adv(x̂_sub,s) - B_adv(x_t)||²_fro subject to L2 constraint on trigger perturbation
    4. **Extensions:** Multi-attacker mode with decomposed sub-triggers across multiple compromised participants

---

# 📊 Results

BadVFL demonstrates highly effective attacks across multiple datasets with varying configurations.
![[Pasted image 20251028135508.png]]
**Key Findings:**

- Two-party setting achieves 85% ASR with only 4% accuracy drop
- Optimal class selection improves ASR by 4-7% over random selection
- Saliency map-guided trigger insertion increases ASR from 62% to 85%
- Multi-attacker mode achieves 78% ASR vs 77% single attacker (10-party)
- Attack remains effective even with 4-10 participants (ASR 61-74%)



---

# 💡 Key Insights

> This work reveals critical vulnerabilities in VFL systems and provides important lessons for secure federated learning deployment.

- **Strengths:**
    - First principled backdoor attack specifically designed for VFL architecture
    - Works without label access through clever label inference strategy
    - Maintains high stealth with minimal utility degradation
    - Effective across both image and tabular datasets
    - Scales to multi-party and multi-attacker scenarios
- **Weaknesses:**
    - Requires auxiliary dataset (though only 1% of training data needed)
    - Choosing optimal R_n (transition point between phases) is challenging
    - Some utility drop may raise suspicions in production systems
    - Dependent on accurate label inference for effective attack
- **Could combine with:**
    - Advanced label inference techniques to reduce auxiliary data requirements
    - Gradient matching methods for more sophisticated trigger design
    - Byzantine-robust aggregation evasion techniques
- **Might help in:**
    - Designing robust defense mechanisms for VFL systems
    - Understanding feature-level vulnerabilities in split learning
    - Developing privacy-preserving backdoor detection methods
    - Establishing security benchmarks for vertical federated systems

---
## 🔒 Why BadVFL Attack is [[Robust]]

**1. Clean-Label Design:**

- Doesn't require flipping labels (impossible in VFL anyway)
- Operates purely in feature embedding space
- Harder to detect than dirty-label attacks

**2. Adaptive to VFL Constraints:**

- Works despite no access to loss function or classifier
- Only needs gradient signals from server (∂L/∂E_i)
- Can manipulate only owned feature subsets yet remain effective

**3. Saliency-Guided Trigger Placement:**

- Maximizes classification loss change with minimal perturbation
- Places triggers in high-gradient regions for stronger association
- Reduces detectability while maintaining high ASR

**4. Optimization-Based Approach:**

- Minimizes ||B_adv(triggered_source) - B_adv(target)||² ensures close embedding proximity
- L2 constraint keeps perturbations small and stealthy
- Forces classifier confusion between source and target classes

**5. Persistence Across Configurations:**

- Remains effective with 4-10 participants (61-74% ASR)
- Works with small poisoning budgets (1-10%)
- Multi-attacker mode improves performance (78% ASR with sub-triggers)

**6. Bypasses Traditional Defenses:**

- Neural Cleanse fails (operates on embeddings, not raw inputs)
- Byzantine-robust aggregation not applicable (only one model per participant)
- Foolsgold ineffective (not HFL setting)
- **Weaknesses:**
    - Requires auxiliary dataset (though only 1% of training data needed)
    - Choosing optimal R_n (transition point between phases) is challenging
    - Some utility drop may raise suspicions in production systems
    - Dependent on accurate label inference for effective attack
- **Could combine with:**
    - Advanced label inference techniques to reduce auxiliary data requirements
    - Gradient matching methods for more sophisticated trigger design
    - Byzantine-robust aggregation evasion techniques
- **Might help in:**
    - Designing robust defense mechanisms for VFL systems
    - Understanding feature-level vulnerabilities in split learning
    - Developing privacy-preserving backdoor detection methods
    - Establishing security benchmarks for vertical federated systems
# 🧩 Related Works
> How does this relate to other papers or concepts?

- Builds on [[backdoor]]
	- Clean-label backdoor attacks (centralized learning), label inference attacks in VFL (Fu et al. 2022), split learning architectures
- **Similar to:** HFL backdoor attacks (Bagdasaryan et al., DBA), but adapted for VFL's unique constraints
- **Contradicts:** Assumption that VFL's label separation provides inherent security against backdoor attacks
- **Extends:** Previous VFL security work focused primarily on privacy leakage rather than integrity attacks

---

# 💬 Notes / Quotes

> Important technical details and definitions from the paper.

**VFL Definition:** "Each participant hosts the same set of training instances but owns different and non-overlapping features of the same training instances."

**Attack Objective:**

```
B*_adv = arg min ||B_adv(x̂_sub,s) - B_adv(x_t)||²_fro
subject to: x̂_sub,s = x_sub,s + δ, ||δ||_L2 ≤ ε
```

**Key Challenge:** "The malicious participants cannot access the loss function or the classifier used by the server. Only the server can define the loss function to train the top-layer classification module."

**Critical Insight on R_n:** "Empirically set R_n so that the main learning accuracy of the VFL model reaches around 70% of the testing accuracy obtained at the convergence of VFL training."

**Defense Findings:** "DP-based defense mechanisms can potentially achieve reasonable utility-integrity trade-offs... ASR drops from 85% to 58% and 42% with variance 1e-1 and 1 respectively."

---

# 🧠 My Thoughts


---

# 📚 Citation
