# Play Store Game Review Sentiment Analysis

## Project Overview

This project aims to analyze user reviews from popular mobile games on Google Play Store and build machine learning models capable of predicting sentiment from textual reviews.

The study explores the complete Natural Language Processing (NLP) pipeline, including data collection, exploratory data analysis, text preprocessing, text representation, machine learning modeling, hyperparameter tuning, and class imbalance handling.

Three popular simulation games were selected:

* Roblox
* BitLife
* The Sims FreePlay

The original reviews were associated with ratings from 1 to 5 stars. To create a more practical classification task and address class imbalance issues, ratings were transformed into sentiment labels:

| Rating | Sentiment |
| ------ | --------- |
| 1-2    | Negative  |
| 3      | Neutral   |
| 4-5    | Positive  |

---

## Objectives

* Collect and analyze real user reviews from Google Play Store.
* Explore linguistic patterns across different rating categories.
* Apply NLP preprocessing techniques.
* Compare different text representation methods.
* Train and optimize machine learning models.
* Investigate the impact of class imbalance treatment.
* Identify the best-performing sentiment classification model.

---

## Dataset

### Data Source

Reviews were scraped directly from Google Play Store.

### Games Included

| Game              |
| ----------------- |
| Roblox            |
| BitLife           |
| The Sims FreePlay |

### Dataset Characteristics

| Attribute       | Description        |
| --------------- | ------------------ |
| Language        | English            |
| Total Reviews   | ~1000              |
| Review Text     | User comments      |
| Rating          | 1–5 stars          |
| Target Variable | Sentiment Category |

---

## Project Workflow

```text
Data Collection
        ↓
Exploratory Data Analysis
        ↓
Text Preprocessing
        ↓
Text Representation
        ↓
Machine Learning Modeling
        ↓
Hyperparameter Tuning
        ↓
Performance Evaluation
        ↓
Imbalance Handling
        ↓
Model Comparison
```

---

## Exploratory Data Analysis (EDA)

The exploratory phase focused on:

* Rating distribution analysis
* Sentiment distribution analysis
* Most frequent words by rating category
* Detection of non-standard language usage
* Word frequency visualization

### Example Insights

* Positive reviews frequently contain words related to enjoyment, gameplay quality, and updates.
* Negative reviews often mention bugs, crashes, ads, or technical issues.
* Neutral reviews tend to describe gameplay experiences without strong emotional sentiment.

---

## Text Preprocessing

Several NLP preprocessing techniques were applied to improve text quality while preserving semantic meaning.

### Preprocessing Steps

* Lowercasing
* URL removal
* Emoji removal
* Punctuation removal
* Contraction expansion
* Tokenization
* Stopword removal
* Lemmatization

### Special Handling

Negation words were preserved:

```python
no
not
nor
```

This helps maintain sentiment information that could otherwise be lost during preprocessing.

---

## Text Representation Methods

Two different text representation approaches were evaluated.

### 1. TF-IDF

Term Frequency–Inverse Document Frequency converts text into numerical vectors based on word importance within documents.

Advantages:

* Simple and interpretable
* Effective for sparse text classification problems

---

### 2. Word2Vec (Skip-Gram)

Word embeddings were trained using the Skip-Gram architecture.

Advantages:

* Captures semantic relationships
* Produces dense vector representations
* Learns contextual meaning of words

---

## Machine Learning Models

Two machine learning algorithms were selected.

### Logistic Regression

A strong baseline model for text classification tasks.

### XGBoost

A gradient boosting algorithm known for its predictive performance and robustness.

---

## Hyperparameter Tuning

Grid Search Cross Validation was used to optimize model performance.

### Logistic Regression

Example parameters:

* C
* Solver

### XGBoost

Example parameters:

* max_depth
* learning_rate
* n_estimators

---

## Handling Imbalanced Data

The dataset exhibited class imbalance.

Different strategies were applied:

### TF-IDF Models

* Random Over Sampling

### Word2Vec Models

* Class Weight Balancing
* Sample Weight Adjustment

The objective was to determine whether balancing techniques improve model performance and minority class recognition.

---

## Evaluation Metrics

The models were evaluated using:

* Accuracy
* Precision
* Recall
* F1-Score

The comparison was conducted across:

* TF-IDF + Logistic Regression
* TF-IDF + XGBoost
* Word2Vec + Logistic Regression
* Word2Vec + XGBoost

Both before and after imbalance treatment.

---

## Results Summary

| Text Representation | Model               | Accuracy | Precision | Recall | F1 Score |
| ------------------- | ------------------- | -------- | --------- | ------ | -------- |
| TF-IDF              | Logistic Regression | 0.8       | 0.74        | 0.8     | 0.53       |
| TF-IDF              | XGBoost             | 0.74       | 0.68        | 0.74     | 0.48       |
| Word2Vec            | Logistic Regression | 0.65       | 0.42        | 0.65     | 0.26       |
| Word2Vec            | XGBoost             | 0.77       | 0.71        | 0.77     | 0.5       |

---

## Key Findings

* TF-IDF provides a strong baseline for sentiment classification.
* Word2Vec captures semantic relationships but may require larger datasets for maximum effectiveness.
* Hyperparameter tuning significantly improves model performance.
* Imbalance handling improves minority class representation and overall model robustness.
* The best-performing model achieved the highest balance between precision, recall, and F1-score.
