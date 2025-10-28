---
title: "A3FL: Adversarially Adaptive Backdoor Attacks to Federated Learning"
authors: Hangfan Zhang, Jinyuan Jia, Jinghui Chen, Lu Lin, Dinghao Wu
year:
tags:
  - backdoor
  - federated-learning
  - ds
source: https://dl.acm.org/doi/10.5555/3666122.3668797
---
**Read:** [Open in Zotero](zotero://select/items/2_TAUGX7SA)

# 🧠 Summary

A3FL introduces a novel backdoor attack on federated learning that adaptively optimizes triggers to survive global model dynamics. Unlike existing attacks that only optimize on local models, A3FL uses adversarial training to make backdoors persistent even when the server attempts to unlearn them. The method achieves up to 10x better attack success rates against defenses while maintaining model utility and significantly longer backdoor lifespans (over 1000 rounds vs. under 150 for baselines).



---

# 🎯 Problem Statement

Existing backdoor attacks on federated learning have two key limitations: (1) they use fixed triggers or optimize only on local models, ignoring global training dynamics, and (2) they apply strict regularization that limits backdoor effectiveness. This creates a "local-global gap" where triggers effective on local models become much less effective when transferred to the global model after server-side aggregation.

---

# ⚙️ Method / Approach

A3FL optimizes the backdoor trigger using adversarial adaptation to bridge the local-global gap.

- **Technique used:** Adversarial training-like optimization with bi-level optimization
- **Framework type:** Backdoor attack in federated learning
- **Dataset:** [[CIFAR-10]], [[Tiny-ImageNet]], nyImageNet, FEMNIST
- **Evaluation metrics:** Attack Success Rate (ASR), Accuracy (ACC), Backdoor Accuracy (BAC), Lifespan
- **Key equations:**
    - Trigger optimization: δ* = argmin E[(L(x⊕δ, ỹ; θₜ) + λL(x⊕δ, ỹ; θ'ₜ))]
    - Adversarial model: θ'ₜ = argmin E[L(x⊕δ, y; θ)] (simulates backdoor unlearning)
    - Balancing coefficient: λ = λ₀ × sim(θ'ₜ, θₜ)

**Algorithm:** Compromised clients iteratively optimize the trigger against both current global model (θₜ) and an adversarial model (θ'ₜ) that attempts to unlearn the backdoor. This makes the trigger robust to future global model updates.

---

# 📊 Results
 ![[Pasted image 20251028113101.png]]

**Key Findings:**

- **Utility preserved:** Maximum accuracy drop of only 0.28%
- **Higher ASR:** Consistently outperforms 4 baseline attacks across 13 defenses
- **Longer lifespan:** 1000+ rounds vs <150 for baselines (with 50% ASR threshold)
- **Local-global gap bridged:** Minimal difference between local and global ASR for A3FL
---

# 💡 Key Insights
- **Strengths:**
    - Addresses fundamental limitation of existing attacks by considering global dynamics
    - Highly effective with minimal compromised clients (P=1 sufficient in many cases)
    - Maintains attack effectiveness across different data heterogeneity levels
    - Significantly more durable than existing methods
    - Stealthy - preserves model utility on clean tasks
- **Weaknesses:**
    - Requires knowledge of global model architecture and training process
    - Computational overhead from bi-level optimization
    - Assumes attacker can control clients during attack window
    - Still partially vulnerable to strong defenses like CRFL with high noise
- **Could combine with:**
    - Different trigger patterns or distributed triggers (DBA-style)
    - Gradient masking techniques for additional stealth
    - Multi-target backdoor strategies
- **Might help in:**
    - Understanding robustness requirements for FL systems
    - Developing better defense mechanisms
    - Designing adaptive defense strategies that consider attacker adaptation

---

# 🧩 Related Works
How does this relate to other papers or concepts?

- Builds on [[backdoor]]in [[Federated Learning]]
	- Fixed-trigger attacks (Neurotoxin, DBA, Scaling Attack)
    - Trigger-optimization attacks (F3BA, CerP)
    - Adversarial training methodology (Madry et al.)
- **Similar to:**
    - CerP: Both optimize triggers, but A3FL adds adversarial adaptation
    - F3BA: Both consider latent representations, but A3FL focuses on global dynamics
- **Contradicts:**
    - Common belief that backdoors in FL quickly vanish after attacks end
    - Assumption that strict regularization improves attack effectiveness

---

# 💬 Notes / Quotes
**Key Definitions:**

- **Attack Success Rate (ASR):** Fraction of trigger-embedded test inputs misclassified as target class
- **Backdoor Accuracy (BAC):** Accuracy on clean inputs when backdoor is present (should ≈ ACC for stealth)
- **Lifespan:** Period during which ASR remains above 50% after attack ends

**Important Observations:**

- "The difference between the global model and local model in FL makes the local-optimized trigger much less effective when transferred to the global model"
- A3FL uses cosine similarity sim(θ'ₜ, θₜ) to automatically adjust the weight on adversarial model
- Attack window: By default, rounds 1,900-2,000 (last 100 of 2,000 total rounds)

**Experimental Setup:**

- N=100 clients, M=10 selected per round
- ResNet-18 architecture
- Non-i.i.d data (Dirichlet concentration h=0.9)
- 25% local data poisoning rate

---

# 🧠 My Thoughts
> 
---

# 📚 Citation
> 