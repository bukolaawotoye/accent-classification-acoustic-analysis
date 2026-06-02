# Accent Classification Using Acoustic Features and SpeechBrain Embeddings

### Overview

This project investigates how speech accents can be distinguished using both handcrafted acoustic features and deep neural speech embeddings. The goal is to identify which acoustic properties contribute most strongly to accent variation and to evaluate the effectiveness of modern speech representation learning for accent classification.

The study combines traditional speech processing techniques, including MFCCs, spectral contrast, vowel formants, and prosodic features, with SpeechBrain's ECAPA-TDNN speaker embedding model.

<hr>

__Research Motivation__

Accent classification remains challenging because accent differences are often subtle and distributed across multiple acoustic dimensions. Many speech systems perform poorly on underrepresented accents, leading to reduced accessibility and fairness.

This project explores whether accent differences can be detected automatically while also providing interpretable acoustic explanations for those differences.

<hr>
### Dataset

The dataset contains 241 speech recordings representing 13 accent categories.

Due to severe class imbalance, the primary classification experiments focused on:

Mexican English (110 samples)
American English (79 samples)
Nigerian English (35 samples)

The complete dataset was used for exploratory analyses such as PCA, t-SNE, and vowel-space visualization.

Each recording was manually labeled with:

Accent
Gender
Audio duration

All speakers read the same sentence to minimize lexical variation and focus on pronunciation differences.

<hr>
### Methodology

Audio Preprocessing
FLAC to WAV conversion
Resampling to 16 kHz
Metadata creation
Manifest dictionary generation
Handcrafted Acoustic Features

More than 70 acoustic features were extracted, including:

MFCCs
Mel-filterbank energies
Spectral contrast
Voice Onset Time (VOT)
TH-fricative energy
Fundamental frequency (F0)
Vowel duration
Spectral centroid
RMS energy
Deep Speech Embeddings

SpeechBrain's ECAPA-TDNN model was used to generate 192-dimensional embeddings for each recording. These embeddings capture high-level speaker and accent-related characteristics.

Visualization

Dimensionality reduction techniques:

PCA
t-SNE

were used to visualize accent separation in embedding space.

Classification Models
Logistic Regression
Support Vector Machine (SVM)
Random Forest
Results
Best Performing Model

Logistic Regression trained on ECAPA embeddings achieved:

80.4% accuracy

compared to a random baseline of 33.3%.

Pairwise Accent Classification
Accent Pair	Accuracy
Mexican vs Nigerian	95.9%
American vs Nigerian	89.4%
Mexican vs American	68.9%

These results indicate that Nigerian English was the most acoustically distinct accent in the dataset, while Mexican and American accents showed greater overlap.

Vowel Space Analysis

Average vowel formants:

| Accent | Mean F1 | Mean F2 |
| :--- | :---: | ---: |
| Mexican | 637 Hz | 1803 Hz |
| American | 607 Hz | 1644 Hz |
| Nigerian | 685 Hz | 1713 Hz |

Vowel formants provided interpretable accent information but did not fully separate the accent groups on their own.

<hr>
Key Findings

1. Deep speech embeddings outperformed handcrafted acoustic features.
2. Accent information is distributed across multiple acoustic dimensions.
3. Nigerian English formed the most compact and separable cluster.
4. Most classification errors occurred between American and Mexican speakers.
5. Vowel formants alone are insufficient for complete accent classification.

<hr>
Technologies

1. Python
2. SpeechBrain
3. PyTorch
4. Librosa
5. Praat-Parselmouth
6. Scikit-Learn
7. NumPy
8. Pandas
9. Matplotlib

<hr>
Future Work

1. Expand the dataset with additional accents.
2. Build a real-time accent prediction interface.
3. Incorporate temporal phonetic analysis.
4. Explore interpretable embedding analysis techniques.

<hr>
References

SpeechBrain: A General-Purpose Speech Toolkit (2021)
Open-Source Conversational AI with SpeechBrain 1.0 (2024)
Jaisinghani & Yoon (2025) – Effects of F1–F2 Frequency Spacing on Spectral Integration in Combined Electric and Acoustic Stimulation.
