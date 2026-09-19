# Benchmarking-Lexical-Distributional-and-Contextual-Representations-for-NLP-Text-Analytics

## 1. Project Overview

This project investigates different approaches to **Natural Language Processing (NLP)** and large-scale text analytics by comparing **lexical, distributional, and contextual text representations**.

The project focuses on:

* Topic modelling
* Text classification
* Sentiment analysis
* Comparison of TF-IDF and word-embedding representations
* Evaluation of representation quality across different NLP tasks

The objective was to understand how different text representations affect classification performance, computational efficiency, and the ability to capture meaningful information from large-scale text collections.

---

## 2. Datasets

Two benchmark datasets were used for the experiments.

### 20 Newsgroups

The **20 Newsgroups** dataset was used for multi-class document classification and topic modelling.

```text
Training documents: 10,964
Testing documents: 7,284
Number of categories: 20
```

The dataset contains documents distributed across 20 different subject categories.

### IMDb Movie Reviews

The **IMDb Movie Reviews** dataset was used for binary sentiment analysis.

```text
Training documents: 20,000
Testing documents: 5,000
Task: Binary sentiment classification
```

---

## 3. Methodology

The project follows an NLP pipeline consisting of:

```text
Raw Text Data
      │
      ▼
Text Preprocessing
      │
      ▼
Text Representation
      │
 ┌────┼───────────────┐
 ▼    ▼               ▼
TF-IDF  Word2Vec      GloVe
 │      │             │
 └──────┴─────────────┘
          │
          ▼
 Classification
          │
     ┌────┴─────┐
     ▼          ▼
Logistic      Linear
Regression      SVM
     │          │
     └────┬─────┘
          ▼
   Model Evaluation
          │
          ├── Accuracy
          ├── F1-Score
          └── Training Time
```

Topic modelling was performed separately using **Latent Dirichlet Allocation (LDA)**.

---

## 4. Topic Modelling

### Latent Dirichlet Allocation

**Latent Dirichlet Allocation (LDA)** was used to discover latent topics within the text corpus.

The model was configured with:

```text
Number of topics: 20
Mean topic coherence score: 0.2040
```

### Example Topics

Representative topics discovered by LDA included:

| Topic    | Interpretation         | Representative Terms                      |
| -------- | ---------------------- | ----------------------------------------- |
| Topic 1  | Discussion / Opinions  | don, think, people, just, know, like, say |
| Topic 3  | System / OS / Software | file, windows, software, image, graphics  |
| Topic 6  | Religion / Philosophy  | god, jesus, bible, christian, believe     |
| Topic 12 | Law / Politics         | gun, law, people, government, rights      |

---

## 5. Text Representations

Three major representation approaches were investigated.

### TF-IDF

**Term Frequency–Inverse Document Frequency (TF-IDF)** represents documents using the importance of individual terms within documents and across the corpus.

TF-IDF was evaluated using:

* Logistic Regression
* Linear SVM

### Word2Vec

**Word2Vec** was used as a distributional representation that captures semantic relationships between words.

Word vectors were aggregated to obtain document-level representations for classification.

### GloVe

**GloVe (Global Vectors for Word Representation)** was evaluated as another static distributional representation for document classification.

---

## 6. Classification Models

The project evaluated different combinations of text representations and classification algorithms.

### Logistic Regression

Logistic Regression was used with:

* TF-IDF
* Word2Vec
* GloVe

### Linear SVM

A **Linear Support Vector Machine** was evaluated using TF-IDF representations.

---

## 7. Classification Results

The representation methods were evaluated on the **20 Newsgroups** dataset using accuracy, F1-score, and training time.

| Representation | Model               | Dataset       |   Accuracy |   F1-Score | Training Time |
| -------------- | ------------------- | ------------- | ---------: | ---------: | ------------: |
| TF-IDF         | Logistic Regression | 20 Newsgroups | **71.06%** | **70.73%** |        18.78s |
| TF-IDF         | Linear SVM          | 20 Newsgroups |     70.50% |     70.28% |     **2.10s** |
| Word2Vec       | Logistic Regression | 20 Newsgroups |     62.97% |     62.37% |         8.66s |
| GloVe          | Logistic Regression | 20 Newsgroups |     59.49% |     58.81% |        11.85s |
| TF-IDF         | Logistic Regression | IMDb          | **88.44%** | **88.40%** |         0.65s |

---

## 8. Performance Analysis

### 20 Newsgroups Classification

For the multi-class **20 Newsgroups** classification task, TF-IDF achieved higher accuracy and F1-score than the averaged Word2Vec and GloVe representations.

The reported results were:

```text
TF-IDF + Logistic Regression
Accuracy: 71.06%
F1-Score: 70.73%

TF-IDF + Linear SVM
Accuracy: 70.50%
F1-Score: 70.28%

Word2Vec + Logistic Regression
Accuracy: 62.97%
F1-Score: 62.37%

GloVe + Logistic Regression
Accuracy: 59.49%
F1-Score: 58.81%
```

---

## 9. Sentiment Analysis

The **IMDb Movie Reviews** dataset was used for binary sentiment classification.

The TF-IDF + Logistic Regression model achieved:

```text
Accuracy: 88.44%
F1-Score: 88.40%
Training Time: 0.65 seconds
```

This demonstrates that a relatively simple lexical representation can provide strong performance for sentiment classification while remaining computationally efficient.

---

## 10. Key Findings

### Lexical Representations

For the **20 Newsgroups** multi-class classification task, TF-IDF outperformed the averaged Word2Vec and GloVe representations by approximately **8–11 percentage points in accuracy**.

The report attributes this behaviour to the fact that keyword presence can be highly informative for distinguishing clearly defined subject categories, while averaging word vectors can dilute specific keyword signals.

### Sentiment Classification

For IMDb sentiment analysis, TF-IDF achieved **88.44% accuracy** and **88.40% F1-score**, demonstrating strong performance as a fast baseline for sentiment classification.

---

## 11. Topic Modelling Pipeline

```text
20 Newsgroups Corpus
        │
        ▼
 Text Preprocessing
        │
        ▼
 Document-Term Matrix
        │
        ▼
 Latent Dirichlet Allocation
        │
        ▼
    20 Topics
        │
        ▼
 Topic Coherence Analysis
        │
        ▼
Topic Interpretation
```

---

## 12. Representation Comparison

```text
                    Text Corpus
                        │
          ┌─────────────┼─────────────┐
          ▼             ▼             ▼
        TF-IDF       Word2Vec       GloVe
          │             │             │
          ▼             ▼             ▼
      Logistic       Logistic       Logistic
     Regression     Regression     Regression
          │             │             │
          └─────────────┼─────────────┘
                        ▼
                 Performance
                  Comparison
```

The comparison provides an experimental basis for analysing the differences between **lexical representations** and **static distributional representations** for downstream NLP tasks.

---

## 13. Technologies Used

* Python
* Pandas
* NumPy
* Scikit-learn
* NLTK
* Gensim
* Matplotlib
* Seaborn
* TF-IDF
* Word2Vec
* GloVe
* Logistic Regression
* Linear SVM
* Latent Dirichlet Allocation (LDA)

---

## 14. Key Outputs

The project produces outputs covering:

### Topic Modelling

* Discovered latent topics
* Topic-word distributions
* Topic coherence score
* Representative terms for each topic

### Classification

* Accuracy
* F1-score
* Training time
* Model comparison

### Analysis

* Representation performance comparison
* Topic interpretation
* Computational efficiency analysis

---

## 15. Conclusion

This project provides a comparative study of **lexical and distributional text representations** for large-scale NLP tasks.

The experiments demonstrated that TF-IDF performed strongly on both the **20 Newsgroups multi-class classification task** and the **IMDb sentiment classification task**. On 20 Newsgroups, TF-IDF achieved higher performance than the averaged Word2Vec and GloVe representations.

The project also demonstrated the use of **LDA for unsupervised topic discovery**, producing 20 latent topics with a mean topic coherence score of **0.2040**.

Overall, the work provides practical experience in **text representation, topic modelling, document classification, sentiment analysis, and comparative evaluation of NLP approaches**.

---

## 16. Research Relevance

This project demonstrates experience in:

* **Natural Language Processing**
* **Large-scale text analytics**
* **Text representation learning**
* **Topic modelling**
* **Sentiment analysis**
* **Multi-class document classification**
* **Feature engineering**
* **Machine learning for text**
* **Word embeddings**
* **Model evaluation**
* **Computational efficiency analysis**

The project provides a foundation for further investigation of **contextual language representations, transformer-based models, semantic representation learning, and large-scale NLP systems**.

