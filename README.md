# DS357 – Explainable AI | Course Project

## Prompt-CAM Replication and Swin Extension

### "Prompt-CAM: Making Vision Transformers Interpretable for Fine-Grained Analysis" — Chowdhury et al. (CVPR 2025)

---

## Team Information

| Field         | Details                                                                          |
| ------------- | -------------------------------------------------------------------------------- |
| Course        | DS357 – Explainable AI (XAI)                                                     |
| Project       | Research Replication and Extension                                               |
| Paper         | "Prompt-CAM: Making Vision Transformers Interpretable for Fine-Grained Analysis" |
| Conference    | CVPR 2025 (A* Conference)                                                        |
| Authors       | Chowdhury et al.                                                                 |
| Paper Link    | https://arxiv.org/abs/2501.09333                                                 |
| Preetham P       | 23bds046                                                                        |
| Prem Sagar TK    | 23bds065                                                                         |

---

## Project Overview

This project focuses on **Explainable AI (XAI)** for deep learning models in computer vision.

We:

* ✅ Replicate the Prompt-CAM method on Vision Transformers (ViT)
* 🚀 Extend the method to **Swin Transformer**
* 📊 Evaluate explanation quality using multiple metrics

---

# Phase 1 — Paper Study & Research Gap

## Problem Statement

Vision Transformers (ViTs) achieve strong performance but lack **interpretability**, especially for fine-grained classification tasks.

---

## Key Idea of Prompt-CAM

Prompt-CAM introduces **class-specific prompts** that interact with patch features to generate **interpretable attention maps**.

These maps highlight the most important regions contributing to a prediction.

---

## Method Overview

1. Image is divided into patches (ViT)
2. Class-specific prompts are introduced
3. Prompts attend to patch features
4. Attention weights generate heatmaps

---

## Research Gap

The original paper evaluates Prompt-CAM only on:

* ❌ Flat Vision Transformers (ViT)

It does NOT explore:

* ❌ Hierarchical transformers like Swin
* ❌ Effect of architecture on explanation quality

---

## Proposed Idea (Phase 3)

> Extend Prompt-CAM to **Swin Transformer** and evaluate whether hierarchical attention improves explanation quality.

---

# Phase 2 — Replication (ViT)

## Dataset

* CUB-200-2011

  * 200 bird species
  * Fine-grained classification
  * ~11,788 images

---

## Model Setup

| Component   | Details          |
| ----------- | ---------------- |
| Backbone    | DINO ViT-B/16    |
| Pretraining | ImageNet         |
| Features    | Patch embeddings |
| XAI Method  | Prompt-CAM       |

---

## Results (Replication)

| Metric                | Paper | Ours   |
| --------------------- | ----- | ------ |
| Linear Probe Accuracy | 78.6% | 53.76% |
| Prompt-CAM Accuracy   | 73.2% | 65.46% |
| Insertion Score ↑     | 0.61  | 0.266  |
| Deletion Score ↓      | 0.09  | 0.190  |

---

## Observation

* Method successfully replicated
* Performance gap due to implementation/training differences
* Explanation trends match the paper

---

# Phase 3 — Extension (Swin Transformer)

## Motivation

Swin Transformer uses **hierarchical shifted-window attention**, which preserves spatial information better than ViT.

---

## Hypothesis

> Swin will produce more accurate and sharper explanations than ViT.

---

## Model Setup

| Component    | Details                  |
| ------------ | ------------------------ |
| Backbone     | Swin-Base                |
| Architecture | Hierarchical Transformer |
| Attention    | Shifted-window           |

---

## Results (Extension)

| Metric                | ViT    | Swin       |
| --------------------- | ------ | ---------- |
| Prompt-CAM Accuracy   | 65.46% | **88.07%** |
| Insertion Score ↑     | 0.266  | **0.701**  |
| Deletion Score ↓      | 0.190  | **0.040**  |
| Attention Sharpness ↑ | 0.0015 | **0.0022** |

---

## Key Findings

* Swin significantly improves:

  * Accuracy
  * Faithfulness
  * Attention quality

---

# Evaluation Metrics

## Insertion Score (↑ better)

Measures how quickly confidence increases when important regions are added.

---

## Deletion Score (↓ better)

Measures how quickly confidence drops when important regions are removed.

---

## Attention Sharpness

Measures how focused the attention distribution is.

---

# Results

Generated outputs:

* `phase3_result1_accuracy.png`
* `phase3_result2_attn_maps.png`
* `phase3_result3_faithfulness.png`
* `phase3_result4_sharpness.png`

---

# Conclusion

* Prompt-CAM successfully replicated on ViT
* Swin extension demonstrates clear improvements
* Hypothesis validated:

  > Hierarchical attention improves explanation quality

---
---

## Project Structure

```text
XAI_swin/
├── .idea/                           # IDE configuration directory
├── .lightning_studio/               # Lightning Studio configuration
├── .vscode/                         # VS Code configuration
├── .cursor-server                   # Cursor IDE server symlink
├── .vscode-server                   # VS Code server symlink
├── .windsurf-server                 # Windsurf server symlink
├── .wget-hsts                       # Wget HSTS file
│
├── data/                            # Data directory
│   ├── CUB_200_2011/               # CUB dataset (Caltech-UCSD Birds)
│   └── attributes.txt              # Attribute definitions
│
├── scikit_learn_data/              # Machine learning datasets
│   └── 20news-bydate_py3.pkz       # 20 newsgroups dataset
│
├── README.md                        # Project documentation
├── main.py                          # Main entry point
├── Untitled.ipynb                   # Jupyter notebook for analysis
│
├── Model Weights (PyTorch):
│   ├── pcam_best.pth               # Best model checkpoint
│   ├── pcam_swin.pth               # Swin Transformer model
│   └── pcam_vit.pth                # Vision Transformer model
│
├── Results Visualization:
│   ├── result1_accuracy.png        # Accuracy comparison results
│   ├── result2_attention_maps.png  # Attention map visualizations
│   ├── result3_faithfulness.png    # Faithfulness metrics
│   ├── phase3_result1_accuracy.png
│   ├── phase3_result2_attn_maps.png
│   ├── phase3_result3_faithfulness.png
│   └── phase3_result4_sharpness.png
