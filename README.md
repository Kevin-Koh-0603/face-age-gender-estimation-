# face-age-gender-estimation-
# Face Age & Gender Estimation under Memory Constraints

## Overview
This project implements convolutional neural network (CNN) models for
**age regression** and **gender classification** using facial images.
The main focus of the project is not only model performance, but also
**designing a memory-efficient training pipeline under limited RAM constraints**.

## Problem
Training deep learning models on large image datasets can easily exceed
available memory, especially when data is duplicated during preprocessing.
Early versions of this project repeatedly crashed due to memory exhaustion
caused by inefficient data handling.

## Solution
To address this issue, the data pipeline was redesigned to:
- Perform dataset splitting only once using index-based splitting
- Share input images across tasks while separating age and gender labels
- Reduce input resolution and batch size to minimize memory usage

This approach enabled stable training without sacrificing core model performance.

## Data
- Dataset: **UTKFace**
- Source: https://www.kaggle.com/datasets/jangedoo/utkface-new
- Size: **20,000+ facial images**
- Labels: Age (regression), Gender (binary classification)

> The dataset is not included in this repository due to size constraints.

## Models
- Framework: **TensorFlow (Keras)**
- Architecture: Convolutional Neural Networks (CNNs)
- Tasks:
  - Age prediction (regression)
  - Gender classification (binary)

## Evaluation Metrics
### Age Model
- MAE: ~8.1 years
- RMSE: ~11.3 years
- R²: ~0.69
- ±10 years accuracy: ~71%

### Gender Model
- Accuracy: ~80%
- F1-score: ~0.78
- ROC-AUC: ~0.88

## Key Takeaways
This project demonstrates that effective machine learning requires
system-level thinking. Memory-aware data pipeline design was critical
to achieving stable and reproducible training under hardware limitations.

## How to Run
1. Install dependencies:
   ```bash
   pip install -r requirements.txt
