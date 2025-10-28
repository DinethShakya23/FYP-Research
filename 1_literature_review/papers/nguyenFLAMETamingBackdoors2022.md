---
title: "FLAME: Taming Backdoors in Federated Learning"
authors: "Thien Duc Nguyen, Phillip Rieger, Huili Chen, Hossein Yalame, Helen Möllering, Hossein Fereidooni, Samuel Marchal, Markus Miettinen, Azalia Mirhoseini, Shaza Zeitouni, Farinaz Koushanfar, Ahmad-Reza Sadeghi, Thomas Schneider"
year: "2022"
tags: [backdoor]
source: 
---
**Read:** [Open in Zotero](zotero://select/items/2_2ZZ84AUU)

# 🧠 Summary
> Write your 3–5 line summary of the paper here in your own words.  
> What problem does it solve? What’s the main idea?

FLAME is a defense framework for federated learning that mitigates backdoor attacks without sacrificing model accuracy. It combines dynamic clustering to detect malicious updates, adaptive weight clipping to limit their impact, and minimal Gaussian noise to remove residual backdoors. FLAME also introduces a privacy-preserving variant using secure two-party computation. Experiments across NLP, vision, and IoT tasks show FLAME outperforms existing defenses with negligible accuracy loss.

---

# 🎯 Problem Statement
> What specific issue or gap does this paper address?

 existing defenses against backdoor attacks are either too restrictive (assuming IID data or single attacks) or degrade model accuracy significantly (e.g., differential privacy noise injection). FLAME fills this gap by providing a robust, generalizable defense that works under realistic conditions—non-IID data, multiple simultaneous attacks—while preserving accuracy and offering a privacy-preserving variant.

# ⚙️ Method / Approach
> Summarize the proposed method, algorithms, or architecture.

- Technique used:  
	- Dynamic clustering ([[HDBSCAN]]) for **anomaly detection**
	- [[adaptive weight clipping]], and [[adaptive Gaussian noise injection]] to **neutralize backdoors**.
	- Secure Two-Party Computation for [[privacy preserving]]
- Framework type:  
- Dataset:  
- Evaluation metrics:  
- Key equations / pseudocode (if important):

---

# 📊 Results
> Capture the main results or comparison metrics.

| Metric | Baseline | Proposed | Improvement |
|---------|-----------|----------|--------------|
| Accuracy | 88.2% | 91.5% | +3.3% |
| Attack Success Rate | 12.4% | 2.7% | ↓ 9.7% |

---

# 💡 Key Insights
> Your personal understanding — why does this matter for your project?

- Strengths:  
  - 
- Weaknesses:  
  - 
- Could combine with: 
- Might help in: 

---

# 🧩 Related Works
> How does this relate to other papers or concepts?

- Builds on 
- Similar to 
- Contradicts 

---

# 💬 Notes / Quotes
> Copy any important definitions, equations, or quotes here.

---

# 🧠 My Thoughts
> Reflect on how this influences your FYP.

Example:  
I can use this aggregation method as the base for my framework, then add a DP noise layer to enhance privacy. Test on CICIDS2017 dataset.

---

# 📚 Citation
> (Li et al., 2022) – *Robust Aggregation for Federated Learning*