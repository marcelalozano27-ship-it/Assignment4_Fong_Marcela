# Named Entity Recognition (NER) Project

**Authors:** Fong Lieu, Marcela Lozano  

---

## 1. Introduction

This project builds a complete Named Entity Recognition (NER) pipeline using the Broad Twitter Corpus. The goal is to identify named entities in informal social media text and evaluate how annotation quality and dataset size impact model performance.

The dataset consists of short Twitter posts, which present unique challenges such as abbreviations, inconsistent capitalization, hashtags, usernames, and noisy formatting. These characteristics make NER more difficult compared to formal text.

We annotated the data using Label Studio and focused on the following entity types:
- PERSON (PER)
- ORGANIZATION (ORG)
- LOCATION (LOC)

A total of 300+ documents were manually annotated and used to train and evaluate custom models.

---

## 2. Methods

### Pretrained Model

We first applied a pretrained NER model to establish a baseline. This model performed reasonably well on standard entities but struggled with informal language, hashtags, and non-standard naming conventions common in Twitter data.

### Annotation Process

The annotation process was conducted in multiple batches:

- **Batch 1:** Full overlap between annotators (10 documents)
- **Batch 2:** Partial overlap (20% of documents)
- **Batch 3:** Correction of pre-annotated data

Annotation guidelines were refined after Batch 1 to improve consistency and reduce ambiguity in entity labeling.

### Custom Model Training

We trained a spaCy NER model using an 80/20 train-test split.

- **Model 1:** Trained on initial annotated dataset  
- **Model 2:** Trained on expanded dataset with corrected pre-annotations  

Hyperparameters were kept consistent across both models to isolate the effect of improved training data.

---

## 3. Results

### Baseline (Pretrained Model)

The pretrained model struggled with informal and noisy text. Common errors included:
- Mislabeling usernames and hashtags
- Missing entities due to inconsistent capitalization
- Incorrect boundary detection

---

### Inter-Annotator Agreement (IAA)

- **Batch 1 IAA:** 70.00% (0.70)  
- **Batch 2 IAA:** 81.80% (0.818)  

The improvement from Batch 1 to Batch 2 shows that refining annotation guidelines significantly increased consistency between annotators.

---

### Model Performance

#### Model 1 (Initial Training)

**Overall Results**
- Precision: 0.6250  
- Recall:    0.1562  
- F1 Score:  0.2500  

**Interpretation:**  
Model 1 had relatively high precision but extremely low recall, meaning it failed to identify many entities. This was primarily due to limited training data.

---

#### Model 2 (Fine-Tuned Model)

**Overall Results**
- Precision: 0.7083  
- Recall:    0.5312  
- F1 Score:  0.6071  

**Interpretation:**  
Model 2 shows a large improvement in recall and overall F1 score. This improvement came from increasing the size and quality of the training dataset through corrected annotations.

---

### Key Comparison

| Metric   | Model 1 | Model 2 |
|----------|--------|--------|
| Precision | 0.6250 | 0.7083 |
| Recall    | 0.1562 | 0.5312 |
| F1 Score  | 0.2500 | 0.6071 |

---

### Per-Entity Analysis

- **LOC** had the highest precision in Model 1, but still suffered from low recall  
- **PER** performed the worst due to variability in naming and informal references  
- **ORG** showed moderate performance but was still limited by data scarcity  

Overall, all entity types improved in Model 2 due to increased training data.

---

## 4. Conclusion

This project demonstrates that annotation quality and dataset size are the most important factors in improving NER performance, especially in noisy domains like Twitter.

Key takeaways:
- Refining annotation guidelines significantly improves inter-annotator agreement  
- Increasing annotated data leads to major performance gains  
- Informal text introduces challenges that pretrained models struggle to handle  
- Low evaluation scores are often caused by limited data rather than code errors  

By expanding and improving the training dataset, we increased F1 score from 0.2500 to 0.6071 without changing model architecture, highlighting the importance of high-quality labeled data in NER tasks.
