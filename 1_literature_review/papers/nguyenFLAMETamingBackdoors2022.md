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

FLAME is a defense framework for [[Federated Learning]] that mitigates [[backdoor]] attacks without sacrificing model accuracy. It combines dynamic clustering to detect malicious updates, adaptive weight clipping to limit their impact, and minimal Gaussian noise to remove residual backdoors. FLAME also introduces a privacy-preserving variant using secure two-party computation. Experiments across NLP, vision, and IoT tasks show FLAME outperforms existing defenses with negligible accuracy loss.

---

# 🎯 Problem Statement
> What specific issue or gap does this paper address?

 existing defenses against backdoor attacks are either too restrictive (assuming IID data or single attacks) or degrade model accuracy significantly (e.g., differential privacy noise injection). FLAME fills this gap by providing a robust, generalizable defense that works under realistic conditions—non-IID data, multiple simultaneous attacks—while preserving accuracy and offering a privacy-preserving variant.

# ⚙️ Method / Approach
> Summarize the proposed method, algorithms, or architecture.

- Technique used:  
	- Dynamic clustering ([[HDBSCAN]]) for **anomaly detection**
	- [[adaptive weight clipping]], and [[adaptive Gaussian noise injection]] to **neutralize backdoors**.
	- Secure Two-Party Computation([[STPC]]) for [[privacy preserving]]
- Framework type:  
- Dataset:  [[Reddit]] (word prediction), [[CIFAR-10]], [[MNIST]], [[Tiny-ImageNet]] (image classification), [[IoT-Traffic]]
- Evaluation metrics:  
	- Main Task Accuracy ([[MTA]]) – performance on the primary task.
	- Backdoor Accuracy (BA) – success rate of the backdoor attack. [[ASR]]
- Key equations / pseudocode (if important):
	- Noise bound estimation $$
\sigma \ge 2 \log\left(\frac{1}{\delta}\right) \Delta
$$
	   For each round: 
		   Collect client updates Cluster updates using HDBSCAN
		    Filter outliers (potential backdoors) 
		    Apply adaptive weight clipping 
		    Add minimal Gaussian noise 
		    Aggregate remaining updates


---

# 📊 Results
> Capture the main results or comparison metrics.

| Defense    | BA ↓        | MA ↓              | Notes                              |
|------------|-------------|-------------------|------------------------------------|
| FLAME      | ~0%         | Negligible        | Handles multiple attacks, non-IID data |
| Krum       | High        | Moderate          | Fails under multiple backdoors     |
| FoolsGold  | High        | Moderate          | Assumes IID data                   |
| Auror      | Moderate    | Moderate          | Limited scalability                |
| DP-based   | Low BA      | Severe MA drop    | Accuracy trade-off                 |

---

# 💡 Key Insights
> Your personal understanding — why does this matter for your project?

- Strengths:  
  - Works under [[non-IID]] data and multiple simultaneous attacks, which is realistic for network traffic.
  - Minimal accuracy loss compared to DP-based defenses.
  - Includes a privacy-preserving variant using [[STPC]]
- Weaknesses:  
  - Assumes majority of clients are benign (>50%), which may not hold in adversarial networks.
  - Private FLAME introduces high computational overhead, making it less practical for real-time anomaly detection.
  
- Could combine with:
	- [[Federated Learning]] + [[DP]] for additional privacy guarantees.
	- [[secure aggregation]] protocols to reduce inference risks without heavy [[STPC]] overhead.
	- [[Anomaly scoring techniques]] for network-specific threat detection.
	
- Might help in: 
	- Designing a [[robust aggregation]] mechanism for your federated anomaly detection model.
	- 

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