# Low-Resource Neural Machine Translation for English–Nagamese

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

<img width="1110" height="792" alt="image" src="https://github.com/user-attachments/assets/bf890aea-f5f9-4a00-a992-3c373f87abcf" />


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

