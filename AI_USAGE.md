# AI_USAGE.md

## AI Tool Usage Declaration

This document describes how AI tools were used in the development of this project.

---

## Tool Used

* **Tool:** ChatGPT (OpenAI)
* **Purpose:** Assistance in understanding concepts, generating code structure, debugging, and documentation support

---

## Scope of Usage

AI assistance was used in the following areas:

### 1. Conceptual Understanding

* Understanding Prompt-CAM methodology
* Clarifying evaluation metrics such as:

  * Insertion Score
  * Deletion Score
  * Attention Sharpness
* Understanding differences between Vision Transformers (ViT) and Swin Transformer

---

### 2. Code Assistance

AI was used to:

* Generate initial code templates for:

  * Feature extraction (ViT / Swin)
  * Prompt-CAM implementation
* Suggest improvements for:

  * Training loops
  * Evaluation metrics
* Debug runtime errors and optimize execution

---

### 3. Prompt-Based Code Generation

The following prompts were used:

---

#### 🔹 Phase 2 (Replication Prompt)

> You are an expert in Explainable AI and Computer Vision.
> I am working on a project based on the paper: "Prompt-CAM: Making Vision Transformers Interpretable for Fine-Grained Analysis".
> Give me clean, runnable Google Colab code to replicate Prompt-CAM using:
>
> * CUB-200 dataset
> * DINO ViT backbone
> * Feature extraction + Prompt-based attention
> * Evaluation metrics including accuracy, insertion and deletion scores
>   Use tqdm progress bars and keep the code modular.

---

#### 🔹 Phase 3 (Improvement Prompt)

> I have replicated Prompt-CAM on ViT.
> Now extend this work by applying Prompt-CAM to Swin Transformer.
> Compare performance using:
>
> * Accuracy
> * Faithfulness metrics (insertion, deletion)
> * Attention sharpness
>   Show how hierarchical attention improves explanation quality.
>   Provide clean, structured, and runnable code.

---

---

### 4. Documentation Assistance

AI was used to:

* Generate README.md
* Structure project into Phase 1, Phase 2, and Phase 3
* Prepare explanations for:

  * Research gap
  * Methodology
  * Results interpretation

---


**Authors:**

* Preetham P (23bds046)
* Prem Sagar TK (23bds065)

