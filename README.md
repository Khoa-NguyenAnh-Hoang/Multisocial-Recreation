# MultiSocial-Recreation

Multilingual stereotype and speech classification across **Arabic, English, Vietnamese, and Chinese**.

This project was developed for **DS319 — Large Language Models** and recreates and extends experiments around multilingual synthetic text generation and classification.

## Overview

The project investigates how multilingual language models perform when detecting machine-generated content across multiple languages.

The workflow covers:

* Dataset preparation and validation
* Pretrained / zero-shot baselines
* Statistical baselines
* XLM-R fine-tuning
* Cross-lingual transfer experiments
* Multilingual synthetic data generation
* Statistical and classification evaluation

## Languages

| Language   | Code |
| ---------- | ---- |
| English    | `en` |
| Vietnamese | `vi` |
| Chinese    | `zh` |
| Arabic     | `ar` |

## Dataset

The final classification experiments use:

* **12,789 training samples**
* **3,197 test samples**
* Four languages: English, Vietnamese, Chinese, and Arabic
* Text, binary label, and language metadata

The test set contains approximately 800 samples per language.

Generated multilingual data and experiment outputs are stored under `multisocial_outupts/`.

## Experiments

### 1. Data Preparation

`00_data_prep.ipynb`

Prepares, validates, and organizes the multilingual dataset used by the downstream experiments.

### 2. Pretrained / Zero-Shot Baselines

`01_pretrained.ipynb`

Evaluates pretrained models without task-specific fine-tuning to establish baseline performance.

### 3. XLM-R Fine-Tuning

`02_finetuning.ipynb`

Fine-tunes `xlm-roberta-base` for binary sequence classification.

Configuration includes:

* Maximum sequence length: 256
* Learning rate: `2e-5`
* Epochs: 3
* Training batch size: 16
* Evaluation batch size: 16
* Random seed: 42

Evaluation metrics:

* Accuracy
* Macro-F1
* ROC-AUC
* Precision
* Recall
* Confusion matrix

### 4. Statistical Baselines

`03_statistical.ipynb`

Evaluates statistical / non-transformer approaches as additional baselines for comparison.

### 5. Cross-Lingual Transfer

`04_transfer.ipynb`

Evaluates cross-lingual generalization using leave-one-language-out experiments:

* Train on three languages
* Hold out one language
* Evaluate on the unseen language
* Repeat for all four languages

The experiment produced a macro-average of:

| Metric   |  Score |
| -------- | -----: |
| Accuracy | 54.92% |
| F1       | 54.34% |
| ROC-AUC  | 67.74% |

The results demonstrate that cross-lingual transfer is substantially more difficult than evaluating a model on the combined multilingual setting.

## Main Result

The fine-tuned XLM-R model achieved the following overall test performance:

| Metric   |    Overall |
| -------- | ---------: |
| Accuracy | **81.36%** |
| Macro-F1 | **81.35%** |
| ROC-AUC  | **91.44%** |

Performance varies substantially across languages, highlighting the difficulty of maintaining consistent multilingual classification quality.

Per-language results:

| Language   | Accuracy | Macro-F1 | ROC-AUC |
| ---------- | -------: | -------: | ------: |
| English    |   95.38% |   95.38% |  98.42% |
| Vietnamese |   70.26% |   70.16% |  78.17% |
| Chinese    |   71.50% |   71.23% |  81.11% |
| Arabic     |   88.25% |   88.25% |  96.20% |

## Repository Structure

```text
.
├── 00_data_prep.ipynb
├── 01_pretrained.ipynb
├── 02_finetuning.ipynb
├── 03_statistical.ipynb
├── 04_transfer.ipynb
│
├── generate_multisocial_ar.ipynb
├── generate_multisocial_en.ipynb
├── generate_multisocial_vi.ipynb
├── generate_multisocial_zh.ipynb
│
├── multisocial_outupts/
├── paper/
│
├── 2025.acl-long.36.pdf
├── 21_23520736_BaocaoCK.pdf
└── 21_23520736_Slidebaocao.pdf
```

## Tech Stack

* Python
* PyTorch
* Hugging Face Transformers
* Hugging Face Datasets
* XLM-RoBERTa
* scikit-learn
* NumPy
* Pandas
* Matplotlib
* Seaborn
* Jupyter / Google Colab

## Key Takeaways

The experiments show that strong aggregate multilingual performance does not necessarily imply consistent performance across individual languages.

The fine-tuned XLM-R model performed strongly overall, but Vietnamese and Chinese showed noticeably lower performance than English and Arabic. The cross-lingual transfer experiments further demonstrate the difficulty of generalizing to a language excluded from training.

This project therefore focuses not only on model performance, but also on **comparative evaluation, language-level analysis, and cross-lingual generalization**.

## Course

**DS319 — Large Language Models**

University of Information Technology — VNU-HCM

