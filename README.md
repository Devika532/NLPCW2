# Offensive Language Detection Using DistilBERT  
### Natural Language Processing – CW2  
**Module:** 7120CEM  
**University:** Coventry University  
**Coursework:** CW2 – Deep Learning Solution  
**Student:** Devika  

---

## Overview  
This repository presents a deep-learning system for classifying offensive language in social-media text. The model fine-tunes DistilBERT on the OffensEval 2019 Subtask A dataset and builds on the classical machine-learning baselines developed in CW1. The goal is to show how transformer-based contextual representations improve classification of subtle or implicit offensive content.

---

## Dataset  
The project uses the OffensEval 2019 Subtask A English dataset.

- **Total tweets:** 13,240  
- **Labels:**  
  - NOT — Not Offensive  
  - OFF — Offensive  

**Class counts:**  
- NOT: 8,840  
- OFF: 4,400  

A stratified 80/20 split was used to create training and test sets.

---

## Preprocessing  
Minimal preprocessing is applied to avoid removing semantic cues needed by transformers.

Steps used:
- Lowercasing  
- Removing URLs  
- Removing user mentions  
- Removing non-alphabet characters  
- Normalising whitespace  

---

## Tokenisation  
Tokenisation uses **DistilBertTokenizerFast** with:  
- max_length = 128  
- padding = True  
- truncation = True  

---

## Model  
The classifier is **DistilBERT For Sequence Classification**, a lightweight transformer with six encoder layers. A binary classification head is added on top.

**Training configuration:**
- Optimiser: AdamW  
- Learning rate: 5e-5  
- Batch size: 16  
- Epochs: 3  
- Loss function: Cross-entropy  
- Hardware: Google Colab GPU (T4)  

---

## Training  
The model is fine-tuned end-to-end. Both the transformer layers and classifier head update during training. A training loss curve is generated to monitor learning behaviour.

---

## Evaluation Metrics  
- Accuracy  
- Precision  
- Recall  
- F1-score  
- Confusion Matrix  

---

## Results  

**Classification Report (Test Set):**

| Class | Precision | Recall | F1-score | Support |
|-------|-----------|---------|-----------|----------|
| NOT   | 0.83      | 0.86    | 0.85      | 1768     |
| OFF   | 0.70      | 0.64    | 0.67      | 880      |

**Overall:**  
- **Accuracy:** 0.79  
- **Macro F1:** 0.76  

Confusion matrix and training loss plots are included

---

## Author  
**Devika Giriyappa**  
MSc Data Science & Computational Intelligence  
Coventry University  

