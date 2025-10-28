---
title: Defending against Backdoor Attacks in Federated Learning by Using Differential Privacy and OOD Data Attributes
authors: Qingyu Tan, Yan Li, Byeong-Seok Shin
year: "2025"
tags:
  - backdoor
  - federated-learning
  - differential-privacy
  - ds
source: https://doi.org/10.32604/cmes.2025.063811
---
**Read:** [Open in Zotero](zotero://select/items/2_5LC6C5CE)

# 🧠 Summary

This paper proposes a **defense mechanism** for [[Federated Learning]] (FL) that mitigates [[backdoor]] attacks** using **differential privacy (DP)** combined with **out-of-distribution (OOD) data attributes**.  
It identifies and filters malicious client updates based on OOD behavior before applying DP, reducing the required noise and improving overall accuracy.  
The method demonstrates high resistance to various backdoor types while maintaining main task performance on **CIFAR10** and **FEMNIST** datasets.  
The work strikes a balance between **robustness, privacy, and model accuracy**.



---

# 🎯 Problem Statement

Federated learning, despite preserving data privacy, is **highly vulnerable to backdoor attacks**, where malicious clients poison local updates to embed hidden behaviors into the global model.  
Existing **DP-based defenses** mitigate such attacks but **significantly degrade accuracy** due to excessive noise addition.  
The paper addresses the **trade-off between DP noise and model performance** while maintaining strong backdoor resistance.

---

# ⚙️ Method / Approach

A **two-stage defense mechanism**:

1. **Out-of-Distribution (OOD) Detection Stage** – detects and excludes malicious model updates by leveraging the OOD characteristics of backdoor samples.
    
2. [[Differential Privacy]] (DP) Stage** – adds calibrated Gaussian noise to remaining benign updates for privacy and robustness.
    

- **Technique used:** OOD detection + Approximate Differential Privacy (ADP)
    
- **Framework type:** Federated Learning (FedAvg-based)
    
- **Datasets:** [[CIFAR-10]], FEMNIST (indicator dataset from CIFAR100)
    
- **Evaluation metrics:** Main Task Accuracy (MA), Backdoor Accuracy (BA)
    
- **Key equations:**
    
    - DP condition: Pr(M(D)∈S)≤eεPr(M(D′)∈S)+δPr(M(D) \in S) \le e^\varepsilon Pr(M(D') \in S) + \deltaPr(M(D)∈S)≤eεPr(M(D′)∈S)+δ
        
    - Noise scale: δG≈Stε2ln⁡1.25δ\delta_G \approx \frac{S_t}{\varepsilon} \sqrt{2 \ln \frac{1.25}{\delta}}δG​≈εSt​​2lnδ1.25​​

---

# 📊 Results

|Metric|Baseline (No Defense)|Proposed|Improvement|
|---|---|---|---|
|**CIFAR10 (Pixel-pattern BA)**|78.3%|**12.6%**|↓ 65.7%|
|**CIFAR10 (Edge-case BA)**|49.4%|**9.3%**|↓ 40.1%|
|**FEMNIST (Pixel-pattern BA)**|91.8%|**7.4%**|↓ 84.4%|
|**FEMNIST (Edge-case BA)**|75.6%|**3.1%**|↓ 72.5%|
|**Main Task Accuracy (CIFAR10)**|87.9%|**86.8%**|−1.1%|
|**Main Task Accuracy (FEMNIST)**|88.2%|**86.1%**|−2.1%|
Compared to **FLAME** and **Foolsgold**, the proposed method maintained high task accuracy while reducing backdoor accuracy below **15%**.

---

# 💡 Key Insights

- **Strengths:**
    
    - Combines OOD detection with DP, reducing required noise and improving performance.
        
    - Robust to multiple backdoor types and neural architectures (ResNet, VGG).
        
    - Works effectively even under non-IID data conditions.
        
- **Weaknesses:**
    
    - Less effective if backdoor samples are not clearly OOD from the target class.
        
    - Requires constructing an additional indicator dataset.
        
- **Could combine with:** Adaptive noise calibration or clustering-based aggregation (e.g., FLAME).
    
- **Might help in:** Secure and privacy-preserving FL frameworks for edge/IoT applications.

---

# 🧩 Related Works
> How does this relate to other papers or concepts?

- **Builds on:** BackdoorIndicator (Li & Dai, 2024), FLAME (Nguyen et al., 2022), DP-based defenses (Miao et al., 2022).
    
- **Similar to:** Outlier detection (Multikrum), Consistency detection (Foolsgold).
    
- **Contradicts:** DP-only approaches that prioritize privacy but degrade accuracy heavily.
---

# 💬 Notes / Quotes

> “By filtering out models that are clearly backdoor-infected before applying differential privacy, our method reduces the required noise level for differential privacy, thereby enhancing model robustness while preserving performance.”

> “Our method effectively limits the backdoor accuracy to below 15% across various backdoor scenarios while maintaining high main task accuracy.”

---

# 🧠 My Thoughts

It’s a practical direction for maintaining both **robustness and privacy** in distributed GAN training environments.

---

# 📚 Citation
