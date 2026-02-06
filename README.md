# Transformer Gradient Geometry Analysis

This repository presents an empirical study of optimization dynamics in Transformer-based language models, with a focus on comparing **Full Fine-Tuning** and **Low-Rank Adaptation (LoRA)**. The project analyzes gradient geometry, learning rate sensitivity, optimization alignment, and layer-wise learning activity to understand how parameter-efficient fine-tuning constrains and shapes the training trajectory.

This work is intended as a systematic experimental investigation into the mechanisms underlying LoRA and related adaptation methods.

---

## Table of Contents

- Project Objectives  
- Experimental Overview  
- Methodology  
- Repository Structure  
- Installation  
- Usage  
- Key Findings  
- Research Contributions  
- Limitations  
- Future Work  
- Citation  
- License  
- Contact  

---

## Project Objectives

The primary objectives of this project are:

- To characterize the geometric structure of gradients during Transformer fine-tuning.
- To analyze how learning rate affects optimization stability.
- To compare Full Fine-Tuning and LoRA in terms of update direction, magnitude, and variance.
- To study where learning is concentrated across model depth.
- To provide empirical explanations for the effectiveness of LoRA.

---

## Experimental Overview

The project is organized as a sequence of controlled experiments implemented in Jupyter notebooks.

### 1. Baseline Gradient Geometry

**Notebook:** `01_baseline_gradient_geometry.ipynb`

- Logs gradient norms and random projections.
- Establishes baseline optimization behavior.
- Serves as a reference for subsequent experiments.

---

### 2. Learning Rate Sensitivity

**Notebook:** `02_lr_sensitivity_gradient_geometry.ipynb`

- Studies optimization behavior under multiple learning rates.
- Analyzes gradient stability and dispersion.
- Evaluates sensitivity to step size.

---

### 3. Full Fine-Tuning vs LoRA

**Notebook:** `03_lora_vs_fullft_gradient_geometry.ipynb`

- Compares gradient statistics between Full FT and LoRA.
- Measures magnitude, variance, and distribution differences.
- Characterizes constraints induced by low-rank adaptation.

---

### 4. Alignment Analysis

**Notebook:** `04_alignment_check.ipynb`

- Computes cosine similarity between Full FT and LoRA updates.
- Tracks alignment dynamics across training steps.
- Evaluates how closely LoRA approximates the full optimization trajectory.

---

### 5. Layer-wise Learning Activity

**Notebook:** `05_layer_activity.ipynb`

- Aggregates gradient norms by Transformer layer.
- Analyzes depth-wise learning distribution.
- Reports mean and variance per layer.
- Reveals depth-selective learning patterns.

---

## Methodology

### Model

- Base model: DistilGPT-2
- Architecture: Decoder-only Transformer
- Framework: Hugging Face Transformers

### Fine-Tuning Methods

- Full Fine-Tuning (all parameters trainable)
- LoRA-based parameter-efficient adaptation

### Metrics

- Gradient L2 norms
- Random subspace projections
- Cosine similarity of update vectors
- Layer-wise gradient statistics
- Variance and stability measures

### Data

- Language modeling datasets (WikiText variants or synthetic batches)
- Tokenization using pretrained tokenizers

### Logging

Training procedures log per-parameter gradient statistics and store them as `.pt` files for post-hoc analysis.

---

## Repository Structure

```text
transformer-gradient-geometry/
│
├── notebooks/
│   ├── 01_baseline_gradient_geometry.ipynb
│   ├── 02_lr_sensitivity_gradient_geometry.ipynb
│   ├── 03_lora_vs_fullft_gradient_geometry.ipynb
│   ├── 04_alignment_check.ipynb
│   └── 05_layer_activity.ipynb
│
├── logs/                 # Ignored (experiment artifacts)
├── figures/              # Ignored (generated plots)
├── README.md
├── requirements.txt
└── .gitignore
