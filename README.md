<h1 align="center">Congressional Voting Record — Classifier Benchmark</h1>

<p align="center">
  <code>Python</code> &nbsp;&nbsp; <code>Machine Learning from Scratch</code> &nbsp;&nbsp; <code>Classification</code>
</p>

<p align="center">
  Academic Project &nbsp;·&nbsp; MPSTME, NMIMS &nbsp;·&nbsp; 2025–2026
</p>

---

### Overview

A rigorous benchmarking study of three supervised machine learning classifiers — Decision Tree, K-Nearest Neighbours, and Naive Bayes — built entirely from scratch in Python without any ML libraries. Applied to the UCI Congressional Voting Records dataset to predict party affiliation (Democrat vs Republican) from 16 key congressional votes.

A distinguishing feature of this project is the use of **Hamming distance** for KNN rather than Euclidean — a deliberate methodological choice justified by the categorical nature of voting data, where numeric distance would impose a false ordering relationship between vote values.

All algorithms implemented using only: `pandas`, `numpy`, `math`, `random`, `matplotlib`, and `collections`.

---

### Dataset

<table style="border: none; border-collapse: collapse;">
  <tr>
    <td style="border: none; padding: 6px 24px 6px 0;"><strong>Source</strong></td>
    <td style="border: none; padding: 6px 0;">UCI Machine Learning Repository — Congressional Voting Records (1984)</td>
  </tr>
  <tr>
    <td style="border: none; padding: 6px 24px 6px 0;"><strong>Records</strong></td>
    <td style="border: none; padding: 6px 0;">435 U.S. House of Representatives members</td>
  </tr>
  <tr>
    <td style="border: none; padding: 6px 24px 6px 0;"><strong>Features</strong></td>
    <td style="border: none; padding: 6px 0;">16 binary congressional votes (Yes / No / Abstain)</td>
  </tr>
  <tr>
    <td style="border: none; padding: 6px 24px 6px 0;"><strong>Target</strong></td>
    <td style="border: none; padding: 6px 0;">Party affiliation — Democrat (0) vs Republican (1)</td>
  </tr>
  <tr>
    <td style="border: none; padding: 6px 24px 6px 0;"><strong>Class Distribution</strong></td>
    <td style="border: none; padding: 6px 0;">61% Democrat · 39% Republican (moderate imbalance)</td>
  </tr>
  <tr>
    <td style="border: none; padding: 6px 24px 6px 0;"><strong>Missing Values</strong></td>
    <td style="border: none; padding: 6px 0;">Abstentions encoded as <code>?</code> — retained as a third category (2), not imputed, as abstention is itself politically informative</td>
  </tr>
  <tr>
    <td style="border: none; padding: 6px 24px 6px 0;"><strong>Train / Test Split</strong></td>
    <td style="border: none; padding: 6px 0;">80/20 (348 train · 87 test · seed=42)</td>
  </tr>
</table>

---

### Classifiers Implemented

<table style="border: none; border-collapse: collapse;">
  <tr>
    <td style="border: none; padding: 6px 24px 6px 0;"><strong>Decision Tree</strong></td>
    <td style="border: none; padding: 6px 0;">Recursive entropy-based splitting with Information Gain; max_depth=8, min_samples=3; feature importance tracked via cumulative information gain across all splits</td>
  </tr>
  <tr>
    <td style="border: none; padding: 6px 24px 6px 0;"><strong>K-Nearest Neighbours</strong></td>
    <td style="border: none; padding: 6px 0;">Hamming distance on categorical vote encodings (0/1/2); majority vote classification; k=7 selected via sensitivity analysis across k=1–21</td>
  </tr>
  <tr>
    <td style="border: none; padding: 6px 24px 6px 0;"><strong>Naive Bayes</strong></td>
    <td style="border: none; padding: 6px 0;">Frequency-based classifier with Laplace smoothing (α=1.0); no binning required as features are already categorical; smoothing sensitivity analysed across α=0.01–10.0</td>
  </tr>
</table>

---

### Analyses Included

<table style="border: none; border-collapse: collapse;">
  <tr>
    <td style="border: none; padding: 6px 24px 6px 0;"><strong>Feature Importance</strong></td>
    <td style="border: none; padding: 6px 0;">Cumulative normalised information gain per vote — identifies which congressional votes are the strongest predictors of party affiliation</td>
  </tr>
  <tr>
    <td style="border: none; padding: 6px 24px 6px 0;"><strong>k-Sensitivity Analysis</strong></td>
    <td style="border: none; padding: 6px 0;">F1-Score evaluated for k=1 to 21 (odd values) to identify the optimal k and quantify sensitivity to neighbourhood size</td>
  </tr>
  <tr>
    <td style="border: none; padding: 6px 24px 6px 0;"><strong>Smoothing Sensitivity</strong></td>
    <td style="border: none; padding: 6px 0;">Naive Bayes accuracy across Laplace smoothing values α=0.01–10.0 on a log scale — demonstrates robustness of the chosen α=1.0</td>
  </tr>
  <tr>
    <td style="border: none; padding: 6px 24px 6px 0;"><strong>5-Fold Cross-Validation</strong></td>
    <td style="border: none; padding: 6px 0;">Mean F1-Score and standard deviation across 5 folds for all three models — provides statistically robust performance estimates beyond a single split</td>
  </tr>
  <tr>
    <td style="border: none; padding: 6px 24px 6px 0;"><strong>Learning Curves</strong></td>
    <td style="border: none; padding: 6px 0;">Training vs validation F1-Score across increasing training set sizes — diagnoses overfitting, underfitting, and convergence behaviour per model</td>
  </tr>
</table>

---

### Results

<table style="border: none; border-collapse: collapse;">
  <tr>
    <td style="border: none; padding: 6px 24px 6px 0;"><strong>Model</strong></td>
    <td style="border: none; padding: 6px 20px 6px 0;"><strong>Accuracy</strong></td>
    <td style="border: none; padding: 6px 20px 6px 0;"><strong>Precision</strong></td>
    <td style="border: none; padding: 6px 20px 6px 0;"><strong>Recall</strong></td>
    <td style="border: none; padding: 6px 0;"><strong>F1-Score</strong></td>
  </tr>
  <tr>
    <td style="border: none; padding: 6px 24px 6px 0;">Decision Tree</td>
    <td style="border: none; padding: 6px 20px 6px 0;">0.9655</td>
    <td style="border: none; padding: 6px 20px 6px 0;">0.9487</td>
    <td style="border: none; padding: 6px 20px 6px 0;">0.9737</td>
    <td style="border: none; padding: 6px 0;">0.9610</td>
  </tr>
  <tr>
    <td style="border: none; padding: 6px 24px 6px 0;">KNN (k=7)</td>
    <td style="border: none; padding: 6px 20px 6px 0;">0.9195</td>
    <td style="border: none; padding: 6px 20px 6px 0;">0.9429</td>
    <td style="border: none; padding: 6px 20px 6px 0;">0.8684</td>
    <td style="border: none; padding: 6px 0;">0.9041</td>
  </tr>
  <tr>
    <td style="border: none; padding: 6px 24px 6px 0;">Naive Bayes</td>
    <td style="border: none; padding: 6px 20px 6px 0;">0.8966</td>
    <td style="border: none; padding: 6px 20px 6px 0;">0.8919</td>
    <td style="border: none; padding: 6px 20px 6px 0;">0.8684</td>
    <td style="border: none; padding: 6px 0;">0.8800</td>
  </tr>
</table>

F1-Score is the primary evaluation metric, selected for its ability to penalise classifiers that sacrifice Precision for Recall on this moderately imbalanced dataset (61/39).

**Recommended model: Decision Tree** — leads on all four metrics (Accuracy 0.9655, Precision 0.9487, Recall 0.9737, F1 0.9610). Its interpretability is an additional advantage: the trained tree produces human-readable if-else rules directly traceable to specific congressional votes, making predictions auditable. For applications where cross-fold stability is the priority, Naive Bayes is preferred due to its lower variance across 5-fold CV.

---

### Key Findings

- **Decision Tree is the clear benchmark winner**, achieving the highest score on every metric — an unusual result that reflects the strongly rule-like structure of congressional voting patterns, which decision boundaries align with naturally
- **Physician Fee Freeze** and **El Salvador Aid** emerged as the strongest predictors of party affiliation by information gain — consistent with the major partisan divides of the 1984 U.S. Congress
- **k-Sensitivity analysis** showed KNN performance peaks at small odd values of k and stabilises by k=7, confirming the chosen value sits at the plateau rather than the elbow — a deliberate conservative choice
- **Hamming distance** is the correct choice for KNN on this dataset — Euclidean distance would impose a false numeric ordering on categorical vote values (0=No, 1=Yes, 2=Abstain)
- **Naive Bayes accuracy is robust** across a wide range of Laplace smoothing values (α=0.1–2.0), validating the choice of α=1.0; performance degrades only at extremes
- **Abstention as a third category** rather than imputed yes/no preserves political signal — legislators who abstain on specific votes exhibit distinct partisan patterns

---

### Technologies

<table style="border: none; border-collapse: collapse;">
  <tr>
    <td style="border: none; padding: 6px 24px 6px 0;"><strong>Language</strong></td>
    <td style="border: none; padding: 6px 0;">Python</td>
  </tr>
  <tr>
    <td style="border: none; padding: 6px 24px 6px 0;"><strong>Environment</strong></td>
    <td style="border: none; padding: 6px 0;">Google Colab</td>
  </tr>
  <tr>
    <td style="border: none; padding: 6px 24px 6px 0;"><strong>Libraries</strong></td>
    <td style="border: none; padding: 6px 0;">pandas · numpy · math · random · matplotlib · collections</td>
  </tr>
</table>

---

*Academic project submitted in partial fulfilment of B.Tech in Information Technology, MPSTME NMIMS, 2025–2026.*
