# Low-Resource Neural Machine Translation for English–Nagamese

> **Status**: Under Review  
> **Institution**: ABV-IIITM Gwalior  
> **Research Intern**: Anant Maheshwari, Priya Keshri  
> **Supervisor**: Dr. Anjali

---

## Overview

This repository introduces the **first curated English–Nagamese parallel corpus**, designed to improve machine translation for this underrepresented Assamese-lexified creole spoken in Nagaland, India. We benchmark multiple multilingual models on this corpus and analyze both quantitative and qualitative results.

---

## Visual Abstract

> _Overview diagram of dataset pipeline, models, and evaluation strategy_

![Visual Abstract Placeholder](path/to/visual_abstract.png)

---

## Dataset

We compiled a dataset of **8,771 sentence pairs** from four diverse sources:

- **Bible** – 7,950 pairs (formal/literary)
- **Bilingual Comic ("Jesus Messiah: Near to You")** – 378 pairs (conversational)
- **Nagamese Khobor** – 56 pairs (news domain)
- **Miscellaneous** – 387 pairs (daily expressions, travel, market, etc.)

![Dataset Stats Placeholder](path/to/dataset_stats.png)

---

## Models Used

We fine-tuned the following multilingual translation models using HuggingFace’s Transformers:

| Model | Params | Description |
|-------|--------|-------------|
| `facebook/mbart-large-50-many-to-many-mmt` | 680M | Fine-tuned for many-to-many translation |
| `facebook/m2m100_418M` | 418M | Supports 100 languages directly |
| `facebook/nllb-200-distilled-600M` | 600M | Best performance on Nagamese ↔ English |

---

## Evaluation Metrics

We used a mix of surface- and character-level metrics:

- **BLEU** – Word-level n-gram overlap
- **CHR-F** – Character-level F-score, better for morphologically rich/low-resource languages
- **TER** – Edit distance to human reference

---

## Results

### Dataset 1: Bible Only

| Direction | Model | BLEU | TER | CHR-F |
|-----------|-------|------|-----|--------|
| En → Naga | mBART | 23.06 | 64.15 | 54.25 |
|           | NLLB  | 23.01 | 63.54 | **54.98** |
| Naga → En | mBART | 28.66 | 64.01 | 47.62 |
|           | NLLB  | **41.35** | **49.55** | **57.81** |

### Dataset 2: Bible + News + Comic + Others

| Direction | Model | BLEU | TER | CHR-F |
|-----------|-------|------|-----|--------|
| En → Naga | mBART | 21.43 | 64.32 | 53.30 |
|           | NLLB  | 22.88 | 63.05 | **55.01** |
| Naga → En | mBART | 28.77 | 66.38 | 47.84 |
|           | NLLB  | **41.54** | **49.76** | **57.92** |

![Model Comparison Graph Placeholder](path/to/model_comparison_graph.png)

---

## Learning Curves

> Loss and metric trend over epochs for NLLB

![Validation Loss Placeholder](path/to/val_loss_curve.png)  
![BLEU/CHR-F/TER over Epochs Placeholder](path/to/metrics_epoch_curve.png)

---

## Qualitative Analysis

We evaluate translations on representative religious, conversational, and formal sentences.

> Example format:
> - **Input**: Nagamese / English
> - **Reference**: Human translation
> - **Outputs**: mBART, M2M100, NLLB

![Sample Translation Table Placeholder](path/to/qualitative_table.png)

---

## Attention Visualization

> Cross-attention maps from the decoder layer of NLLB

- **English → Nagamese**

  ![Attention Heatmap En2Naga](path/to/attention_en2naga.png)

- **Nagamese → English**

  ![Attention Heatmap Naga2En](path/to/attention_naga2en.png)

---

## Key Insights

- Data augmentation with domain diversity doesn't guarantee better performance.
- **NLLB-200** consistently outperforms mBART and M2M100, especially **Nagamese → English**.
- **CHR-F** is more reliable than **BLEU** in low-resource settings.
- **Qualitative review** reveals many semantically accurate outputs that BLEU fails to reward.
- All models perform well on literal translations, but struggle with abstract/idiomatic language.

---

## 🔮 Future Work

- Joint training for bidirectional translation
- Pivot translation via Assamese/Bengali
- LoRA-based LLM fine-tuning
- Back-translation + domain adaptation
- Broader NLP applications: sentiment, code-switching, chatbots

---

