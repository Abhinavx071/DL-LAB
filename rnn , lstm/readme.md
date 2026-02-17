# Text Generation using RNN and LSTM

### Comparison of One-Hot Encoding vs Trainable Word Embeddings

---

## Project Overview

This project explores how different word representation techniques affect text generation performance using recurrent neural networks. Two encoding strategies were implemented and compared:

* **One-Hot Encoding**
* **Trainable Word Embeddings**

Each encoding method was tested with two neural architectures:

* Vanilla **RNN**
* **LSTM**

The goal is to analyze how representation choice impacts learning efficiency, convergence speed, and overall model performance.

---

## Objectives

* Implement RNN and LSTM models from scratch using PyTorch
* Train models on a poetry dataset
* Compare performance between one-hot and embedding representations
* Evaluate training loss trends and convergence behavior

---

## Dataset

The dataset consists of **100 poems** stored in a CSV file with a single column:

```
text
```

Each row contains a complete poem.
During preprocessing:

* Poems were tokenized into words
* Vocabulary mapping was created
* Sequences of fixed length were generated for training

---

## Model Architectures

### One-Hot Models

Input words are converted into sparse vectors where only one index is active.

* OneHot + RNN
* OneHot + LSTM

---

### Embedding Models

Words are converted into dense trainable vectors.

* Embedding + RNN
* Embedding + LSTM

---

## Training Configuration

| Parameter       | Value        |
| --------------- | ------------ |
| Optimizer       | Adam         |
| Loss            | CrossEntropy |
| Hidden size     | 128          |
| Sequence length | 5            |
| Embedding size  | 100          |

Batch sizes:

* One-Hot models → 16
* Embedding models → 64

---

## Final Results

| Model          | Final Loss |
| -------------- | ---------- |
| OneHot RNN     | 8565       |
| OneHot LSTM    | 8906       |
| Embedding RNN  | 723        |
| Embedding LSTM | **677**    |
<img width="1102" height="847" alt="image" src="https://github.com/user-attachments/assets/547cf7db-7b4a-4171-88de-ed1f2981eb75" />

---

## Observations

* Embedding-based models learned significantly faster than one-hot models.
* One-hot representations produced extremely large sparse inputs, making training inefficient.
* Embeddings captured semantic similarity between words, leading to lower loss.
* LSTM performed better than vanilla RNN due to its ability to retain long-term dependencies.
* The best performing architecture overall was **Embedding + LSTM**.

---

## Conclusion

The experiment demonstrates that **word representation is as important as model architecture** in natural language processing tasks. While RNN and LSTM architectures influence sequence learning, the choice of encoding method has a larger impact on training efficiency and final performance. Dense trainable embeddings consistently outperform one-hot encodings because they provide meaningful vector representations rather than sparse symbolic inputs.


