# Spatial Attention BiMamba for EEG Classification

## Author

**Putra Khaeran Shauma**

Computer Science Student  
Universitas Jenderal Achmad Yani

---

## Overview

This project presents an experimental deep learning architecture called **Spatial Attention BiMamba (SA-BiMamba)** for multi-task Electroencephalogram (EEG) signal classification.

The research investigates EEG representations across three different classification tasks:

- **Motor Imagery (MI)**
- **Emotion Recognition**
- **Cognitive Focus Classification**

The proposed approach combines spatial EEG representation, attention mechanisms, and bidirectional Mamba-based sequence modeling to capture both spatial and sequential information within EEG signals.

In addition to supervised classification, this research also explores **Self-Supervised Learning (SSL)** for EEG representation learning through signal reconstruction and pre-training.

This project was developed as part of a collaborative student research initiative under **Program Kreativitas Mahasiswa (PKM)**.

---

## Research Objectives

The main objectives of this research are:

1. Develop a deep learning architecture for multi-task EEG classification.
2. Explore spatial relationships between EEG channels.
3. Apply spatial attention to emphasize informative EEG representations.
4. Utilize Bidirectional Mamba for sequential EEG modeling.
5. Evaluate individual architectural components through ablation experiments.
6. Explore Self-Supervised Learning for EEG representation pre-training.
7. Evaluate the learned representations across Motor Imagery, Emotion, and Focus classification tasks.

---

## Classification Tasks

The proposed architecture is evaluated across three EEG classification tasks:

| Task | Description |
|---|---|
| **Motor Imagery (MI)** | Classification of EEG patterns associated with imagined motor activity |
| **Emotion** | Classification of EEG signals associated with emotional states |
| **Focus** | Classification of EEG patterns associated with cognitive focus states |

---

## Methodology

The general experimental workflow consists of:

1. EEG dataset preparation
2. EEG signal preprocessing
3. Spatial and temporal representation
4. Spatial Attention processing
5. Bidirectional Mamba feature modeling
6. Multi-task classification
7. Model training and validation
8. Ablation study
9. Self-Supervised Learning pre-training
10. Model evaluation and analysis

---

## Model Architecture

The proposed **Spatial Attention BiMamba (SA-BiMamba)** architecture is designed to model spatial and sequential characteristics of EEG signals.

The architecture incorporates several main components:

- EEG Input Representation
- Spatial Feature Processing
- Spatial Attention
- Mamba-based Spatial Modeling
- Bidirectional Sequential Modeling
- Temporal Feature Processing
- Classification Layers

### Spatial Attention

The Spatial Attention mechanism is designed to emphasize informative spatial relationships across EEG channels.

Since EEG signals are recorded through multiple electrodes positioned across different scalp regions, spatial modeling allows the architecture to learn relationships between channel-level representations.

### Bidirectional Mamba

Bidirectional Mamba is used to model sequential EEG representations from multiple directions.

This allows the architecture to capture contextual dependencies within the EEG representation while maintaining the efficient sequence modeling characteristics of Mamba-based architectures.

---

## Validation Performance

The model was evaluated across Motor Imagery, Emotion, and Focus classification tasks using validation Accuracy and Macro F1-Score.

The validation curves show different performance characteristics across the three EEG tasks.

### Validation Performance Summary

| Classification Task | Validation Accuracy | Macro F1-Score |
|---|---:|---:|
| **Motor Imagery** | ~71% | ~71% |
| **Emotion** | ~84% | ~84% |
| **Focus** | ~97% | ~97% |

> Values shown above are approximate values based on the final validation curves and may vary slightly between experimental runs.

### Validation Accuracy and Macro F1

<p align="center">
  <img src="results/validation_performance_curves.png"
       alt="Validation Accuracy and Macro F1 Curves"
       width="1000">
</p>

The figure shows the validation Accuracy and Macro F1-Score across training epochs for the three classification tasks.

---

## Confusion Matrix Analysis

Confusion matrices were used to analyze the prediction distribution of the model across each classification task.

<p align="center">
  <img src="results/confusion_matrices.png"
       alt="Confusion Matrices for Motor Imagery Emotion and Focus"
       width="1000">
</p>

The confusion matrices provide a class-level view of model predictions for:

- Motor Imagery
- Emotion
- Focus

This evaluation complements the aggregate Accuracy and Macro F1 metrics by showing how predictions are distributed across individual classes.

---

## Ablation Study

An ablation study was conducted to evaluate the contribution of individual components within the proposed **Spatial Attention BiMamba (SA-BiMamba)** architecture.

The full architecture was compared against several modified configurations where specific components were removed.

The evaluated configurations include:

- **Full SA-BiMamba**
- Without Graph-based components (PLV and LCE)
- Without Spatial Mamba Block
- Without CWT
- Without Temporal Mamba Block

<p align="center">
  <img src="results/ablation_study_accuracy.png"
       alt="Spatial Attention BiMamba Ablation Study"
       width="1000">
</p>

The ablation experiment helps analyze how individual architectural components contribute to performance across Motor Imagery, Emotion, and Focus classification tasks.

---

## Self-Supervised Learning

Self-Supervised Learning (SSL) was explored as a pre-training strategy for learning EEG representations before downstream classification.

The SSL experiments focus on learning representations through EEG reconstruction and evaluating whether pre-trained representations improve downstream classification performance.

### EEG Signal Reconstruction

During SSL pre-training, the model learns to reconstruct EEG representations from the input signal.

The visualization below presents:

- Original target EEG representation
- Reconstructed representation
- Absolute reconstruction error
- One-dimensional signal tracking between target and prediction

<p align="center">
  <img src="results/ssl_eeg_signal_reconstruction.png"
       alt="Self-Supervised EEG Signal Reconstruction"
       width="1000">
</p>

The reconstruction task encourages the model to learn structural characteristics of EEG signals without relying directly on classification labels.

---

## SSL Pre-training Analysis

To evaluate the representations learned through Self-Supervised Learning, layer-wise features were compared between:

- **Random Initialization**
- **SSL Pre-trained Initialization**

The comparison was performed across the Spatial representation, Block 1, and Block 2.

<p align="center">
  <img src="results/ssl_pretraining_layerwise_performance.png"
       alt="SSL Pretraining Layer-wise Performance"
       width="1000">
</p>

### Layer-wise Accuracy Comparison

| Task | Layer | Random Init | SSL Pre-trained |
|---|---|---:|---:|
| **Motor Imagery** | Spatial | 36.5% | 45.5% |
| | Block 1 | 42.4% | 45.5% |
| | Block 2 | 46.2% | 51.0% |
| **Emotion** | Spatial | 58.9% | 60.8% |
| | Block 1 | 62.7% | 67.8% |
| | Block 2 | 63.7% | 69.3% |
| **Focus** | Spatial | 59.1% | 64.6% |
| | Block 1 | 65.3% | 70.1% |
| | Block 2 | 66.7% | 75.0% |

Across the evaluated representations, the SSL pre-trained initialization produced higher downstream accuracy than random initialization in the reported experiments.

---

## Experimental Results Summary

The experiments evaluate the proposed architecture from multiple perspectives:

| Experiment | Purpose |
|---|---|
| **Validation Accuracy** | Evaluate overall classification performance |
| **Macro F1-Score** | Evaluate balanced classification performance across classes |
| **Confusion Matrix** | Analyze class-level prediction behavior |
| **Ablation Study** | Evaluate contributions of individual architecture components |
| **SSL Reconstruction** | Analyze self-supervised EEG representation learning |
| **Layer-wise SSL Analysis** | Compare SSL pre-training against random initialization |

These experiments provide both classification-level and representation-level analysis of the proposed architecture.

---

## Technologies

The project involves:

- Python
- Jupyter Notebook
- Artificial Intelligence
- Machine Learning
- Deep Learning
- Mamba / BiMamba
- Spatial Attention
- Self-Supervised Learning
- EEG Signal Processing
- Signal Reconstruction
- Brain-Computer Interface

---

## Project Structure

```text
Spatial-Attention-Bimamba-EEG-Classification/
│
├── results/
│   ├── validation_performance_curves.png
│   ├── confusion_matrices.png
│   ├── ablation_study_accuracy.png
│   ├── ssl_eeg_signal_reconstruction.png
│   └── ssl_pretraining_layerwise_performance.png
│
├── .gitignore
├── README.md
├── BiMamba_FINAL_v16.ipynb
└── requirements.txt
```

### File Description

- `README.md` — Complete project documentation and experimental overview.
- `BiMamba_FINAL_v16.ipynb` — Main experimental notebook containing the model implementation, training, and evaluation pipeline.
- `requirements.txt` — Python dependencies required to run the project.
- `results/` — Experimental results and visualization outputs.

---

## Project Context

This project was developed as part of a collaborative student research initiative under **Program Kreativitas Mahasiswa (PKM)**.

The research investigates modern deep learning approaches for EEG signal analysis by combining spatial modeling, attention mechanisms, Mamba-based sequence modeling, and Self-Supervised Learning.

This repository documents the experimental implementation and research process and is maintained as part of my academic and Artificial Intelligence / Machine Learning portfolio.

---

## Contribution

This research was conducted collaboratively as part of a student research team.

My involvement includes participation in the development, experimentation, implementation, and evaluation of the EEG classification research pipeline and the **Spatial Attention BiMamba** approach.

> Individual contributions are presented within the context of a collaborative research project.

---

## Project Status

**Research / Experimental Project**

The repository represents the experimental implementation developed during the research process. The architecture and evaluation pipeline may continue to be refined as further experiments are conducted.

---

## Research Areas

`EEG` · `Artificial Intelligence` · `Machine Learning` · `Deep Learning` · `Mamba` · `BiMamba` · `Spatial Attention` · `Self-Supervised Learning` · `Brain-Computer Interface`

---

## Author

**Putra Khaeran Shauma**

Computer Science Student  
Universitas Jenderal Achmad Yani

**Interests:** Software Engineering · Artificial Intelligence · Machine Learning · Deep Learning
