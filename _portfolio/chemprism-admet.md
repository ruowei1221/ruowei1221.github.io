---
title: "Five models, one predictor: ADMET prediction on small data"
excerpt: "22 TDC ADMET tasks, no external data, no pretrained weights. What limits accuracy on small molecular datasets?"
collection: portfolio
permalink: /portfolio/chemprism-admet/
date: 2026-11-01
---

**Team ChemPrism** · Xingzhi Cup Small-Molecule Drug Prediction Challenge, 2026
Poster at SUSTech BME Research Day, 2026 · Advisor: Prof. Bo Zhang
<!-- TODO：确认导师英文名写法 -->

## The problem

The challenge covers all **22 ADMET endpoints** of the TDC benchmark (8 AUROC, 5 AUPRC, 4 Spearman, 5 MAE tasks). The rules are strict: **no external data, no pretrained weights**, and every feature has to be computed with RDKit from the given SMILES. Most tasks are small. 13 of the 22 have fewer than 1,000 training molecules, and the smallest (DILI) has 379.

## What I built

- **Features:** 3,455 base dimensions (ECFP4, Morgan counts, MACCS, 2D descriptors) plus 5,435 extended dimensions (Avalon, atom-pair, topological torsion, RDKit path, FCFP, ErG).
- **Cross-task transfer:** out-of-fold predictions from large endpoints are fed to small endpoints as extra features.
- **Five model families:** LightGBM, ExtraTrees, regularized linear, RBF-SVM and kNN, combined by **rank-based** rather than value-based ensembling. The ensemble beat every single family on 22/22 tasks.
- **Size-aware weighting rule:** grid-searched weights when n ≥ 2,000; equal weights below that, with a cap on any single family for MAE tasks.
- **Submission discipline:** the leaderboard was used only to test one pre-registered rule at a time, never to tune per task.

Final method score: **50.27** on the official scale, where 50 means parity with the official baseline.
<!-- TODO：如果要写"22 个任务中有 X 个超过基线"，先确认这个数字和 50.27 的方法口径一致 -->

## Three findings

**1. Random splits overstate accuracy by up to 62%.**
The official train/valid/test splits share **0%** of Murcko scaffolds; a random 80/20 split shares 83%. With the same model and data, the PPBR MAE is 6.45 under random folds but 10.44 under scaffold folds.

**2. On small data, local cross-validation points the wrong way.**
In six pre-registered tests (CV prediction written down *before* submitting), CV got the **direction** of the change wrong five times. These were sign errors, not precision errors.

**3. Five models behave like 1.2.**
The five families have a mean pairwise rank correlation of ρ = 0.782, which gives an effective number of independent models of k_eff = 5 / (1 + 4ρ) ≈ **1.21**. Equal-weight fusion cuts the variance to only 83% of a single family's. Across nine candidate families, the first principal component explains **80.9%** of the variance on average (76–89% on all 13 tasks checked). Four extra families built to be more independent (SVD embedding + SVM/kNN, Tanimoto-kernel SVM/kNN) all lost accuracy: the more independent a model was, the less accurate it was.

**Takeaway:** on small molecular data, the ceiling is set by the **representation and the evaluation protocol**, not by the choice of model.

## Stack

Python · NumPy · scikit-learn · LightGBM · RDKit · CPU only (one full run takes about 1–1.5 h)

## Links

- Poster (PDF): [TODO](/files/chemprism-poster.pdf) <!-- TODO：把墙报 PDF 上传到 files/，文件名改成 chemprism-poster.pdf；导师同意公开前先删掉这一行 -->
- Code: [TODO](https://github.com/TODO) <!-- TODO：比赛规则允许、导师同意后再公开代码；否则删掉这一行 -->
