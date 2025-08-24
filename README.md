# Low-Resource Neural Machine Translation for English–Nagamese

[![View Dataset on Kaggle](https://img.shields.io/badge/View%20Dataset-Kaggle-blue?logo=kaggle)]([https://www.kaggle.com/your-username/your-dataset-name]https://www.kaggle.com/datasets/belovedorange/first-nagamese-english-parallel-corpus-fnpc-25))

> **Status**: Under Review  
> **Institution**: ABV-IIITM Gwalior  
> **Research Intern**: Anant Maheshwari, Priya Keshri  
> **Supervisor**: Dr. Anjali

---

## Overview

This repository introduces the **first curated English–Nagamese parallel corpus**, designed to improve machine translation for this underrepresented creole spoken in Nagaland, India. We benchmark multiple multilingual models on this corpus and analyze both quantitative and qualitative results.

---

## Dataset

We compiled a dataset of **8,771 sentence pairs** from four diverse sources:

- **Bible** – 7,950 pairs (formal/literary)
- **Bilingual Comic ("Jesus Messiah: Near to You")** – 378 pairs (conversational)
- **Nagamese Khobor** – 56 pairs (news domain)
- **Miscellaneous** – 387 pairs (daily expressions, travel, market, etc.)

<img width="658" height="520" alt="image" src="https://github.com/user-attachments/assets/b1a6afb4-9df1-4fa4-a73e-1a24ea58a1d3" />


---

## Models Used

We fine-tuned the following multilingual translation models using HuggingFace’s Transformers:

| Model | Params | Pre trained Lnaguages |
|-------|--------|-------------|
| `facebook/mbart-large-50-many-to-many-mmt` | 680M | 50 |
| `facebook/m2m100_418M` | 418M | 100 |
| `facebook/nllb-200-distilled-600M` | 600M | 200 |

---

## Evaluation Metrics

We used a mix of surface- and character-level metrics:

- **BLEU** – Word-level n-gram overlap
- **CHR-F** – Character-level F-score, better for morphologically rich/low-resource languages
- **TER** – Edit distance to human reference

---

## Results

### Dataset 1: Bible Only

<img width="543" height="425" alt="image" src="https://github.com/user-attachments/assets/28841a5c-6de6-4625-90e7-9248051a9847" />


### Dataset 2: Bible + News + Comic + Others

<img width="680" height="482" alt="image" src="https://github.com/user-attachments/assets/53cc2ca2-e165-4834-8c8a-f62dbf40316d" />

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
## Contact

For questions or collaboration opportunities, feel free to reach out:

priya.keshrinis@gmail.com
anant200519@gmail.com


