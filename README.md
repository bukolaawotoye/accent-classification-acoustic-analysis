# Accent Classification Using Acoustic Features and SpeechBrain Embeddings

## Overview

This project investigates how speech accents can be distinguished using both handcrafted acoustic features and deep neural speech embeddings. The goal is to identify which acoustic properties contribute most strongly to accent variation while evaluating the effectiveness of modern speech representation learning for accent classification.

The study combines traditional speech processing techniques—including MFCCs, spectral contrast, vowel formants, and prosodic features—with **SpeechBrain's ECAPA-TDNN** speaker embedding model.

---

## Research Motivation

Accent classification remains a challenging task because accent differences are often subtle and distributed across multiple acoustic dimensions. Many speech recognition systems perform poorly on underrepresented accents, leading to reduced accessibility and fairness.

This project explores whether accent differences can be detected automatically while also providing interpretable acoustic explanations for those differences.

---

# Dataset

The dataset contains **241 speech recordings** representing **13 English accent categories**.

Due to severe class imbalance, the primary classification experiments focused on three major accent groups:

| Accent | Samples |
|---------|---------|
| Mexican English | 110 |
| American English | 79 |
| Nigerian English | 35 |

The complete dataset was used for exploratory analyses such as:

- Principal Component Analysis (PCA)
- t-distributed Stochastic Neighbor Embedding (t-SNE)
- Vowel-space visualization

Each recording was manually labeled with:

- Accent
- Gender
- Audio duration

To minimize lexical variation, every speaker read the same sentence so the analysis focused primarily on pronunciation differences.

---

# Methodology

## Audio Preprocessing

The preprocessing pipeline included:

- FLAC → WAV conversion
- Audio resampling to **16 kHz**
- Metadata generation
- Manifest dictionary creation

---

## Handcrafted Acoustic Feature Extraction

More than **70 acoustic features** were extracted, including:

- Mel-Frequency Cepstral Coefficients (MFCCs)
- Mel Filterbank Energies
- Spectral Contrast
- Voice Onset Time (VOT)
- TH Fricative Energy
- Fundamental Frequency (F0)
- Vowel Duration
- Spectral Centroid
- Root Mean Square (RMS) Energy

---

## Deep Speech Embeddings

SpeechBrain's **ECAPA-TDNN** pretrained model was used to generate **192-dimensional embeddings** for every recording.

These embeddings capture high-level speaker and accent-related characteristics learned through deep neural representation learning.

---

## Dimensionality Reduction

To visualize accent separation within the learned embedding space, two dimensionality reduction techniques were applied:

- Principal Component Analysis (PCA)
- t-distributed Stochastic Neighbor Embedding (t-SNE)

---

## Classification Models

The following machine learning models were evaluated:

- Logistic Regression
- Support Vector Machine (SVM)
- Random Forest

---

# Results

## Best Performing Model

**Logistic Regression** trained on ECAPA embeddings achieved:

| Metric | Score |
|---------|-------|
| Accuracy | **80.4%** |
| Random Baseline | 33.3% |

---

## Pairwise Accent Classification

| Accent Pair | Accuracy |
|--------------|---------|
| Mexican vs Nigerian | **95.9%** |
| American vs Nigerian | **89.4%** |
| Mexican vs American | **68.9%** |

These findings indicate that **Nigerian English** was the most acoustically distinct accent in the dataset, whereas **Mexican** and **American English** exhibited greater overlap.

---

## Vowel Space Analysis

Average vowel formant frequencies:

| Accent | Mean F1 (Hz) | Mean F2 (Hz) |
|---------|-------------:|-------------:|
| Mexican | 637 | 1803 |
| American | 607 | 1644 |
| Nigerian | 685 | 1713 |

Although vowel formants provided interpretable accent information, they were insufficient for completely separating accent groups.

---

# Key Findings

- Deep speech embeddings outperformed handcrafted acoustic features.
- Accent information is distributed across multiple acoustic dimensions.
- Nigerian English formed the most compact and separable cluster.
- Most classification errors occurred between American and Mexican English.
- Vowel formants alone are insufficient for complete accent classification.

---

# Technologies

- Python
- SpeechBrain
- PyTorch
- Librosa
- Praat-Parselmouth
- Scikit-learn
- NumPy
- Pandas
- Matplotlib

---

# Future Work

Potential improvements include:

- Expanding the dataset with additional English accents.
- Developing a real-time accent prediction application.
- Incorporating temporal phonetic analysis.
- Exploring interpretable deep embedding analysis methods.

---

# References

1. SpeechBrain: A General-Purpose Speech Toolkit (2021)
2. Open-Source Conversational AI with SpeechBrain 1.0 (2024)
3. Jaisinghani & Yoon (2025). *Effects of F1–F2 Frequency Spacing on Spectral Integration in Combined Electric and Acoustic Stimulation.*

---

## Author

**Bukola Awotoye**

Bachelor of Science in Computer Science  
Minor in Applied Statistics and Data Science  
University of Texas Rio Grande Valley

Interested in Speech Processing, Machine Learning, Data Science, and AI.
