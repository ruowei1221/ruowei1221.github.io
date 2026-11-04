---
permalink: /
title: "About me"
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

I am a second-year undergraduate in **Biomedical Engineering** at the [Southern University of Science and Technology (SUSTech)](https://www.sustech.edu.cn/en/), Shenzhen, China, where I do research in the group of [Prof. Bo Zhang](TODO-导师主页链接).

I work on **machine learning for biology and chemistry**: small molecules, single cells and brain signals. The question I care about most is a practical one: *when can an ML result on small biomedical data actually be trusted?* In my recent work on ADMET property prediction, I found that random train/test splits overstate accuracy, that local cross-validation can point in the wrong direction on small datasets, and that combining many models helps far less than it seems, because they make almost the same mistakes.

I plan to apply for graduate study abroad and am looking for research collaborations and summer research opportunities. Feel free to reach out by email.

## News

- **2026.12** — Team ChemPrism will give the on-site final presentation of the Xingzhi Cup Small-Molecule Drug Prediction Challenge in Shenzhen. <!-- TODO：确认已进入现场答辩，再保留这条 -->
- **2026.11** — Presenting the poster *Five models, one predictor* at SUSTech BME Research Day. <!-- TODO：填具体日期；如果还没展出，改成 "Will present" -->
- **2026.10** — Submitted my final entry to the Arc Institute [Virtual Cell Challenge 2026](https://virtualcellchallenge.org/). Results are announced on Nov 19.

## Projects

- **[Five models, one predictor: ADMET prediction on small data](/portfolio/chemprism-admet/)**
  22 TDC ADMET tasks under strict rules (no external data, no pretrained weights, RDKit features only). A study of why evaluation and model diversity, not model choice, limit performance on small molecular datasets.

- **Virtual Cell Challenge 2026** (Arc Institute)
  Predicting single-cell transcriptomic responses to genetic perturbations. Final entry submitted in October 2026; a write-up will follow the results.

- **OmniEEG Challenge 2026: sleep-staging track** *(ongoing)* <!-- TODO：没报名/没提交就删掉这一条 -->
  Sleep stage classification from EEG, as part of a challenge on EEG foundation models.

- **Enveda CASMI 2026** *(ongoing)* <!-- TODO：没提交过就删掉这一条 -->
  Identifying small molecules from tandem mass spectra (Kaggle).

- **Changjiang Cup 2026 Global AI Protein Design Challenge** *(team, ongoing)* <!-- TODO：没报名就删掉这一条 -->

## Skills

**Programming:** Python, NumPy, scikit-learn, LightGBM, RDKit
**Methods:** scaffold-grouped cross-validation, out-of-fold stacking, rank-based ensembling, molecular fingerprints and descriptors
