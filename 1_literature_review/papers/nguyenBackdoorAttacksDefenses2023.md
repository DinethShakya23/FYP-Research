---
title: "Backdoor Attacks and Defenses in Federated Learning: Survey, Challenges and Future Research Directions"
authors: Thuy Dung Nguyen, Tuan Nguyen, Phi Le Nguyen, Hieu H. Pham, Khoa Doan, Kok-Seng Wong
year: "2023"
tags:
  - backdoor
source: https://doi.org/10.48550/arXiv.2303.02213
---
**Read:** [Open in Zotero](zotero://select/items/2_DJ4II5NH)

# 🧠 Summary
> Write your 3–5 line summary of the paper here in your own words.  
> What problem does it solve? What’s the main idea?

The paper categorizes attacks into data poisoning and model poisoning, and reviews defense strategies across pre-, in-, and post-aggregation phases. It highlights evaluation metrics like **Attack Success Rate (ASR) and Main Task Accuracy (MTA)**, and discusses challenges such as stealth, durability, and real-world robustness. Future research directions include improving defense efficiency, fairness, and interpretability in FL security.

problem : [[backdoor]] attacks on [[Federated Learning]]
main idea : talks about attack types and defenses. evaluation metrics like Attack Success Rate (ASR) and Main Task Accuracy (MTA)

---

# 🎯 Problem Statement
> What specific issue or gap does this paper address?

systematically categorizing attack strategies, defense mechanisms, and evaluation metrics, and by identifying open challenges and future research directions 

---

# ⚙️ Method / Approach
> Summarize the proposed method, algorithms, or architecture.

- Technique used:  Survey and taxonomy approach; systematically categorizes backdoor attack techniques (data poisoning, model poisoning) and defense strategies (pre-, in-, post-aggregation)
- Framework type:  [[Federated Learning]]
- Dataset:  N/A
- Evaluation metrics:  
	- **Attack Success Rate (ASR)**: Probability that the backdoor trigger causes misclassification
	- **Main Task Accuracy (MTA)**: Accuracy on benign sample
	- **TPR**: measures how well the defense identifies poisoned models
	- **TNR** : Measures how well the defense identifies benign models:
- Key equations / pseudocode (if important):

---

# 💡 Key Insights
> Your personal understanding — why does this matter for your project?

- Strengths:  
  - help to identify the threat model (with comprehensive attacks and defenses)
  - evaluation metrics (ASR, MTA)
  - stealth and durability challenges

- Weaknesses:  
  - Limited focus on privacy-preserving techniques
  - Does not address real-time IDS constraints or network-specific attack vectors

- Could combine with: [[Robust Aggregation]], [[Federated unlearning]]
- Might help in: 
	- Designing your threat model for backdoor-resistant IDS
	- Selecting defense strategies for different phases (pre-, in-, post-aggregation).
	- Building a literature review section that justifies the need for robustness and privacy in FL-based IDS.

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


---

# 📚 Citation
> (Li et al., 2022) – *Robust Aggregation for Federated Learning*