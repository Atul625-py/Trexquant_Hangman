# Trexquant Hangman Challenge

**Author:** Atul Kumar Pandey  
**Approach:** BiLSTM + Regex Fallback

---

## 🧠 Overview

This project solves Hangman using a hybrid of deep learning and rule-based methods. A BiLSTM model predicts missing letters from masked words, and regex-based fallbacks handle uncertain cases.

---

## 🧾 Dataset

- Words augmented by masking random/consonant letters
- Input: 35-length padded sequences with `{a-z} → 1–26`, `_ → 27`, pad → 0
- Output: 26D binary vector of present letters
- Vowel priors stored for improved fallback guessing

---

## 🧱 Model

- Embedding → BiLSTM (64) → BiLSTM (32) → Dense (32) → Output (26 sigmoid)
- Trained with `binary_crossentropy` & SGD
- Saved as `bi_lstm.weights.h5`

---

## 🔁 Fallback

- Uses regex to match word patterns in dictionary
- Chooses letter with highest occurrence in candidates
- Vowel priors assist if model is uncertain

---

## 🎯 Results

| Threshold | Accuracy (%) |
|-----------|---------------|
| 0.55      | 48            |
| 0.60      | 52            |
| 0.65      | 58            |



