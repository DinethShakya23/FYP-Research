---
title: Robust Federated Learning against Backdoor Attackers
authors: Priyesh Ranjan, Ashish Gupta, Federico Coro, Sajal K. Das
year: "2023"
tags:
source: https://doi.org/10.1109/INFOCOMWKSHPS57453.2023.10225922
---
**Read:** [Open in Zotero](zotero://select/items/2_GVRQQGGY)

# 🧠 Summary
> Write your 3–5 line summary of the paper here in your own words.  
> What problem does it solve? What’s the main idea?

The paper addresses the vulnerability of Federated Learning to backdoor attacks, where malicious clients inject triggers into local data to manipulate global model predictions. It proposes two graph-based algorithms—[[MST-AD]] and [[Density-AD]]—that detect and isolate adversarial clients by analyzing correlation patterns in model updates. These methods remain effective even when attackers form the majority, achieving low attack success rates and high accuracy compared to existing defenses

---

# 🎯 Problem Statement
> What specific issue or gap does this paper address?

most existing defenses against backdoor attacks assume that malicious clients are a small minority. This assumption fails when attackers form a majority or a large fraction of participants, making traditional aggregation-based defenses ineffective.

---

# ⚙️ Method / Approach
> Summarize the proposed method, algorithms, or architecture.

- Technique used:  
	- Graph-theoretic adversary detection using correlation analysis of client model updates
	- [[MST-AD]]
	- [[Density-AD]]
- Framework type:  [[Federated Learning]] [[secure aggregation]]
- Dataset:  [[Fashion-MNIST]]
- Evaluation metrics:  
	- [[ASR]]
	- F1-score
- Key equations / pseudocode (if important):
	- Correlation computation:
	$$
\text{corr}(u_i, u_j) = \frac{u_i \cdot u_j}{\|u_i\| \, \|u_j\|}
$$


---

# 📊 Results
> Capture the main results or comparison metrics.

![[Pasted image 20251028181745.png]]
 ASR, ED and FP with varying attack scenarios for Backdoor Attacks with a moving trigger pattern

---

# 💡 Key Insights
> Your personal understanding — why does this matter for your project?

- Strengths:  
  - [[Robustness]] is high
  - High accuracy retention: Maintains near-benign performance while minimizing attack success.
  - Graph-based detection: Exploits strong correlation patterns among adversaries for effective isolation.

- Weaknesses:  
  - Computational overhead: Density-AD has O(n²) complexity, making it less scalable for very large client sets.
  - Single attack type focus: Designed for backdoor attacks; may not generalize to Byzantine or mixed attacks.
  - Limited dataset diversity: Experiments only on [[Fashion-MNIST]]; real-world heterogeneity not fully tested.

- Could combine with: 
	- [[DP]] or [[secure aggregation]] for stronger privacy guarantees.
	- Byzantine-resilient aggregation methods to handle mixed adversarial behaviors.
	- [[Adaptive client sampling]] to reduce overhead in large-scale deployments.
	
- Might help in: 
	- [[IDS]]

---

# 🧩 Related Works
> How does this relate to other papers or concepts?

- Builds on [[FedAvg]], [[GeoMed]], [[FoolsGold]]
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
> 