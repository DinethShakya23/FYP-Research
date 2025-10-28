---
title: "Sniper Backdoor: Single Client Targeted Backdoor Attack in Federated Learning"
authors: Gorka Abad, Servio Paguada, Oğuzhan Ersoy, Stjepan Picek, Víctor Julio Ramírez-Durán, Aitor Urbieta
year: "2023"
tags:
  - Training
  - Collaboration
  - Deep learning
  - Deep Learning
  - Neural networks
  - Threat modeling
  - Toxicology
  - backdoor
  - federated-learning
  - ds
source: https://doi.org/10.1109/SaTML54575.2023.00033
---
**Read:** [Open in Zotero](zotero://select/items/2_S5CMHRLA)

# 🧠 Summary

The paper proposes the first _client-targeted backdoor attack_ in Federated Learning (FL), where only one client’s model is compromised while others remain unaffected.  
It combines model inversion (via GANs) and Siamese Neural Networks to identify and target a victim client anonymously.  
The attack achieves up to 99% accuracy on both clean and backdoored tasks, even bypassing state-of-the-art defenses such as Neural Cleanse.

---

# 🎯 Problem Statement

Existing FL backdoor attacks affect all clients globally.  
This study explores whether a backdoor can be injected to compromise only a single client’s model — without degrading the global performance or other clients’ models.

---

# ⚙️ Method / Approach

- **Technique used:** Combined _model inversion_ (using GANs) and _Siamese Neural Network (SNN)_ for client identification, followed by a _BadNets_ or _input-aware dynamic_ backdoor injection.
    
- **Framework type:** Federated Learning (malicious aggregator threat model).
    
- **Dataset:** MNIST, F-MNIST, EMNIST, CIFAR-100.
    
- **Evaluation metrics:** Clean accuracy, Clean accuracy degradation, Source class accuracy, Attack Success Rate (ASR).
    
- **Key steps:**
    
    1. Collect client updates during FL training.
        
    2. Reconstruct client-like datasets via GAN-based model inversion.
        
    3. Train a shadow FL network and SNN to identify the victim client.
        
    4. Inject the backdoor just before convergence so only the victim receives a poisoned model.

---

# 📊 Results

|Metric|Baseline|Proposed|Improvement|
|---|---|---|---|
|Clean Accuracy (MNIST)|99%|99%|0%|
|Backdoor ASR (MNIST)|—|99%|—|
|Backdoor ASR (F-MNIST)|—|94%|—|
|Backdoor ASR (EMNIST)|—|96%|—|
|Backdoor ASR (CIFAR-100)|—|84%|—|
- Neural Cleanse failed to detect the attack.
    
- Minimal degradation (<1%) in clean accuracy.
    
- Attack successful against both IID and Non-IID data distributions.

---

# 💡 Key Insights

- **Strengths:**
    
    - First demonstration of _client-specific_ backdoor injection.
        
    - Bypasses existing FL defense mechanisms.
        
    - Modular design adaptable to various backdoor techniques.
        
- **Weaknesses:**
    
    - Requires high computational resources.
        
    - Assumes a _malicious server_, which might not always hold in real deployments.
        
- **Could combine with:** Differential privacy or trusted third-party aggregation to mitigate the attack.
    
- **Might help in:** Understanding new security threats and designing FL systems resilient to client-specific attacks.

---

# 🧩 Related Works
> How does this relate to other papers or concepts?

focus on [[backdoor]] attcaks
- **Builds on:** BadNets (Gu et al., 2019), model inversion attacks (Fredrikson et al., 2015), GAN-based privacy attacks.
    
- **Similar to:** DBA (Distributed Backdoor Attack) and edge-case poisoning methods.
    
- **Contradicts:** Standard FL security assumption that aggregation inherently dilutes single-client attacks.

---

# 💬 Notes / Quotes

“Our attack allows a malicious server to poison a single client’s model while maintaining the integrity of others.”  
“Neural Cleanse and smoothing defenses failed to detect or mitigate the proposed attack.”  
“Combining model inversion and backdoor injection opens a new threat vector in FL.”

---

# 🧠 My Thoughts

This work shows a _new vulnerability model_ in FL where client-level privacy and trust are undermined by a malicious aggregator.  
For the FYP on **“Robust and Privacy-Preserving Federated Learning Framework for Backdoor-Resistant IDS”**, this paper is crucial to:

- Understand targeted backdoor mechanisms.
    
- Design defense strategies such as differential privacy, secure aggregation, or adversarial detection for single-client attacks.

---

# 📚 Citation

