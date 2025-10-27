---
title: "{{title}}"
authors: "{{authors}}"
year: {% if date %}"{{date | format("YYYY")}}"{% endif %}
tags: [{% if allTags %}{{allTags}}{% endif %}]
source: {% if DOI %}https://doi.org/{{DOI}}{% endif %}
---
**Read:** [Open in Zotero](zotero://select/items/{{libraryID | default(0)}}_{{key}})

# 🧠 Summary
> Write your 3–5 line summary of the paper here in your own words.  
> What problem does it solve? What’s the main idea?



---

# 🎯 Problem Statement
> What specific issue or gap does this paper address?

---

# ⚙️ Method / Approach
> Summarize the proposed method, algorithms, or architecture.

- Technique used:  
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